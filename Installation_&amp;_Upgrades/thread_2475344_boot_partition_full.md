---
title: "boot partition full"
date: 2022-05-23
forum: Installation &amp; Upgrades
---

### Post by Deanobats on 2022-05-23
Hi all,
I got myself into this situation in the past and now I can't remember how I got myself out of it. I'm using Kubuntu 20.04 LTS and I have a 731 MB boot partition. As it fills up with new kernels I do a manual clear-out with:

[FONT=monospace][COLOR=#000000]sudo apt-get purge linux-image-5.13.0-28-generic[/COLOR]

replacing the image number with the oldest image and I keep going until I have two or three of the most recent images left and enough space. However! I didn't have a clear out BEFORE installing the most recent kernel and the boot partition is full and I can no longer remove old kernels.

The output of [/FONT][FONT=monospace][FONT=monospace][COLOR=#000000]dpkg --list | grep linux-image shows:

[/COLOR][/FONT][/FONT][FONT=monospace][FONT=monospace][COLOR=#000000][FONT=monospace][COLOR=#000000]ic  [/COLOR][COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-5.13.0-28-generic                 5.13.0-28.31~20.04.1                        amd64        Signed kernel image generic [/COLOR]
ic  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-5.13.0-30-generic                 5.13.0-30.33~20.04.1                        amd64        Signed kernel image generic [/COLOR]
ic  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-5.13.0-35-generic                 5.13.0-35.40~20.04.1                        amd64        Signed kernel image generic [/COLOR]
ii  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-5.13.0-37-generic                 5.13.0-37.42~20.04.1                        amd64        Signed kernel image generic [/COLOR]
ii  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-5.13.0-39-generic                 5.13.0-39.44~20.04.1                        amd64        Signed kernel image generic [/COLOR]
ii  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-5.13.0-40-generic                 5.13.0-40.45~20.04.1                        amd64        Signed kernel image generic [/COLOR]
ii  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-5.13.0-41-generic                 5.13.0-41.46~20.04.1                        amd64        Signed kernel image generic [/COLOR]
ii  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-5.13.0-44-generic                 5.13.0-44.49~20.04.1                        amd64        Signed kernel image generic [/COLOR]
ii  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-generic-hwe-20.04                 5.13.0.44.49~20.04.28                       amd64        Generic Linux kernel image [/COLOR]
ii  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-unsigned-5.11.0-27-generic        5.11.0-27.29~20.04.1                        amd64        Linux kernel image for version 5.11.0 on 64 bit x86 SMP [/COLOR]
iF  [COLOR=#ff5454]**linux-image**[/COLOR][COLOR=#000000]-unsigned-5.13.0-30-generic        5.13.0-30.33~20.04.1                        amd64        Linux kernel image for version 5.13.0 on 64 bit x86 SMP[/COLOR]
[/FONT]
[/COLOR][/FONT][/FONT]
[FONT=monospace][FONT=monospace][COLOR=#000000][FONT=monospace][COLOR=#000000]ls -l /boot shows the following:

[/COLOR][FONT=monospace][COLOR=#000000]-rw-r--r-- 1 root root    253599 Aug 11  2021 config-5.11.0-27-generic [/COLOR]
-rw-r--r-- 1 root root    257734 Feb  7 14:01 config-5.13.0-30-generic 
-rw-r--r-- 1 root root    257733 Mar 15 15:26 config-5.13.0-37-generic 
-rw-r--r-- 1 root root    257735 Mar 24 16:27 config-5.13.0-39-generic 
-rw-r--r-- 1 root root    257735 Apr  4 10:22 config-5.13.0-40-generic 
-rw-r--r-- 1 root root    257795 Apr 20 13:57 config-5.13.0-41-generic 
-rw-r--r-- 1 root root    257795 May 18 16:44 config-5.13.0-44-generic 
drwx------ 2 root root      4096 Jan  1  1970 [COLOR=#5454ff]**efi**[/COLOR]
drwxr-xr-x 4 root root      4096 May 23 18:54 [COLOR=#5454ff]**grub**[/COLOR]
lrwxrwxrwx 1 root root        28 May 23 18:53 [COLOR=#ff5454]**initrd.img**[/COLOR][COLOR=#000000] -> [/COLOR][COLOR=#ff5454]**initrd.img-5.13.0-30-generic**[/COLOR]
-rw-r--r-- 1 root root 110638485 May 23 18:53 initrd.img-5.13.0-37-generic 
-rw-r--r-- 1 root root 110639369 May 23 18:52 initrd.img-5.13.0-39-generic 
-rw-r--r-- 1 root root 110645626 May 23 18:52 initrd.img-5.13.0-40-generic 
-rw-r--r-- 1 root root 111260016 May 23 18:51 initrd.img-5.13.0-41-generic 
-rw-r--r-- 1 root root 111260658 May 23 18:53 initrd.img-5.13.0-44-generic 
lrwxrwxrwx 1 root root        28 May 23 18:59 [COLOR=#54ffff]**initrd.img.old**[/COLOR][COLOR=#000000] -> initrd.img-5.13.0-44-generic [/COLOR]
drwx------ 2 root root     16384 Feb  7 11:47 [COLOR=#5454ff]**lost+found**[/COLOR]
-rw-r--r-- 1 root root    182704 Aug 18  2020 memtest86+.bin 
-rw-r--r-- 1 root root    184380 Aug 18  2020 memtest86+.elf 
-rw-r--r-- 1 root root    184884 Aug 18  2020 memtest86+_multiboot.bin 
-rw------- 1 root root   5833109 Aug 11  2021 System.map-5.11.0-27-generic 
-rw------- 1 root root   5960334 Feb  7 14:01 System.map-5.13.0-30-generic 
-rw------- 1 root root   5963072 Mar 15 15:26 System.map-5.13.0-37-generic 
-rw------- 1 root root   5963072 Mar 24 16:27 System.map-5.13.0-39-generic 
-rw------- 1 root root   5964108 Apr  4 10:22 System.map-5.13.0-40-generic 
-rw------- 1 root root   5964620 Apr 20 13:57 System.map-5.13.0-41-generic 
-rw------- 1 root root   5964660 May 18 16:44 System.map-5.13.0-44-generic 
lrwxrwxrwx 1 root root        25 May 23 18:53 [COLOR=#54ffff]**vmlinuz**[/COLOR][COLOR=#000000] -> vmlinuz-5.13.0-30-generic [/COLOR]
-rw------- 1 root root  10123744 Aug 11  2021 vmlinuz-5.11.0-27-generic 
-rw------- 1 root root  10169120 Feb  7 14:01 vmlinuz-5.13.0-30-generic 
-rw------- 1 root root  10174368 Mar 15 15:28 vmlinuz-5.13.0-37-generic 
-rw------- 1 root root  10174400 Mar 24 16:34 vmlinuz-5.13.0-39-generic 
-rw------- 1 root root  10177344 Apr  4 10:25 vmlinuz-5.13.0-40-generic 
-rw------- 1 root root  10176704 Apr 20 14:00 vmlinuz-5.13.0-41-generic 
-rw------- 1 root root  10176896 May 18 16:47 vmlinuz-5.13.0-44-generic 
lrwxrwxrwx 1 root root        25 May 23 18:53 [COLOR=#54ffff]**vmlinuz.old**[/COLOR][COLOR=#000000] -> vmlinuz-5.13.0-44-generic[/COLOR]


I'm not sure why 5.13.0-44-generic is showing as old as that's the most recent kernel, but then I don't know much to be honest. Can anyone suggest how to get rid of the old kernels so that I keep the few most recent and get some space back on my boot partition? Noting I've tried seems to work as the partition is full. I had the same problem a few years back but can't remember how I solved it. Help would be much appreciated![/FONT]
[/FONT] 
[/COLOR]
[/FONT][/FONT]

---

### Post by GhX6GZMB on 2022-05-23
Wow! That's a lot of deadwood. This my ls -la /boot:
```
macro@macro-pc:~$ ls -la /boot
total 209196
drwxr-xr-x  3 root root     4096 May 20 22:44 .
drwxr-xr-x 20 root root     4096 Jan  5 21:58 ..
-rw-r--r--  1 root root   237975 Apr  8 10:44 config-5.4.0-109-generic
-rw-r--r--  1 root root   237975 Apr 14 14:19 config-5.4.0-110-generic
drwxr-xr-x  4 root root     4096 May 12 23:16 grub
lrwxrwxrwx  1 root root       28 May 12 23:15 initrd.img -> initrd.img-5.4.0-110-generic
-rw-------  1 root root 88142566 May 20 22:44 initrd.img-5.4.0-109-generic
-rw-------  1 root root 88143885 May 20 22:44 initrd.img-5.4.0-110-generic
lrwxrwxrwx  1 root root       28 May 12 23:15 initrd.img.old -> initrd.img-5.4.0-109-generic
-rw-r--r--  1 root root   182704 Aug 18  2020 memtest86+.bin
-rw-r--r--  1 root root   184380 Aug 18  2020 memtest86+.elf
-rw-r--r--  1 root root   184884 Aug 18  2020 memtest86+_multiboot.bin
-rw-------  1 root root  4759493 Apr  8 10:44 System.map-5.4.0-109-generic
-rw-------  1 root root  4759819 Apr 14 14:19 System.map-5.4.0-110-generic
lrwxrwxrwx  1 root root       25 May 12 23:15 vmlinuz -> vmlinuz-5.4.0-110-generic
-rw-------  1 root root 13668608 Apr  8 10:45 vmlinuz-5.4.0-109-generic
-rw-------  1 root root 13668608 Apr 14 14:56 vmlinuz-5.4.0-110-generic
lrwxrwxrwx  1 root root       25 May 12 23:15 vmlinuz.old -> vmlinuz-5.4.0-109-generic
macro@macro-pc:~$
```
As you see, only the current kernel and the previous is present, which is how it should be.

I suspect you're not upgrading correctly..
You normally need to run three commands to do it right:
```
sudo apt update
sudo apt upgrade
sudo apt autoremove
```

I've written a little script in /usr/local/sbin called myupgrade that contains the following:
```
#! /bin/bash
sudo apt update && sudo apt upgrade && sudo apt autoremove
```
permissions: rwx------ root:root

Just typing sudo myupgrade in my CLI will then do the upgrade.

Now with so many old kernels hanging in there, I'm not sure autoremove will do the job, but you can try (won't do any harm).
Otherwise you'll need to do a manual purge of each except the last two.

---

### Post by coley9225 on 2022-05-23
ml9104, /boot looks like yours, but diffenet kernals.

Deanobats, where ml9104 uses an alias, I use a script. It runs update, lists any upgradable packages, and asks if I want to upgrade now or wait. It also checks if I need to reboot, and what packages require the reboot, and gives me the option to reboot or wait. I also have a root crontab entry to run apt autoremove && apt auto clean on the first of every month. I'll post the script, if you would like. I have a keyboard shortcut( super + u ) to launch my terminal, then runs the script with sudo.

I also, about once every couple weeks, will run update manually, and anything is to be upgraded I use sudo apt full-upgrade.

Sorry, I don't enough to help you with your full /boot problem, but when you get that fixed, remember to run sudo apt autoremove from time to time.
Good luck

---

### Post by Deanobats on 2022-05-23
Yup! I've been very remiss at keeping it tidy in there. Ive had an issue since this install that autoremove hasnt worked so ive had to manually remove. The big problem is that when the boot partition is full, the manual purge fails, which is why I'm stuck! I need to purge to create space to upgrade but I can't purge until I make some space.

---

### Post by GhX6GZMB on 2022-05-23
In that case we're down to:
1: system backup (eg, Timeshift).
2: brute force deletion of some old kernels and initrd using rm.

I actually don't think it would create problems. The old files are dead and no longer in use.
Don't be timid :)

---

### Post by Impavidus on 2022-05-24
There's no need for rm yet, as dpkg should still be capable of removing those old kernels. Apart from the linux-image packages, there are the linux-modules and linux-headers packages. First use dpkg to find them:```
dpkg --list linux-*
```Pick the version you want to remove and use dpkg to remove it. dpkg will ignore broken packages, as long as they don't conflict with the packages you ask it to do something with.```
sudo dpkg --purge linux-headers-5.13.0-40-generic linux-image-5.13.0-40-generic linux-modules-5.13.0-40-generic linux-modules-extra-5.13.0-40-generic
```After making some free space this way, apt should be able to fix the partially installe[COLOR=#000000]d linux-[/COLOR]image-unsigned-5.13.0-30-generic.

---

### Post by Deanobats on 2022-05-24
woohoo! Last suggestion worked like a charm! Thanks so much for your help everyone, it's quite uplifting when people chip in with help like this. It's very much appreciated.

---

### Post by TheFu on 2022-05-24
Are you running **sudo apt autoremove** every week or 2?  That should handle this. 

Also, avoid having more than 1 line of kernels installed at a time.  20.04 shipped with 5.4.x.  Then it was upgraded to 5.8 (or was that 5.10)?  Then 5.11 in the HWE lines.  My 20.04 systems are on 5.4 still, this is on purpose.  I've pushed all my 18.04 systems to the HWE 5.4.x kernels, to be consistent and as preparation for moving to 20.04.

---

### Post by Deanobats on 2022-05-24
For some reason sudo apt autoremove has never worked for kernels for me since my clean install of 20.04. I never got to the bottom of why, so I always did a manual purge and got it down to two or three kernels (current plus one or two backups), the problem I ran into is that on this one is I didn't do a purge before a new kernel update and then the boot partition got full - once it's full, you can't remove or purge anything, so I got stuck.

---

### Post by TheFu on 2022-05-24
> **Deanobats said:**
> For some reason sudo apt autoremove has never worked for kernels for me since my clean install of 20.04. I never got to the bottom of why, so I always did a manual purge and got it down to two or three kernels (current plus one or two backups), the problem I ran into is that on this one is I didn't do a purge before a new kernel update and then the boot partition got full - once it's full, you can't remove or purge anything, so I got stuck.

If you have 3 kernel lines, then all three of those lines will be maintained, effectively using 3x the space.  Here's a 20.04 system:
```
$ ls /boot/vmlinuz*
/boot/vmlinuz@                   /boot/vmlinuz-5.4.0-110-generic
/boot/vmlinuz-5.4.0-109-generic  /boot/vmlinuz.old@

```
If I installed the HWE kernel, then the 5.4.x and 5.11.x kernel lines would be on the system - using 2x the space.  If I was happy with the 5.11.x kernel after a week, then I'd manually remove all the 5.4.x kernels, modules, headers.  It isn't hard to get a list of those, if you are average with the CLI, but perhaps using **Synaptic** would be easiest? Search for all 5.4 packages, select each that is a kernel, module, header and remove them. I haven't used synaptic in some time, does it have a 'purge' option? If so, use that too.  If you have 5.8.x or 5.10.x kernels, do the same cleanup with synaptic.

Here's the space used on a clean system by /boot:
```
$ du -sh /boot
219M    /boot

```

And on another system:
```
$ du -sh /boot/
193M    /boot/
```

And on another system:
```
$ du -sh /boot/
167M    /boot/
```

---

### Post by rsteinmetz70112 on 2022-05-26
You might also want to check and see if you have a lot of old configuration files 

```
$ dpkg -l | grep "^rc"
```

---

