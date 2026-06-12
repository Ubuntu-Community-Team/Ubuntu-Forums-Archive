---
title: "problem when trying to install"
date: 2010-01-08
forum: Installation &amp; Upgrades
---

### Post by 3n!Gma on 2010-01-08
hello everybody,

I have Dell latitude505, and winxp workd perfecty on it. I tried so hard to repair the hardisk damages caused by a virus, but i couldn't .. my laptop do not recognizes any win cd, i tried with avira (based on ubuntu)  and other probgrams but didn't succeed, so i thought that inux could solve the problem. i tried live cd session without any positive result,  now that i try to install xubuntu/ubuntu/kubuntu, it shows several problems, this is what kubuntu install shows:

  	 	 	 	 	 	  udevd[110]: worker [112] unexpectedly returned with status 0x0100
 udevd[110]: worker [112] failed while handling '/devices/pci0000:00/0000:00:1f.1/host0/target0:0:0/0:0:0:0/block/sda'
 
any suggestions?

---

### Post by chrisinspace on 2010-01-08
At what point do you see this error?  While booting the live cd?  What version of Kubuntu are you trying to use...9.10?

---

### Post by 3n!Gma on 2010-01-08
the version is 9.10, and the error showd up after the boot, now it shows :

stdin: I/0 error 
stdin: I/0 error 
stdin: I/0 error
stdin: I/0 error 
...

BusyBox v1.13.3 (ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) unable to find a medium containing a live file system

---

### Post by chrisinspace on 2010-01-08
> **3n!Gma said:**
> the version is 9.10, and the error showd up after the boot, now it shows :

stdin: I/0 error 
stdin: I/0 error 
stdin: I/0 error
stdin: I/0 error 
...

BusyBox v1.13.3 (ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) unable to find a medium containing a live file system

Sounds like an optical (CD/DVD) disk drive problem.  Verify the ISO with the MD5 (just google it...plenty of how-tos out there).  Are you even getting to the Ubuntu menu that gives the following options:
[LIST]
[*]Try Ubuntu without any change to your computer
[*]Install Ubuntu
[*]Check disc for defects
[*]etc
[/LIST]

If so, run 'Check disc for defects'.  You could also test the CD on another computer if you access to one.

---

### Post by 3n!Gma on 2010-01-08
[chrisinspace]("http://ubuntuforums.org/member.php?u=434753") thanks for reply, 

the cds i used are working perfectly on other computers, and i received them after a free cd request so they're original! 

+ I tried that 'Check disc for defects' and it shows alot of err msgz :S

help!!

---

### Post by chrisinspace on 2010-01-08
Then it may be that your CD/DVD Rom drive is bad.  Definitely sounds like your machine is having problems reading the disk.  A simple think to check is to make sure that the data cable going from the drive to the motherboard is tight.  If that doesn't do it you may need to replace the drive.

---

