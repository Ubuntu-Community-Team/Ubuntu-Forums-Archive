---
title: "Install Ubuntu with 2 harddrive"
date: 2010-04-27
forum: Installation &amp; Upgrades
---

### Post by duongthaiha on 2010-04-27
Hi 
I got a problem when install ubuntu in my PC.
There are two hard drive
C: with Win 7
D: with nothing 
I boot from the CD and there is no option for auto partition option to install on C drive.
I change the option to D drive however, the system said this computer have no operation installed. (There is one in C still :confused:) So I don't know what to do?

I have check the with Gpart and there are 3 partition in C already. The recovery partition and another for the dell utility. And I don't want to delete that.

Please give me some advise what I should do.

Thank you very much in advance.

---

### Post by limey_rick on 2010-04-27
Sorry, but I am a little confused about your problem. When you boot from CD (Live CD) and you select to install Ubuntu (which version?), you end up in the Partition Manager. This is where you try select the disk you want to install Ubuntu on but when you select Drive D, with nothing on it, it tells you that there is no operating system installed - is this not what you'd expect? 

You should be able to select Drive D and use the entire disk to install Ubuntu on, which will then automatically partition the disk for you.

I am missing something? Sorry if I am stating the obvious.

---

### Post by duongthaiha on 2010-04-27
No it;s my fault not to state clearly.

I was trying to install Ubuntu 9.10. When i select the D drive then it said the computer have no OS install. Where there is one in C drive. Is that really mean "There is no OS installed in this hard drive" ? 

Also I noticed that Ubuntu 10.04 will be released in 2 days. Should I wait for the release date?

Once again thanks a lot for your help.

Best regards

---

### Post by limey_rick on 2010-04-27
If you have your Drive D with nothing on it, then the partition manger will say that it cannot find an OS. All its doing at this stage is telling you what it finds on the disks. Drive D is blank right? So it won't find anything on it. When you install Ubuntu, I presume you want to install onto this blank drive.

---

### Post by duongthaiha on 2010-04-27
Well the message said the computer does not have OS install which have a different meaning to it. However, I tried to install using auto partition in D drive. However, when I finish and re-start the machine then it come straight into windows. There is no screen for GRUB.

Do I have to change the some setting in my laptop so it read the D drive first??

---

### Post by oldfred on 2010-04-27
I am actually surprised that grub did not install to sda. Did you use the advanced button on the last partition screen to install grub on sdb?

If grub is in sdb you have to in BIOS change boot drive to sdb. It will not call it sdb but give you size. I have two Identical 160GB drives and if it boots one thing I know I chose the wrong 160 and have to choose the other 160 to get the boot I want. You also can check that it works with the f12 key on my desktop or f2 on my portable or whatever choose boot key that most BIOS now have during the post screen.

---

### Post by duongthaiha on 2010-04-27
Hi all 
Firstly thank you very much for your help.
The problem is now sorted. However it confused me a bit because I have done something different in attempt to install. Before i used a USB to boot and try to install ubuntu. Now i burn the CD and when i boot from it. It gave me the option to install ubuntu on C drive dual boot with Windows. 
:confused:
I have NO IDEA WHY AND HOW however I posting this one via Ubuntu now. Waiting for the 10.04 to release :D

Thank you all:popcorn:

---

### Post by garvinrick4 on 2010-04-27
> **duongthaiha said:**
> Hi all 
Firstly thank you very much for your help.
The problem is now sorted. However it confused me a bit because I have done something different in attempt to install. Before i used a USB to boot and try to install ubuntu. Now i burn the CD and when i boot from it. It gave me the option to install ubuntu on C drive dual boot with Windows. 
:confused:
I have NO IDEA WHY AND HOW however I posting this one via Ubuntu now. Waiting for the 10.04 to release :D
Thank you all:popcorn:That is a WUBI install, it is a folder within Windows that  is right next to USERS in C: drive. It also attaches itself to Windows boot manager. 
  Do not get this confused with a partition install, it is not. Nice to learn on though. Has one extra folder in file system called 'host' that is C: drive. Can transfer files to Ubuntu from there but cannot copy files from Linux into Windows with WUBI install.
 But from here on in look for info on WUBI install for info it is a different installation.

---

### Post by duongthaiha on 2010-04-27
No no its not WUBI I have tried with WUBI before and got some problem with it. Thats why I want to have a actual partition for Ubuntu. I am dealing with a big number of file therfore wubi will have disadvantage in run time.

But it quite a interesting to find out about how OS is boost and how Ubuntu work.

---

