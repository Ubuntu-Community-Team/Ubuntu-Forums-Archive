---
title: "cannot boot into karmic after pkg update via synaptic"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by t54 on 2009-12-29
My computer is an i386, which had an original install of jaunty, then upgraded to karmic and now with several later kernel updates. 

This machine just developed a boot failure problem after attempting to update all application pkgs in synaptic.  

Synaptic completed most -but not all- of its recommended application upgrades. Not all were installed even after repeating the exercise several times.

However, everything on the system still ran completely OK -- ***until I tried to reboot.** *

[LIST=1]
[*]Choosing the latest version of karmic in GRUB, led to a screen frozen with the Ubuntu logo. 


[*]Trying 'Recovery' mode in GRUB resulted in some activity which halted with this msg :
[/LIST]

[INDENT][B]....  /sbin/init: relocation error: /sbin/init: symbol __abort_msg, version GLIBC_PRIVATE not defined in file libc.so.6 with link time reference
Kernel Panic - not syncing: Attempted to kill init! ....[/B][/INDENT]

The computer then just freezes  with the screen displaying the above error msg.

The foregoing results occurred no matter which version of karmic one chooses in GRUB, ie, the earlier installed karmic kernel versions. A power off hard reboot is then necessary to return to GRUB. 

I am making this post via a Fedora LIVE CD.  My karmic install -with all its installed applications and data files- is unusable.

Would be most grateful for a quick solution. I sincerely hope it does NOT involve a total new install of karmic with data loss.

---

### Post by stlsaint on 2009-12-29
im sorry i cant help more with situation but it would seem that a fresh install of karmic would be best. As for the files...you should be able to mount them using ubuntu livecd and recovery files over to external hdd. if this is an option you would like please post back for step by step instructions.

---

### Post by t54 on 2009-12-29
> **stlsaint said:**
> im sorry i cant help more with situation but it would seem that a fresh install of karmic would be best. As for the files...you should be able to mount them using ubuntu livecd and recovery files over to external hdd. if this is an option you would like please post back for step by step instructions.

Tried to back up home folder but did not have permission to copy it to external harddrive. This may be because I am compelled to run Fedora LIVE CD. Cannot burn karmic ISO as Fedora will not eject whilst it is the running OS.   Your suggestions are welcomed.

---

### Post by stlsaint on 2009-12-29
Was the ubuntu cd you used for installing a live cd or alternate cd? meaning did live as in gui? if so than boot to that and mount your hdd to /mnt dir or create a new one.../mnt/ext or whatever name you want to give it. also do you only have one hdd in system? and are you dual booting? just a few questions before i start giving step by step instructions.
also try booting into ubuntu livecd and under Places look for the hdd and click on it to mount it. Then you should be able to pull files over to external hdd. (make sure ext hdd is connected before you boot into livecd)

---

### Post by t54 on 2009-12-30
> **stlsaint said:**
> Was the ubuntu cd you used for installing a live cd or alternate cd? meaning did live as in gui? if so than boot to that and mount your hdd to /mnt dir or create a new one.../mnt/ext or whatever name you want to give it. also do you only have one hdd in system? and are you dual booting? just a few questions before i start giving step by step instructions.
also try booting into ubuntu livecd and under Places look for the hdd and click on it to mount it. Then you should be able to pull files over to external hdd. (make sure ext hdd is connected before you boot into livecd)

Many thanks for your quick and kind replies.

Original Ubuntu install was from jaunty LIVE CD.  Then upgraded the original install internally via updater to karmic when it was released, since then have updated as new kernel versions were released.

Only 1 internal HD, it is formatted in NTFS, it has factory winXP on it but it was never installed. Ubuntu is on, of course, a separate partition, sda3.

I do not have a karmic CD; have the ISO but have not been able to burn it for the reason given above. I do have a jaunty CD. 

No problem seeing the root, home and other directories; but cannot copy them because of 'no permission'.  Tried sudo -i in terminal but no success in getting root access.

---

### Post by t54 on 2010-01-04
see post instantly below

---

### Post by t54 on 2010-01-05
**UPDATE:**

1. Have obtained a karmic live CD and run it.

2. Also have mounted and backed up my home folder located on unbootable karmic HD install.

3. This appears to not be a GRUB problem per se. GRUB installed on this machine is the legacy version, which I have established by the absence of a grub.cfg file. On boot GRUB appears but after a selection of any version of karmic is made, the boot routine starts and then freezes up with the error msgs first reported and posted above.

4. Trying to update the karmic HD install *from live CD* has not been successful, even though I have used root to access root directory in HD karmic install folder and run synaptic, aptitude, as upgrade, update, etc. So if there are corrupted or missing kernel files causing the boot failure, I cannot presently sort out how to identify, update or replace them.

Help would be greatly appreciated on how to restore and boot the Ubuntu karmic kernel installed on my harddrive.

---

### Post by lemming465 on 2010-01-06
When you tried to update from a live CD, did you use *chroot* first?

---

### Post by kansasnoob on 2010-01-06
You might want to compare notes here:

[http://ubuntuforums.org/showthread.php?t=1373916](http://ubuntuforums.org/showthread.php?t=1373916)

It seems that some got a partial upgrade today that hosed things.

---

### Post by t54 on 2010-01-07
Many thanks to all who have replied!

@lemming465
I tried unsuccessfully to use your instructions at:
Re: system restore on 9.10
[http://ubuntuforums.org/showthread.php?p=8612003](http://ubuntuforums.org/showthread.php?p=8612003)

sudo -i
mkdir /media/root
mount /dev/sda3 /media/root # use whatever your root partition is if it's not sda3
cd /media/root
for f in sys dev proc ; do mount -o bind /$f $f; done
chroot .
aptitude clean
aptitude update
aptitude full-upgrade -f

But I am rather new at Linux so I cannot promise I was able to follow them faithfully.

@kansasnoob
The link you posted is very interesting, including the detailed internal links re mount, unmount, exit commands, etc. Executing the chain of commands there and adding in the update context might be a bit advanced presently for me without further assistance.

Am I correct in presuming my problem in using the live CD has been a failure to (bind?) the HD karmic install drive and thus am not  updating it? I thought I had mounted it but perhaps I omitted a critical step?

I have just succeeded in using a karmic *alternate* live CD in making a permanent (not live) install on a USB stick and running it. The boot loader for this device is installed ONLY on the USB to avoid creating a further problem with the karmic HD install and its boot loader.  Can I also mount and update the karmic HD install from this USB device or must it be a 'live CD'?

It was a nightmare configuring many of the software applications on my karmic HD install and I would mightily like to avoid repeating that experience by being able to restore that install to a bootable condition.  They all worked great until this 'update/upgrade' abortion occurred.

PS: I recall that when the update manager was repeatedly failing to complete the updates, it was incorrectly reporting that 'The package information was last updated 65 (SIXTY FIVE!) days ago'.  In fact, the system was checked for updates and they were installed almost every day as available.  

Could there be a corrupted 'update database' or config file that is causing the errant update behaviour?  This is a question that needs to be answered as it appears that incomplete or conflicting updates could easily cause boot failures.

---

