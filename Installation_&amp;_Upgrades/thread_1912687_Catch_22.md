---
title: "Catch 22?"
date: 2012-01-21
forum: Installation &amp; Upgrades
---

### Post by eilandman on 2012-01-21
hi,

i'm not a computer illiterate, but i'm stuck here. really. i've a dual boot system windows xp + kubuntu 8.10 intrepid. xp doesn't boot anymore, and kubuntu doesn't allow me to install new software anymore, for one reason or another that i don't get. so this is a pc that's bound to die. 

things i've already tried to do but won't work:
- booting with an xp installation cd
- deleting partitions from within kubuntu

i would like to format my pc entirely and install a clean os, windows xp preferably.

somebody ever been in the same vicious circle? people smarter than me?

thanks!

---

### Post by whatthefunk on 2012-01-21
Your Kubuntu version is horribly out of date.  You should upgrade to 10.04 at least.  maybe try a fresh Kubuntu install and then a fresh XP install?  What kind of hardware do you have?

---

### Post by eilandman on 2012-01-21
thanks for the swift reaction 

i know, i know. another thing i've tried but that won't work. can't upgrade. gives error messages all the time. can't install anything new and can't upgrade. 8.10 simply refuses to do it.

sorry, how do i check my hw specs in 8.10?

you mean boot with a 10.04 cd? not sure that will work since booting with an xp cd won't work either. hd failure maybe?

thanks

---

### Post by varunendra on 2012-01-21
> **eilandman said:**
> you mean boot with a 10.04 cd? not sure that will work since booting with an xp cd won't work either. hd failure maybe?
It doesn't matter what is installed 'on the hard disk' if you are booting from a CD, and are ready to wipe out everything on the drive to make a fresh install.

So I don't see any "catch 22" here.

What kind of failure occurs when you boot from XP installation disc? Is it unable to 'see' your hard disk, or isn't able to boot at all?

If you can still boot into Kubuntu, then the hdd is obviously not 'gone' yet. Not sure what's wrong with XP (maybe some BIOS issue, like accidentally enabling 'ahci'??), but an Ubuntu CD 'should' be able to not only see, but also install itself on the same drive if one is already running from it. Things you should try (in the given order)-

[LIST=1]
[*]Reset BIOS to default, and retry to boot with the XP CD
[*]Download Ubuntu live cd (looks like you'll need 32 bit version), burn it to a cd or create a live USB from it, and try booting from that cd/usb.
[/LIST]
If the system is too old, I'd recommend using [Xubuntu]("http://www.xubuntu.org/getubuntu") (any of 11.10 or 10.04) instead of either XP or default Ubuntu. It'll be much lighter and faster.





As for checking hw specs in 8.10, isn't **lshw **command available in it? If not, try **lspci -v**. You can redirect the output to a file if it is too long to read on the terminal. For example-
```
sudo lshw > ~/Desktop/hwspecs.txt
```

---

### Post by snowpine on 2012-01-21
I recommend:

1. Boot with any Linux Live CD and use Gparted Partition editor to delete your partitions and create your new partition scheme

2. Boot with Windows CD and install Windows (I am not an expert on this step) OR install a current Kubuntu (10.04 or newer) OR install both and have a dual boot.


If you have hardware issues like a broken CD-ROM drive or failed hard drive, you need to fix them before you can complete steps 1 and 2. :)

---

### Post by wieman01 on 2012-01-21
Just as a sidenote... You can't install anything because the version of Ubuntu you are running is no longer supported. The software repositories have been disabled.

---

### Post by eilandman on 2012-01-23
thanks all. resetting bios to default did not allow me to boot xp properly. i got stuck on a black screen saying blèh blèh or something of the sort like some sheep laughing me in the face.

so i booted with an ubuntu 11.10 install cd. the installer crashed suggesting several possible problems among which a broken hd was one, and the install cd burnt at maximum speed was another. 

so i am now burning an install cd at Middle Ages speed and will retry will that. all very tiresome, this. where are the haydays where a boot cd just ... booted?

---

### Post by eilandman on 2012-01-23
as to the question why this is a catch 22: i want to install something new. but i got a system that won't let me. so i need to install something new in order to be allowed to install something new. but i can't. for all that i know i call that a catch 22.

---

### Post by snowpine on 2012-01-23
> **eilandman said:**
> thanks all. resetting bios to default did not allow me to boot xp properly. i got stuck on a black screen saying blèh blèh or something of the sort like some sheep laughing me in the face.

so i booted with an ubuntu 11.10 install cd. the installer crashed suggesting several possible problems among which a broken hd was one, and the install cd burnt at maximum speed was another. 

How can we help if you do not tell us the error messages? That is the only "catch 22" I see here.

---

### Post by eilandman on 2012-01-23
there is no error message.
when i boot with an ubuntu cd there's just a black screen with the cursor blinking.
boot menu doesn't appear anymore so i can't even get to try to boot xp anymore either.
 i'm sorry that there's is no more information that i can give.

---

### Post by whatthefunk on 2012-01-23
Again, what is your hardware?  If you were running XP, Im guessing its on the older side?  How old is your PC?  Model number?  It could be that your hardware cant handle the installation disk.  Maybe try an alternate install .iso.

---

### Post by varunendra on 2012-01-24
> **eilandman said:**
> there is no error message.
when i boot with an ubuntu cd there's just a black screen with the cursor blinking.
There are a few possibilities that may cause such behaviour with a live cd. But..
> **eilandman said:**
> boot menu doesn't appear anymore so i can't even get to try to boot xp anymore either.
- if this is happening to the installed system as well (without involving the cd), then a hardware failure or a loose connection seem more probable reasons. Yes, a failing hdd is one of these possible reasons. If you can, please disconnect the hdd, and try again to boot with the cd. If it boots ok this time, we can be sure it is the hdd itself causing all the trouble. A few more questions:

[LIST]
[*]Do you have access to another computer where you can verify if the cd itself is ok?
[*]Hardware specs: CPU, RAM, graphics
[*]Version of ubuntu live cd (with less than 1GB RAM, you should try [Xubuntu]("http://www.xubuntu.org/getubuntu") rather than default Ubuntu 11.10)
[*]While trying to boot **without** cd, do you see initial BIOS messages or is it just the black screen from the very beginning?
[*]Is this 'black screen' thing same with and without cd or is there a difference between the two cases? Details if there is a difference.
[/LIST]
Hope answers to these may help us pin-pointing the problem.

---

### Post by mastablasta on 2012-01-24
also here is how you upgrade the End of life Ubuntu release to a newer one: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by eilandman on 2012-01-25
thank you all for the new suggestions. will check them a s a p and get back.

---

### Post by wieman01 on 2012-01-28
If everything fails, try the alternate install. It's a different Ubuntu image you can download.

---

