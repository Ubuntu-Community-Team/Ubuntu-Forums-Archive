---
title: "HELP! How to recover vista Boot"
date: 2007-10-10
forum: Installation &amp; Upgrades
---

### Post by dennisros on 2007-10-10
Hi i installed PCLinuxOs, which uses Grub as a Bootloader just like Ubuntu. Then I was in Windows and deleted the partition with Linux, now i cant load windows, it only says that it failed with starting GRUB, How can I fix the Vista boot, I dont have a recovery CD, but I have a LiveCD for Ubuntu Gutsy, that is what im using now. Need to get this fixed fast.
So is there maybe a way to do a fixmbr in linux, or a fixboot so that i can start windows vista.

PLEASE HELP!!!

Another fix would help me to install Gutsy, the problem i have with it is that it says that "Migration Assistant couldn't unmount", it says that something is mounted and couldn't mount Migration. This happens after 88% of install. 

HELP!!

/Dennis

---

### Post by Steve1961 on 2007-10-10
I'm not sure what the "Migration Assistant couldn't unmount" is about, but if someone has a fix for this you just need to install Gutsy, which will resurrect Grub.  You can then boot into windows and download easyBCD.  This allows you to restore the vista boot sector, which you can also setup to boot Gutsy instead of using grub.

---

### Post by dennisros on 2007-10-10
Thanks for the aswer. But could solve the problem my self after a while. The problem I had was with this bug:       Bug #112672 in migration-assistant (Ubuntu)

"The second time through the install process, though, I guessed that the reason Migration Assistant couldn't unmount /dev/hda3 from '/suse' might be because /dev/hda6 was still mounted at '/suse/home' - so I opened a terminal window, manually unmounted /dev/hda6, and clicked 'Continue' on the Migration Assistant error box, and sure enough, everything was peachy."

After that i found that in terminal you go to root, and after that you type df to find which disk that Migration Assistant is occupying, and you type "eject "and the disk" for example "eject /dev/hda2/" and the i chosed continue in the installation process and it worked.

Thanks again

/Dennis

---

### Post by Steve1961 on 2007-10-10
Glad you managed to resolve the issue :)

---

### Post by r5ive on 2008-02-12
Hi, i´ve installed UBUNTU directly from a Working Vista, :confused: now i couldn't boot from vista and coudnt recover my files from Vista Partitions. tried to get it from a live CD, but still have the same problem. i need to recover my files fast.

Please Help Me!!:confused:

---

### Post by Steve1961 on 2008-02-12
What do you mean when you say you installed ubuntu directly from vista?  You install Ubuntu by booting from a CD, unless you mean you installed Wubi.  Anyway, what happened when you used the live cd to try and recover your files?

---

