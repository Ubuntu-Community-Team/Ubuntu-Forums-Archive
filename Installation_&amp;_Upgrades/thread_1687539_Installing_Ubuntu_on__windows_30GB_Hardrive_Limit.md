---
title: "Installing Ubuntu on  windows 30GB Hardrive Limit?"
date: 2011-02-14
forum: Installation &amp; Upgrades
---

### Post by grahambo2005 on 2011-02-14
Hi

Is it possible to increase the size of the Hard drive to 200GB when installing Ubuntu on top of Windows.

The Reason I ask it that I have a Laptop with a 500GB Hard drive, which has windows installed on it

Obviously I cannot create a new Partition on this drive to do a separate install.

30GB is just to small for what I want to do on Ubuntu, I know I can access the hard drive using /host/* but that is hassle that I do not want.

Any Ideas?

---

### Post by ajgreeny on 2011-02-14
> **grahambo2005 said:**
> Hi

Is it possible to increase the size of the Hard drive to 200GB when installing Ubuntu on top of Windows.

The Reason I ask it that I have a Laptop with a 500GB Hard drive, which has windows installed on it

Obviously I cannot create a new Partition on this drive to do a separate install.

30GB is just to small for what I want to do on Ubuntu, I know I can access the hard drive using /host/* but that is hassle that I do not want.

Any Ideas?

If you have a 500GB hard disk, I suggest you do a proper install to a separate partition, not the wubi install, which is what I think you are contemplating at the moment.  Wubi is really only for use as a check that you like the OS, and that it will run successfully on your hardware, not to use permanently, and certainly not using a 200GB virtual disk arrangement.

Why do you say "Obviously I cannot create a new Partition on this drive to do a separate install." because you probably can do just that without too many problems.Boot a live CD or USB of ubuntu and choose "Try Ubuntu", not install.  Run the terminal ,Applications->Accessories->Terminal and use command ```
sudo fdisk -l
```lower case L at end, and report back the output here.  It may also be useful to attach a screenshot of gparted from the System>Administration menu, as that will give a good view of your current partition layout.

---

### Post by grahambo2005 on 2011-02-14
Hey

Thanks for your reply, 

I'll get that info up shortly

I have already installed using a 30GB Drive and I've had a number of Issues

First and Foremost is the Wireless Networking Issue.
I installed 10.10 and had major problem getting the wireless going
the Card is an RT3090.

And while using WPA or WPA2 the connection kept dropping.

Tried A LOT to get this fixed from changing network managers, to different drivers, to router settings, to Windows Wireless Drivers and nothing fixed the problem

I ended up reverting to version 9.* LTS Wireless works fine then.

2nd issue was the ATI Driver did not work (Black Screen after restart) I have an Ati Raedon HD5650.

3rd was blue tooth did not work (didn't really try to hard to fix this, but I do have a USB mouse that I cannot use because of it.)



Basically the Laptop is brand new. Windows is on the Largest partition and then there a 3 additional Primary Partitions (small).

Creating a 200 GB Partition would involve me having to reinstall windows from the system recovery partition.

I am willing to try and find a solution to the Problems but I cannot risk being without an OS for any long period of time.

G.

---

### Post by Mark Phelps on 2011-02-14
> **grahambo2005 said:**
> ... I am willing to try and find a solution to the Problems but I cannot risk being without an OS for any long period of time.

ANY installation comes with some risk -- which is why the best first step is to backup what you have so you can restore it if needed.

Sounds like you already have the 4-partition limit on your drive, and I'm guessing, if the laptop is new, that you're running Win7.  IF the latter is true, and you still want to go through with installing Ubuntu, then before you do anything else, launch the Backup feature in Win7 to create and burn a Win7 Repair CD.  You might need that later to recover your Win7 boot loader if there are problems with the Ubuntu install.

Also, if you do decide to remove a partition and install Ubuntu to its own partition, be VERY CAREFUL!!  The new installer is confusing (to say the least) and it is very easy to accidentally reformat your Win7 install, thus wiping out everything you have.

The lowest risk course of action you have is a Wubi install -- you won't have to mess with partitioning, you won't risk overwriting Win7.

If you're deadset opposed to Wubi, then you'll have to bear the risks of the different install method.

---

### Post by grahambo2005 on 2011-02-14
> **Mark Phelps said:**
> ANY installation comes with some risk -- which is why the best first step is to backup what you have so you can restore it if needed.

Sounds like you already have the 4-partition limit on your drive, and I'm guessing, if the laptop is new, that you're running Win7.  IF the latter is true, and you still want to go through with installing Ubuntu, then before you do anything else, launch the Backup feature in Win7 to create and burn a Win7 Repair CD.  You might need that later to recover your Win7 boot loader if there are problems with the Ubuntu install.

Also, if you do decide to remove a partition and install Ubuntu to its own partition, be VERY CAREFUL!!  The new installer is confusing (to say the least) and it is very easy to accidentally reformat your Win7 install, thus wiping out everything you have.

The lowest risk course of action you have is a Wubi install -- you won't have to mess with partitioning, you won't risk overwriting Win7.

If you're deadset opposed to Wubi, then you'll have to bear the risks of the different install method.

I'll probably Stick with Wubi for the moment,

You can backup your Ubuntu installation prior to making change (IE installing the ATI driver which screws everything up)

Ill keep at it until I can confirm I have everything working, And then if I can get it all up and going I'll buy a new hard disk and just install Ubuntu on it.

Thanks for your help
G.

---

### Post by oldfred on 2011-02-14
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

I do not have bluetooth, but a while back someone posted the instructions on how to make it work. Part of the issue is that the same unique ID must be one both the windows and Ubuntu installs. So you have to install one and then find the ID and copy it to the other's install.

---

