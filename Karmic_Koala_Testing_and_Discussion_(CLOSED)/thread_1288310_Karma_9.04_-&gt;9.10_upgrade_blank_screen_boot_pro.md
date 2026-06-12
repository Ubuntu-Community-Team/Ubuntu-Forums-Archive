---
title: "Karma 9.04 -&gt;9.10 upgrade blank screen boot problems"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Karmic_Chameleon on 2009-10-11
I am a Windows refugee, new to Ubuntu.  

I installed 9.04 and then foolishly upgraded to 9.10.

The system won't boot and dies on stage 1.5.  

I can get to a grub> command by choosing one of two OSes in the grub menu: 9.04 ending in ...11 or ...15.

I can't get to a shell where I can run sudo commands, although  my knowledge of unix is quite limited.  

When I do Alt-f1 here is where I see it all going wrong:
Boot from (hd0,0) ext 3 9eETCETCETC
Starting up...
[     5.XXXXXX] IO APIC resources could not be allocated.
Loading, please wait...
[      5.XXXXXX] hub 1-0:1.0: over-current change on port 2

19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/aaXXXXXXX) = dev(8,5)
kinit: tring to resume from /dev/disk/by-uuid/aaXXXXXXXX
kinit: No resume image, doing normal boot...


And that's it.  I realize that great minds are working on this bug as we speak.  My questions are these:

1)  Is there an obvious workaround that will get the system to boot? 
2) Failing that, what are the commands to get the computer to boot from a CD or USB disk?  I have a bootable ISO image in my CD drive and it won't boot.   I must explain I know virtually no unix.  

Thanks!

---

### Post by gj_clt on 2009-10-11
Have you checked the Bios to see if your first boot device is set to cd/dvd not hd.

---

### Post by Karmic_Chameleon on 2009-10-11
Yes.  Boot order is 

1. ATAPI CD-ROM Drive
2. Removable Devices
3.  Network Boot 
4.  Internal Hard drive.


BTW computer is a Dell Latitutde L400, BIOS v. A01.

---

### Post by wirechief on 2009-10-23
I had a similar issue [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/453054](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/453054)  blank screen after update
boots to blank screen

I tried this and was successfull at getting to the desktop.

ctrl alt f3
sudo service gdm stop
X -configure
sudo service gdm start
then you can return to vt with ctrl alt f3 and back to desktop with ctrl alt f7

---

