---
title: "Cannot boot after upgrading to Feisty"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by Fibonacci on 2007-04-19
Hello,

This morning I tried to upgrade to Feisty using update-manager, but since it found no upgrades I decided to use the unofficial method of editing sources.list and dist-upgrading (yes, I know, stupid me). Now, when trying to boot into kernel-2.6.20-14-generic, recovery mode or not, I only get to a BusyBox shell. Recovery mode prints a long stream of messages that ends on this before getting to BusyBox:

```
Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/hdb1 does not exist. Dropping to a shell!

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands
/bin/sh: can't access tty; job control turned off

(initramfs)
```

Non-recovery mode prints only from the line beginning with BusyBox.

Any ideas of what can I do to solve this problem, short of wiping the partition and reinstalling?
I have liveCDs of both Dapper and Edgy if they're of any use - in fact, I'm posting from the former.

Thanks in advance,

-Fibo

---

### Post by rich.bradshaw on 2007-04-20
Why did you upgrade like that?

I would just reinstall it's easier...

I would advise making a seperate /home partition so that you can just reinstall the OS without messing up your files if you do reinstall.

---

### Post by apace79 on 2007-04-20
I had the same problem. But i didn't write down all of the error message. I just remember the last part, and it was the same. I also remember some error messages before reeboting, they all had tty in them.
I installed Feisty from the cd and now it seems to work, but it didn't mount my windows hd automatically. I also tried the user migration thing from my windows XP drive, but it didn't seem to have worked. It just copied some files from "my documents" (which is useless in my opinion) but no settings for firefox for example.

---

### Post by Fibonacci on 2007-04-20
> **rich.bradshaw said:**
> Why did you upgrade like that?

Because update-manager found no upgrades.

> **rich.bradshaw said:**
> I would just reinstall it's easier...

Except that it takes lots of time to backup my files before wiping the partition. I wouldn't say it's easier.

> **rich.bradshaw said:**
> I would advise making a seperate /home partition so that you can just reinstall the OS without messing up your files if you do reinstall.

I don't think I can do that - I'm not touching the other partitions in /dev/hdb (I mean, besides the one I'm installing Feisty on).

---

### Post by Fibonacci on 2007-04-21
After backing up all my files and preparing for a reinstall, I finally got it to boot.
Problem was, in the new install all hard drives' names are changed to /dev/sda, /dev/sdb, etc, **even if they're IDE discs**. All I had to do was change all instances of root=/dev/hdb1 to root=/dev/sdb1 on my /boot/grub/menu.lst, and I got it to boot again!

Hope this helps anyone else with the same problem.

-Fibo

---

### Post by btoone on 2007-04-23
Changing from hda to sda worked for me.  My system locked during the upgrade and would not boot until I made this change.  Why did they change to referencing via sda anyway?
Thanks for the post, it saved me!

---

### Post by docdailey on 2007-04-23
I have what sounds like the same problem...I don't have hda in my menu.list though...they are referenced using uuid... see the details....help if possible...

[http://ubuntuforums.org/showthread.php?t=419701](http://ubuntuforums.org/showthread.php?t=419701)

thanks,

bill

---

