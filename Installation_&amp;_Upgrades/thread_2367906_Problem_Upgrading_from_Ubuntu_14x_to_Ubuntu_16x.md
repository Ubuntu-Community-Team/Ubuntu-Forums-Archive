---
title: "Problem Upgrading from Ubuntu 14x to Ubuntu 16x"
date: 2017-08-04
forum: Installation &amp; Upgrades
---

### Post by napoloso on 2017-08-04
Hello everyone, 
I'm new to Ubunto, slowly leaving windows and getting familiarized with Ubuntu. I installed Ubuntu 14.xx something I forgot the exact version,  after playing with it for a few days I got a notification to upgrade to Ubuntu 16, so I clicked Yes, let it download, started the installation, and after some 40 minutes or so, my laptop overheated and shut down in the middle of the installation process.  I turned it back on but nothing would load, just a black screen.  

I looked on youtube for a tutorial on how to recover the instalation or go back to the previous one I had, but it didn't work. I would like to ask you guys if there's a way to restore my previous version of Ubuntu, or something. I would really appreciate it if you point me to a tutorial or a tool. I don't mind reformatting my drive and reinstalling ubuntu 14 then upgrading again. But if there's a way to fix it I'd like to learn. 

Thanks in advanced for your help.

---

### Post by deadflowr on 2017-08-04
Possible fix is to 
1)Turn on computer.

2)After the Machines first screen appears (the one that usually says the machine name, or Brand) press the shift button, or if this is a new machine you might need to press the ESC key;
this need to be done as soon as that first Brand/Machine name screen goes black)
Hopefully this will bring up the Boot menu.

3)In here go to Advanced Options.
In Advanced Options go to Any of the options which lists a (recovery mode)
Select recovery mode and hit enter.

4)In the recovery mode main window go to Enable Networking
Hopefully it can actual enable you networking setup.

5)if networking is successfully enabled go to Root Shell and hit enter.

6)Now in the root shell inpuit these commands
```
apt-get update
apt-get dist-upgrade
apt-get install -f
```
and 
then 
```
reboot
```
This will be about the best you can do.
If it fails at any point your probably better off reinstalling.

If the original install is 14.04 then no need to run the upgrade immediately, that is still supported for 2 more years. No rush.
So you can ignore the upgrade and play around with 14.04 until you feel more understanding or comfortable with it.

---

### Post by Autodave on 2017-08-04
Or, if you are going to do a reinstall anyway, download 16.04: it is the latest long term servoce (LTS) release and will be supported for 5 years since its release (April, 2016).

---

### Post by napoloso on 2017-08-06
> **deadflowr said:**
> Possible fix is to 
1)Turn on computer.

2)After the Machines first screen appears (the one that usually says the machine name, or Brand) press the shift button, or if this is a new machine you might need to press the ESC key;
this need to be done as soon as that first Brand/Machine name screen goes black)
Hopefully this will bring up the Boot menu.

3)In here go to Advanced Options.
In Advanced Options go to Any of the options which lists a (recovery mode)
Select recovery mode and hit enter.

4)In the recovery mode main window go to Enable Networking
Hopefully it can actual enable you networking setup.

5)if networking is successfully enabled go to Root Shell and hit enter.

6)Now in the root shell inpuit these commands
```
apt-get update
apt-get dist-upgrade
apt-get install -f
```
and 
then 
```
reboot
```
This will be about the best you can do.
If it fails at any point your probably better off reinstalling.

If the original install is 14.04 then no need to run the upgrade immediately, that is still supported for 2 more years. No rush.
So you can ignore the upgrade and play around with 14.04 until you feel more understanding or comfortable with it.

Hello and thanks for your quick reply. I got to step 6. For some reason it looked like it was downloading something but then I got an error message. I think I will just reinstall everything. But I appreciate your help.

---

### Post by napoloso on 2017-08-06
> **Autodave said:**
> Or, if you are going to do a reinstall anyway, download 16.04: it is the latest long term servoce (LTS) release and will be supported for 5 years since its release (April, 2016).

Thanks for your suggestion I will look into that.

---

