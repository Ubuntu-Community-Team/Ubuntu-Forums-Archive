---
title: "Upgrade 9.10 to 10.4 - Kernel Panic - Unable to mount root"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by AcidFr33ze on 2010-05-13
So a little background. I had 9.10 installed on my IBM Lenovo Thinkpad, x301. I was performing updates as normal, and chose the Upgrade button to upgrade me to 10.04. Everything started fine, but upon reboot, no bueno, Kernel Panic! 

The exact message was "Kernel Panic ubuntu - not synching VFS Unable to mount root fs".


I thought this was a grub issue. Since grub2 now is installed... But it was not. I think it ended up being a problem with some of my configuration files.
I have three kernels I tried:
1. 2.6.32-22
2. 2.6.31-21
3. 2.6.31-20


The first threw me into the kernel panic.
The second would hang on "init crypto disks"
The third would hang on "checking battery state"

I noticed (from reading another thread) that while these are loading up that you can click on alt-ctl-F1 thru F6 and get prompt. (I also had my home directory encrypted, thought that was part of the problem, but it wasnt).

Once I get passed the loging, I am able to poke around. I tried manually start Gnome via "sudo service gdm start", but it failed. Said it was missing a configuration file. Then I tried on "sudo dpkg-reconfigure gdm" and it would not work. Saying some configuration files are missing or broken. It also said something about dpkg --configure -a, I am assuming this configures everything...

So I tried "sudo dpkg --configure -a" And selected 'y' to every option. Which basically installs the package creators default settings, and viola! Works.

Just wanted to share that knowledge for the other stuck in the upgrade hell.

Normally I would just copy my files off and reinstall, but it was encrypted... :( Another headache. I guess good in case someone stole my laptop.


Remember try to "sudo dpkg --config -a"


Good luck.:popcorn:

---

### Post by breusshe on 2010-05-21
You used two versions of the command.  It's:

sudo dpkg --configure -a

Brett Ussher

---

### Post by SiliconS on 2010-05-25
AcidFr33ze, I'm a newb with a similar problem but I don't understand your post. Can you provide more detail about exactly what you did to   overcome the 'Kernel panic' message?

After upgrading from Karmic to Lucid, all four Ubuntu options in Grub   stall after literally a second with a series of error messages   including a similar one to yours. This is what I can see on the boot-up  (black/white) screen when it's stalled:
```
VFS: Cannot open root device   "UUID=xxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx" or unknown-block(0,0)
Please append a correct "root=" boot option; here are the available   partitions:
0800   156290904 sda driver: sd
  0801     124479621 sda1
  0802             1 sda2
  0805      30451176 sda5
  0806       1357461 sda6
0b00         1048575 sr0 driver: sr
Kernel panic - not syncing: VFS: Unable to mount root fs on   unknown-block(0,0)
Pid: 1, comm: swapper Not tainted 2.6.32-22-generic #33-Ubuntu
Call Trace:
[bunch of obscure codes]
```After choosing an Ubuntu option in Grub I don't have time to press  Ctrl-Alt-Fx before that error message appears and the computer hangs.

Windows XP boots normally, fortunately.

Are you able to offer any help/advice please?

---

### Post by SiliconS on 2010-05-29
Bumpity bump. :)

---

### Post by FrankL on 2010-06-12
I second the bump. I have exactly the same problem and can't seem to find out how to solve it. All my older versions also crash with a kernel panic, any ideas would be greatly appreciated.

Thanks a lot in advance,

       Frank

---

### Post by SiliconS on 2010-06-12
Thanks for the bump, Frank. I was beginning to think it was just me.

I'm not using Ubuntu at all now. :( But I would if I could fix that problem. :)

---

### Post by duleorlovic on 2010-06-18
I also have the problem with 10.4, kernel panic.
When I select older version of kernel in grub, and tried " sudo dpkg --configure -a" in terminal, nothing happens. 
When I select current version of kernel in grub it freezes while booting with some message "EDD information not available".
Why is this thread marked as SOLVED?
Does anybody know how to log in without gnome, ie only text login black screen ? Maybe, when I login in current version of kernel, than the command " sudo dpkg --configure -a"  will work.

---

### Post by duleorlovic on 2010-06-18
I have found this [thread]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1511863") where [u01p2109]("http://ubuntu-ky.ubuntuforums.org/member.php?u=67591") said "After Upgrade You should run $sudo grub-install /dev/sda"
I did not run that command, so I will reinstall ubuntu 10.4
It seems that reinstall is the easiest way to get ubuntu works.
Bye

---

