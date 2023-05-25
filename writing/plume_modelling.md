## Plume modelling

We use the one-dimensional plume model originally formulated by Bowen and ?
(1956), modified for ice-ocean interactions by Jenkins (1992?) and used in
numerous applications in glacier-ocean environments (REFS). We use the
model as formulated in Jenkins (2019): a line plume where melt is
parameterized with the three-equation formulation. The conservation equations for
buoyancy, momentum, heat and salinity fluxes were integrated using the RK45
method of the initial value problem solver from the *scipy.integrate* module.
The output is used to analyse profiles of plume properties as well as neutral
depth, DN, and minimal depth, DM. Neutral depth is taken as the depth where
plume and ambient density temperature are equal to within 10^X. Mimimal plume
depth is taken as the depth where the plume upward momentum is zero to within  10^X.
The plume is initialized with a freshwater flux at the grounding line, with
minimum values 10^X m2s-1 representing near-zero freshwater runoff, and 10^X
representing a maximum runoff through a relatively narrow area of 100 m. We
assumed a grounding line depth of 100 m, representative of the grounding like
depth in Hartogbukta based on bathymetry. Ambient
ocean and salinity was prescribed as detailed below. The Python program package used to perform the experiments can be
found
at
*https://github.com/oyvlun/ice_ocean_plume*. 

#### Idealized ambient ocean profiles

We took the records from M1-1 and M1-3, when three 

Between the top and bottom of the three sensors, we assumed a functional form *y
= ad^n + b*, with *d* being depth and *a, b,* and *n* being free parameters
determined analytically. *n* was restricted to the range [0.25, 3]. Above the
top sensor, we assumed uniform temperature but a 0.2% reduction in salinity in
order to represent a weak but stable salinity stratification. 

<img src="images/ambient_function_example.png"  width="405" height="250">

*Example of ambient temperature and salinity profiles (lines) generated from
three made-up data points (dots)*.

In a few cases when the water column was nearly uniformly stratified. and
occasionally . The difference was in most cases within the manufacturer
specified accuracy for salinity. Whether or not static instabilities did occur 
during these periods, we assumed a statically stable or neutral water column by 
introducing a small decrease in salinity at the top sensor until the value of
sigma0 was smaller near 20 m than near 100 m. 