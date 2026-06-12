---
title: "Major, major boot issues"
date: 2010-03-10
forum: Installation &amp; Upgrades
---

### Post by wyomingpat on 2010-03-10
I posted this on the Lucid development site but have no interest.
It started with LDAP Problems in Lucid Alpha 3 after uninstalling Apache2.
Well I de-installed Apache now it seems LDAP is corrupted. I cannot install or uninstall programs from the terminal window or synaptic. Update manager fails also. I cannot reinstall, deinstall or install LDAP for the same reasons.
 So I thought I would just reinstall the system. I downloaded the latest image to another machine, created a disc and checked it over. I then try and boot from it and that seems to lock up. My other machine boots from it fine. The CDROM drive is fine checking with utilities.
 My system also runs fine otherwise. Just cannot add or delete packages or update.
 Any answers?
**Then further info posted...**

 

 Nobody has replied to this yet but as further info. I now have 3 Ubuntu bootable CD's of 9.10 and 10.04. They will all boot on other computers but not on the one in question.
 That machine will boot happily on Partition magic so I used that to wipe the hard disk and the MBR. Still will not boot on the Ubuntu CD.
 Booted up fine on Windows Vista recovery disks and on an old DOS CD.
 In Ubuntu the computer appears to be booting then the screen goes blank with "no signal" all the /home is on a separate drive. The CD is active then it all stops.

 

 This is really mysterious.

---

### Post by kansasnoob on 2010-03-10
Have you tried any "boot options":

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Note: 10.04 doesn't have the F4 > Safe Graphics option, so you have to use F6 > nomodeset in Lucid.

I'm not sure which option or combination of options to try but it sounds like a plan to me ;)

---

### Post by wyomingpat on 2010-03-10
Yes I did - however I loaded my Vista system on to the drive without a problem and I can load other software from CD. If I put ANY of the Ubuntu CDs into the CD drive under Windows the CD loads and displays WUBI.exe. If I try to run WUBI under Windows I get "No CD detected, cannot run CD Menu". All these CDs images checkout fine and all will boot fine on 2 other machines. There seems to be no way of installing Ubuntu back onto this machine.

Of course keeping my user data safe on  another machine is not that helpful as Windows cannot read EXT4 file systems. Seems I will have to buy an external enclosure and remove the drive to attach to a Linux system.

Now I accessed the CD from Windows and ran wubi as administrator and it appears to be running so far. System still will not boot of any of the Ubuntu CDs at this point.

Now Ubuntu installed aparrently OK from within windows and I now have a dual boot. I cannot boot into Ubuntu as after the option of Windows Vista and Ubuntu I select Ubuntu and I get a Grub prompt. 

I am still in the position where the original CDs I set up this machine from originally will not work on this machine. Tried Ubuntu 9.10, 10.04 and Kubuntu systems too.

---

### Post by wyomingpat on 2010-03-11
After installing Vista again I was able to install an old copy of Ubuntu 9.10 downloaded in December. It is now on as a dual boot system. Funny how I had to go through to reinstalling windows to over write what ever had been corrupted in the MBR (i guess)

---

