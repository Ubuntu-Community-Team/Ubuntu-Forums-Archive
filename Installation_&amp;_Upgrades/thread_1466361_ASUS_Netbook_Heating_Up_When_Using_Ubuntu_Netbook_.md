---
title: "ASUS Netbook Heating Up When Using Ubuntu Netbook 10.04"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by bme on 2010-04-30
I installed Ubuntu Netbook 10.04 and immediately noticed the keyboard of my eeepc 1000HE was abnormally warm. Since I dual boot XP I booted to XP and found the fan running faster to compensate for the previous heat. This did not happen on Ubuntu-the fan just was barely running. I had to place the side of the netbook in order to feel the fan running.
I issued "sensors" in terminal and it showed 67 degrees C for the cpu temp.
What is wrong? Is the latest Ubuntu such a resource hug that it heats up the CPU?

---

### Post by ajgreeny on 2010-04-30
I can't speak about the ASUS you have but there have been a lot of problems with laptops running very hot if using the open source ATI driver for ATI graphic cards.  Perhaps your hot running is just another example of that.

It has stopped me using Lucid on my old laptop, which gets unbearably hot with Lucid, but runs beautifully cool with jaunty or Karmic.  I hope the problem is sorted soon as it is a show stopper for me, and I really did want to love Lucid.  I do have a desktop which seems to run Lucid OK, even though it has an ATI card with that same driver, but I think desktops seldom have the same heat problems as laptops.

---

### Post by bme on 2010-05-01
The asus 1000he uses intel not ATI for the display...I am sorry to say that I have removed ubuntu for the time being as I don't want my netbook to cook while using ubuntu.......

---

### Post by iponeverything on 2010-05-01
> **bme said:**
> 
What is wrong? Is the latest Ubuntu such a resource hug that it heats up the CPU?

It's not a hog. These types of issues are almost always issues with drivers interacting with particular hardware. You might want to watch launchpad for bugs related to the 1000HE, also check to see if there is a bios update available for your unit.

---

### Post by bme on 2010-05-01
yes I did file overheating issue as a bug under ubuntu netbook on launchpad.I believe it has something to do with acpi thermal trip point set too high(mine at 85 C and 82C,active and passive ,resp). Since 8.04 they have removed the ability to change the trip points.
This has been a complaint filed on similar bugs since January 2010.

---

### Post by jack_mccauley on 2010-05-03
I am having the same problem with overheating with my 1000he under Lucid Lynx.  The system maintains a usable temp under both Windows XP and Karmic but under Lucid Lynx it will heat up to the point of shutdown in under an hour.

---

### Post by jako on 2010-05-03
My understanding is that heat problems are caused by the open source drivers not dealing with power management well and that this will be fixed in the .35 kernel and consequent Xorg upgrades. This is certainly the case for my X1600 ATI laptop. My inten G855 laptop doesn't suffer from heat due to Intel drivers - they don't work at all, rather it's using Vesa drivers which causes extra heat there.

---

### Post by t1010011 on 2010-05-06
I'm experiencing the same problem with a 1000he. 

The fan runs with a constant speed even if keyboard and bottom of the netbook start getting hot...

Anyone knows any work around or fix to this? I'm afraid to be damaging the machine.

---

### Post by aldeby on 2010-05-22
I experience this issue too, although I cannot say it's strictly related to Ubuntu Lucid. 
Karmic has shipped during the winter season, this detail should be taken into consideration!

here is my ```
sensors
``` output

```
#sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +75.0°C  (crit = +85.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +46.0°C  (crit = +90.0°C)                  

```

could anyboby post his output too?

---

### Post by t1010011 on 2010-05-22
I think I partially solved the problem... Right now my sensors output is:

```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +51.0°C  (crit = +85.0°C)                  

eeepc-isa-0000
Adapter: ISA adapter
fan1:       1230 RPM

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +17.0°C  (crit = +90.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +17.0°C  (crit = +90.0°C) 
```

also if of any relevance, the ambient temperature is about 20 Celsius and I have the netbook on for about 30 minutes...

 I did  two things, the first I'm not sure if interfere in the problem, but since it fixes  some nasty issues with the fn keys no bad to post it here:

```
gksudo gedit /etc/default/grub
```

change the line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"
```

and then run:

```
sudo update-grub
```

restart

I was told that this should inform to the 1000he bios that OS is linux based and a small fix for the brightness fn keys,

Then the second thing was to play a  bit with fancontrol, installed by default in Lucid...

```
sudo sensor-detect
```

pressing yes and enter whenever required...
then I verified if it had added the coretemp driver in the modules

```
gksudo gedit /etc/modules
```

if not, just add the line:

```

# Chip drivers
coretemp

```

Then restarted again, and:

```
sudo pwmconfig
```

I run the required tests and when it gave me some options to configure, pressed 5:

```
Common Settings:
INTERVAL=10

Settings of hwmon1/pwm1:
  Depends on 
  Controls 
  MINTEMP=
  MAXTEMP=
  MINSTART=
  MINSTOP=
```

then chose 1 twice:
```
1) hwmon1/pwm1	
```
```
1) hwmon0/temp1_input
```

it let me configure some voltage parameters for the fan a certain temperatures. My final configuration was:

```
Common Settings:
INTERVAL=10

Settings of hwmon1/pwm1:
  Depends on hwmon0/temp1_input
  Controls hwmon1/fan1_input
  MINTEMP=20
  MAXTEMP=60
  MINSTART=90
  MINSTOP=20
  MINPWM=20
  MAXPWM=225
```

but I strongly recommend to play a bit with this values to chose the ones that work best for you, also I'm no expert, I might be reducing the life of my fan or worst my CPU (I'd be glad if someone who understands about this to give me some advice here...)

then
```
 4) Save and quit
```

and finally

```
sudo /usr/sbin/fancontrol &
```

witch took some time, to add it to startup
and restarted once again...

some doubts I still have, if i want to reconfigure with pwmconfig, get the error:
```
File /var/run/fancontrol.pid exists. This typically means that the
fancontrol deamon is running. You should stop it before running pwmconfig.
If you are certain that fancontrol is not running, then you can delete
/var/run/fancontrol.pid manually.
```

I don't know how to stop it, so I usually delete the pid file and restart... 
```
sudo rm /var/run/fancontrol.pid
```
but i don't know if that is correct thing to do...

then other issue is when run:
```
fancontrol
```
gives at the very bottom it shows:
```
Error: file hwmon1/pwm1 doesn't exist

```
how could this be? How it's reading the temperature them?



hope it helps, as I hope someone can help me...

---

### Post by Sandy Al on 2010-06-08
Hate to say it, but this 'hotness' has happened with both a Dell Mini 1012 and a hp tc1100 tablet pc that I have put UNE on.

The mini has no 'hot' issues with Window7, and the tc1100 didn't have any 'hot' issues when running karmic.

---

### Post by shadowclic on 2010-07-24
My toshiba satellite which also is running an ATI card had overheating issues. A simple fix for this was to use proprietary drivers instead of open source drivers. 

By going to System, administration, hardware drivers. It will automatically search for drivers, and should return an ATI proprietary driver. At the bottom of the window it should say something about this driver not being active, and have an option to enable the driver. Enable the driver and after installing, reboot the computer. 

My computer went from extreme hot (the card could burn me if I kept my hand there for too long) to so cool it felt like normal air coming off the card (the breeze from the fan feels cool :wink:) It ran even cooler than it did under windows!

Hope this helps!

---

### Post by aldeby on 2011-01-11
Hi t1010011, 
Thank you for your interesting post sharing your experience!

> **t1010011 said:**
> also I'm no expert, I might be reducing the life of my fan or worst my CPU (I'd be glad if someone who understands about this to give me some advice here...)

CPUs generally speaking have a very high tolerance towards high temperatures. For instance the Intel Atom is stated by lm-sensors to bear a maximum temperature of 90C which is far higher than those ever reported by its sensors. In your case that was 17C!

What concerns me are two things:
1) acpitz-virtual-0 
temp1:       +51.0°C  (crit = +85.0°C)
this sensor apparently always reports a very high temperature also on my friend's 1000he laptop. It often surpasses 60C... but the value reported must be fake since its temperature is ~ 50C even 5 seconds after resuming from suspend, which is highly unlikely. There should be some positive offset set.
2) the coretemp-isa-0000 should be the one reported by the CPU internal sensor. It is ugually very low, however sometimes it reports a NEGATIVE temperature! (eg. -2.0°C ). This leads me to think this one may suffer from a negative offset too.

> **t1010011 said:**
> 
some doubts I still have, if i want to reconfigure with pwmconfig, get the error:
```
File /var/run/fancontrol.pid exists. This typically means that the
fancontrol deamon is running. You should stop it before running pwmconfig.
If you are certain that fancontrol is not running, then you can delete
/var/run/fancontrol.pid manually.
```

I don't know how to stop it, so I usually delete the pid file and restart... 
```
sudo rm /var/run/fancontrol.pid
```
but i don't know if that is correct thing to do...


This is because the fancontrol service is running!
Deleting the .pid is not the correct approach, instead you should type in the terminal shell:
```
 service fancontrol stop
```

> 
then other issue is when run:
```
fancontrol
```
gives at the very bottom it shows:
```
Error: file hwmon1/pwm1 doesn't exist

```
how could this be? How it's reading the temperature them?


This is another issue my friend also experiences with this laptop model. The path to the device sensors very often changes without a reason and you have to re-run pwmconfig. 
Some users have reported this issue is correlated to other temperature kernel modules competing for the sensors interface. You may check whether in /etc/modules you have other useless modules listed for manual loading other than the only one you need on the eeepc 1000he: 
```
coretemp
```

---

### Post by johncc on 2011-01-11
> **t1010011 said:**
> 
and finally

```
sudo /usr/sbin/fancontrol &
```

witch took some time, to add it to startup
and restarted once again...

some doubts I still have, if i want to reconfigure with pwmconfig, get the error:
```
File /var/run/fancontrol.pid exists. This typically means that the
fancontrol deamon is running. You should stop it before running pwmconfig.
If you are certain that fancontrol is not running, then you can delete
/var/run/fancontrol.pid manually.
```

I don't know how to stop it, so I usually delete the pid file and restart... 
```
sudo rm /var/run/fancontrol.pid
```
but i don't know if that is correct thing to do...



After pwmconfig all you need to do is
```
sudo service fancontrol restart
```

to get it to use the new parameters (in /etc/fancontrol).

Cheers,
John

---

