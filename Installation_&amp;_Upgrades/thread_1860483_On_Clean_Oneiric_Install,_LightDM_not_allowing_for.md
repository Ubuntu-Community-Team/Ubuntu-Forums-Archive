---
title: "On Clean Oneiric Install, LightDM not allowing for login"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by LukeMorrison on 2011-10-14
I did a clean install with the mini.iso making certain that I did not touch my /home partition (100 GB).  As I see it, I currently have two issues (possibly related).  The no logon issue: i.e., I put in the correct password and it sends me back to the LightDM login screen.  I can log in using the TTY terminal, so the password would appear to be valid, but I have no .Xauthority file to delete in my /home/luke directory.  Also attempting:


```
sudo dpkg-reconfigure lightdm
```gives me these warnings:

```
environment variable DPKG_MAINTSCRIPT_NAME missing
environment variable DPKG_MAINTSCRIPT_PACKAGE missing
```Secondly, even with a LiveCD, I can not access my /home/luke directory, which leads me to believe I unintentionally encrypted my home drive.  Perhaps if I can solve the first issue, it will do the same for the second issue.    I hope this is clear enough, and any help is much appreciated.

---

### Post by Hakunka-Matata on 2011-10-14
I had the same symptom, I would enter the correct password and it would appear to start, but then recycle right back to the login screen, and wait for my password.

When this was happening, /etc/fstab was loading a separate /home partition.  I changed that to a different /home partition and it's working fine.  

SO:  I can say it has something to do with loading a particular /home partition.  Thinking about it now, I 'm not sure I have fixed that yet on this machine.  

Machine, Asus M4N78 PRO, 11.10 beta 2 X86 (32bit)

Machine

---

### Post by LukeMorrison on 2011-10-14
Using a combination of /etc/fstab and blkid, it does not appear that this is the issue.  The one thing I did notice was that even though my drives are all on /dev/sda, it says that each of them was on /dev/sdb during installation.  Not sure if this is pertinent, but thought I'd mention it.  Also, the options on /dev/sda7 (my / partition) were set to errors=remount-ro, whereas the /boot, /home were set to defaults.  I changed /dev/sda7 to defaults, but that did not make a difference.  I'm really hesitant to re-install as I'm not sure of the state of my /home partition.

---

### Post by LukeMorrison on 2011-10-15
Well, I'm headed in the right direction.  It turns out that I was correct regarding my home drive being encrypted.  I was able to mount it following the instructions in this thread, specifically post #10.
[URL="http://ubuntuforums.org/showthread.php?t=1622210"]
http://ubuntuforums.org/showthread.php?t=1622210[/URL]

The one step that was missed was that after you mount it, you need to run 

```
ecryptfs-mount-private
```

So, now, how do I either have it automounted or disable encryption?

---

### Post by LukeMorrison on 2011-10-15
Apparently, I just needed to be able to log in once with the home drive decrypted and things seem to be working fine now.  I guess I'll just need to pay more attention next time to what I'm doing when it asks if I want to encrypt my home drive

---

