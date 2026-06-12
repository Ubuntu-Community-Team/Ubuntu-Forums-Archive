---
title: "Help!!  Can't boot 9.10"
date: 2011-01-01
forum: Installation &amp; Upgrades
---

### Post by SVEN1 on 2011-01-01
I have been running Ubuntu 9.04 for the past year. Tonight decided to upgrade to 9.10 thru update manager. Every thing regarding the install seemed fine until the request to restart the computer. I hit the restart and it will not boot up. Computer goes thru the normal restart screens.

Screen flashes with bios info--no hard drive detected, then proceeds to show booting from hd, then loads grub stage 1.5 (not grub 2)and screen goes blank.

Any ideas how to fix this??

---

### Post by Rubi1200 on 2011-01-02
Hi,
what graphics card do you have installed?

The other thing that would really help is if you could run the boot info script linked at the bottom of my post (instructions included).

Post the results back here.

By the way, have you tried booting into recovery mode?

---

### Post by SVEN1 on 2011-01-02
> **Rubi1200 said:**
> Hi,
what graphics card do you have installed?

The other thing that would really help is if you could run the boot info script linked at the bottom of my post (instructions included).

Post the results back here.

By the way, have you tried booting into recovery mode?

I just managed to have a 8.10 live cd, downloaded 9.10, transfered to a usb and burned a Iso cd. Right now running off the live iso cd. was able to check my hard drive and all my files etc are sitting there and looked into the boot folder and found grub stage 1.5. Never had problems with my graphic card ATI XT1900Xtx. So I am semi operational running the live CD

At least I know my 9.04 Ubuntu contents are safe on the hard drive, just need to get the right Grub to boot.

No haven't tried the recovery mode yet. Still learning the terminal. Any help is appreciated. Thanks

I just loaded the scrip to my jump drive and will run the script later on. Wife needs to work on the desk here.

---

### Post by Rubi1200 on 2011-01-02
This is more than likely a GRUB issue. To confirm that this is the case, please use the LiveCD and run the boot info script I mentioned previously.

Thanks.

---

### Post by SVEN1 on 2011-01-02
Ran the script

---

### Post by drs305 on 2011-01-02
If you are ready to take the plunge to Grub2, you can boot the LiveCD, purge grub and install G2. It shouldn't have any problems dealing with your system. 

Here is the link to the 'chroot' procedure:
[HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099")

In Step 1c, the partition to mount is "sda1". In Step 3, purge only "grub grub-common", omitting "grub-pc" since it's not installed.

Grub2 is quite a bit different than Grub legacy, but if you decide to install G2 you might want to take a look at the "G2-Basics" or "GRUB2" links in my signature line for an introduction.

---

### Post by SVEN1 on 2011-01-03
Sorry to say, it would not work.

rather than spending too much time trying to make it work. I downloaded Ubuntu 10.04, burned as iso disc and did a fresh install after backing up my documents and photos.

All is good again!!!

---

