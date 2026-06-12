---
title: "Miserably failed to upgrade ubuntu to 16.4"
date: 2017-06-26
forum: Installation &amp; Upgrades
---

### Post by lr270 on 2017-06-26
I did not use my Ubuntu box for some time and decided to revive it. So, I tried to upgrade my old version 14 to 16.4 and miserably failed. Now I can't do anything.

Here is description. 

I have dual boot Ubuntu/Windows on my Dell laptop. Windows boots properly no problem and I have access to Internet.
On Ubuntu I can't do anything, right away after boot I am on terminal command line. More over, when I set boot from CD/DVD and created DVD with bootable iso file grub still goes to hard drive boot (on windows I can see that that drive contains iso file). I created CD on my other machine - Mac.

Another thing, if I try to run 'sudo apt-get update' command I'm getting message that I don't have Internet connection and system can't find specified URLs.

I'm at loss. 

Can anyone help?

Many thanks.

---

### Post by SeijiSensei on 2017-06-26
Are your personal files backed up somewhere?  If so, then I'd suggest installing 16.04 from scratch and copying back your files.  If they are not, and you have enough room on the Windows side, I'd open Windows and install [ext2fsd]("http://www.ext2fsd.com/?page_id=16") which will let you read Linux filesystems.  You can then back up your personal files on Linux before installing.

Note:  Windows doesn't support *nix filesystem features like permissions and such.  So this approach only works for things that are platform independent like photos or documents.  After you've installed 16.04 you should be able to see the Windows filesystem and copy back the files you saved.

If you're having problems with connectivity, plug the computer directly into your router with an Ethernet cable.  Even if your system can't detect the wifi card properly, it should still work over Ethernet.

---

### Post by lr270 on 2017-06-26
Hmm, I tried to boot machine from CD/DVD but failed. How can I reinstall Ubuntu? I do have backups.

---

### Post by CatKiller on 2017-06-26
> **lr270 said:**
> on windows I can see that that drive contains iso file

Then you didn't burn it correctly. You don't want a disc with an iso file on it, you want to burn a disc from the image that the iso file contains.

---

### Post by lr270 on 2017-06-28
I tried to read what other saying and all I see is to download .iso file and burn it on cd. What am I doing wrong? Thanks

---

### Post by CatKiller on 2017-06-28
[https://help.ubuntu.com/community/BurningIsoHowto#Burning_from_Mac_OS_X](https://help.ubuntu.com/community/BurningIsoHowto#Burning_from_Mac_OS_X)

---

### Post by johndough2 on 2017-06-28
Hi

The easiest way is to have a burner, cdburnerxp for instance and K3B , and select burn iso.  The compressed iso file is extracted and burned to dvd.  There are programs apps that will put it onto a USB stick so it can be removed and the stick reused after install.

 
 We have a Plan A, B and C.
 
 
 Plan A is to follow the excellent idea of a network cable plugged into your router.
 
 
 cd /
 sudo apt update
 sudo apt dist-upgrade (it&#8217;s a biggie and will take time).
 sudo apt install joe

 sudo chmod 755 /etc/apt/sources.list
 
 
 sudo joe /etc/apt/sources.list
 
 
 Change the word trusty, utopic (or whatever your repos are) to "zesty" in a few places.
 
 
 deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) xenial main restricted universe multiverse

 deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) xenial-updates main restricted universe multiverse
 deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) xenial-security main restricted universe multiverse
 
 
 deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) zesty main restricted universe multiverse
 deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) zesty-updates main restricted universe multiverse
 deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) zesty-security main restricted universe multiverse
 
 
 No mouse, so edit with arrow keys for navigation.
 
 
 Ctrl K + X   3 keypress Save and Exit.
 
 
 sudo chmod 644 /etc/apt/sources.list
 
 
 sudo apt update
 sudo apt dist-upgrade (it&#8217;s a biggie and will take time). You can always press NO.
 
 
 Plan B use something like &#8220;LinuxLive USB Creator&#8221; or &#8220;CDBurnerXP&#8221; and do a fresh install using your current .iso file.

 
 
 Plan C is to go to your local Sainsbury (UK mainly) and buy a Linux Mag with a cover disk for £6 and you will have a backup.  It might be something non-mainstream, but derived from Debian.

---

### Post by lr270 on 2017-06-29
Thanks, but my latest OS Sierra does not allow to drop on left side anything.

I was able to create bootable flash drive and all is fine now. I have 17.04 with all updates and still dual boot on my machine

---

