---
title: "Lucid Lynx and WinXP: Dual booting with 2 hard drives"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by Gyanos422 on 2010-04-30
Ok, so this is a question and an experience.

First, I downloaded the image from the website AND from the Torrent. Burned the first to the disc with ImgBurn (on WinXP..its the only program i use to burn images and never had a bad burn). it didn't boot properly. I burned at the slowest speed i could as i always do for important discs.  Well, it didn't boot right. So i tried the other copy i downloaded. Same result, didn't boot properly.

SO i put in my copy of 9.10 and installed that. From there i just chose to upgrade from the Update manager and (although slow as hell) it upgraded with no problems. 

[note: i swapped out hard drives so not to damage my Windows XP setup which has lot of important stuff.  I'm not looking to make a 100% switch to Ubuntu but i'm tired of XP. I only need to use it for certain programs that do EXACTLY what i want them to do, that i haven't found yet for Ubuntu...namely a program to create dvds (like ConvertXtoDVD) that will make a menu and convert the movie files to dvd format]

What i want to do is use Ubuntu 10.04 to boot by default but give me the option to boot from the 2nd hard drive which contains WinXP.  There was a really easy way to do this in 9.04 but in 9.10 grub2 came along and the method changed.

Anyone that can help?  I see there's a bunch of other questions with answers that involve partitioning hard drives which i have no interest in doing.

Thanks

---

### Post by ladypcer on 2010-04-30
Two hard drives here too. XP on one and 10.4 on the other. My 10.4 install saw the XP drive and listed the choice at boot. I didn't do anything special.:confused:

---

### Post by carl4926 on 2010-04-30
First off - the Linux Application 'Devede' will make up your dvd's.

Your question is not clear to me about booting. because Ubuntu will boot either OS from the Grub menu. By default Ubuntu will be the default OS to boot. And it doesn't matter that XP is on a different HD. But you should ideally make the Ubuntu HD first in the BIOS boot order and install grub to it's MBR (You should have it this way when you install Ubuntu rather than change it later), this leaves XP MBR intact.

---

### Post by Gyanos422 on 2010-04-30
I will hook them both up and see if it detects them.  If this works, could someone tell me where to edit the boot menu?

---

### Post by carl4926 on 2010-04-30
No need to edit

But you need to explain how you have been booting. What Ubuntu are you using. When I know this I can explain more.

---

### Post by Gyanos422 on 2010-04-30
I've been using XP on a 100GB hard drive with a 60gb slave.  I unhooked the winxp hard drive and installed Ubuntu 10.04.  I started using Ubuntu at 9.04 and to boot from seperate hard drives you needed to edit the menu.lst file and insert this: 

```
title Microsoft Windows XP
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

But when 9.10 was released, this was changed because of Grub being changed in the release so it had to be done differently. I didn't bother finding out then, so i forgot about it.  But I like 10.04 and would really like to use it mostly full time, but i still need windows and would like it to be easier to switch back and forth without swapping drives in and out because my wife needs to use windows too (and she wouldn't understand swapping anyway)

so to be clear, I want a boot menu that will give me an option to boot to WindowsXP or boot into Ubuntu if no action is taken. But each OS is on its own hard drive.

---

### Post by Gyanos422 on 2010-04-30
Oh yea, I plugged my WinXP hard drive back in (as slave) and it didn't give me an option to choose an OS. just went right to Ubuntu.  

I don't know if its related, but when it started Ubuntu up again, the bars at the top and bottom were blank. No Ubuntu button, shutdown button or anything.  Now there's nothing there at all and i can't launch anything. Had to shut down and restart with the XP hdd because I dont know how to replace it....I may end up doing a fresh install to try to get things back to default..

---

### Post by carl4926 on 2010-04-30
The difference is the old Grub (Grub Legacy) was replaced in 9.04 with Grub2. Grub2 is also used in 10.04

I would make sure you set the Ubuntu HD first to boot in BIOS. When you re-install Ubuntu will pick up windows and add it to the grub menu. 
If these are old PATA IDE drives (I say this because you mention slave), there is no need for slave setting. Both should be master.
And don't keep unplugging the HD's, because it switches boot order settings.

---

### Post by kansasnoob on 2010-04-30
> **Gyanos422 said:**
> Oh yea, I plugged my WinXP hard drive back in (as slave) and it didn't give me an option to choose an OS. just went right to Ubuntu.  

I don't know if its related, but when it started Ubuntu up again, the bars at the top and bottom were blank. No Ubuntu button, shutdown button or anything.  Now there's nothing there at all and i can't launch anything. Had to shut down and restart with the XP hdd because I dont know how to replace it....I may end up doing a fresh install to try to get things back to default..

First of all slow down, take a deep breath and be patient. Losing the panels in Ubuntu should be unrelated.

Give me a few minutes to type some other instructions.

---

### Post by kansasnoob on 2010-04-30
Since you mention Master and Slave it seems apparent that you have two IDE drives, eh?

If so are they both on the same cable?

If yes **it does matter** how the jumper settings are on the drives!

Most of the newer drives have a cable select option while many of the older drives do not.

The thing is, if you do not want to change the mbr on the Windows drive, it will need to be set and attached as Slave.

Although changing mbr's is easy and safe with nothing but an Ubuntu Live CD :)

So please explain a bit more thoroughly what your situation is and we'll go from there.

To restore those panels to their defaults:

[http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

---

### Post by Gyanos422 on 2010-04-30
Thanks for the link, I think i found my answer browsing around, apparently its a common 'problem' for noobs to Linux like me.

> **kansasnoob said:**
> Since you mention Master and Slave it seems apparent that you have two IDE drives, eh?

If so are they both on the same cable?

**Yes they are both on the same cable.**

> **kansasnoob said:**
> If yes **it does matter** how the jumper settings are on the drives!

Most of the newer drives have a cable select option while many of the older drives do not.

The thing is, if you do not want to change the mbr on the Windows drive, it will need to be set and attached as Slave.

[B]I have them set up (and for as long as i've been building computers) as Cable Select. It always was easier that way.  Is it required that i set master and slave? Because i really hate doing that if i can avoid it.
[/B] 

> **kansasnoob said:**
>  Although changing mbr's is easy and safe with nothing but an Ubuntu Live CD :)

So please explain a bit more thoroughly what your situation is and we'll go from there.

[B]To be as short as possible: Currently running XP Pro. Put in old blank hdd, tried Ubuntu 10.04 and liked it.  I want to keep it but also need to be able to access XP for certain progs right now, but mainly for my wife who isn't as adventurous when it comes to computers as I am.  

I don't want to partition, i want to use 2 hard drives and boot each OS from its own hard drive.  Ubuntu should be the default OS to load, if WinXP isn't selected to boot.

*I'd also prefer to keep the existing installation of Ubuntu i have, but if i need to reinstall for it to see ubuntu and xp, then no big deal.*[/B]

---

### Post by carl4926 on 2010-04-30
It will make a difference if you had the XP HD disconnected when you installed Ubuntu. If you did, the Ubuntu expects to be hd0
With windows it doesn't matter, because you chainload to it anyway.

All you need to do is run this form Ubuntu (this is with both HD's connected)

```
sudo update-grub
```
then
```
sudo grub-install /dev/sda
```

NOTE:
you should check with **fdisk -l**
to see your partition info and edit the above accordingly. For example you Ubuntu HD should be either sda or hda
If in doubt post result of **sudo fdisk -l** here

---

### Post by oldfred on 2010-04-30
both windows & Ubuntu have a few settings that plugging & unplugging a drive may change drive order and cause issues.

Check /boot/grub/device.map in Ubuntu.

IF you want to see where everything is at:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

Cable select is setting master & slave, it is just easier than those tiny jumper pins that get lost or are not always well documented. SATA is even better as you set boot drive (primary master) in BIOS.

---

### Post by Gyanos422 on 2010-04-30
I am going to reboot into Ubuntu. I will let you know how things go.

Thanks for all the help so far btw. Ubuntu forums are the most helpful forums i've been on in a loooong time!

---

### Post by Gyanos422 on 2010-04-30
YES! BOTH PROBLEMS SOLVED! YOU GUYS ARE AWESOME!!  Sorry for the caps but i've been ready to pull my hair out before you guys provided EXACT information. took care of my problems without a hitch.

I just wanna note that when i restored the panels to default install settings, it said ROOT at the me menu.  But when i restarted it went back to normal.  If anyone else gets themselves in a spot like this then this thread will help.

THANKS GUYS!


[SIZE=5]\\:D/\\:D/\\:D/\\:D/[/SIZE]

---

