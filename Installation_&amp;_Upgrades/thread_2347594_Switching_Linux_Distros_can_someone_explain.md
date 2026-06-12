---
title: "Switching Linux Distros can someone explain?"
date: 2016-12-27
forum: Installation &amp; Upgrades
---

### Post by sgtkeebler on 2016-12-27
So right now I want to install Kubuntu but say I wanted to switch to Ubuntu later on. All I would have to do is create a live usb and format my hard drive right? I dont want to keep any data I would just want format and install Ubuntu. It would be like going from windows 10 to 7 right? Can someone explain switching distros without keeping data?

---

### Post by Keith_Helms on 2016-12-27
That's correct.  If you don't want to keep anything, you can just install a different distro by letting the install disc for it format the entire hard drive.

---

### Post by howefield on 2016-12-27
Sort of, create the live USB and boot from it, during the installation process you will see a screen detailing your partitioning options from which you can choose how you want to proceed, eg, formatting and using the whole disk or mounting the existing partitions and installing over them, incidentally should you mount an existing partition and not mark it for formatting everything bar /home will be deleted, in other words /home will be retained as is.

---

### Post by RobGoss on 2016-12-27
If you are using the entire disk then yes it's a straight forward process and you can repeat how you installed it the first time

It gets a bit more complicated when you're dual booting let's say Windows and Ubuntu, there's a lot more involved and one needs to pay attention to details

---

### Post by sgtkeebler on 2016-12-28
Hey thanks guys I am a newbie if you all haven't been able to already tell. I am coming from literally 10 years of windows and I really like Linux because of how it is and how its tailored to give the best user experience. But I was just confused on how reformatting and installing a different flavor on my machine.

---

### Post by SeijiSensei on 2016-12-28
If you want to try out a different distribution, the best method these days is to run them in a "virtual machine."  I use [VirtualBox]("http://www.virtualbox.org/") for this purpose.  Right now I'm on Windows and have a Kubuntu 16.04 virtual machine running as well.  When I use Linux, I'll often run a Windows virtual machine on top of it.  You can install a version of VirtualBox from the Ubuntu repositories either with a graphical package manager or by running the command

```
sudo apt-get install virtualbox
```

from a terminal.  If you like it, you might consider [adding the Oracle repositories]("https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions") to your Ubuntu system and getting VB from there instead. That will ensure that the version of VB you are running is always up-to-date.

The number of virtual machines you can run is limited by the amount of physical memory in your machine.  I'm on an 8 GB machine and typically allocate 2 GB to a Linux VM or 3 GB to a Windows VM.  That still leaves lots of memory for the primary operating system.

There are versions of VirtualBox for Windows and Macs as well.

---

