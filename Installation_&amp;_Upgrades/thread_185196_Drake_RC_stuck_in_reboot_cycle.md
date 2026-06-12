---
title: "Drake RC stuck in reboot cycle"
date: 2006-05-31
forum: Installation &amp; Upgrades
---

### Post by yellowstar5 on 2006-05-31
Testing the server version of Drake RC.

The install went well, this time I set up LVM as the last test I did I found the 'hangs on reboot with lvm ecms' issue.  So I got things going before with a non lvm install.

This time I did a fresh LVM install again and things seemed to go well.  I have /boot on an ext3 disk partition and /root and swap on LVM.  Now grub gets round to `boot' and voila - machine reboots into an endless loop.

Rescue disk gets me into the system but what do I do from here to fathom this one ?

Thanks,
Neil

---

### Post by nmuntz on 2006-06-01
I am having the exact same problem with the release i386 server install.   It doesn't matter what partitioning scheme I use.   The install goes fine but on reboot to the installed OS, grub loads the kernel and the machine reboots immediately after it grub issues "boot".  It even does it in rescue mode.  

I had been running Dapper on this machine (800MHz EPIA) for months, but when the release came out I did a fresh install and now I have this problem.  

I'm trying the desktop install to see if the same thing happens.

---

### Post by theimpostor on 2006-06-02
I having the exact same problem with 6.06 Server as nmuntz.

I've previously had Debian running fine on it.

Install completed without issue, and it now enters a reboot cycle following grub issuing boot.  I'm running a VIA EPIA M10000 board.

Need some ideas.  Is this an EPIA specific issue which can be sorted?

---

### Post by confused57 on 2006-06-02
Think there's a problem(bug) with the Dapper-rc-server install iso, at least it was for me with the i386 version.

[http://www.ubuntuforums.org/showthread.php?t=185298](http://www.ubuntuforums.org/showthread.php?t=185298)

---

### Post by nmuntz on 2006-06-02
I used the alternate install CD and did a text install and it works fine.  I really don't know what is going on with that server iso.

---

### Post by Dorowan on 2006-06-05
Same problem here. Going to try alternate install now.

I have an via epia m9000.

---

### Post by ElectusUnum on 2006-06-06
Any solution? I guess I'm going for the alt install.

---

### Post by markba on 2006-06-25
[QUOTE=ElectusUnum]Any solution? I guess I'm going for the alt install.[/QUOTE]
See my post on this thread:
[http://ubuntuforums.org/showthread.p...63#post1179363](http://ubuntuforums.org/showthread.p...63#post1179363)
Bottom line: this issue can be solved, either by installing 5.10 and upgrading to 6.06 or by using another install-iso (though I have not tried the last solution).

---

### Post by kaze on 2006-06-26
Have the same thing going on - see this thread:

[installation] Ubuntu 6.06 - fresh install | just reboots | /media | RSDP 
[http://www.ubuntuforums.org/showthread.php?p=1182185#post1182185]("http://www.ubuntuforums.org/showthread.php?p=1182185#post1182185")

Burning the alt iso right now.

Question: what is the alternative CD - really. I looked around for a while and all I could find was that it is for special cases. But how do you use it and what makes it different and is there a nice list of specific commands or switches for it. Does anyone have a nice link to a clean page on just WHAT it is?

- kaze

---

### Post by kaze on 2006-06-28
Server install from alternate iso CD went fine...

---

### Post by jav1231 on 2006-07-26
Why hasn't this been fixed? I just downloaded the 6.06 server CD and this still happens. Shouldn't this be pulled?

<<JAV>>

---

### Post by Spookster on 2006-08-22
This appears to be [bug #48266]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/48266"). Hope it gets looked at soon!

---

### Post by T-One on 2006-09-12
I think I may have licked this one:
 
Boot the rescue disk. Get a command prompt on your root hard drive. Edit your /etc/apt/sources.list (must use VI, nano won't work), 
 
```
vi /etc/apt/sources.list
```
uncomment the "universe" repos, save it,
```
apt-get install linux-386
```
When install is finished,
```
exit
```
Select Reboot from the rescue menu. ENJOY!
 
Prequisites: must know how to use vi. Nano gives an error about not liking "bterm" terminal environment. Anyone know a way around that?

---

