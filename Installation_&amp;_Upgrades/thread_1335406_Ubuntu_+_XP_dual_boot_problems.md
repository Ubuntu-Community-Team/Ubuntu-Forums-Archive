---
title: "Ubuntu + XP dual boot problems"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by false_cognate on 2009-11-23
I decided to install XP so I could take advantage of Netflix's streaming service.

I'm running 9.10.

I took the live disc and used GParted to resize my main partition, shrinking it by 6 gigs for the new XP partition. I formatted the new one with ntfs.

First time I tried to install XP it didn't work, so I let it re-format the partition in ntfs thinking maybe XP didn't play nice with ntfs formatted by a different OS. It worked this time, and I was able to boot XP, although there seems to be redraw issues and the sound wasn't working.

At this point, I wanted to boot back into Ubuntu so I could just try the streaming using the VMware that I'd gotten from Synaptic earlier. Problem is, XP usurped GRUB and would only let me boot XP.

I ran the 9.10 live disc again and noticed that in GParted it was set to boot from the XP partition. I switched that to my Ubuntu partition.

When I tried to boot Ubuntu again, it won't even load Grub... it just says:
"No os found".

So, what I'm trying to find out here is whether I accidently nuked my 9.10 installation, or if (hopefully) Grub is just pointing in the wrong direction, or something else entirely.

I'm using the 9.10 live cd now, and I can mount my 9.10 partition; I can access most folders, but some have an X on them.

Please be patient with me; I haven't had to use the terminal extensively in a year, since Ubuntu has been so stellar and bug-free for me for a while now.

The computer is a Lenovo Thinkpad R61. I can try to give you any other info you need, eg my boot/grub/menu.lst

---

### Post by phillw on 2009-11-23
Hi,

sorry for the delay ... had forgotten the link .... anyways ... here it is   [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

It does exactly what it says & should get you up & running.

Post back If you still have a problem.

Regards,

Phill.

---

### Post by darkod on 2009-11-23
The step to make another partition marked as boot was the wrong one. After windows bootloader has erased grub on the MBR you have to use the ubuntu cd with Try Ubuntu option and restore grub.

If you had only 9.10 without previous version, you are probably using grub2. The steps are here:
[http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)

Scroll to number 2) Using Ubuntu 9.10 liveCD.

---

### Post by phillw on 2009-11-23
> **darkod said:**
> The step to make another partition marked as boot was the wrong one. After windows bootloader has erased grub on the MBR you have to use the ubuntu cd with Try Ubuntu option and restore grub.

If you had only 9.10 without previous version, you are probably using grub2. The steps are here:
[http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)

Scroll to number 2) Using Ubuntu 9.10 liveCD.

Okies, darkod ... I'll have a look at that one, dave pointed me to the one I currently post. It's not one of his, but does show the system as having the boot flag on the windows area.

Regards,

Phill.

---

### Post by darkod on 2009-11-23
Maybe I used too strong words. The move to mark root as boot maybe is not wrong, what I actually meant is that it's not needed to my knowledge.
He just needed to restore grub2 and even if the boot flag remained on xp partition it should have worked.
As for grub2 restore, there are quite few tutorials but I find this link has the shortest and most precise set of commands especially if someone is new to linux.
I hope they work, haven't used them myself because luckily I never needed to restore grub2 so far. :) Hope I'm not sending links with wrong info all this time.

---

### Post by false_cognate on 2009-11-23
@phil - I tried both options in the thread, here is the output in the terminal (as I don't think it worked, although I haven't tried to reboot yet):
```
ubuntu@ubuntu:~$ sudo grub
sudo: grub: command not found
ubuntu@ubuntu:~$ find /boot/grub/stage1
find: `/boot/grub/stage1': No such file or directory
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x97a5bb25

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         137       19729   148119300   83  Linux
/dev/sda2           19729       20541     6136830    7  HPFS/NTFS
/dev/sda3           20542       20673      997920    5  Extended
/dev/sda5           20542       20673      997888+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mkdir /media/sda1
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /media/sda1
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/sda1 /dev/sda1
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/grub/core.img' correctly

```

@darkod - I haven't tried those instructions yet because my install isn't a clean install of Karmic; I've upgraded (I think) twice since my last fresh install. Would it matter? Does grub2 look different than grub? (It didn't appear to look different after I upgraded, but I could be wrong)

---

### Post by phillw on 2009-11-23
> **darkod said:**
> Maybe I used too strong words. The move to mark root as boot maybe is not wrong, what I actually meant is that it's not needed to my knowledge.
He just needed to restore grub2 and even if the boot flag remained on xp partition it should have worked.
As for grub2 restore, there are quite few tutorials but I find this link has the shortest and most precise set of commands especially if someone is new to linux.
I hope they work, haven't used them myself because luckily I never needed to restore grub2 so far. :) Hope I'm not sending links with wrong info all this time.

You and me both - It's always a hard call when you don't have the 'box' in front of you. As you do, so do I - namely give the best information we can from what we are given.

You may not have read my attempt of Grub2 ... It's good for a giggle....

[http://ubuntuforums.org/showthread.php?t=1331465](http://ubuntuforums.org/showthread.php?t=1331465)

I learned loads !!!!   Thankfully, dave was on hand to help me out.

Phill.

---

### Post by phillw on 2009-11-23
> **false_cognate said:**
> @phil - I tried both options in the thread, here is the output in the terminal (as I don't think it worked, although I haven't tried to reboot yet):
```
ubuntu@ubuntu:~$ sudo grub
sudo: grub: command not found
ubuntu@ubuntu:~$ find /boot/grub/stage1
find: `/boot/grub/stage1': No such file or directory
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x97a5bb25

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         137       19729   148119300   83  Linux
/dev/sda2           19729       20541     6136830    7  HPFS/NTFS
/dev/sda3           20542       20673      997920    5  Extended
/dev/sda5           20542       20673      997888+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mkdir /media/sda1
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /media/sda1
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/sda1 /dev/sda1
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/grub/core.img' correctly

```@darkod - I haven't tried those instructions yet because my install isn't a clean install of Karmic; I've upgraded (I think) twice since my last fresh install. Would it matter? Does grub2 look different than grub? (It didn't appear to look different after I upgraded, but I could be wrong)

Forget it ...   You have a different problem .... bbs

---

### Post by darkod on 2009-11-23
OK, for checking the grub version the first thing on my mind is simply rebooting. Look above the grub menu and if it says something like 1.97 that grub2 (don't ask why :) ).

You tried using:

sudo grub-install --root-directory=/media/sda1 /dev/sda1

which would try to install it on the first partition, sda1, not on MBR (sda). Grub2 doesn't like being told to install on partition instead of MBR. Actually the warning message you got looks just like a warning about that.

See if above your grub menu it says 1.97 and use my link to try, I think it should work.

PS. Not that Phill is giving you bad links. :)

---

### Post by false_cognate on 2009-11-23
@Phil - I didn't use sda5 because in the thread you linked to he just uses it because it happens to be the partition with the Ubuntu installation (so in my case it would be sda1 instead).

@darkod - I can't check the grub version because grub won't even load! My computer boots and immediately goes to "No os found." I will try your link now, and let you know how it goes.

---

### Post by phillw on 2009-11-23
Section 12


[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

sda1 is yours...

Regards,

Phill.

---

### Post by phillw on 2009-11-23
> **false_cognate said:**
> @Phil - I didn't use sda5 because in the thread you linked to he just uses it because it happens to be the partition with the Ubuntu installation (so in my case it would be sda1 instead).

@darkod - I can't check the grub version because grub won't even load! My computer boots and immediately goes to "No os found." I will try your link now, and let you know how it goes.


In my pathetic defence, from reading your thread - I thought M$ was in primary partition & had boot rights. - Next time - I'll ask for a fdisk -l !!!!!

Lesson learned.

Rebuild as per drs's instructions on that thread. It may even spot your windows area, if not - we can sort that out later.

Phill.

---

### Post by phillw on 2009-11-23
btw, dark - have you managed to restore matrimonial harmony in the 'wife messing about' thread ? - I've lost the link to it.

Phill.

---

### Post by darkod on 2009-11-23
OK, I have learned something new. It seems you can check the grub version with grub-install -v  don't know if you need sudo in front, where I read it it was just like that. Try either way and at least that would show you your grub version.  Unless you've sorted the problem already.

---

### Post by false_cognate on 2009-11-23
I went through the instructions from the link that darkod showed, using the one for the live cd. They look similar to the thread that phil just linked me to, although I didn't unmount the partition before restarting.

So now Grub loads, but there isn't a list of OSs to boot from. It just gives me a command line, something like "<grub.sh>:" or something similar. I tried "boot hd0" and it wouldn't work.

I exited grub, and it took me to some master boot menu, showing all my boot devices. Problem is, after my Ubuntu partition it says "No valid operating system" or something similar. Also, it excludes my winxp partition from the list as well.

Hmmmm.

---

### Post by phillw on 2009-11-23
Having re-read his post and seen fdisk-l  I'm pretty sure he's on grub2 ... but, again, I was assuming and messed that one up :-(

I recall someting I was told, many years ago ...

Never assume, because ...
You make an '***' (donkey, 3 letters)
out of 'U'
and 'ME'.

Phill.

---

### Post by darkod on 2009-11-23
It might be missing the grub.cfg file or something. Do the same again and including the bottom part of the instructions:

```
sudo -i
mount /dev/sda7 /mnt
mount /dev/sda6 /mnt/boot
grub-install --root-directory=/mnt/ /dev/sda
mount --bind /proc /mnt/proc
mount --bind /dev /mnt/dev
mount --bind /sys /mnt/sys
chroot /mnt update-grub
umount /mnt/sys
umount /mnt/dev
umount /mnt/proc
exit
```That should update grub2.

PS. Phill, I took a very good sentence from one movie (not that good of a movie in fact): Assumption is the mother of all f**k ups. :) However, sometimes we can't do without it right?

---

### Post by false_cognate on 2009-11-23
I did as above, updating Grub. It seemed to work at the time, however when I rebooted the system Grub gives me the same prompt as before: "sh:grub>".

I am pulling out my hair!

---

