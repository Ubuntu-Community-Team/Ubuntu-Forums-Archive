---
title: "I need help to sucessfully install"
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by crisb1 on 2007-06-04
Hi everyone. 

    I'm trying to install Ubutu 7.04 Desktop x86.

hardware
    ECS A928 laptop
2.4 GHz CPU
480 MB RAM
60 GB harddrive

 from an .iso cd I downloaded and burned from ubuntu website. The hash checksum was correct after the download.

   The install went well. it said it completed the installization. then on the reboot it gives some ominous errors.

bogl_init failed: reading screen info: Inappropriate ioctl for device screen init failed
*Unmounting temporary filesystems...
Umount:/cow:not found                [Fail]
*Unmounting local filesystems...
Umount2:Device or resource busy
Umount: /cdrom busy -remounted read-only
Umount2:Device or resource busy
Umount: /rofs busy -remounted read-only
mount: Function not implemented

after it did the re-boot it drops into the shell with the message

udevd-event[1913]: run_program:'/sbin/modprobe' abnormal exit

BusyBox v1.1.3(Debian 1:1.1.3-3ubuntu3) Built-inshell(ash)
enter 'help' for a list of built in commands.

/bin/sh:can't access tty; job control turned off


If anyone can help me i would appriciate it.

---

### Post by wpshooter on 2007-06-04
I have received this same or similar problem several times before when doing an installation but to this point in time (after reading many, many posts hereon), I have yet to come up with a DEFINITIVE answer as to what causes this problem.

I am almost beginning to believe that inspite of the fact that the sumcheck on the CD is O.K. and the integrity check of the CD is O.K., that these problems have something to do with a mis-reading of the information of the burned Ubuntu CDs.

Let us know if you find a definitive answer.

P.S. - I have received these error on a system on which I had just complete WIPED the hard drive clean, so I pretty much know that it was not being caused by something that was already on the system/hard drive.

Good luck.

---

### Post by crisb1 on 2007-06-04
Thanks for the reply wpshooter. Even though you didn't find a difinative answer did you ever get it to install? with a different cd burn or anything.

   With the little linux knoweldge I have, The best i can think of is that Ubuntu dosn't have the drivers for the CD-Rom drive hardware I have. after the failed install i was unable to boot from my cd-rom. the bios didn't even have the cd-drive as an option. i had to manually mount the drive from the commandline before i could re-boot from the live-cd.
  This still dosen't explain why it wont boot up from the hard-drive install, just hints at some hardware incompatibilities.



I forgot to mention in the original post that on boot up it hanges up at  the Ubuntu logo with the very first line of the progress bar showing before it drops to the shell.

---

### Post by Pumalite on 2007-06-04
> **crisb1 said:**
> Thanks for the reply wpshooter. Even though you didn't find a difinative answer did you ever get it to install? with a different cd burn or anything.

   With the little linux knoweldge I have, The best i can think of is that Ubuntu dosn't have the drivers for the CD-Rom drive hardware I have. after the failed install i was unable to boot from my cd-rom. the bios didn't even have the cd-drive as an option. i had to manually mount the drive from the commandline before i could re-boot from the live-cd.
  This still dosen't explain why it wont boot up from the hard-drive install, just hints at some hardware incompatibilities.



I forgot to mention in the original post that on boot up it hanges up at  the Ubuntu logo with the very first line of the progress bar showing before it drops to the shell.

Make sure the firmware on your hardware is up to date. Also update your BIOS. Make sure is setup correctly. I would also check on the compatibility of your hardware with Linux in general and Ubuntu in particular. Then try again.

---

### Post by crisb1 on 2007-06-05
I was installing ubuntu over fedora so i know my hardware at least is compatable with that distro. I'll look into if there are any known issues with my hard ware and ubuntu in specific. I'm pretty sure my BIOS is setup right but i will look into it.
  How do I check up on the firmware for my hardware? is this getting the most current drivers?

Thank you for your help.

---

### Post by confused57 on 2007-06-05
It could be a Feisty bug for your particular chipset, I have a SiS chipset and get a similar error when I reboot or shutdown, when using Feisty...I've never had this error on any other version of Ubuntu.

Here's the launchpad bug report for the shutdown problem in Feisty:
[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/102894](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/102894)

You might want to try Dapper or Edgy, just to see if you get the error.

---

### Post by crisb1 on 2007-06-05
I definatly have a SiS chipset.

I tried installing Dapper with no luck.

---

### Post by crisb1 on 2007-06-06
Well after several more installation attempts of both dapper drake and fiesty fawn i was about to give up so after an install of fiesty i started messing around with the live cd. surfing the web, logging out not getting back in because of password not working then shutting down (not restarting). To my suprise it booted up.

   I did physically hold my cd-rom in with a C++ text book. (it has about 1/2mm play due to me taking it apartmany times)
  I did download an update to my bios firmware (but couldn't figgure out how to install the .exe)
  I did mess around on the cd-live ubuntu after the install. including a log out and shut down(not restart)

I don't see how any of these actions could have have any effect on that peticular install attempt. but if anyone has any ideas maybe it could help someone else.

Thank you all for your help

---

