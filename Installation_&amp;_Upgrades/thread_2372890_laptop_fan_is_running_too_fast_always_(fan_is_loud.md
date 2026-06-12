---
title: "laptop fan is running too fast always (fan is loud), system temp is below trip points"
date: 2017-09-29
forum: Installation &amp; Upgrades
---

### Post by dimitrisdad on 2017-09-29
Installed Ubuntu 17.04 Gnome on an Lenovo Ideapad 510s. 

Tried to ignore this problem, but Yikes, my ears actually hurt from working in front of this laptop and the non-stop high speed fan. Also I'm using the machine to record audio and the fan is interfering sometimes - I would like to have a quiet base line on the spectrum to see where we are at.

As shown below from lm-sensor the temperature is not so high that the fan must be on.  The ambient temperature is quite low so the fan really should be on a very low speed. (I'm wearing a sweater in this room.)   Now I have heard the fan go faster, like a hair dryer on high, when the machine is number crunching, but that too seems excessive for the operating temperatures.  It seems the fan is overreacting, at least for my needs.

Note lm-sensor does not see the fan nor report the RPMs.  Perhaps this is indicative of the problem.  I've also checked thermal-conf.xml,  also shown below.  And the thermal zone trip points are higher than the current temps - yet the fan is running pretty high - not quite top.

Found the cpu specs,  its max operating temp is 100 C, so even the current trip points are conservative.  I would like to raise them some.  But that is another issue ..

--> How do I slow the fan, or have its minimum be zero instead of 'high' ?
```
> cat /proc/sys/kernel/version 
#39-Ubuntu SMP Wed Sep 13 07:46:59 UTC 2017

> lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 17.04
Release:    17.04
Codename:    zesty

> sensors
pch_skylake-virtual-0
Adapter: Virtual device
temp1:        +36.0°C  

acpitz-virtual-0
Adapter: Virtual device
temp1:        +38.0°C  (crit = +127.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Package id 0:  +37.0°C  (high = +100.0°C, crit = +100.0°C)
Core 0:        +35.0°C  (high = +100.0°C, crit = +100.0°C)
Core 1:        +36.0°C  (high = +100.0°C, crit = +100.0°C)

amdgpu-pci-0100
Adapter: PCI adapter
fan1:             N/A
temp1:            N/A  (crit =  +0.0°C, hyst =  +0.0°C)

> cat thermal-conf.xml

<?xml version="1.0"?>

<!--
use "man thermal-conf.xml" for details
-->

<!-- BEGIN -->
<ThermalConfiguration>
<Platform>
    <Name>Generic X86 Laptop Device</Name>
    <ProductName>EXAMPLE_SYSTEM</ProductName>
    <Preference>QUIET</Preference>
    <ThermalSensors>
        <ThermalSensor>
            <Type>TSKN</Type>
            <AsyncCapable>1</AsyncCapable>
        </ThermalSensor>
    </ThermalSensors>
    <ThermalZones>
        <ThermalZone>
            <Type>SKIN</Type>
            <TripPoints>
                <TripPoint>
                    <SensorType>TSKN</SensorType>
                    <Temperature>55000</Temperature>
                    <type>passive</type>
                    <ControlType>SEQUENTIAL</ControlType>
                    <CoolingDevice>
                        <index>1</index>
                        <type>rapl_controller</type>
                        <influence> 100 </influence>
                        <SamplingPeriod> 16 </SamplingPeriod>
                    </CoolingDevice>
                    <CoolingDevice>
                        <index>2</index>
                        <type>intel_powerclamp</type>
                        <influence> 100 </influence>
                        <SamplingPeriod> 12 </SamplingPeriod>
                    </CoolingDevice>
                </TripPoint>
            </TripPoints>
        </ThermalZone>
    </ThermalZones>
</Platform>

<!-- Thermal configuration example only -->
<Platform>
    <Name>Example Platform Name</Name>
    <!--UUID is optional, if present this will be matched -->
    <!-- Both product name and UUID can contain
        wild card "*", which matches any platform
     -->
    <UUID>Example UUID</UUID>
    <ProductName>Example Product Name</ProductName>
    <Preference>QUIET</Preference>
    <ThermalSensors>
        <ThermalSensor>
            <!-- New Sensor with a type and path -->
            <Type>example_sensor_1</Type>
            <Path>/some_path</Path>
            <AsyncCapable>0</AsyncCapable>
        </ThermalSensor>
        <ThermalSensor>
            <!-- Already present in thermal sysfs,
                enable this or add/change config
                For example, here we are indicating that
                sensor can do async events to avoid polling
            -->
            <Type>example_thermal_sysfs_sensor</Type>
            <!-- If async capable, then we don't need to poll -->
            <AsyncCapable>1</AsyncCapable>
        </ThermalSensor>
        <ThermalSensor>
            <!-- Examle of a virtual sensor. This sensor
                depends on other real sensor or
                virtual sensor.
                E.g. here the temp will be
                 temp of example_sensor_1 * 0.5 + 10
            -->
            <Type>example_virtual_sensor</Type>
            <Virtual>1</Virtual>
            <SensorLink>
                <SensorType>example_sensor_1</SensorType>
                <Multiplier> 0.5 </Multiplier>
                <Offset> 10 </Offset>
            </SensorLink>
        </ThermalSensor>

    </ThermalSensors>
    <ThermalZones>
        <ThermalZone>
            <Type>Example Zone type</Type>
            <TripPoints>
                <TripPoint>
                    <SensorType>example_sensor_1</SensorType>
                    <!-- Temperature at which to take action -->
                    <Temperature> 75000 </Temperature>
                    <!-- max/passive/active
                        If a MAX type is specified, then
                        daemon will use PID control
                        to aggresively throttle to avoid
                        reaching this temp.
                     -->
                    <type>max</type>
                    <!-- SEQUENTIAL | PARALLEL
                    When a trip point temp is violated, then
                    number of cooling device can be activated.
                    If control type is SEQUENTIAL then
                    It will exhaust first cooling device before trying
                    next.
                    -->
                    <ControlType>SEQUENTIAL</ControlType>
                    <CoolingDevice>
                        <index>1</index>
                        <type>example_cooling_device</type>
                        <!-- Influence will be used order cooling devices.
                            First cooling device will be used, which has
                            highest influence.
                        -->
                        <influence> 100 </influence>
                        <!-- Delay in using this cdev, this takes some time
                        too actually cool a zone
                        -->
                        <SamplingPeriod> 12 </SamplingPeriod>
                    </CoolingDevice>
                </TripPoint>

            </TripPoints>
        </ThermalZone>
    </ThermalZones>
    <CoolingDevices>
        <CoolingDevice>
            <!--
                Cooling device can be specified
                by a type and optionally a sysfs path
                If the type already present in thermal sysfs
                no need of a path.
                Compensation can use min/max and step size
                to increasing cool the system.
                Debounce period can be used to force
                a waiting period for action
            -->
            <Type>example_cooling_device</Type>
            <MinState>0</MinState>
            <IncDecStep>10</IncDecStep>
            <ReadBack> 0 </ReadBack>
            <MaxState>50</MaxState>
            <DebouncePeriod>5000</DebouncePeriod>
            <!--
                If there are no PID parameter
                compensation increase step wise and exponentaially
                if single step is not able to change trend.
                Alternatively a PID parameters can be specified
                then next step will use PID calculation using
                provided PID constants.
            -->>
            <PidControl>
                <kp>0.001</kp>
                <kd>0.0001</kd>
                <ki>0.0001</ki>
            </PidControl>
        </CoolingDevice>
    </CoolingDevices>
</Platform>
</ThermalConfiguration>
<!-- END -->
```

---

