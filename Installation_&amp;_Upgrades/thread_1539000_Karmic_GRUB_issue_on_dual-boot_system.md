---
title: "Karmic GRUB issue on dual-boot system"
date: 2010-07-26
forum: Installation &amp; Upgrades
---

### Post by mtbills on 2010-07-26
Okay, this GRUB issue has been killing me.  I'm a GRUB novice, unfortunately, but I have spent enough time trawling through various other threads without finding a solution that I decided to finally post my own.

First, my system is a 7-year old Dell tower.  Two hard drives, each sliced up into a bunch of ~30 GB partitions.  I dual-boot WinXP and Ubuntu Karmic Koala 9.10.  I think I have GRUB2, but don't know how to check without being able to boot.

This problem arose during a standard upgrade when I didn't pay attention and GRUB updated and apparently destroyed itself.  Now when I boot my system, I get the following message:
```
Booting from local disk...
GRUB loading.
error: no such disk
grub rescue> 
```

Almost every fix I found in my searching involved:
```
grub> find /boot/grub/stage1
```
but none of the solutions said what to do if that file wasn't found.  Then I found this thread:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8730926](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8730926)
that suggested that fix wouldn't work with my system anyway, so maybe that's why I've had so much trouble.

When I boot from my Ubuntu install DVD, I can mount my various partitions and browse their filesystems, so it appears that my data is all still intact, I just can't get to it.  What should I try next?

Thanks in advance for your help.

---

### Post by krishnandu.sarkar on 2010-07-26
Boot from Live CD/DVD and re-install grub sudo apt-get install grub and then sudo update grub

---

### Post by bcbc on 2010-07-26
> **mtbills said:**
> Okay, this GRUB issue has been killing me.  I'm a GRUB novice, unfortunately, but I have spent enough time trawling through various other threads without finding a solution that I decided to finally post my own.

First, my system is a 7-year old Dell tower.  Two hard drives, each sliced up into a bunch of ~30 GB partitions.  I dual-boot WinXP and Ubuntu Karmic Koala 9.10.  I think I have GRUB2, but don't know how to check without being able to boot.

This problem arose during a standard upgrade when I didn't pay attention and GRUB updated and apparently destroyed itself.  Now when I boot my system, I get the following message:
```
Booting from local disk...
GRUB loading.
error: no such disk
grub rescue> 
```

Almost every fix I found in my searching involved:
```
grub> find /boot/grub/stage1
```
but none of the solutions said what to do if that file wasn't found.  Then I found this thread:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8730926](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8730926)
that suggested that fix wouldn't work with my system anyway, so maybe that's why I've had so much trouble.

When I boot from my Ubuntu install DVD, I can mount my various partitions and browse their filesystems, so it appears that my data is all still intact, I just can't get to it.  What should I try next?

Thanks in advance for your help.
Post the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") results - it will tell us whether you have grub2 or not and probably also what the problem is.

If you do what the previous poster suggested you'll be installing grub-legacy.  And the second command won't work. I recommend holding off on that until we can see what the problem is.

---

### Post by mtbills on 2010-07-26
> **bcbc said:**
> Post the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") results - it will tell us whether you have grub2 or not and probably also what the problem is.

If you do what the previous poster suggested you'll be installing grub-legacy.  And the second command won't work. I recommend holding off on that until we can see what the problem is.

Thanks for the responses.  That bootinfoscript is quite useful, and I hadn't come across it before.  I do indeed have GRUB2 installed, and both my WinXP (sda1) and Ubuntu (sdb3) partitions are where I expected them to be.  The two things that jumped out as a possible red flags were "Unknown BootLoader  on sda3" and "Unknown MBR on /dev/sdb".

I have attached the fulls RESULTS.txt for you to look at.  Thanks for your help!

---

### Post by bcbc on 2010-07-26
> **mtbills said:**
> Thanks for the responses.  That bootinfoscript is quite useful, and I hadn't come across it before.  I do indeed have GRUB2 installed, and both my WinXP (sda1) and Ubuntu (sdb3) partitions are where I expected them to be.  The two things that jumped out as a possible red flags were "Unknown BootLoader  on sda3" and "Unknown MBR on /dev/sdb".

I have attached the fulls RESULTS.txt for you to look at.  Thanks for your help!

There are a bunch of things that look wrong - you have two partitions marked with the boot flag on /dev/sdb (the boot flag is supposed to be set on only one). That's not an issue for ubuntu, but it's strange - indicates something weird happened.

Also, the grub2 in /dev/sda is looking for a partition with uuid=8cb06e32-cabf-4e07-b291-1627fcb21633, but from the output of 'sudo blkid -c /dev/null' there is no such partition. The UUID can change if you resize a partition, but if you didn't do anything like that, it's also pretty strange.

Finally, there's no /boot/grub/grub.cfg listed on /dev/sdb3 and only one linux kernel - no initrd either.

Did you do a standard update? or did you try upgrading to 10.04? What else have you done trying to repair your system? 

I would boot in live CD mode and see if you can find the files that are missing on /dev/sdb3. There should be a /vmlinuz and /initrd.img as well as /boot/vmlinuz-2.6.31-14-generic and /boot/initrd.img-2.6.31-14-generic and /boot/grub/grub.cfg.
If not then you've got some major issue and I'd be looking to recover your data (possibly your entire /home directory) and reinstalling.

If everything is still there, then you can try reinstalling the grub2 bootloader pointing at /dev/sdb3 (but I am not feeling that this will solve your issues).
After booting from the live cd run the following:
```
sudo mount /dev/sdb3 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda 
```

---

### Post by mtbills on 2010-07-26
> **bcbc said:**
> There are a bunch of things that look wrong - you have two partitions marked with the boot flag on /dev/sdb (the boot flag is supposed to be set on only one). That's not an issue for ubuntu, but it's strange - indicates something weird happened.Yeah, I set that second boot flag (on sdb3) manually myself two days ago trying to fix this... I'll go back and unflag it.

> **bcbc said:**
> Also, the grub2 in /dev/sda is looking for a partition with uuid=8cb06e32-cabf-4e07-b291-1627fcb21633, but from the output of 'sudo blkid -c /dev/null' there is no such partition. The UUID can change if you resize a partition, but if you didn't do anything like that, it's also pretty strange.
I did resize a partition when I installed Ubuntu about a year ago, but haven't since.  Should I change that UUID to the correct UUID?  How would I go about doing that?

> **bcbc said:**
> Finally, there's no /boot/grub/grub.cfg listed on /dev/sdb3 and only one linux kernel - no initrd either.

Did you do a standard update? or did you try upgrading to 10.04? What else have you done trying to repair your system?I booted into Ubuntu and just updated all the packages normally.  The updater prompted me to enter something when it was updating GRUB, but I wasn't really paying attention and just hit enter, immediately regretted it, and I haven't been able to boot since.  In trying to repair the system I booted off my Ubuntu disc and ran Disk Manager (I think that's what the utility is called) and played around a little in GRUB.

> **bcbc said:**
> I would boot in live CD mode and see if you can find the files that are missing on /dev/sdb3. There should be a /vmlinuz and /initrd.img as well as /boot/vmlinuz-2.6.31-14-generic and /boot/initrd.img-2.6.31-14-generic and /boot/grub/grub.cfg.
If not then you've got some major issue and I'd be looking to recover your data (possibly your entire /home directory) and reinstalling.

If everything is still there, then you can try reinstalling the grub2 bootloader pointing at /dev/sdb3 (but I am not feeling that this will solve your issues).
After booting from the live cd run the following:
```
sudo mount /dev/sdb3 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda 
```
Thanks, I'll give that a try when I get home from work tonight.

---

### Post by vitothegreat on 2010-07-26
Didn't even read after the first post. I had the same problem and NOTHING helped. Use EasyBCD, it's free, easy to use and works like a charm.

---

### Post by bcbc on 2010-07-26
> **mtbills said:**
> I did resize a partition when I installed Ubuntu about a year ago, but haven't since.  Should I change that UUID to the correct UUID?  How would I go about doing that?


don't bother changing the uuid - it's correct in /etc/fstab. It looks like the grub bootloader was refreshed with the old uuid (this might be something you want to report if that's the case). Reinstalling grub as per above should fix this.

Before reinstalling grub, please run and post the output to ```
debconf-show grub-pc
```

---

### Post by mtbills on 2010-07-27
> **bcbc said:**
> Before reinstalling grub, please run and post the output to ```
debconf-show grub-pc
```

My output:

```
ubuntu@ubuntu:~$ sudo debconf-show grub-pc
  grub2/kfreebsd_cmdline:
  grub2/linux_cmdline:
  grub-pc/chainload_from_menu.lst: true
  grub-pc/kopt_extracted: false
  grub-pc/postrm_purge_boot_grub: false
  grub2/kfreebsd_cmdline_default: quiet
  grub2/linux_cmdline_default: quiet splash
  grub-pc/hidden_timeout: true
  grub-pc/timeout: 10
  grub-pc/install_devices:

```

---

### Post by bcbc on 2010-07-27
> **mtbills said:**
> My output:

```
ubuntu@ubuntu:~$ sudo debconf-show grub-pc
  grub2/kfreebsd_cmdline:
  grub2/linux_cmdline:
  grub-pc/chainload_from_menu.lst: true
  grub-pc/kopt_extracted: false
  grub-pc/postrm_purge_boot_grub: false
  grub2/kfreebsd_cmdline_default: quiet
  grub2/linux_cmdline_default: quiet splash
  grub-pc/hidden_timeout: true
  grub-pc/timeout: 10
  grub-pc/install_devices:

```
I was hoping to see the line grub-pc/install_devices: showing the old uuid. But instead it's blank and it says it was chainloaded from menu.lst (grub legacy). It doesn't really explain how you ended up with the grub-bootloader pointing to a non-existent partition.

Anyway thanks for that. Did you reinstall grub - and did that fix  it?

---

### Post by mtbills on 2010-07-27
> **bcbc said:**
> Did you reinstall grub - and did that fix  it?
I did reinstall GRUB, and now when I boot, GRUB does load, but it is not a complete fix.  I see "GNU GRUB version 1.97~beta4" at the top of the screen, some instructions, and then a
```
sh:grub>
```command prompt.

What should I do next?  I assume GRUB is defaulting to a command prompt because it is not finding the configuration files that inform it about my system.

---

### Post by mtbills on 2010-08-05
Okay, time for an update.

From the GRUB2 shell, I can chainload boot Windows, which restores base system functionality.  This is an excellent start.

I cannot get it to boot Ubuntu.  I try the boot via commands:
```
sh:grub> linux (hd1,3)/boot/vmlinuz root=/dev/sdb3
sh:grub> initrd (hd1,3)/boot/initrd.img
```After  entering that second line I get "Error: File Not Found", which I assume  means that initrd.img is a symlink and the file it is pointing to is  missing.  If I then try to boot, I get a kernel panic (no surprise  there).

So, is a missing initrd.img file worth chasing, or is its  absence fairly convincing evidence that my build has been compromised  and I should reinstall Ubunut?  I have backed up all of my files, so  reinstalling seems like the path of least resistance at this point.

If there is anything else I should try let me know, otherwise I will proceed and start fresh.

Thanks for all of your help.

---

### Post by bcbc on 2010-08-05
> **mtbills said:**
> I try the boot via commands:
```
sh:grub> linux (hd1,3)/boot/vmlinuz root=/dev/sdb3
sh:grub> initrd (hd1,3)/boot/initrd.img
```

You should try 
```
sh:grub> linux (hd1,3)/vmlinuz root=/dev/sdb3
sh:grub> initrd (hd1,3)/initrd.img
```

do "ls (hd1,3)/" to see what files are there first. /vmlinuz is linked to the latest kernel in /boot e.g. /boot/vmlinuz-2.6.xxxx

But reinstalling the grub bootloader should have worked. So maybe there is another issue.

---

### Post by mtbills on 2010-08-05
First, I should point out a typo in my previous post: there was no /boot in the commands that I ran.

> **bcbc said:**
> do "ls (hd1,3)/" to see what files are there first. /vmlinuz is linked to the latest kernel in /boot e.g. /boot/vmlinuz-2.6.xxxx
That drive contains all the usual suspects (etc, home, lib, media, mnt, opt, proc, root, sbin, selinux, srv, sys, tmp, usr, var) as well as vmlinuz and initrd.img.

/vmlinuz is linked to /boot/vmlinuz-2.6.31-14-generic, which exists
/initrd.img is linked to /boot/initrd.img-2.6.31-14-generic, which does not exist

That must be my problem, right?  Somehow initrd.img-2.6.31-14-generic got deleted. Can I recover that file without doing a clean install?

---

### Post by bcbc on 2010-08-05
> **mtbills said:**
> First, I should point out a typo in my previous post: there was no /boot in the commands that I ran.


That drive contains all the usual suspects (etc, home, lib, media, mnt, opt, proc, root, sbin, selinux, srv, sys, tmp, usr, var) as well as vmlinuz and initrd.img.

/vmlinuz is linked to /boot/vmlinuz-2.6.31-14-generic, which exists
/initrd.img is linked to /boot/initrd.img-2.6.31-14-generic, which does not exist

That must be my problem, right?  Somehow initrd.img-2.6.31-14-generic got deleted. Can I recover that file without doing a clean install?
maybe if you can copy it off a live cd - it's worth a shot. If it was me, I'd try it before reinstalling anyway.

---

### Post by mtbills on 2010-08-08
Just tying up the loose ends here.

I was unable to restore the initrd.img from the Live CD, so I reinstalled clean and everything works great.

To summarize for posterity, it seems I had two issues: GRUB got messed up (relatively easy to fix) and my kernel (specifically initrd.img) got messed up (I did not find a fix).  Backing up my data and reinstalling Ubuntu cured my problem.

BCBC, thank you so much for all of your help.

-Matt

---

