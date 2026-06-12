---
title: "Updating from 10.04 LTS - 12.04 LTS - blinking cursor and then freeze"
date: 2013-03-26
forum: Installation &amp; Upgrades
---

### Post by AfrikaDietmar on 2013-03-26
Hi,

on my new PC below, i installed 10.04 LTS first from an old CD which works fine. 
Did all the updates and the new graphic card works fine.

I tried to upgrade to 12.04 LTS thinking that with my new powerful PC it would work optimal. It didn't work from the update program.

Then i downloaded the iso file of 12.04 LTS, made a bootable usb stick and cd.
Tried to boot from CD, and would usually get a blinking cursor and then freeze.
Put on boot menu of CD a cross "x" at:
  X noapic
  X nolapic
  X nomodset

I tried different combinations and that didn't help.

I also tried to add the part quiet splash nomodset but this had no effect either.

[HR][/HR]PC Specs: CORE I5-3470 3.2/3.6 GHz Turbo, 6MB Cache, ASUS P8H61-PRO (Intel H61 Chipset), DVD LGA1155, RAM Dual Channel 2 x 4 GB DDR3 1333, 500 GB Hard Drive SATA
Power: Cooler Master 625W Extreme2
Graphic Card: ASUS GT620 (Connected 2x  24" LED LCD Viewsonics, one on HDMI one on the blue connector)

---

### Post by AfrikaDietmar on 2013-03-26
I did follow some steps here:
[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

> You can also try acpi = off and nolapic if nomodset also shows up as a black screen.
none of these worked and no installation was possible. Regarding the part that says

> The solution is to boot Ubuntu *once* in nomodeset  mode (your  screen may look weird) to bypass the black screen, download  and install  the drivers, and then reboot to fix it for ever.
  Start your computer, and press the Shift when booting up, to get the  Grub menu. Use the arrow keys to navigate/highlight the entry you want  (usually the first one).

<< Here its unclear to me if it means an already installed version or off the cd.

[HR][/HR]PC Specs: CORE I5-3470 3.2/3.6 GHz Turbo, 6MB Cache, ASUS P8H61-PRO  (Intel H61 Chipset), DVD LGA1155, RAM Dual Channel 2 x 4 GB DDR3 1333,  500 GB Hard Drive SATA
Power: Cooler Master 625W Extreme2
Graphic Card: ASUS GT620 (Connected 2x  24" LED LCD Viewsonics, one on HDMI one on the blue connector)

---

### Post by oldfred on 2013-03-27
You have a nVidia card, so you at least need the nomodeset, and perhaps the other boot settings.

       Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Some with Asus have posted these comments, but there are many models and they all may be different.

 Asus m4a87td  core unlocker feature on usb3 was causing the problem
Asus - Security> I / O interface Security> "New interface card" or so. SET IT TO LOCKED!!! 
In the Asus BIOS I selected Advanced Mode>Advanced>SATA Configuration.
Changed IDE Mode to AHCI Mode

---

### Post by AfrikaDietmar on 2013-04-10
Hello,

i ordered an original Ubuntu 12.04 LTS cd which arrived.
I followed the steps in: [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
Since I also have a graphic port on the main board i removed the nvidia card when trying to install 12.04 LTS.
I set a cross on nomodset and i added in the boot line:
vga=771

Then installation run smoothly and everything worked.
I then readded my nvidia graphic card into the PC.

NOW when i login into Ubuntu 12.04 LTS it always freezes after 2-5 mins, sometimes it also reboots. (It also did so without the graphic card in the PC.)
I am currently not using the Nvidia card.
I don't know what todo as I read tons of posts but couldn't find an answer to this issue. 

I also did a memtest and no issue with memory. Also it did run stable and well when doing the installation.
What do you suggest I try ?

_After an hour or so_
I tried ```
[I]
uname -a[/I]
```[I]
result: 3.2.0-40-generic-pae #64 -Ubuntu SMP Mon Mar 25 21:44:41 UTC 2013 i686 i686 i386 GNU/Linux[/I]
[U]
Next Step that i tried[/U]
I tried to follow the steps shown here:
[https://wiki.ubuntu.com/X/Backtracing](https://wiki.ubuntu.com/X/Backtracing)

Once 12.04 LTS loaded i did Ctrl+Alt+F1 to get into the terminal and then i carried out:

```
*sudo service apport start force_start=1*
```

This gave no result. I pursued with:
```
*pgrep Xorg*
```
and got 1037

then i tried this:
```
*sudo gdb /usr/bin/Xorg 2>&1 | tee gdb-Xorg.txt*
```

Here the computer froze, tried it at 2 intervals and it just freezes here.

Then on reboot i pressed SHIFT and went into GRUB
I tried to load recovery mode ubuntu but this didn't work.
I tried to get into the terminal there and couldn't do much either nor run the commands above.

Rebooted and went into GRUB again with SHIFT and there i pressed e for edit but i edited nothing and then I just booted the machine from the normal linux 12.04 version that i have.
THEN the boot splash screen looked neat.
I managed to login and then after one minute i got an error message from the system that says:
```
[I]
Sorry, Ubuntu 12.04 has experienced an internal error
Executable path: /usr/bin/jockey -gtk and a lot more details related to this.[/I]
```

NOW it hasn't frozen, am doing some updates and wondering what else I can do to make the system stable - also wondering if it wont freeze anymore...
**BUT why is it working ?** Might post again in 1 hour...

---

### Post by AfrikaDietmar on 2013-05-22
Hi guys, still experiencing similar freeze problem when trying to install 13.04 - check my thread here: [http://ubuntuforums.org/showthread.php?t=2146906](http://ubuntuforums.org/showthread.php?t=2146906)
Thought with the new Kernel and updates it would work when installing from CD or USB Stick.

---

