---
title: "GAG: &quot;boot sector not found or invalid&quot; on new install"
date: 2011-06-17
forum: Installation &amp; Upgrades
---

### Post by dochawk on 2011-06-17
I gave up on the old install after a jaunty/kde3 => natty jump left it without a guy.

I've tried a fresh natty install, which seems to succeed, but get "sector not found or invalid" from GAG on attempted boot.

I've instructed the installer to use hda5 (/) three times, and hda7 (/boot) one time.  I get this message every way I try.

I thought I'd successfully posted this message yesterday, but apparently not . . .

---

### Post by Herman on 2011-06-18
You heed to install GRUB to the PBR or even LiLo instead if you really can't install GRUB there.

You should be able to install GRUB to the first sector of your Ubuntu partition by booting with a Live CD or USB, mounting your Ubuntu installation's file system and running 'sudo grub-setup --force -d /media/ubuntu/boot/grub /dev/sda7',
```
sudo grub-setup --force -d /media/ubuntu/boot/grub /dev/sda7
```Where: 'ubuntu' is the name of your mount point in /media', if you have neglected to set a user friendly name for your file system this will probably default to a UUID number instead.
Where: '/dev/sda7' is your Ubuntu /boot partition.

It used to work the last time I tried but that was a long time ago, so I hope things haven't changed too much.

---

### Post by dochawk on 2011-06-19
It seems that the install wasn't completing, or even coming close, before offering to reboot.  It was failing before even trying to install grub.

Identical results on two different machines, both satellite l305.

The md5 sum on my iso doesn't match the one listed at cs.Utah.edu.  I get the same md5 from the ubuntu site and the Utah mirror after downloading.

The kubuntu 11.04 cd had the same problem, and behaved identically, on the one machine I tried it on.

I finally got a working installation from a combination of the alternate ubuntu cd and experience from 20 years ago on debian installations.

What finally worked was repeated application of aptitude.  Each pass would manage to configure a few more files; it took a half-dozen or so.

*that* got me far enough that apt-get update & upgrade were able to (with a couple more passes get me too fully  installed.

I'm really not sure where I should be posting this description for th right folks to find it . . .

Thanks

hawk, who doesn't see a way to mark this [solved]

---

### Post by Herman on 2011-06-19
Oh, okay, wow, what an ordeal! I'm glad you persevered and were able to win through in the end. 

Regards, Herman

---

### Post by dochawk on 2011-06-19
Yeah' I've learned this stuff over the years.

It was debian 1.0, I think, that was delayed for a bizarre bug I found (something about these machines I was instLling on that would hang on alternate boots . . . )

Hey, I serviced this one without resorting to dpkg . . . 

:)

Given that I'm getting this result on two machines of the same model, though, it probably should be sports to someone or another (and th bad checksums or images, too)

hawkp

---

