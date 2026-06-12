---
title: "Install Ubuntu on Westinghouse NB-14w2 Laptop"
date: 2006-12-12
forum: Installation &amp; Upgrades
---

### Post by seashell11 on 2006-12-12
I am trying to install Ubuntu on a Westinghouse NB-14w2 Laptop it is the laptop included in [THIS PACKAGE]("http://westinghousedigital.com/details.aspx?itemnum=66").



First I tried with the regular Kubuntu 6.10 Live cd. It went for a while, and then all of a sudden it just started repeating this message.
```
[17180091.116000] hda: ide_intr: huh? expected NULL handler on exit
[17180091.164000] Buffer I/O error on device hda, logical block 58694
[17180116.764000] hda: ide_intr: huh? expected NULL handler on exit
[17180136.012000] hda: ide_intr: huh? expected NULL handler on exit
[17180136.060000] Buffer I/O error on device hda, logical block 58705
```
And, as you can see the words stayed the same, but the numbers changed. It didn't go through them really fast, just every little bit. After a while it looked like it totally quit, because it just sat there with the bar flashing at the bottom of the screen, but nothing changed any more.



I then hit CTRL + ALT + DELETE to restart the computer. Then using the same cd, I tried starting it up in safe graphics mode.

```
[17179733.916000] hda: ide_intr: huh? expected NULL handler on exit
[17180091.964000] Buffer I/O error on device hda, logical block 58655
[17180091.964000] SQUASHFS error: sb_bread failed reading block 0x1bc44
[17180091.964000] SQUASHFS unable to read fragment cache block [6f077a9]
[17180091.964000] SQUASHFS unable to read page, block 6f077a9, size 9c16
[17179759.564000] hda: ide_intr: huh? expected NULL handler on exit
[17179778.920000] hda: ide_intr: huh? expected NULL handler on exit
[17179778.968000] Buffer I/O error on device hda, logical block 58705
```



Then I restarted again, and tried it with Kubuntu 6.06 live cd in the regular start-up mode.

This went fine, and it said ok for everything. Then the screen went blank, or flashed like it does when it is going to log in, but instead of logging in, it just put me back to the screen showing the kubuntu logo, and it just sat there not doing anything.



Again I restarted, and this time I used the same 6.06 live cd, but I chose the safe graphics mode at startup.

This time, everything started up and worked fine! But, the graphics weren't the best of course. Also some hardware, like the wifi card, wasn't found; but the wifi card can be fixed later.



I then restarted again, and booted up with a 5.10 live cd, just to see if that would work.

This here went fine for the most part, until it should have started the X xerver. It the popped up the message ```
Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server ourput to diagnose the problem?

          <Yes>        <No>
```
I chose yes. In there at one place it said```
Fatal server error:
Caught signal 4.  Server aborting
```
I then went to the command line and typed in```
sudo dpkg-reconfigure xserver-xorg
```
and tried changing the driver from ati to vesa. This didn't help either.



Then, as I think you have already guessed, I decided that I might as well try a 5.04 live cd too.

This time, it got as far as showing the splash screen and the mouse, before it locked up and wouldn't do anything.



I didn't try the 4.10 cd, beings I didn't have one, and I couldn't find a downloadable iso.



Now does anyone have any idea what I should do to get Edgy Kubuntu running on this laptop? Should I install with Dapper started up in Safe Graphics Mode? Should I download the Alternate install cd and install with that? Will the SATA hard drive cause problems? Where it was having the errors shouldn't it have said sda instead of hda, since it is an SATA hard drive? Is it my Video Card that is causing the problems? Can I just install Kubuntu, and then reconfigure the x server to make it run right? 

I would rather not mess up my windows xp if at all possible. I am wanting to shrink the size of my Windows XP Partition, then creat a ext3 partiton to install linux on, then creat a logical partion, and in the logical partition, I want a partition for ext3 partition for /home, a Fat32 partition for sharing files between windows and linux, and a swap partition of course.

If anyone wants me to try anything else, or give you more information, I will gladly take the time to do it.

---

### Post by seashell11 on 2006-12-12
Ok, I just started up with the 6.06 live cd in safe mode again, and opened up qtparted. It has my hard drive as /dev/sda, and it recognized the ntfs partition that is currently on it. This would mean that it isn't a problem with my hard drive right? or am I wrong?

---

### Post by tominsf on 2006-12-12
I've installed Ubuntu Edgy on that laptop.  It seems to install just fine, except that sound and wifi don't work 
 --see this thread: [http://www.ubuntuforums.org/showthread.php?t=313674&highlight=westinghouse]("http://www.ubuntuforums.org/showthread.php?t=313674&highlight=westinghouse")

When I tried to run Dapper from the live cd, just to see if things worked any better, it gave me the same Failed to start the X server message you got.  It did however work in safe graphics mode.

---

### Post by rlcmcallen on 2007-04-25
Try booting with the latest final 7.04 disk. Sound is now working. I still have to work some more on the wireless to get it to work.

Anyone who tried earlier versions, please try the latest and I think you will be pleased with the improvement on our listtle Westinghouse laptop

---

### Post by 3StrikesDesign on 2008-05-10
Just installed v 8.04 and am quite pleased.... no modification needed had sound and wifi out of the gate. even auto found my Options GT Max 3.6 Express cell card. Now just to get to an area with cell signal to test it out :) 

Here I was already to make ndiswrapper mods and other mods needed for these items and no need to...  the only thing not working is my usb optical mouse, but it also stopped working in windows on this laptop, so it might just be dead. Will try it on one of my other machines later.

Thank-you developers for making this new version a simply install process to get it running out of the gate...

---

### Post by seashell11 on 2008-05-12
That rocks! I'll have to try it on my brothers laptop again.

---

### Post by 3StrikesDesign on 2008-05-12
The mouse was dead, when I tried it on another machine I also had no life... I picked up a cheap wireless optical one from Big Lots for $5 and works like a champ. Will be testing the cell card tonight and will report back if I need to make any modifications.

---

