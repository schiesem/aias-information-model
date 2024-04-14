### ODPs
- BBG needs to be described
- EKI needs to be describes


### Example Use Case
The use case is based on a stamping process done by a stamping machine. The business goal of the use case is to reduce the maintenance costs of the stamp machine. The mentioned stamping machine is used to stamp parts out of blank metal sheets for the automobile industry. The machine consists of a support frame, a fixed lower die and a movable upper die. The upper die is moved by an electric motor, which is mounted on the support frame. The driving force is transmitted via a drive belt and the position of the upper die is measured via a positional sensor. Over time, the drive belt wears out, which leads to the upper die no longer being controlled with sufficient precision. As a result, parts being produced are often unable to satisfy the strict tolerance requirements. For this reason, the drive belt is currently replaced regularly at fixed intervals, but this maintenance strategy results in high maintenance costs. Therefore, the business goal of the use case is to reduce the maintenance costs of the stamping machine by gradually classifying the drive belt condition.

### Description of the Developed AI Application
Some experiments have shown that a worn drive belt causes the upper die to oscillate when it is positioned. Based on that, the measured positioning values recorded during the stamping process by the sensors can be used to infer the belt wear condition. The sensors transmit its data to a controller via a bus network. For the analysis of this position data, an AI application was developed based on a neuronal network. The neural network was trained in a cloud and deployed to an edge device, where the inference is also done. The edge device is connected via a local area network with the controller of the stamp machine. The edge device is also connected via internet with the cloud.


### List of Modeled Elements

#### Components
- AIAS:Sensor <ins>ex:PositionSensor</ins>
- AIAS:Actuator <ins>ex:ElectricMotor</ins>
- AIAS:Controller <ins>ex:SiemensS7</ins>
- AIAS:EdgeDevice <ins>ex:RaspberryPI4</ins>
- AIAS:Cloud <ins>ex:Azure</ins>
- VDI3682:Product <ins>ex:MetalPlate</ins>
- VDI3682:Product <ins>ex:StampedPart</ins>

#### Functions
- ISO22989:Automate (subclassOf:Function)<ins>ex:StampPositionAutomation</ins>
- ISO22989:Normalization (subclassOf: DataProcess) <ins>ex:DataNormalization</ins>
- ISO22989:Merging (subclassOf: DataProcess) <ins>ex:DataMerging</ins>
- ISO22989:Storage (subclassOf:Function)<ins>ex:CloudStorage</ins>
- ISO22989:Acquisition (subclassOf:Function)<ins>ex:PositionDataRecord</ins>
- ISO22989:Acquisition (subclassOf:Function)<ins>ex:TimeDataRecord</ins>
- ISO22989:Validation (subclassOf:Function)<ins>ex:ModelValidation</ins>
- ISO22989:Evaluation (subclassOf:Function) <ins>ex:ModelEvaluation</ins>
- ISO22989:Training (subclassOf:Function) <ins>ex:ModelTraining</ins>
- ISO22989:Inference (subclassOf:Function) <ins>ex:ModelInference</ins>
- ISO22989:Prediction (subclassOf:Function) <ins>ex:ModelPrediction</ins>
- AIAS:Process (subclassOf:Function) <ins>ex:StampingProcess</ins>

#### Relations
- ISO7489:Communication <ins>ex:ControllerSensorCom</ins>
- ISO7489:Communication <ins>ex:ControllerActuatorCom</ins>
- ISO7489:Communication <ins>ex:ControllerEdgeDevCom</ins>
- ISO7489:Communication <ins>ex:EdgeCloudCom</ins>
- VDI3682:Flow <ins>ex:StampInput</ins>
- VDI3682:Flow <ins>ex:StampOutput</ins>
- ISO7489:Assignment <ins>ex:AutomateDeployment</ins>
- ISO7489:Assignment <ins>ex:NormalizationDeployment</ins>
- ISO7489:Assignment <ins>ex:StorageDeployment</ins>
- ISO7489:Assignment <ins>ex:AcquisitionDeployment</ins>
- ISO7489:Assignment <ins>ex:ValidationDeployment</ins>
- ISO7489:Assignment <ins>ex:EvaluationDeployment</ins>
- ISO7489:Assignment <ins>ex:TrainingDeployment</ins>
- ISO7489:Assignment <ins>ex:InferenceDeployment</ins>
- ISO7489:Assignment <ins>ex:ProcessDeployment</ins>
- ISO7489:Assignment <ins>ex:TimeDataRecordDeployment</ins>
- ISO7489:Assignment <ins>ex:PositionDataRecordDeployment</ins>
- ISO7489:Assignment <ins>ex:DataMergingDeployment</ins>

#### ISO 22989 Elements
- ISO22989:AISystem <ins>ex:PredictiveMaintenanceStamp</ins>
- ISO22989:Classification (subclassOf:Task) <ins>ex:BeltWearConditionClassification</ins>
- ISO22989:MLModel <ins>ex:BeltWearConditionModel</ins>
- ISO22989:MLAlgorithm <ins>ex:LongShortTermMemoryNetwork</ins>
- ISO22989:Modelparameter <ins>ex:InputLayer</ins>
- ISO22989:Modelparameter <ins>ex:HiddenLayer1</ins>
- ISO22989:Modelparameter <ins>ex:HiddenLayer2</ins>
- ISO22989:Modelparameter <ins>ex:OutputLayer</ins>
- ISO22989:Modelparameter <ins>ex:Sigmoid</ins>
- ISO22989:MachineLearning <ins>ex:MachineLearning</ins>
- ISO22989:SupervisedLearning (subclassOf:LeaningType) <ins>ex:SupervisedLearning</ins>
- ISO22989:GradientDescent (subclassOf: OptimizingMethod) <ins>ex:GradientDescent</ins>
- ISO22989:Hyperparameter <ins>ex:LearningRate</ins>
- ISO22989:Hyperparameter <ins>ex:BatchSize</ins>
- ISO22989:EvaluationMetric <ins>ex:Accuracy</ins>
- ISO22989:Sample <ins>ex:Postion</ins>
- ISO22989:Sample <ins>ex:Time</ins>
- ISO22989:TrainingData (subclassOf:Data) <ins>ex:TrainingData</ins>
- ISO22989:ValidationData (subclassOf:Data) <ins>ex:ValidationData</ins>
- ISO22989:EvaluationData (subclassOf:Data) <ins>ex:EvaluationData</ins>
- ISO22989:ProductionData (subclassOf:Data) <ins>ex:ProductionData</ins>
- ISO22989:DataSet <ins>ex:TrainingDataSet </ins>
- ISO22989:DataSet <ins>ex:ValidationDataSet </ins>
- ISO22989:DataSet <ins>ex:EvaluationDataSet </ins>

#### ISO 7489 Elements
- ISO7489:Name <ins>ex:EtherCAT</ins>
- ISO7489:Name <ins>ex:Internet</ins>
- ISO7489:Physical (subclassOf:Layer) <ins>ex:Physical</ins>
- ISO7489:DataLink (subclassOf:Layer) <ins>ex:DataLink</ins>
- ISO7489:Network (subclassOf:Layer) <ins>ex:Network</ins>
- ISO7489:Transport (subclassOf:Layer) <ins>ex:Transport</ins>
- ISO7489:Application (subclassOf:Layer) <ins>ex:Application</ins>
- ISO7489:Technology <ins>ex:1000BASE-TX</ins>
- ISO7489:Technology <ins>ex:Ethernet</ins>
- ISO7489:Technology <ins>ex:IP</ins>
- ISO7489:Technology <ins>ex:TCP</ins>
- ISO7489:Technology <ins>ex:http</ins>
- ISO7489:Technology <ins>ex:https</ins>