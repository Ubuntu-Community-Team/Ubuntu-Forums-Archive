---
title: "GRUB error: no such partition - grub rescue&gt;"
date: 2010-04-06
forum: Installation &amp; Upgrades
---

### Post by wesleyzhao on 2010-04-06
I am currently using an Asus EeePc 1005HAB and had Ubuntu and XP running with Grub.

I recently ran into some trouble with XP, so I decided to go into recovery. After it rebooted from recovery, I got the error message:
[I]
GRUB loading.
error: no such partition
grub rescue> 
[/I] 

I have tried booting from my USB with an Ubuntu install image, I have tried the commands "set root=(hd0,0)". But nothing has worked.


I am a newbie at Ubuntu and would love for some advice on how to get out of this sticky situation!


Please, and thank you :)

---

### Post by drs305 on 2010-04-06
wesleyzhao

Welcome to Ubuntu and the Ubuntu forums.

If you had a working Ubuntu and then reinstalled Windows, this guide by Talsemgeest should provide the necessary instructions to restore Grub:
[How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by theDaveTheRave on 2010-04-06
it sounds as though you may need to re-install grub.

XP has a nasty habit of not liking to have other OS's sharing a computer with it (I guess this is good for business!?)

check out the community page for instructions.

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

David

---

### Post by wesleyzhao on 2010-04-07
Thanks for the advice :).


My I looked at both links. 

My netbook does not have a CD drive, only has a USB.


I downloaded the Ubuntu image onto the USB and set the BIOS to boot from the USB, however the error mesagge (GRUB error) appears rather than booting into the CD image of Ubuntu.

Is there a step I am missing??

I cannot access any of my OS' at this point. As soon as I turn on the computer, I can either enter the BIOS or see the GRUB error :(.


Please let me know if I am forgetting something, or should try something specific? 


Thanks everyone!

---

### Post by drs305 on 2010-04-07
I have little experience with trying to boot from a USB, but here is the community doc on how to set it up for 9.10 - perhaps it will help:
[https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

---

### Post by oldfred on 2010-04-07
Scroll down a page from this and it has how to manually enter lines to boot from a rescue line:
[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode)

Reinstall grub:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by wesleyzhao on 2010-04-07
> **drs305 said:**
> I have little experience with trying to boot from a USB, but here is the community doc on how to set it up for 9.10 - perhaps it will help:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)


I followed these instructions but still ended up no where :(. I am now trying to install Ubuntu Netbook Remix and hoping that might help....

---

### Post by wesleyzhao on 2010-04-07
> **oldfred said:**
> Scroll down a page from this and it has how to manually enter lines to boot from a rescue line:
[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode)

Reinstall grub:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)


I looked at the commands for the rescue line but the only commands that were working were 
-set
-insmod

All the other commands that it told me to do gave this error: "Unknown command"

I'm at a loss! I may be looking at the wrong section.. I am looking under the title **Rescue Mode** and followed those steps, but as I said only certain commands are working.

Am I screwed forever??

---

### Post by seanrich on 2010-10-10
I'm having the exact same problem. I installed Ubuntu 10.10 from USB. I created the USB using the recommended creator, and when I reboot I get the grub rescue> menu. None of the commands work except set and insmod.

---

### Post by tjanss on 2010-10-11
More or less the same problem here...

Installed Ubuntu 10.04 a week ago or so (using wubi.)
Tried to upgrade to 10.10.
Now the PC will only boot to grub rescue.

When booting, this is what i get:
[FONT="Courier New"]error: no such device: cd200414-0606-4d7d-8c08-004e9b5dc92d.
grub rescue>[/FONT]

Three commands work: [FONT="Courier New"]ls[/FONT], [FONT="Courier New"]set[/FONT] and [FONT="Courier New"]insmod[/FONT].
The [FONT="Courier New"]ls[/FONT] command only yields: [FONT="Courier New"](hd0)[/FONT]
(no partitions like (hd0,1), (hd0,5), etc.)

I have no idea what to do...

(I have an Asus UL30A without an optical drive.)

---

### Post by kansasnoob on 2010-10-11
> **seanrich said:**
> I'm having the exact same problem. I installed Ubuntu 10.10 from USB. I created the USB using the recommended creator, and when I reboot I get the grub rescue> menu. None of the commands work except set and insmod.

Assuming you can still boot the Live USB please post the output of The Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by kansasnoob on 2010-10-11
> **tjanss said:**
> More or less the same problem here...

Installed Ubuntu 10.04 a week ago or so (using wubi.)
Tried to upgrade to 10.10.
Now the PC will only boot to grub rescue.

When booting, this is what i get:
[FONT="Courier New"]error: no such device: cd200414-0606-4d7d-8c08-004e9b5dc92d.
grub rescue>[/FONT]

Three commands work: [FONT="Courier New"]ls[/FONT], [FONT="Courier New"]set[/FONT] and [FONT="Courier New"]insmod[/FONT].
The [FONT="Courier New"]ls[/FONT] command only yields: [FONT="Courier New"](hd0)[/FONT]
(no partitions like (hd0,1), (hd0,5), etc.)

I have no idea what to do...

(I have an Asus UL30A without an optical drive.)

Wubi is quite a different story, according to the release notes:

[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Boot,%20installation,%20upgrade%20and%20post-install](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Boot,%20installation,%20upgrade%20and%20post-install)

> #

The Wubi Windows installer was reported to be unable to open Windows' boot configuration data store in some (but not all) cases. Investigation of the problems are ongoing (613288)
#

You cannot upgrade if wubi is installed to a partition other than Windows. (610898,653134) 

Drs305 wrote a bit about that at the top of the page here:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

> According to the Release Notes, a Wubi upgrade to 10.10 from 10.04 fails and is still not recommended - "File not found".
Bug # 613288
If you have upgraded to 10.10 and cannot boot normally:
Boot the LiveCD, make mount points and mount your Windows partition. Then mount your wubi installation. Note you must change sda1 to your Windows partition designation.
Code:

sudo mkdir /mnt/windows /mnt/wubi
sudo mount /dev/sda1 /mnt/windows
sudo mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/wubi
gksu gedit +80 /mnt/wubi/boot/grub/grub.cfg

Remove all the lines above the first "menuentry" line (Approximately line 85). Save the file and then reboot. Do not run update-grub before rebooting.

Sadly with no optical drive you'll somehow need to acquire an Ubuntu Live USB:

[http://ubuntuforums.org/showthread.php?t=811397](http://ubuntuforums.org/showthread.php?t=811397)

---

### Post by Bulova on 2010-10-11
Hi:

I have the exact same problem as the person above me.

I was running xp/Ubuntu 9.1 netbook on my Asus 1005. XP was on the "C" drive and Ubuntu was on the "D" drive (Asus factory installs two partitions on the HD).

After trying the 10.4 update, I can't boot in either windows or Ubuntu. I get the "Grub rescue" prompt.

I tried booting from the Ubuntu live disk and from a Kanotix live disk. Nothing. I still end up at the "Grub rescue" prompt.

---

### Post by drs305 on 2010-10-11
I know it is easy to add a request on a thread that has the same title as the problem you are experiencing, but each user may have a unique situation. For example, some posts are for wubi, others for a normal installation. Etiquette is to start your own post rather than hijack another's; it also eliminates confusion.  Or perhaps I should just start a "Grub 2 Rescue Prompt Megathread" ...    ;-)

What I would recommend is that each user experiencing a problem start a new thread with a descriptive title. Please boot to the Desktop or the Live CD Desktop and run meierfra's boot info script linked below. Paste the contents of the RESULTS.txt *in the first post*. We will need that information to help you.

[_http://bootinfoscript.sourceforge.net_]("http://bootinfoscript.sourceforge.net")

Having said that, last night I expanded the information in the [_[U]Ubuntu community Grub 2 doc_[/U]]("https://help.ubuntu.com/community/Grub2") regarding the rescue mode. I have read numerous posts this week with users unable to properly employ the *rescue mode*.

Here are some things to keep in mind regarding the *rescue mode*.

[LIST]
[*]Use the "set" command to review the current rescue mode settings.
[*]Use "ls" to see the partitions. You must determine the Ubuntu partition.
[*]Use "ls (hdX,Y)/boot" to inspect the partition you think is the Ubuntu partition. If you find the correct partition, it will show files and the *grub* folder.  (Example:  ls (hd0,5)/boot )
[*]Use "set prefix=(hdX,Y)/boot/grub  to set the correct path to the grub folder. This must be correct before you can use rescue commands or load the kernel.
[*]You must load modules before you can use them, and the *prefix* path must be correct.
[*]To load modules (if they load, no message): 
```

insmod normal help linux

```
[/LIST]

---

