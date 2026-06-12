---
title: "Install Help Needed 10.04 w/Raid 5 and LVM"
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by WrkWatchr on 2011-01-10
I have spent the last three weeks reading everything I can find and trying most of them without finding a good "total" solution. I have been lucky enough to get a Dell PowerEdge 2950 with 6 2TB drives, Dual Xeon 3Gb Processors, 16 GB ram, etc. What I am trying to do is install Ubuntu 10.04 on Raid 5 with LVM to act as a home server. I think I have the HW raid set up correctly as it shows ~100gb root and swap and a 9.045 TB unused section when I look at the Bios Raid report. Ubuntu 10.04 desktop is working fine, but I cannot access or see the rest of the raid array except in the Bios. When I try to access the 9.04 TB section for Ubuntu either using LVM manager or CL, I can't seem to access it. I am pretty sure the problem is my ineptitude with LVM, but after all of the stuff I have read, all I have done is succeeded in confusing myself and still am unable to get LVM to work. I am fairly new to Linux, but I have been successful in running an other Ubuntu server for several months, but someone else set it up for me.  Any suggestions, step by step direction or help setting up Ubuntu LVM 10.04 would be appreciated.

Thanks

R

---

### Post by ronparent on 2011-01-10
What is the raid chip set? Have you installed kparts?

---

### Post by WrkWatchr on 2011-01-11
From what I can tell, and according to the Dell website, ..." The PowerEdge 2950 with the PERC5i will have one integrated Serial Advanced Technology Attachment (SATA) host controller. It is controlled by the Intel® South Bridge 2-T, which provides the legacy I/O subsystem for the Blackford chipset based platforms"...

Since I am unfamiliar with KPart, I have to say no, I am not familiar with it and unless it was installed by default, it is not installed. I installed 10.04 with the Gnome interface and I am assuming the "K" indicates the KDE interface - right? Since this is the first I have heard of KPart in all of my reading. I am more than ready to learn :-)

Thanks

R

---

### Post by ronparent on 2011-01-11
It appears your raid is controlled by an Intel chip set and as such would be supported for raid level 5.

Since you say you have the raid set up in bios I have to assume you are using a 'fakeraid' with dmraid to access it. Dmraid has a bug as distributed with 10.04. To work around it you have to install kpartx (with the sortware manager, synaptics or sudo apt-get) which will then allow the raid to be seen and worked with in gparted. Let us know if it works for you.

---

### Post by WrkWatchr on 2011-01-11
Perhaps I misspoke. I can see the raid set up in the raid controller configuration menu. The 2950 has a separate Raid Card that all the drives are connected to, so when I said Bios, I was really meaning the Raid Controller Bios/Software on the card - not the MB Bios. Since this is an Enterprise Server, I am assuming (I know assumptions can get me in trouble) that it is not a FakeRaid setup. I will get gparted installed and see if I can move forward from there. 

R

BTW - is there anywhere that anyone knows of that has a step by step HOWTO that will work with 10.04? I have found several but all of them are for previous Ubuntu versions where LVM was not part of the Ubuntu install and following those directions do not seem to work.:-(

---

