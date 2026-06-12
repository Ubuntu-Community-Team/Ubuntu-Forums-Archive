---
title: "New 9.10 Install on T40 Incessantly Freezes"
date: 2010-03-19
forum: Installation &amp; Upgrades
---

### Post by insomniac99 on 2010-03-19
I installed 9.10 using the standard download.  Installation seemed to have gone fine.  However, the system hasn't been usable since.  Every time I try opening any application, Firefox, Open Office or whatever, the system freezes.  I don't get any error messages.  Just a frozen screen.  First experience with Linux.  Any help would be very much appreciated.

My machine is an IBM ThinkPad T40 with 2GB RAM and the Radeon 9000.

---

### Post by tgalati4 on 2010-03-19
Does it freeze opening any applications when booting from the Live CD?

---

### Post by insomniac99 on 2010-03-19
> **tgalati4 said:**
> Does it freeze opening any applications when booting from the Live CD?

Does that mean booting from the installation CD and choosing "try ubuntu before installing"?  If so, then yes, same freeze occurs.

---

### Post by tgalati4 on 2010-03-19
So we have established that your computer freezes whether you boot from Live CD or from your hard disk.

The title of your post implies that there is something wrong with your installation.  Perhaps it is a hardware problem that is causing the freeze.

T4X series thinkpads are known to have issues with the GPU delaminating due to heat, flexing, and perhaps poor soldering.  When you open any applications, the graphics chip heats up causing it to lift off of the board--instant freeze.

Boot your machine into rescue mode.  This will give you a root console--no graphics.  See how long it runs in that mode.  If it runs overnight, then you can be reasonably sure that your machine has developed a graphics problem.

Run sensors to see temperatures:

sensors

If not installed: (presumably in are in a root console)

apt-get install lm-sensors

Go through the configuration.

Post the output:

On a T43p you will get something like:

tgalati4@tpad-Gloria7 ~ $ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +50.0°C  (crit = +99.0°C)                  

thinkpad-isa-0000
Adapter: ISA adapter
fan1:       4675 RPM
temp1:       +50.0°C                                    
temp2:       +48.0°C                                    
temp3:       +37.0°C                                    
temp4:       +59.0°C                                    
temp5:       +36.0°C                                    
ERROR: Can't get value of subfeature temp6_input: Can't read
temp6:        +0.0°C                                    
temp7:       +25.0°C                                    
ERROR: Can't get value of subfeature temp8_input: Can't read
temp8:        +0.0°C                                    
temp9:       +48.0°C                                    
temp10:      +54.0°C                                    
temp11:      +48.0°C                                    
ERROR: Can't get value of subfeature temp12_input: Can't read
temp12:       +0.0°C                                    
ERROR: Can't get value of subfeature temp13_input: Can't read
temp13:       +0.0°C                                    
ERROR: Can't get value of subfeature temp14_input: Can't read
temp14:       +0.0°C                                    
ERROR: Can't get value of subfeature temp15_input: Can't read
temp15:       +0.0°C                                    
ERROR: Can't get value of subfeature temp16_input: Can't read
temp16:       +0.0°C  

-----------------

There are 9 temperature sensors on this machine.  Yours will probably have less.  IBM added sensors as they discovered the heating issues.

The GPU will be the hotest chip (59C in this case).  

------------

Does this machine dual-boot into Windows?  If so, does it freeze in Windows?

Check [http://thinkwiki.org](http://thinkwiki.org)  for other weirdness of the T40 on linux.

---

### Post by insomniac99 on 2010-03-19
I will try the steps you've outlined.  I can add that I had Windows XP and then Windows 7 (up until today) installed on this machine with no problems, software or hardware.  I'll report back.  Thanks for your help.

---

### Post by tgalati4 on 2010-03-19
From thinkwiki:

In some models (At least the T40 with 9000 pro) the problem dissapear if you make an underclock. The default clock of the Mobility 9000 pro is 250mhz in the core and 200mhz in the memory. If you lower the core clock to 100mhz the problem dissapear. In Linux you can use a tool called rovclock [1] to make the underclock. (Example for a Mobility 9000: rovclock -c 100 -m 200) 

sudo apt-get install rovclock

Try underclocking the graphics chip to see if it lasts a little longer.

If it does seem a little more stable at the slower clock speed, then try adding some fan control:

sudo apt-get install tpfan-admin
tpfan-admin

---

### Post by d3v1150m471c on 2010-03-19
Check the disk for errors after you boot to the live cd.

---

### Post by tgalati4 on 2010-03-20
Finally, make sure you use the open driver--radeon.  There may be issues with the proprietary ATI (fglx) driver under 9.10.  This may be fixed under Lucid, not sure though. 

Although if it freezes from the Live CD, they it only uses the open source ATI driver--so that's probably not the issue.

---

### Post by insomniac99 on 2010-03-20
> **tgalati4 said:**
> Finally, make sure you use the open driver--radeon.  There may be issues with the proprietary ATI (fglx) driver under 9.10.  This may be fixed under Lucid, not sure though.

Thanks again, where can I get that?

---

### Post by insomniac99 on 2010-03-20
Ok, an update.  I couldn't get my machine to go to the screen where I can choose Recovery Mode.  So I just booted from the installation CD excepted I chose the Safe Graphics mode.  Everything seems to be working fine this way.  So it seems somewhat safe to assume that the graphics card is the issue.  What would be the best order in which to try some of the graphics card-related suggestions?  Trying the different driver seems like a logical start to me but I don't know how to find that (I don't know exactly what I'm looking for).

---

### Post by insomniac99 on 2010-03-20
> **tgalati4 said:**
> From thinkwiki:

In some models (At least the T40 with 9000 pro) the problem dissapear if you make an underclock. The default clock of the Mobility 9000 pro is 250mhz in the core and 200mhz in the memory. If you lower the core clock to 100mhz the problem dissapear. In Linux you can use a tool called rovclock [1] to make the underclock. (Example for a Mobility 9000: rovclock -c 100 -m 200) 

sudo apt-get install rovclock

Try underclocking the graphics chip to see if it lasts a little longer.


Installed rovclock but when I try the "rovclock -c 100 -m 200" command, I get an I/O error.

---

### Post by tgalati4 on 2010-03-20
The settings could be too slow for your motherboard.  Try different settings:

rovclock -c 150 -m 200
rovclock -c 175 -m 200
rovclock -c 200 -m 200

The fact that you can't boot properly to the GRUB screen suggests that your graphics chip has delaminated.  It may be just a coincidence that it happened while installing Ubuntu.  Try to reload windows and see how far you get.

As far as the open source radeon driver, there is nothing to install, it's used by default.  Check the log file:

cat /var/log/Xorg.0.log

---

### Post by insomniac99 on 2010-03-20
So I'm able to get into recovery mode just fine now and it's stable in that mode.  Just had bad instructions beforehand.

All of the clock commands result in "Error getting I/O permissions (root?)."

---

### Post by tgalati4 on 2010-03-20
sudo rovclock -c 100 -m 200

---

### Post by insomniac99 on 2010-03-21
My temps:

acpitz-virtual-0
Adapter: Virtual device
temp1: +42.0 C (crit = +93.0 C)

thinkpad-isa-0000
Adapter: ISA adapter
fan1: 2923 RPM
temp1: +42.0 C
temp2: +46.0 C
temp3: +36.0 C
temp4: +48.0 C
temp5: +36.0 C
ERROR: Can't get value of subfeature temp6_input: Can't read
temp6: +0.0 C
temp7: +32.0 C
ERROR: Can't get value of subfeature temp8_input: Can't read
temp8: +0.0 C

---

### Post by tgalati4 on 2010-03-21
Your temperatures are low and appear reasonable.  I'm guessing temp4 is the GPU.  You can install tpfan to visually see all of the sensors.  This presumes that your graphical environment is now stable:

sudo apt-get install tpfan-admin

tpfan-admin

My T43p runs hotter than most T4X series.  The tpfan fan control software is helpful for having multiple sensors trigger higher fan speeds to avoid overheat problems.

So is your more stable now?

---

### Post by insomniac99 on 2010-03-22
> **tgalati4 said:**
> So is your more stable now?

I'm having trouble getting the tpfan to install.  It's giving me some error that it could not find it.

Unfortunately, I seem to be in the same boat as before.  To summarize, stable in 1) recovery mode 2) installation CD boot in safe graphics mode.  Unstable in 1) regular boot 2) installation CD boot in regular mode.  Crashes when I try to open an app.  I can open and set most system settings just fine though.

I've run the rovclock and my temps never seem too high.

---

### Post by tgalati4 on 2010-03-22
apt-cache search tpfan

sudo apt-get install tpfan-admin tpfand tpfand-profiles

I'm out of ideas at this point.  Because of known graphics chip failures, it's hard to recommend a course of action.  I would sell the machine for parts on craigslist.org or reinstall windows and use it if it works OK.  I'm running Linux Mint 7 on my T43p.  So one final thing to try is to load jaunty or linux mint 7.

---

### Post by insomniac99 on 2010-03-22
I keep getting:

E: Couldn't find package tpfan-admin

I appreciate your help.  I guess I have to try reinstalling Windows at this point to find out for sure if it's a hardware issue.

---

### Post by insomniac99 on 2010-03-23
Is it worth trying beta 10?  Or does it sound like I'm better off going back to Windows at this point?

---

### Post by insomniac99 on 2010-03-25
Just because reinstalling Windows is such a time commitment, I decided to try the 10 beta.  Lo and behold, the system is now completely stable.  No crashes.  So happy ending even if we never figured out what went wrong with 9.10.  Thanks for your help.

---

