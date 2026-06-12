---
title: "Kernel panic - not syncing: VFS: Unable to mount root fs on unknown - block"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by LacrimaMax on 2009-11-23
Hello!

Sorry, if my English isn't very proper.
I use Ubuntu 9.10 and Windows 7 together. I installed Ubuntu via Wubi.
I had been succesfuly using this configuration for a month untill yesterday. Yesterday I made latest updates suggested by Update Manager to my Ubuntu. After that my Ubuntu crashed.
Now after turning on my laptop I got this error:

**Kernel panic - not syncing: VFS: Unable to mount root fs on unknown - block (8,5)**

Windows 7 always boots succesfuly.
Ubuntu doesn't boot even in recovery mode.

Could you please help me to resolve this problem?

Thanks in advance.

---

### Post by abdurrm on 2009-11-23
it's happens to me too.. can anyone help us?

My system:
-Windows XP, using ubuntu 9.10

---

### Post by Juamps on 2009-11-23
Same here. -VFS: Unable to mount root fs on unknown-block (8,1)-

I'm running Vista and Karmic Koala

Thanks for your help

---

### Post by jesamjasam on 2009-11-23
I installed Ubuntu 9.10 using wubi on my WindowsXP machine. It worked just fine until today. Now i have the same problem you all have. Here's a printout:
**Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,1)**

Now my project is locked in ubuntu and i can't reach it:cry:

---

### Post by drew2222 on 2009-11-25
> **jesamjasam said:**
> I installed Ubuntu 9.10 using wubi on my WindowsXP machine. It worked just fine until today. Now i have the same problem you all have. Here's a printout:
**Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,1)**

Now my project is locked in ubuntu and i can't reach it:cry:

I am running 9.10 latest release and after the latest updates the following errors occured:
Ubuntu would not boot from grub, froze on first splash screen
Ubuntu would boot from recovery mode, screen cycled unreadable messages at speed.Received a kernel panic message at some point.
After trying various suggestions, I got it back by:
Select recovery option (second line in grub)
Wait for screen message "cycling" to start
Press [CTRL+ALT+F2]
This took me to a login screen
Enter Ubuntu username & password
Got to login prompt for Ubnutu installation(Terminal)
Run [sudo fdisk -l]
All seemed ok here as before boot problem started
Type [exit] to close terminal
Reboot to Ubuntu login as normal
I tried other CRTL_ALT options as suggested but F2 seemed to work this time?
Not sure why this happened, and if it was just a fluke I got it back
Will do some research.
My system is not under wubi tho and is dual boot with xp pro.

---

### Post by Gridwalker on 2009-11-29
Same problem, same error message, with a freshly installed version of 9.10 installed "within windows" on an XP Home laptop.

The problem only started after I updated to the latest kernel.

I can still boot into Karmic using the previous version of the kernel.

Any thoughts?

---

### Post by mfratus2001 on 2009-11-29
I did the recommended updates last night, and it cannot mount the drive.
I am using a SATA hard drive, which looks like a SCSI. The kernel seems to be looking for a RAID drive, but this hardware has been working fine until this update.
The generic version of this kernel update (2.6.31-15-generic) is fine, but the 386 version (2.6.31-15-386) won't run.
I am running the generic release right now, the previous 9.10 installation.
I guess they left something vital out of the kernel.

---

### Post by inforfang on 2009-12-03
same problem here ...

-Windows XP
-ubuntu 9.10

---

### Post by inforfang on 2009-12-04
> **mfratus2001 said:**
> I did the recommended updates last night, and it cannot mount the drive.
I am using a SATA hard drive, which looks like a SCSI. The kernel seems to be looking for a RAID drive, but this hardware has been working fine until this update.
The generic version of this kernel update (2.6.31-15-generic) is fine, but the 386 version (2.6.31-15-386) won't run.
I am running the generic release right now, the previous 9.10 installation.
I guess they left something vital out of the kernel.

How should i use previous version of Kernel ? and where should i find its version ?

---

### Post by obroyz on 2009-12-04
Hi everyone,

I'm absolutely new to Linux, leave aside Ubuntu. Having installed Ubuntu Karmic Koala just a few days ago, using Wubi, I have been extremely impressed with this O/S.

Getting to the point, I ran into this problem yesterday and I really couldn't understand a word everyone was saying about fixing this issue. My kernel had been updated to 2.6.31-15 and last morning, my machine wouldn't boot.

I noticed that I was able to boot into 2.6.31-14, so I worked on it for a while, trying to find a 'simple' solution before I went on learning all the technical stuff.

Anyhow, the fix:

1) Go to System > Administration > Synaptic Package Manager
2) Put in a search for linux-image
3) Locate the package "linux-image-2.6.31-15-generic"
4) Select the check-box next to this package and choose "Mark for Reinstallation"
5) Apply this changes
6) Reboot your machine

(For me) problem solved.

I hope it works for all of you as well.

Thanks,

J.

---

### Post by drew2222 on 2009-12-09
**[solved]** Ubuntu freeze on splash screen at boot-up.
Since my last post,this has been resolved by disconnecting a second monitor connected to the system. Maybe need to reconfigure nvidia screens after ubuntu upgrade.

---

### Post by obroyz on 2009-12-09
Hi again all,

I received by new Alienware M15x yesterday and the first thing I did on it was to install Ubuntu Desktop. Straight after, I ran the upgrade, which, in turn, upgraded my kernel to .....16. 

Things were fine upon reboot. The next thing I did was to upgrade device drivers. I received an option to upgrade my graphics card driver. One was 173 and the other one was 186 (recommended). I went along with the recommended one.

After another reboot, I got stuck at the splash screen. I don't know how to use the recovery mode, so I logged in with the old kernel, i.e. ....14. There were slight issues bringing the desktop up and then I received a message that there were problems with my graphics card drivers and I needed to reset them.

I just chose a new profile for the drivers, rebooted and everything was fine. The system chose driver 173.

I hope this helps.

Thanks again,

J.

---

### Post by sac_dos on 2009-12-11
Hi all...
Sorry for my English, but I'm French, it's explain...
I have the same problem... But, no other windows OS...
I have upgrade my ubuntu jaunty to karmic...
Start with kernel panic before starting splash screen...
I use liveDVD for installing directly karmic...
After upgrade to 2.6.31-16 generic and the same problem come on startup...
Freezing using USB or applications needs some HD access...
In fact, I think it's maybe to floppy mount on my desktop computer (It doesn't have it...).
But after reading this, I think problem come with lock xorg.conf... kernel can't access sometimes...
Correct access seems solve problem...
Very sorry for my English...

---

### Post by aiiee on 2009-12-12
> **jesamjasam said:**
> I installed Ubuntu 9.10 using wubi on my WindowsXP machine. It worked just fine until today. Now i have the same problem you all have. Here's a printout:
**Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,1)**

Now my project is locked in ubuntu and i can't reach it:cry:

Lesson learned:  Wubi is nothing but a toy OS.  Don't rely on it. Sad, but apparently true, judging from the lack of help

---

### Post by aiiee on 2009-12-12
> **obroyz said:**
> Hi everyone,

I'm absolutely new to Linux, leave aside Ubuntu. Having installed Ubuntu Karmic Koala just a few days ago, using Wubi, I have been extremely impressed with this O/S.

Getting to the point, I ran into this problem yesterday and I really couldn't understand a word everyone was saying about fixing this issue. My kernel had been updated to 2.6.31-15 and last morning, my machine wouldn't boot.

I noticed that I was able to boot into 2.6.31-14, so I worked on it for a while, trying to find a 'simple' solution before I went on learning all the technical stuff.

Anyhow, the fix:

1) Go to System > Administration > Synaptic Package Manager
2) Put in a search for linux-image
3) Locate the package "linux-image-2.6.31-15-generic"
4) Select the check-box next to this package and choose "Mark for Reinstallation"
5) Apply this changes
6) Reboot your machine

(For me) problem solved.

I hope it works for all of you as well.

Thanks,

J.

thx but didn't work for me for linux-image-2.6.31-16-generic, I just get dumped into grub prompt, and even after running sudo update-grub2, linux-image-2.6.31-16-generic  still generates kernel panic.

anyone make any progress with this?

---

### Post by maddentim on 2009-12-17
here is the bug that is causing your troubles: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/24](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/24)

The post i point you to shows how to get it to boot if you are stuck on the grub prompt.

---

### Post by yduras on 2009-12-31
> **maddentim said:**
> here is the bug that is causing your troubles: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/24](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/24)

The post i point you to shows how to get it to boot if you are stuck on the grub prompt.

Sadly that's still not clearing up the issue.  All seems well until the boot, which starts and then crashes on
```
ALERT! /host/ubuntu/disks/root.disk does not exist. Dropping to shell!
```

From there, I remain stuck.  I'm on a netbook, so I can't use an install CD. 


If I just reinstall from my windows half (which still boots with no issue), I'll loose all my files, won't I?

---

### Post by NovocastrianNomad on 2010-01-08
I had a similar error and found it was being caused by command:
 linux /boot/vml... root=/dev/sda1 loop=/ubuntu/disks/root.disk ro

The /dev/sda1 part is pointing root at the partition on the hard drive where your ubuntu disk file is located.  In my case the hard drive had been setup with two partitions by the equipment supplier (some create a small partition for rescue work I believe).  Apparently Windows 7 does something similar.

So I needed to use root=/dev/sda2 to point to the correct partition.  Once I did that I booted without problem.  I then did 'sudo update-grub' at my terminal prompt and then I was able to boot from the grub menu.

Hope this helps.

---

### Post by keiou on 2010-02-16
Hi All, 

This keeps on occurring every time there is a kernel update. I have tried the suggestions on this thread and on the Bug #477104. Unfortunately it did not work for me. 

Anyway, I hope the steps below could help you some how.

I have followed the step to re-install the kernel and that totally trash the boot up. After searching on the web, I found an article on how to [mount a WUBI disk]("http://ubuntuforums.org/showthread.php?t=1037874") which I did differently ;)

I move the root.disk and swap.disk to a different folder. I then uninstalled and reinstalled WUBI. After I was able to boot to the desktop I executed the following commands.

[I]sudo mkdir -p /media/root.disk
sudo mount -o loop /media/WindowsXP/ubuntu/disks/root.disk /media/root.disk
[/I]
My initial plan is to backup my firefox bookmarks and thunderbird emails. And sure enough the disk was mounted as another hard drive. That gave me an idea and what I did next is to reboot WUBI. At the grub boot menu I press 'e' for edit. I edited the line 

[I]linux /boot/vmlinuz-2.6.31-19-generic root=/dev/sda1 loop=/ubuntu/disks/
root.disk ro  vga=792  quiet splash
[/I]
to

[I]linux /boot/vmlinuz-2.6.31-19-generic root=/dev/sda1 loop=/disks/
root.disk ro  vga=792  quiet splash[/I]

then ctrl-x, it booted normally.

The only thing left is to make it permanent. Any ideas?:p

---

### Post by meierfra. on 2010-02-18
The problem is caused by a bug in Grub2 and can be fixed fairly easily

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by mipesom on 2010-02-19
> **meierfra. said:**
> The problem is caused by a bug in Grub2 and can be fixed fairly easily

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)


Do you mean to install this BEFORE the problem occurs - cause I just tried it after the problem has hit me and that doesn't work at all. :(

Only thing that works is using the boot menu entry with an older kernel. (2.14 in my case)

---

### Post by meierfra. on 2010-02-19
> Do you mean to install this BEFORE the problem occurs - cause I just tried it after the problem has hit me and that doesn't work at all.
If it does not work, it means that your problem has a different cause.


Try reinstalling the kernel:

```

ver=[COLOR="Red"]2.6.31-19[/COLOR]
sudo apt-get purge linux-{headers,image}-$ver-generic linux-headers-$ver
sudo apt-get install linux-{headers,image}-$ver-generic linux-headers-$ver

```
But use the version number for the kernel you are have problems with.

If this did not help, I suggest to start a new thread on the subject. 
In the new thread,  describe exactly what happens during boot-up.

---

### Post by mipesom on 2010-02-19
> **meierfra. said:**
> If it does not work, it means that your problem has a different cause.


Try reinstalling the kernel:

```

ver=[COLOR="Red"]2.6.31-19[/COLOR]
sudo apt-get purge linux-{headers,image}-$ver-generic linux-headers-$ver
sudo apt-get install linux-{headers,image}-$ver-generic linux-headers-$ver

```
But use the version number for the kernel you are have problems with.

If this did not help, I suggest to start a new thread on the subject. 
In the new thread,  describe exactly what happens during boot-up.

Thanks for the tip, but meanwhile I already installed a backup of my Ubuntu from yesterday. So I'm fine ATM and will switch to a genuine installation soon.

---

### Post by mipesom on 2010-02-19
Correction I'm not fine anymore...  I installed the software I wanted (5 hours) - had to go to Windows - returned: Grub prompt!!!!

After I installed backup earlier I replaced the wubildr with the recommended. If it changed something that obviously made it worse not better.

All tips in threads here to rescue the system failed. Of course I could use my backup from yesterday, but then I have to install everything again and probably tomorrow all the work is trashed again.

In 15 years Windows it failed twice to boot, but was easy to rescue. In 5 days Ubuntu all is trashed for the 3rd time! I need a computer to work with it - not for toying around with a suicidal system all the time.

I'm short before returning to Windows. :( Does anyone know for sure if this BS also happens with 9.04 ? Does 9.04 support the Samsung NC10 3G modem, too? 

I like to work with it, but I can not spend half of my time installing and looking for emergency rescue to be able to boot it again.

---

### Post by meierfra. on 2010-02-19
> If it changed something that obviously made it worse not better.
I never have seen a case where the new wubildr caused a problem. Maybe already your backup is corrupted in some way.

> I need a computer to work with it - not for toying around with a suicidal system all the time.
Wubi is meant for trying out Ubuntu. Since Wubi is just a file on your Windows partition it can easily get corrupted.   If you want a  stable operating system, you need to do a regular Ubuntu install.

> Does anyone know for sure if this BS also happens with 9.04 ?
Wubi 9.10  has more problems than Wubi 9.04.  But since I have no idea what is causing your current problem, I cannot guaranty Wubi 9.04 will   work better for you.  If you decide to reinstall, I strongly recommend a regular install instead of Wubi.


> Does support 9.04 the Samsung NC10 3G modem, 
No idea.

If you want to try  to rescue  your current Wubi install, boot from your Ubuntu LiveCD and   follow these [instructions]("http://bootinfoscript.sourceforge.net/") to run the boot info script and post the RESULT.txt

---

### Post by mipesom on 2010-02-19
I can't boot from CD - the Samsung NC10 is a netbook. Will buy an USB stick (always used my 8GB Multimedia player as a stick, but the netbook does not boot from it) and make a regular install. Thanks for taking the time, I'm just quite frustrated ATM.

---

### Post by meierfra. on 2010-02-19
> Will buy an USB stick ...and make a regular install
Great. Make sure to plan ahead. For example, if you have Vista/Window 7 you should use the Windows disk management to resize the Windows partition.

Good luck with your fresh install and sorry for all the problems you had with Wubi.

---

### Post by mipesom on 2010-02-20
I did this 2 days ago already. Wubi had it's own partition (30GB) And I have another 30GB free. And thanks, hope that will work better. :)

---

### Post by Sev7th on 2010-04-14
> **meierfra. said:**
> The problem is caused by a bug in Grub2 and can be fixed fairly easily

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

Thanks meierfra,

This fixed my problem with the following error:
unable to mount root fs on unknown-block(8,1)

replacing the c:\wubildr allowed my Ubuntu 9.10 to boot normal

---

### Post by roderickf on 2010-04-24
> **obroyz said:**
> Hi everyone,

I'm absolutely new to Linux, leave aside Ubuntu. Having installed Ubuntu Karmic Koala just a few days ago, using Wubi, I have been extremely impressed with this O/S.

Getting to the point, I ran into this problem yesterday and I really couldn't understand a word everyone was saying about fixing this issue. My kernel had been updated to 2.6.31-15 and last morning, my machine wouldn't boot.

I noticed that I was able to boot into 2.6.31-14, so I worked on it for a while, trying to find a 'simple' solution before I went on learning all the technical stuff.

Anyhow, the fix:

1) Go to System > Administration > Synaptic Package Manager
2) Put in a search for linux-image
3) Locate the package "linux-image-2.6.31-[COLOR="Red"]x[/COLOR]-generic"
4) Select the check-box next to this package and choose "Mark for Reinstallation"
5) Apply this changes
6) Reboot your machine

(For me) problem solved.

I hope it works for all of you as well.

Thanks,

J.

Thanks J.! This works for me too!! I just did an update with include updating linux-image.

Notice what number appears on your selection in GRUB during the boot. For example, Ubuntu linux image 2.6.31-[COLOR="Red"]20[/COLOR] generic. You just do what J. said with replaced value on red value i marked above.

---

### Post by catxk on 2010-04-29
> **obroyz said:**
> Hi everyone,

I'm absolutely new to Linux, leave aside Ubuntu. Having installed Ubuntu Karmic Koala just a few days ago, using Wubi, I have been extremely impressed with this O/S.

Getting to the point, I ran into this problem yesterday and I really couldn't understand a word everyone was saying about fixing this issue. My kernel had been updated to 2.6.31-15 and last morning, my machine wouldn't boot.

I noticed that I was able to boot into 2.6.31-14, so I worked on it for a while, trying to find a 'simple' solution before I went on learning all the technical stuff.

Anyhow, the fix:

1) Go to System > Administration > Synaptic Package Manager
2) Put in a search for linux-image
3) Locate the package "linux-image-2.6.31-15-generic"
4) Select the check-box next to this package and choose "Mark for Reinstallation"
5) Apply this changes
6) Reboot your machine

(For me) problem solved.

I hope it works for all of you as well.

Thanks,

J.

This did it for me as well, thanks a lot. I got the kernel panic message when booting into 2.6.31-20-generic, but was able to boot with 2.6.31-14-generic. From there, I could reinstall the linux-image for 2.6.31-20-generic and that solved the problem.

---

### Post by arpitrusia on 2010-05-24
I felt disappointed at the support and i got for the ubuntu . I updated my system last night and in the morning when i restarted my comp it showed kernel panic error. This is not the first time its happening to me. Last time when i upgraded it stuck at the (grub) prompt at start up. I tried to mount kernel manully but all was in vain. If the kernel updates are not stable y the hell they r provided in the list. All are not advance user that they can work around the problem easily. I lost my 3 months project bcoz of ubuntu and lack of support . Thank You team ubuntu ... for your horrible problem solving blog..

---

### Post by qutab on 2010-05-30
well i'm quiet frustrated too as i have had the same problem twice in two days..first time i just reinstalled ubuntu...but i also have to install like a million packages on karmic before i can do my work with a fresh installation..just came across this thread..havnt tried any of the solution but if any of this doesn't work i'm dead..the project's due very soon :confused::cry:

---

### Post by gansvv on 2011-09-27
Your kernel does not support the RAID configuration, or have the driver for it in-built. Until the latest Ubuntu kernel comes with support for your config, you will need to get the drivers (from the manufacturer's website) and install it as a loadable kernel module (insmod). Then alone the kernel will "see" the drive.

I remember doing this because "2.6.35-22-server" did not have support for 3ware 9750 RAID controller in my machine. The only disadvantage is that you have to be careful not to do a direct kernel upgrade through aptitude.

---

