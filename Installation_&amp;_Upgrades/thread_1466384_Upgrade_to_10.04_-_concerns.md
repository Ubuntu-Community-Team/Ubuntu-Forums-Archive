---
title: "Upgrade to 10.04 - concerns"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by gewitty on 2010-04-30
I have a 64 bit installation of 9.10, which I have spent a lot of time getting just the way I want it; quite a lot of apps installed and everything running perfectly.

10.04 looks good and I'd like to upgrade. However, the last time I tried an upgrade, as opposed to a fresh installation, things did not go well and I ended up with a seriously broken system. Fortunately, I had taken the precaution of cloning the whole drive before attempting the upgrade, but putting it back was time-consuming and not everything worked properly afterwards.

So my question is this: How safe it is it to use the upgrade option and what precautions should be taken (apart from backing up the Home folder) to ensure that, if things go wrong, I can recover without having to spend hours re-installing everything.

---

### Post by iponeverything on 2010-04-30
> How safe it is it to use the upgrade option 

No two systems are alike. Some, it might work great, others.. well you get idea. Can't really generalize by saying safe or unsafe.  I can generalize by saying that it's gamble. 

If you have the option of doing this.. clone the disk -- test it boot to it and do the upgrade on the clone. If it proves to be too much of pain, switch the disk back. I have found that $100 spent on a spare disk is cheaper than spending a week trying to fix my system. Kinda like PITA insurance..

---

### Post by dvlchd3 on 2010-04-30
If you previously upgraded from 9.04 -> 9.10 there were several issues.  GRUB2, EXT4, and other various components would not be upgraded via apt-get dist-upgrade or similar method.  It was a very confusing and frustrating process for several people.

However, 9.10 -> 10.04 should not be quite as bad.  There were minimal changes (relative to the 9.04->9.10 change), and everything should be upgradable by a dist-upgrade.

With that being said, I still prefer doing a clean install.  Any number of the 200+ packages could be corrupted during download, extracting, etc, and potentially break a system.  I prefer to just not deal with the headaches.

If you prefer this route, create a seperate partition for your /home directory. (If you do not do so already)  This will keep your files and most of your configurations intact when doing a clean install.  DISCLAIMER: ALWAYS BACKUP YOUR DATA REGARDLESS!

---

### Post by binary10 on 2010-04-30
Must echo the above comments.

 Seriously - buy a spare disk and clone/rsync it. Test it's bootable etc and do a test upgrade on that. Learn the pitfalls to get you respectable working state (especially if you customized the ui etc).

---

### Post by drorlev on 2010-04-30
I've upgraded from 9.10 to 10.4.
And now it doesn't work.
Problems with booting.
So I read many posts in many threads ...

And in one of them there was a wise idea I wish I had read it before.
Install the new sytem along-side the old-n-working one. Apparently, if and when you'll find the new system satisfactory you can remove the old one.

good luck anyway,
dror

---

### Post by Peter09 on 2010-04-30
Don't give up - tell us what problems you have, they may be easily fixed

---

### Post by strange_cathect on 2010-04-30
After upgrading from 9.10, my graphics are really messed up. I'm functioning in low-graphics mode and seem unable to get my NVIDIA graphics to kick in. Any clues as to what steps to take?

---

### Post by kansasnoob on 2010-04-30
> **drorlev said:**
> I've upgraded from 9.10 to 10.4.
And now it doesn't work.
Problems with booting.
So I read many posts in many threads ...

And in one of them there was a wise idea I wish I had read it before.
Install the new sytem along-side the old-n-working one. Apparently, if and when you'll find the new system satisfactory you can remove the old one.

good luck anyway,
dror

That's why I multi-boot:

> lance@lance-desktop:~$ sudo update-grub
[sudo] password for lance: 
Generating grub.cfg ...
Found background image: moreblue-orbit-grub.png
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found Windows NT/2000/XP (loader) on /dev/sda1
Found Debian GNU/Linux (squeeze/sid) on /dev/sda12
Found Debian GNU/Linux (5.0.4) on /dev/sda14
Found Ubuntu 10.04 LTS (10.04) on /dev/sda16
Found Ubuntu 10.04 LTS (10.04) on /dev/sda18
Found Ubuntu 9.10 (9.10) on /dev/sda3
Found Ubuntu 10.04 LTS (10.04) on /dev/sdb1
Found Ubuntu 10.04 LTS (10.04) on /dev/sdb6
done


And symlink my Data folders:

> lance@lance-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2              8649576   3469972   4740228  43% /
none                   1021800       356   1021444   1% /dev
none                   1026016         0   1026016   0% /dev/shm
none                   1026016        92   1025924   1% /var/run
none                   1026016         0   1026016   0% /var/lock
none                   1026016         0   1026016   0% /lib/init/rw
/dev/sda5              4617268    420168   3962560  10% /home
/dev/sda10            10866200     87500  10226888   1% /mnt/sda10
/dev/sda9             21195728   5343876  14775100  27% /mnt/sda9
/dev/sda8             21023124    148624  19806592   1% /mnt/sda8
/dev/sda7             10388064   2420436   7439900  25% /mnt/sda7
lance@lance-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / is on /dev/sda2
UUID=fb0e61a6-d355-4687-9a98-da164a56cc60 /               ext3    errors=remount-ro 0       1
# /home is on /dev/sda5
UUID=9397c183-6db2-4b47-b8d2-98234ce442d9 /home           ext3    defaults          0       2
# swap is on /dev/sda11
UUID=bf502251-6ccd-4b66-8f9a-458603a6d2f2 none            swap    sw                0       0     
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
#/dev/sda10    /mnt/sda10 /home/lance/Documents
UUID=571cfad8-68c7-4703-883e-c0baa2a381d4 /mnt/sda10      ext3    defaults          0       2
#/dev/sda9    /mnt/sda9 /home/lance/Downloads
UUID=05289ee4-d681-4806-b6fd-aefd784f9323 /mnt/sda9       ext3    defaults          0       2
#/dev/sda8    /mnt/sda8 /home/lance/Pictures
UUID=8a3f6c83-cb52-4caf-96b8-5faf2c830453 /mnt/sda8       ext3    defaults          0       2
#/dev/sda7    /mnt/sda7 /home/lance/Backups
UUID=594c3d40-2791-4c0a-8644-d9812545da2d /mnt/sda7       ext3    defaults          0       2


I always have at least one OS I haven't managed to break yet :guitar:

---

### Post by gewitty on 2010-04-30
Interesting set of responses so far. Is this something that Canonical could tackle in a future release?

Say the install process first created a list of all installed apps and backed up the Home folder (you'd need to do this to a second drive or maybe a DVD), then, instead of running an upgrade, it did a clean install. After this was done, it would re-install all the apps and then the Home folder.  

Somebody's going to tell me why that wouldn't work - but it sounds like a good idea.

---

### Post by suryaccnamcse on 2010-04-30
I was running 9.10 and was very eager to test the 10.04 so I did a side by side fresh installation  of 10.04 along with 9.10 and it works very well. I did not have the guts to format 9.10 and do a clean install of 10.04 but now as I have tested 10.04, I may do it after a few days.

---

### Post by dvlchd3 on 2010-04-30
> **gewitty said:**
> Interesting set of responses so far. Is this something that Canonical could tackle in a future release?

Say the install process first created a list of all installed apps and backed up the Home folder (you'd need to do this to a second drive or maybe a DVD), then, instead of running an upgrade, it did a clean install. After this was done, it would re-install all the apps and then the Home folder.  

Somebody's going to tell me why that wouldn't work - but it sounds like a good idea.
That sounds like a great idea, however, would be difficult to accomplish successfully and consistently.

You must keep in mind, with each Ubuntu version, the repositories change.  Package upgrades require other packages to upgrade, etc.  What you are describing is precisely what a dist-upgrade attempts to do, without having to boot into a live CD.

The only problem with a dist-upgrade is all the new packages need to be downloaded, decompressed, configured/compiled, and installed.  A break in one of these steps (a corrupt download, a package corrupted while decompressing, etc) causes the potential to break a system.

It doesn't happen as often when you use a Live CD because the installer essentially copies everything it decompressed when it booted onto the target partition.  Most of the work has already been done successfully, and if it didn't, you would know when you booted the Live CD.

Anyway, even if the Live CD offered an "upgrade" option, all your currently installed programs would have to be "upgraded" as well.  This means you must have an Internet connection, and those of us who require proprietary drives to connect to the Internet would have to do extra steps to successfully upgrade.

Ubuntu is meant to be usable by "human beings", meaning, all those non-technical people out there should still be able to use Ubuntu for their basic needs with little difficulty.  This was the main reason the release of 10.04LTS was pushed back a few hours, so these "human beings" wouldn't think Ubuntu erased their Windows installation.  (It was a bug report, don't have the link handy...)

Honestly, the number one priority of the Ubuntu developers is to keep things simple.  Fedora and other mainstream Linux distributions come with A LOT of pre-installed software.  This is great for most Linux powerusers, however, the users that want to just get on the Internet, don't utilize 90% of the OS.  (On a side note, more SLOC [source lines of code] = more bugs/security vulnerabilities.  Win7=over a trillion SLOC, Fedora=~2 million SLOC, Ubuntu=less [not sure the precise number off-hand...].  This is one of the main reasons Windows is so buggy and vulnerably to cyber attacks :guitar: )

With that in mind, more automation does not necessarily make things easier for the user.  Perhaps in the future something similar to what you described would be implemented, but right now I personally think the process is the best it could be, keeping everything above in mind.

Sorry for the extremely long response...not sure where all that came from, but it seems to follow some sort of logic progression, hopefully everyone else can follow it as well :)

---

### Post by gewitty on 2010-04-30
Makes sense to me.

What I might try as an alternative is to install 10.04 alongside 9.10 as a dual boot. Then build up 10.04 with the apps I want and transfer the Home folder across. Once I know everything is working OK, I can presumably delete 9.10, although this will necessitate a change to GRUB, which I don't know how to tackle.

---

### Post by pete_m on 2010-05-10
Hmm . .

interesting stuff.  .  . as a comparative newcomer to Linux desktops with the inclination to work with the latest versions of system and application software . . .

i'm wondering when to take the plunge from karmic to lucid . .

perhaps for those of us without tbe luxury of many disks and/ or the skills to do grub-update to find all those lovely installs .. 

might it be possible to create an option to run from the Live CD that would 

( given an i'net connection ) . .

 "Upgrade existing installation" . .

interrogate dpkg d'base of existing install . .
( as per aptoncd ( or its gnome equivalent if such exists) )

rename/ copy  any local folders we need to keep ( /home, /root  . .others ? )
rename/ copy  any local files we need to keep ( /etc/apt/sources.list  . .others ? )
 
do clean install without format ( i've done that successfully when moving from hardy -> karmic )

use our gleaned knowledge of pre-existing packages to apt-get install the latest versions - from fresh sources.list

restore/ merge  any local folders we need to keep ( /home, /root  . .others ? )
 restore/ merge  any local files we need to keep ( /etc/apt/sources.list  . .others ? )
  ( interactive shell prog needed here )

voila ( perhaps ! )

just a thought . .

<ed>
i appreciate ( on re-reading the thread ) that this is merely restating the suggestion made above . .and follows  the steps outlined on the response, but perhaps  . .

one might imagine a situation where pkgs behave like mozilla extensions and express the versions ( of their dependencies) that they are happy to run with . .

upgrading firefox may/ does result in broken extns and there is then the possibility to update if poss or remove broken extensions.

and perhaps even without such a mechanism an interactive script might find its way through . .
<ed>

i have read elsewhere on these forums  of the possible pitfalls of partial upgrades.  .

[http://ubuntuforums.org/showthread.php?t=1479547](http://ubuntuforums.org/showthread.php?t=1479547)

and found these notes . .

[http://www.webupd8.org/2009/11/how-to-upgrade-to-ubuntu-1004-lucid.html](http://www.webupd8.org/2009/11/how-to-upgrade-to-ubuntu-1004-lucid.html)

observations from the wise would be most welcome . .

specifically . .. 
[B]
what is the relation between ubuntu and the underlying debian?[/B]

my eee pc now on karmic was running (pinned ) xandros and using first debian etch and subsequently lenny ..

then things went wrong and i've since installed karmic on the ( once readonly) partition leaving a remnant xandros on the second partition with a view to dual-booting . .but tho' grub sees the partition n kernel i have not managed to boot it  ..(  but not been putting much effort into that)
 
i've been patching lucid and sid repos in and out of my sources.list to try n get a better picture in synaptic of what's moving . .
[B]
when/ how to move to new kernels ?


[/B]

---

