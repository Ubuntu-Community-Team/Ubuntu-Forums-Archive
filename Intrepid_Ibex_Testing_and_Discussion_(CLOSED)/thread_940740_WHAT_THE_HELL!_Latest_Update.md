---
title: "WHAT THE HELL! Latest Update"
date: 2008-10-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by doubad on 2008-10-07
So I wake up this morning and I'm prompted with an update as I am most mornings. It's usualy some kind of improvement, however, today I was terribly dissapointed. There was an x-org core update somewhere in there and when I restarted, I get nothing but white screen. I'm writing this from windows XP right now, as I am a dual booter. I've tried booting from "last successful boot" in the grub and I've tried doing some kindof "gnome without script" dealy at login and that didn't work.  I'm out of ideas.

---

### Post by overdrank on 2008-10-07
> **doubad said:**
> So I wake up this morning and I'm prompted with an update as I am most mornings. It's usualy some kind of improvement, however, today I was terribly dissapointed. There was an x-org core update somewhere in there and when I restarted, I get nothing but white screen. I'm writing this from windows XP right now, as I am a dual booter. I've tried booting from "last successful boot" in the grub and I've tried doing some kindof "gnome without script" dealy at login and that didn't work.  I'm out of ideas.

Hi and are you using intrepid?

---

### Post by doubad on 2008-10-07
Yes, Forgot to mention.
I'm in a bit of a panic. I need my Resume.

---

### Post by overdrank on 2008-10-07
> **doubad said:**
> Yes, Forgot to mention.
I'm in a bit of a panic. I need my Resume.

Ok you can expect issue like this when testing. :)  What is the model of the graphics card and have you tried to reconfigure your xorg. If you have tried the last known config then that would be my next shot.

---

### Post by doubad on 2008-10-07
I've got a Radeon x1600.
I have not reconfigured my xorg.

---

### Post by Archmage on 2008-10-07
Telling us what graphic card you are using might help.

---

### Post by stephantom on 2008-10-07
> **doubad said:**
> Yes, Forgot to mention.
I'm in a bit of a panic. I need my Resume.

If it's that urgent, just boot into Windows, install a [driver for the ext2 file system](http://www.fs-driver.org/) and grab it from there.
But you shouldn't really use Intrepid in a production environment with critical data yet. You knew that, right?

---

### Post by doubad on 2008-10-07
I found another copy lying around anyways, no worries with the resume.

But I still would like to fix Intrepid

---

### Post by dabl on 2008-10-07
I didn't get White-Screened, but I did have a broken video driver and my snd-hda-intel sound driver mysteriously disappeared from /etc/modules, both as a result of last night's updates.  I reinstalled my Nvidia driver (177.78 ) and the sound driver, and it is back to "normal", if there is such a state for Intrepid.

There are numerous other reports of the white screen problem -- you're not alone:

[http://kubuntuforums.net/forums/index.php?topic=3098021.msg148839;topicseen#msg148839](http://kubuntuforums.net/forums/index.php?topic=3098021.msg148839;topicseen#msg148839)

---

### Post by Kevbert on 2008-10-07
Similar problem here. I'm using a Nvidia 7600GS. I can't boot to the new -5 kernel but I can boot to recovery mode, reset xorg, no damaged packages and can start normally.  Then try to boot first Kubuntu grub item and PC hangs during boot normally when checking battery (on a desktop ?) and goes no further. May try burning an -5 kernel ISO.

---

### Post by doubad on 2008-10-07
I'll try recovery mode tonight when i get back home

---

### Post by Gedemins on 2008-10-07
last update really messed things up for me. 
1. ATI x1900. no white screens etc. but desktop effects stopped working. if I try turning them on by right clicking desktop > change background > visual effects the message of "searching for drivers" appears and then it says effects cannot be enabled. if i try typing compiz --replace, it says i'm not whitelisted. 
2. another thing - mp3 won't play in rhythmbox after updates, although skype sound or ubuntu sounds work, and i'm able to play music in vlc. 

so what is wrong with those updates? shouldn't they improve the system, not damage it? because the more updates for me from alpha6, the more problems i have to fix manually.. disappointed..

---

### Post by Gina on 2008-10-07
If you prefer a Linux system (Ubuntu) but would like to test Intrepid, I suggest a triple boot setup.  Windows, Hardy and Intrepid.  Then if Intrepid won't boot (not uncommon) you can access all your files from Hardy.  Apart from hard drive space, there is no practical limit to how many operating systems you can have installed.

I test several flavours of Ubuntu and have over a dozen partitions on my PCs.

---

### Post by Kevbert on 2008-10-07
Ubuntu as opposed to Kubuntu seems to work well with the -6 kernel.  If I run up the old -4 kernel in Kubuntu and do a dist-upgrade to -6 it might work....or will it just see the -5 kernel and only upgrade that ?

---

### Post by doubad on 2008-10-08
I can't seem to get past the white screen, I'm simply not good enough at this stuff to fix it myself. I think I'm going to just wait for the next update to hopefuly fix it.

---

### Post by Vietman on 2008-10-08
That last update just FUX0Red my Internet connection. I booted up with a Linux Mint LiveCD, but I'm not sure how to fix it as the GUI is not responding well, and I'm a newbie to ifconfig.

---

### Post by magicmanfk on 2008-10-08
> **Gedemins said:**
> last update really messed things up for me. 
1. ATI x1900. no white screens etc. but desktop effects stopped working. if I try turning them on by right clicking desktop > change background > visual effects the message of "searching for drivers" appears and then it says effects cannot be enabled. if i try typing compiz --replace, it says i'm not whitelisted. 
2. another thing - mp3 won't play in rhythmbox after updates, although skype sound or ubuntu sounds work, and i'm able to play music in vlc. 

so what is wrong with those updates? shouldn't they improve the system, not damage it? because the more updates for me from alpha6, the more problems i have to fix manually.. disappointed..

I have the same problem, where desktop effects don't work. I have intrepid as well and it started just after the most recent updates. I'm using an ATE x1300 mobility graphics card. I assume the next update will fix this but any insights would be appreciated.

---

### Post by MaX on 2008-10-08
This thread is the perfect example of why you should NOT run Intrepid before it's released on the machine you do work on...

---

### Post by waspbr on 2008-10-08
The White screen is a bit of a typical annoyance for radeon users, check this out:
[http://ubuntuforums.org/showthread.php?p=5883283#post5883283]("http://ubuntuforums.org/showthread.php?p=5883283#post5883283")

hope it helps

---

### Post by Kevbert on 2008-10-08
> **MaX said:**
> This thread is the perfect example of why you should NOT run Intrepid before it's released on the machine you do work on...

Agreed.  It's in beta, that's B for bugs, but as part of a multiboot system it should be OK.  After all the more people that test it the more bugs will be found by official release time.

---

### Post by Kevbert on 2008-10-08
> **doubad said:**
> So I wake up this morning and I'm prompted with an update as I am most mornings. It's usualy some kind of improvement, however, today I was terribly dissapointed. There was an x-org core update somewhere in there and when I restarted, I get nothing but white screen. I'm writing this from windows XP right now, as I am a dual booter. I've tried booting from "last successful boot" in the grub and I've tried doing some kindof "gnome without script" dealy at login and that didn't work.  I'm out of ideas.
If you can boot the old -4 kernel (hopefully that still works).  Then enter the following in terminal:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
You should now have the new -6 kernel which came out yesterday evening.
It looks like the -5 kernel is a bit of a problem, but the new -6 kernel is fine at least for me in Kubuntu.

---

### Post by beercz on 2008-10-08
> **MaX said:**
> This thread is the perfect example of why you should NOT run Intrepid before it's released on the machine you do work on...
And also a good reminder to keep backups!

---

### Post by poopypants on 2008-10-09
the update broke sound for me as well--Kevbert's sudo upgrade/update steps didn't fix so I'll have to tinker more or wait for the fix.

this is ubuntu 8.10 current-as-of-2-minutes-ago using the asus p5b deluxe on-board sound. worked before the update, doesn't work now. Funny because I can hear audio until it gets into gnome if there's a dvd spinning in the drive.

despite this--after years without linux--this is way cool--will probably make the leap over from windows if adobe air/flash works on it....

---

### Post by winc87 on 2008-10-09
I thought the latest update broke my IBM Thinkpad T40 sound as well but I double clicked the sound applet and found that the PCM volume is already muted. I set it to highest and I got back the sound finally.

---

### Post by bigdoby on 2008-10-09
my sound is broken too (and PCM is not muted for me...)
i don't understand what broke the sound, after the login in gnome it works.. :confused::confused:

---

### Post by philinux on 2008-10-09
Logout and login should fix it. Or reboot.

---

### Post by bigdoby on 2008-10-09
no, it doesn't fix anything... every movie player stops at 00:00 seconds and rhythmbox does the same thing

---

### Post by poopypants on 2008-10-10
was able to fix this just now changing all the sound drivers to OSS (System > Preferences > Sound), updated thru the update manager then changed all the options to the OSS choice, rebooted, audio seems to work everywhere

sweet! ubuntu rocks again.

---

### Post by poopypants on 2008-10-10
yesterday's sound+gnome updates seem to allow setting back to autodetect--sound appears to be fixed

---

