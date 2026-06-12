---
title: "Normal PS/2 keyboard doesn't work"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by lassel on 2006-06-02
Hi,

I have tried installing Ubuntu 6.06

When I boot into the CD i get the boot menu. From there my keyboard works fine. I can select to continue loading the live cd.

After the live cd loads only my mouse works! My old standard PS/2 keyboard doesn't respond.

Stubbern as I am I found the character map from the menues and used the mouse to click-type the info I needed to install and I managed to work through the installer that way.

Then I booted and once again the keyboard worked fine in GRUB but once it got into my new ubuntu login screen it stopped working!!!

I have had no problems at all with my setup in neither Ubuntu 5.04, 5.10, all dapper betas nor Windows XP.

My setup is an athlon xp 2400 with 1.5gb ram, 160gb hdd, nvidia 6600gt gfx, a standard fujitsu siemens keyboard, a logitech mouse and an external usb dvd drive.

Please help!   ](*,) 
There must be some magic boot option or something I can use?

---

### Post by Blender on 2006-06-02
I am having exactly the same problem. My keyboard works fine with SUSE, Windows, and GRUB, yet it does not work in Ubuntu.

---

### Post by Izzie on 2006-06-02
I m using a logitech USB ultra flat keyboard and a logitech mx1000 (connected via PS2) and I'm experiencing a same same problem. chipset is nforce4.

the keyboard and mouse are working fine during install, but now that I've installed rebooted, and added some apps including nvidia-glx. And from that point when I try to boot to ubuntu keyboard is simply not working at all, sometimes I can't even enter grub menu, sometimes I can enter grub but then I'm stuck at ubuntu login screen with no kb and no mouse.

I switched to my older logitech kb which is PS2 to no success. I even tried with both kb connected. 

After a few tries (sometimes 10-20) for no apparent reason, it works.

-edit-
I just checked the boot msg and noticed this line :
ohci_hcd USB HC takeover failed! (BIOS/SMM bug)
I never heard about this bug before, so I guess, it's digging for info time

-edit2- 
read here [http://lkml.org/lkml/2005/9/27/110](http://lkml.org/lkml/2005/9/27/110) that usb legacy option in BIOS could be the problem.
usb kb support and usb mouse support are the closest option to usb legacy in my BIOS.
both were enabled, I disabled both (my mouse being connected in PS2 there's no need for it) and now mouse is working 100% and the keyboard at first didn't worked, I rebooted a couple times and now it's working.
so you might want to check your BIOS for usb legacy option, it may solve your problem.
USB kb and mouse support is enabled in BIOS (also tried to disable it).

---

### Post by lassel on 2006-06-03
I found the same fix as the previous poster.

I enabled "USB legacy support" in my BIOS and had no problems after doing that.

---

### Post by Blender on 2006-06-05
Well, I managed to fix it too. I turned off the option for USB mouse in BIOS (that for USB keyboard was off). After that my PS/2 keyboard works fine. Funny thing :)

---

### Post by lassel on 2006-06-06
I read at launchpad that they have worked to fix some problems with usb keyboards that didn't work out-of-the-box.

I guess they must have broken PS/2 keyboards in the process. =D>

I'd say that it clearly is a kernel configuration bug.

---

### Post by Ymer on 2006-06-08
I had almost the same problem during installation from Live CD, I was using a normal PS2 keyboard with a USB mouse. When all connected in this way, I had mouse working but no keyboard after Live CD boot up (I could use the keyboard in boot menu, but not after that anymore). I changed my mouse to PS2 (using a convertor) and everything worked fine. :D I installed the Dapper succesfully, and then tried again with the original setting (mouse back to USB). But this time it detected it correctly and everything was fine. Both are working happily. So for my case I think the problem was somewhere in Live CD that it wasn't able to detect and use a USB mouse and PS2 keyboard at the same time.

Edit: I somehow figured out what is the problem: during booting up (after selection of booting type), when you keep doing something with keyboard (like turning on and off Num-Lock key :P), then it recognizes the keyboard. But if you leave it alone, it almost forgets that there is a keyboard.

---

### Post by cmire on 2007-01-17
I've got a Logitech MX-700 wireless mouse & keyboard, and I've been using it for a couple of months now on Kubuntu 6.06 without any problems -- then all of a sudden today the keyboad just stopped responding after the login.  I've rebooted several times, and the mouse continues to work fine, but the keyboard just will not respond.](*,) 

The mouse is ps/2, and the keyboard is USB but plugged into ps/2 using an adapter.  I tested the keyboard on my laptop using the USB port, and it works fine (the laptop is also running Kubuntu 6.06).

I tried just plugging the keyboard into the usb port on the workstation, but that made no difference.  I was able to use the keyboard to login, but then could not use it once KDE was up.

I checked the BIOS for the tip mentioned in this thread, but I don't have that particular setting.

Is there a system or hardware config file that could have gotten corrupted or something to cause the keyboard to drop off like that after login?

---

### Post by Slade Winstone on 2007-02-12
Hi, I'm running Edgy, 2.6.17-11-generic, and found a strange, kinda, partial work-around, for this problem:
[http://ubuntuforums.org/showthread.php?p=2143128]("http://ubuntuforums.org/showthread.php?p=2143128")

---

### Post by photomoto on 2007-04-27
I just ran into this same problem. Keyboard works fine in grub, and while booting up the BIOS etc, but as soon as X comes up, the keyboard does not respond. 

My problem happened when I upgraded from Edgy 6.10 to Feisty 7.04.
In 6.1 my standard ps/2 keyboard worked fine. But after I upgraded to Feisty, my mouse worked, but my ps/2 keyboard would not respond. I thought it was a problem in /etc/xorg/X11/xorg.conf but that ****WAS NOT**** the case.

It was a BIOS setting. It had something to do with USB Keyboard legacy driver support settung in the bios. Actually my old p4 2ghz shuttle box has something called "Assign USB IRQ" once I disabled the IRQ, my ps/2 keyboard works like a champ.

So I think the solution is to disable USB legacy support, USB IRQ settings, or direct USB keyboard support, or whatever your flavor of BIOS calls this crap.

I can't take all the credit here. I actually found the answer via google via this link
[http://www.linuxquestions.org/questions/showthread.php?t=304148](http://www.linuxquestions.org/questions/showthread.php?t=304148)

Anyway I hope this helps someone out... Especially on an Upgrade from 6.10 Edgy to Feisty 7.04.

---

### Post by soho2014 on 2007-05-04
I am having the same problem with my PS/2 keyboard.  I tried another one which I know works, so I know that it's not the keyboard itself.

I was not able to do the HD install because that is the exact point that the keyboard failed.  I am using a USB wireless mouse, and a PS/2 keyboard.

When I got home, I'm going to change some of the BIOS settings as people here have suggested and see if that helps.  This is my first experience with Linux of any sort.  The screen looks wonderful ,but it was frustrating that I was so close, but yet, so far!

---

### Post by Pistolla on 2007-05-05
I have a question more than a reply. My keyboard works fine and dandy...under Ubuntu (i have just upgraded to Feisty)
Before i upgraded to Feisty i had Edgy (of course, of course) i also run from time to time (in the past-under Drake, at least) Kubuntu. and i dual-boot with windoze XP (Pro)
Some time after Edgy was up running and doing it's thing (maybe2-5 months) the keyboard wouldn't work anymore (Kubuntu). So i was stuck (i thought) for two days with a "dead Linux." i could go under windoze and it'll work. i can go to Splash screen and type my name/p-word not a problem go to Kubuntu, stops working. I thought i'd try it under Ubuntu and everything works fine!! So basically i didn't use Kubuntu after that. After all, i can use KDE stuff under Gnome. The problem's still there even after upgrading to Feisty! It just gets under my craw that something's not working, and like a little kid who closes his/her eyes and thinks no one can see them, i try to do that and cannot. 
i don't know if the BIOS thing is the culprit or not. I don't know how to get into it or anything.
On an aside, i was having difficulties with runnin' ClamAV (sayin things like it could see this type or that type of file) i couldn't update it. iit would say i am not under Root. So i went to Synaptic and looked through there and saw i needed a coupla those 'wares and since i did that i have had no problems and can, now, check for viruses. i am not one of those who thinks we will never get a virus under Linux plus i also dual-boot. I am now that much closer to chunkin the Whole windoze OS. i love Linux (had it since Dapper). The people who actually catered to us "wienies" who would not "jump ship" b/c it don't run like windoze (in my case it was fear of a new thing but wanted to try it badly-glad i did). I can say it works better. the only difference is that we have to "rework our brains" a little bit to run (X)(K)Ubuntu and Linux in general
Anyhoo, 'nuff "butterin the bread" (of which i was lying) i just need help with keyboard issue and it would be GREATLY appreciated
Thanx a lot
Pistolla

---

### Post by warp07 on 2007-10-29
Ubuntu from 7.04 my machine does not recognize it booting the keyboard. The Ubuntu 6.10 nothing was a trouble yet, but the 7.04, and then unfortunately the 7.10 make this.
The keyboard Genius KB-06X, PS/2, all Op. systems know this nice. I tried out an A4 keyboard already: the same phenomenon.
The interest(?) of the situation, that in as much the bung of the keyboard the booting I pull it out. I stick it back then the contact arrives!!!
(I do not believe in the fact that he is hardware would be a mistake!)
I use currently it i386 Gutsy Gibbon, which I refreshed on the net from 7.04
Detail of the xorg.conf:
Section "InputDevice"
 Identifier "Generic Keyboard"
 Driver "kbd"
 Option "CoreKeyboard"
 Option "XkbRules" "xorg"
 Option "XkbModel" "pc105"
 Option "XkbLayout" "hu"
EndSection
Hardverinfo:
24: PS/2 00.0: 10800 Keyboard
  [Created at input.139]
  UDI: /org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input
  Unique ID: EXC1.TBWTwSuMeW2
  Hardware Class: keyboard
  Model: "AT Translated Set 2 keyboard"
  Vendor: int 0x0211
  Device: int 0x0001 "AT Translated Set 2 keyboard"
  Device File: /dev/input/event1
  Device Files: /dev/input/event1, /dev/input/by-path/platform-i8042-serio-0-event-kbd
  Device Number: char 13:65
  Driver Info #0:
    XkbRules: xfree86
    XkbModel: pc104
  Config Status: cfg=new, avail=yes, need=no, active=unknown

Please help me !!!

---

### Post by warp07 on 2007-11-05
I tested the undermentioned one in my final despair:
1) it mouse(!) back I had plug the PS2 into a socket and the miracle of miracles handled the keyboard again Linux.
2) mouse again in USB, the system does not recognize the keyboard again
Presumably, who touched it, hardware and kernel knows the explanation possibly on a level.
Though presumably something not sterile

---

### Post by still_water on 2007-11-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106289](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106289) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi,

I had the same problem after installing the latest Ubuntu Studio i.e. usb mouse worked fine but PS/2 keyboard would not work. 

If I used a USB->PS/2 converter for my mouse and rebooted both keyboard and mouse would work.

I tried disabling certain USB features in bios (did not have the USB leagacy as an option but had USB IRQ settings) but that did not help. 

What did help was to explicitally add "acpi=off" to my menu.lst file.
This was advised from the following forum:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106289](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106289)

So the steps I took: 
First had to get keyboard working by using usb->PS/2 converter on mouse.
Once Ubuntu Studio loaded I opened up a terminal, typed su root, then cd boot/grub, and then gedit menu.lst.
In menu.lst I added acpi=off to the kernel line.

Rebooted and now can use PS/2 keyboard and usb mouse. This way is flawed because I had to get my keyboard to work first(by using usb->PS/2 converter on mouse) so that I could edit the menu.lst file, but I am new to linux and I do not know how I can edit files before boot up. If someone does could they please share that with me ??

---

### Post by sandr on 2008-02-28
I'm running Gutsy and had the same problem: with my USB mouse plugged in, the PS/2 keyboard did not work anymore (before, I used a PS/2 mouse and had no problems). Simply plugging the keyboard out and in again while the Ubuntu login screen was showing made it work until the next reboot.
Now I've also added "acpi=off" to the topmost "kernel" line in /boot/grub/menu.lst, and the keyboard remains working after reboots! Thanks for this tip, people.

---

### Post by sandr on 2008-03-04
Update: while it solved the keyboard problem, the "acpi=off" option also caused the system not to power-off after the shutdown sequence. (and I think it may also be related to a jumpy mouse cursor that I had) [This fix]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117899/comments/6") works better for me (rebinding keyboard in an init script).
I am using kernel 2.6.22-14-generic and have the VIA KT266A chipset on my motherboard.

---

