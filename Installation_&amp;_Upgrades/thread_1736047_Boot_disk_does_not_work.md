---
title: "Boot disk does not work"
date: 2011-04-22
forum: Installation &amp; Upgrades
---

### Post by mlempenau on 2011-04-22
Thanks for helping.  I'm sure there is something here that I want to learn. When windows was installed I could boot to a windows promp and then I could take out the cd or usb and install another one with a program and run it.   Could someone explain why my computer bios will not let me do this now that I have a ubuntu load?  I'm sure there is a logical explanation.  Also maybe a work around?  (It will run a windows or ubuntu install cd or usb but no simple boot disk.)  Mike

---

### Post by mörgæs on 2011-04-22
I don't understand what this is about, sorry. Please explain again, step by step, what you are expecting and what is happening. 

Forget the Windoze part, just focus on Ubuntu.

---

### Post by mlempenau on 2011-04-24
I have made a cd that will boot to a command prompt.  I have also done the same thing with a USB stick.  I did this with two cds and two sticks.  One for ubuntu and one for windows.  None will boot to a c prompt.  The ubuntu ones after a short time send me to my ubuntu load.  The windows ones give me an error.  I am wanting a windows c prompt so I can load a windows program from a cd.  When I try to use any of my cds with windows programs on them I get an error.

---

### Post by Hedgehog1 on 2011-04-25
It looks like you need to re-install or fix your Windows install, then.

Please create a new Windows Rescue disk (you can do this from Ubuntu) buy downloading the correct ISO for   [VISTA]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") or [WINDOWS7]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Then burn the ISO to CD using your Ubuntu burning software.  With any luck, this should give you a functional Windows Rescue disk so you can fix-up your windows install.


***The Hedge***

:KS

---

### Post by mlempenau on 2011-04-25
I made the vista rescue disk and then tried to boot.  I pressed F8 to get me to my bios boot menu.  Clicked on the cd and after about 20 sec. it went to grub.  Grub menu did not have anything about a cd so I pressed c and got a command line.  If I have the correct info I should be able to use "ls" and get info.  This did not work.  Not sure what to do now?  Thanks for helping.  MIke

---

### Post by Rubi1200 on 2011-04-25
Hi,

please do the following so we can see what is going on:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

