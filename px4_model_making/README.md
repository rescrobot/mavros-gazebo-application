## ● Making new models requires 
  + Model making
  + gain tuning

<br>

### ● Making new model
  + refer [here](https://discuss.px4.io/t/create-custom-model-for-sitl/6700/4), belows are copy-pasted from the link.
    + Create a folder under Tools/sitl_gazebo/models for your model, let’s call it my_vehicle
    + Create the following files under Tools/sitl_gazebo/models/my_vehicle: model.config and my_vehicle.sdf 
      + these can be based off the iris or solo models in Tools/sitl_gazebo/models
    + Create a world file in Tools/sitl_gazebo/worlds called my_vehicle.world 
      + Again, this can be based off the iris or solo world files
    + Create an airframe file under ROMFS/px4fmu_common/init.d-posix 
      + Yet again, this can be based off the iris or solo airframe files
    + give it a number and name it number_my_vehicle
    + Add the airframe name to the file platforms/posix/cmake/sitl_target.cmake in the command set -> models …
  + Now you are free to tweak any of the model values in the SDF file and any of the controller gains in the airframe file.
  + You can launch SITL with your model with 
  ~~~shell
  $ make px4_sitl gazebo_my_vehicle
  ~~~
  1. When increasing the mass of the vehicle, also increase the inertias. I found that Gazebo does not like really small inertias.
  2. With the larger vehicle, tweak the motor values
  3. If the quad is unstable, it is probably due to bad controller gains. Tweak them for the larger vehicle.

<br>

### ● Gain tuning
  + refer [here](https://docs.px4.io/v1.9.0/en/config_mc/pid_tuning_guide_multicopter.html)