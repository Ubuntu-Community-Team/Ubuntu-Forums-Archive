---
title: "Reinstalling Ubuntu w/ encrypted home"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by Buchinho99 on 2009-11-27
Hi,

I currently have Karmic Koala beta installed but it keeps getting on my nerves so I would like to start with a fresh install.
Since I have my home partition encrypted (karmic standard install encryption) I would like to know how I can keep my stuff in the home partition without needing to push it to a disk and later after install push it back.

Thank you very much.

---

### Post by movieman on 2009-11-27
As I understand it, the files are encrypted with a key which is then encrypted with your password, so in theory so long as you use the same password you should be OK. There's also a program which will ask for your password and decrypt the key so that you can save it away somewhere in case your configuration gets screwed up.

Note that I haven't tried a reinstall in practice, so I'd still recommend backing up the unencrypted files beforehand.

---

### Post by Buchinho99 on 2009-11-28
Thank you movieman, but that is not the case.
When trying to install a "fresh" version using the GUI Installer it cannot access the encrypted home partition...

So I have to wait for somebody else who did the trick!:sad:

---

### Post by mdebusk on 2009-11-29
> **Buchinho99 said:**
> Since I have my home partition encrypted (karmic standard install encryption) I would like to know how I can keep my stuff in the home partition without needing to push it to a disk and later after install push it back.

I've done it. I didn't take notes, so I can't offer you a step-by-step, but I can tell you it's a PITA.

Copy your fstab and crypttab to a flash drive. 

Install Karmic and let it create a /home partition in the default location. After it's up and running, you have to install eCryptFS. You *should* be able to restore fstab and crypttab, reboot, and have your old /home back. Seems to me I recall having to jump through another hoop or two, though.

---

### Post by shaggy999 on 2009-11-29
Which type of encrypted partition are you talking about? Are you talking about a dedicated partition made with LUKS or are you talking about the ecryptFS option that's used when you select "automatically encrypt my home directory" during install?

The reason why I ask is because I don't think the ecryptFS option actually puts the files on a seperate partition by default. So if you wipe your install you wipe your home directory and all your encrypted files.

Also the recovery procedure for each is different.

---

### Post by mdebusk on 2009-11-30
> **shaggy999 said:**
> Which type of encrypted partition are you talking about? Are you talking about a dedicated partition made with LUKS or are you talking about the ecryptFS option that's used when you select "automatically encrypt my home directory" during install?

I'm glad you asked. I used cryptsetup, following [these instructions on the Command Line Warriors blog]("http://commandline.org.uk/linux/encrypt-for-xmas/")... not eCryptFS.

I have an Asus Eee 900 with a 4 gig internal drive and a 16 gig SD card. I use the external card as my /home. The entire thing is encrypted, and has been since I installed Hardy on it. Since then, I've installed Jaunty twice and now am running Karmic. (I don't use apt-get dist-upgrade; I do a fresh install.)

---

### Post by shaggy999 on 2009-11-30
It sounds to me like the easiest way to do it is to just simply install the entire OS on your main drive and then after you reboot into the OS you will want to install luks and setup the files, change crypttab and fstab and then just shred the old home files on the main drive. The only other way to do it that I know of is to chroot into the new install right after the installer completes and do essentially the same setup. So really you're just making it easier on yourself by doing it after you reboot.

---

### Post by itmozart on 2010-02-09
I was wondering a similar thing.
Providing that my crypttab is empty (my home folder has been encrypted chosing the option installation-time (distro=Karmic)), and that I have separate partitions mounted on root and /home, what's going to happen if for some reason the linux partition blows up?
If it's unrecoverable (salt, I suppose?), what should I back up in order to prevent this to happen?

Saverio

---

