---
title: "Ubuntu 9.10 &amp; Above, Hang during startup."
date: 2011-06-26
forum: Installation &amp; Upgrades
---

### Post by Panties on 2011-06-26
Hi all,
I'm not a linux guru. I'm just a casual IT user. Here's my info:

Computer Spec:-
Asus P5PE-VM
Core 2 Duo 2.21Ghz (I think..)
2GB RAM DDR1
PCIE 3850 HIS (AGP Edition)
DVD, Harddisk..etc etc...

To simply put, I have not been sleeping for 2 days, on 56k Modem, on...
1. Download 32bit version of Ubuntu 11.04, burn to CD - Installed & After boot up, Select Ubuntu on GRUB loader, it hang on "UBUNTU" Screen... so...
2. Download 32bit version of Ubuntu 10.10, burn to CD - Installed & After boot up, Select Ubuntu on GRUB loader, it hang on "UBUNTU" Screen... so...
3. Download 32bit version of Ubuntu 10.04, burn to CD - Installed & After boot up, Select Ubuntu on GRUB loader, it hang on "UBUNTU" Screen... so... 
( You get the picture... )
Right down to Ubuntu 8.04... AMEN! Finally my Ubuntu works! However,...

I thought I can try to update Ubuntu from 8.04, right up to 10.10...  or 10.04... using sudo update-manager -d.... or through CD upgrades.. or something..etc..

Cut to the chase, I am unable to upgrade (through 56k Modem over internet or through CD), spend hours & hours, with coffee's help... Sun up till Sun down, just trying to find ways to upgrade/install successfully to 10.10, but it always hang on "UBUNTU" Screen!

Without any luck, ONLY 8.04 works (For unknown reason)!


So, here's my question:-

1 . If I use ubuntu 8.04 & update all the packages to the MAXIMUM (update-manager), Will I be missing out some cool application? Will newer application (Example, Google chrome), still works with 8.04? Do I need to upgrade to version my Ubuntu distros, to enjoy cool Desktop like Compiz? Does newer application, require newer Ubuntu to work?

2. I realized in Ubuntu 8.04, It only have 2 Working Deskop Enviroment (Buttom Right). I thought Linux have 4 Desktop Enviroment... How do I set it to 4?

3. Any Idea why Ubuntu 9.10 and above, hang during "Ubuntu" screen? (I have tried from "Dual Boot with Windows" till/to.. "Clean & Full installation of Ubuntu" - EPIC FAIL) Only version 8.04 works..  :(


I Hope there are Ubuntu Gurus who is out there, will listen to my cry... T.T

Please help! I'll check this forum tomorrow. I need to sleep, recovering 48 hours of non-sleep! OMG.. @@!

Thank you in advance. Appreciate your time in advance. :)

---

### Post by Panties on 2011-06-26
In Addition...

I also tried the option "Recovery mode" or something.. also do no work on 9.10 and above.. it just hangs on "Ubuntu" Screen at startup...

8.04 works like a charm.

I just ran "Update Manager", it now shows me...

"New distribution release "10.04.2 LTS" is available"..

Should I or should I not upgrade? I'm just worried it happens again if I do so. But I am willing to give it a go, if you guys got any cool ideas/resolution...

Regards,
Panties.

---

### Post by mörgæs on 2011-06-26
Does any of the releases work well in a live boot?

---

### Post by Panties on 2011-06-26
just tried...

Liveboot fails! (I assuming, putting into CD, Boot to the CD and select Liveboot)

for version 9.10, 10.04LTS, 10.10 & 11.04... they have the same symptoms, which they got stuck/frozen during bootup.

8.04 just works normally.

:(

I'm not going to switch to other distros like Fedora or Gentoo, unless i'm absolutely sure.

I'm not giving up on Ubuntu yet.. (The black shadow, start to cover beneath my eyes.. i'm too sleepy)

---

### Post by mörgæs on 2011-06-26
Good to hear that you are persistent! 

Testing the ISO's before burning is worth trying:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

From the main menu while booting there is an option to self-test the CD's. How does that work?

By the way, running Ubuntu (or any operative system) from a 56 k modem will be a tedious task. Do you have any option of using a faster connection, at least while installing?

---

### Post by Panties on 2011-06-26
Thanks Mon!

Okay, I actually test the CD before I install it! The CD's are fine. 

However, you are right on "Try Ubuntu" First! At least I know if the Ubuntu Operating system, will work fine or not without installing to the harddisk!

>.< Wasted hours! >.< it should had save me a lot of time!


Anyway, yeah, I also tried Md5SUM and the CD's are fine. Working properly!

You know what? I'm going to try to disable everything in BIOS (LAN, Soundcard, 32-Bit Transfer RATE for Harddisk, S.M.A.R.T. for harddrive...etc)
In fact, I'm gonna unplug my Microsoft FULL 1080 HD Webcam, ReadyBoost Pendrive...anything that is USB related, except for keyboard & mouse.

After that, proceed to upgrade my Ubuntu 8.04 -> 10.04LTS using sudo update-manager -d .

I'll keep you posted tomorrow morning, as upgrading using 56k, will take a while.

Yes, the reason why I am still using 56k modem because the 56k modem is faster than ADSL! (Don't laugh, The ISP here is trying to filter website and throttle their internet speed for their customers! It's very close to "unusable")

It took me only 45 minutes to download Ubuntu CD over 56k modem, but ADSL 1MBPS (Which was supposedly fast), took me 1 hour and 15 minutes. (No, my computer is not infected by any virus nor worm, nor sharing internet connection with anyone, nor effected by WIFI as I use cable, nor downloading anything torrent..etc)

So yeah, Ill update you  later... :)

---

### Post by Orion13622 on 2011-06-27
I too am having this problem, however it's only with the 32 bit version of the 11.04, not the 64 bit.  Strange that the 32 bit would fail out, and not the 64 bit.  I hit the esc key to watch what was happening during startup, and it looks like it's hanging on the configure network device on startup, during the final installation proceedure.

Anyone else having this option, have you found a work around for this?  Here's my system specs just to see if it helps.

Compaq Presario R3000Z CTO
AMD Athlon 64 Bit
1 Gig memory
nVidia GeForce Go440 64MB
125GB HDD
(Is just a little portable linux machine I hope...)
Broadcom Wi-Fi card

---

### Post by MAFoElffen on 2011-06-27
> **Panties said:**
> Thanks Mon!

Okay, I actually test the CD before I install it! The CD's are fine. 

However, you are right on "Try Ubuntu" First! At least I know if the Ubuntu Operating system, will work fine or not without installing to the harddisk!

>.< Wasted hours! >.< it should had save me a lot of time!


Anyway, yeah, I also tried Md5SUM and the CD's are fine. Working properly!

You know what? I'm going to try to disable everything in BIOS (LAN, Soundcard, 32-Bit Transfer RATE for Harddisk, S.M.A.R.T. for harddrive...etc)
In fact, I'm gonna unplug my Microsoft FULL 1080 HD Webcam, ReadyBoost Pendrive...anything that is USB related, except for keyboard & mouse.

After that, proceed to upgrade my Ubuntu 8.04 -> 10.04LTS using sudo update-manager -d .

I'll keep you posted tomorrow morning, as upgrading using 56k, will take a while.

Yes, the reason why I am still using 56k modem because the 56k modem is faster than ADSL! (Don't laugh, The ISP here is trying to filter website and throttle their internet speed for their customers! It's very close to "unusable")

It took me only 45 minutes to download Ubuntu CD over 56k modem, but ADSL 1MBPS (Which was supposedly fast), took me 1 hour and 15 minutes. (No, my computer is not infected by any virus nor worm, nor sharing internet connection with anyone, nor effected by WIFI as I use cable, nor downloading anything torrent..etc)

So yeah, Ill update you  later... :)
Your video card uses the RV670 chipset (ati radeon)...

First off, sounds like you have a successful kernel boot, but is locking up when the graphics loads.  To confirm this, read post 1-3 of this sticky:
[http://ubuntuforums.org/showthread.php?p=10985233#post10985233](http://ubuntuforums.org/showthread.php?p=10985233#post10985233)

While you are locked up at the Ubuntu Screen of the LiveCD > Press <cntrl><alt><F1> and it should take you to a text console > enter your username and password...

Once you can get to a text console mode:
```
[FONT=monospace]
[/FONT]sudo service gdm stop
sudo modprobe -r radeon drm 
sudo modprobe radeon modeset=1 
sudo service gdm start

```If that works, then
```

sudo nano /etc/default/grub. 

```Go to the line that says GRUB_CMDLINE_LINUX_DEFAULT=  Inside the quotation marks, remove the word "splash" from that line.  At the end of that line, inside the quotation marks add 

```


radeon.modeset=1

```Save and exit the file.  Then 

```


sudo update-grub

```The opensource driver for your card is radeon(xserver-xorg-video-radeon).  ATI's driver does perform better and will keep that driver through dist-upgrades. However- It is a manual install.  

Look at this post:
[http://ubuntuforums.org/showpost.php?p=10950714&postcount=334](http://ubuntuforums.org/showpost.php?p=10950714&postcount=334)

You might be able to do that install from Ubuntu 8.04 then do a dist-upgrade through current.

---

### Post by MAFoElffen on 2011-06-27
> **Orion13622 said:**
> I too am having this problem, however it's only with the 32 bit version of the 11.04, not the 64 bit.  Strange that the 32 bit would fail out, and not the 64 bit.  I hit the esc key to watch what was happening during startup, and it looks like it's hanging on the configure network device on startup, during the final installation proceedure.

Anyone else having this option, have you found a work around for this?  Here's my system specs just to see if it helps.

Compaq Presario R3000Z CTO
AMD Athlon 64 Bit
1 Gig memory
nVidia GeForce Go440 64MB
125GB HDD
(Is just a little portable linux machine I hope...)
Broadcom Wi-Fi card
There was a problem that affected 32bit and nvidia when the kernel header files didn't install or where corrupted.... which are needed to install the nvidia drivers.

Look at this post:
[http://ubuntuforums.org/showpost.php?p=10909540&postcount=280](http://ubuntuforums.org/showpost.php?p=10909540&postcount=280)

To confirm it's your video or something else- first boot into a text console turning on verbose logging, using the instructions in post 1 of this sticky:
**[B]Sticky:**[/B]                                      [COLOR=#008C00]**[all variants]**[/COLOR]                          [Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535")
If you can't see anything suspect from that, check your /var/log/xorg.0.log

---

### Post by Panties on 2011-06-27
Okay, here's what I did...

I did try to follow your steps...

After fresh install, on first reboot, it stuck on "Ubuntu Screen".

I hit Ctrl-Alt-F1-F7 and all, it didn't do anything. I even hit "Ctrl-Alt-Del" just to see if it could restart, but no respond. it just hung there.

I press "RESET" on the PC, and now, after Grub selection ,it did *not* stuck on "Ubuntu Screen" anymore, but rather directly goto console.

I login at console.

I follow your steps on [http://ubuntuforums.org/showthread.p...3#post10985233]("http://ubuntuforums.org/showthread.php?p=10985233#post10985233"),
well, now I'm at least in the console, but things get rough.

This command:
[FONT=monospace]
[/FONT]sudo service gdm stop
sudo modprobe -r radeon drm 
sudo modprobe radeon modeset=1 
sudo service gdm start
did not do much, except for the last part.

when GDM Starts, It prompt me if I wanna start it under Low Graphic resolution for troubleshooting, so I did.
and it goes back to  Console once I done that. It didn't do much. It didn't even try to go into the Desktop.

After much attempt, If I type "startx"

It took me into the GUI Desktop and I was relieved for only that moment.

The Desktop was seriously a problem. It doesn't allow me to Launch Network Tools to configure my network, nor anything actually work. It was a dump GUI desktop. The shutdown/Restart button, is also grayed out.

Somehow, I think this was a bad idea, I try to even start Mozilla. It gives me an error. Something tells me, the installation was not completed? @@

I'm confuse and I don't know what I do wrong. I re-print your post onto a piece a paper and give it another go. Yet, nothing prevails.


I guess I'm stuck with 8.04. It works like a charm ... Any suggestion? 

Will it be better, if I disable the Ubuntu 8.04 graphic Drivers only, than Upgrade it to 10.04, and than hopefully, we could enter 10.04 GUI Desktop like normal VGA driver, without ATI? Does that work? @@

---

### Post by Panties on 2011-06-27
Okay, I almost wanna give up.. but I have NOT!

this time, I will upgrade all packages and ATI Drivers using 8.04.

sudo update-manager -d!

to Ubuntu 10.04.


I know it will crash at restart, but I'm gonna do it again.

After reboot, what you guys want me to invoke?

---

### Post by Panties on 2011-06-27
After much googling, I discovered that there are Ubuntu MinimalCD for 10.10 and 11..04..

interesting..


I am downloading those, burn it and give it a ago! :) 

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by Panties on 2011-06-28
epic fail..

okay, this what I have done so far...

I have install and update all through MinimalCD.

After installation completed, it still hang/stuck at Ubuntu splash screen.

Unfortunately, Ctrl-Alt F1-F7 do not work at this point!

[B]<Ctrl><Atl><Backspace> also no go.

[/B]
[B]<Alt>-<SysReq>-<k> doesn't work either.


[/B]At this point, even if I remove the splash screen, I cannot see the error. The screen was too fast! 

Any idea what el****[B]se I miss?
[/B]

---

### Post by MAFoElffen on 2011-06-28
> **Panties said:**
> Okay, here's what I did...

I did try to follow your steps...

After fresh install, on first reboot, it stuck on "Ubuntu Screen".

I hit [COLOR=Green]Ctrl-Alt-F1-F7[/COLOR] and all, it didn't do anything. I even hit "Ctrl-Alt-Del" just to see if it could restart, but no respond. it just hung there.
The terminal session are 1 through 12.  The first 6 terminal sessions are Text console sessions and are hotkeys F1 through F6... The Graphical Xsession starts at default terminal 7, hotkey F7.  So pressing <Cntrl><Alt><F7> while in that same session (Terminal session 7) does go nowhere, because it is already there.  Hitting <Cntrl><Alt><F1>, <Cntrl><Alt><F2>, <Cntrl><Alt><F3>, <Cntrl><Alt><F4><Cntrl><Alt><F5> and <Cntrl><Alt><F6> should toggle through the first 6 terminal sessions.
> **Panties said:**
> I press "RESET" on the PC, and now, after Grub selection ,it did *not* stuck on "Ubuntu Screen" anymore, but rather directly goto console.

I login at console.

I follow your steps on [http://ubuntuforums.org/showthread.p...3#post10985233]("http://ubuntuforums.org/showthread.php?p=10985233#post10985233"),
well, now I'm at least in the console, but things get rough.

This command:
[FONT=monospace]```


```[/FONT]```
sudo service gdm stop
sudo modprobe -r radeon drm 
sudo modprobe radeon modeset=1 
sudo service gdm start

```did not do much, except for the last part.

when GDM Starts, It prompt me if I wanna start it under Low Graphic resolution for troubleshooting, so I did.
and it goes back to  Console once I done that. It didn't do much. It didn't even try to go into the Desktop.

After much attempt, If I type "startx"

It took me into the GUI Desktop and I was relieved for only that moment.

The Desktop was seriously a problem. It doesn't allow me to Launch Network Tools to configure my network, nor anything actually work. It was a dump GUI desktop. The shutdown/Restart button, is also grayed out.

Somehow, I think this was a bad idea, I try to even start Mozilla. It gives me an error. Something tells me, the installation was not completed? @@

I'm confuse and I don't know what I do wrong. I re-print your post onto a piece a paper and give it another go. Yet, nothing prevails.

I guess I'm stuck with 8.04. It works like a charm ... Any suggestion? 

Will it be better, if I disable the Ubuntu 8.04 graphic Drivers only, than Upgrade it to 10.04, and than hopefully, we could enter 10.04 GUI Desktop like normal VGA driver, without ATI? Does that work? @@
Well, IMHO you moved foreward in baby steps, but stil forward.  Between 8,05 abd newer versions there is some graphics changes.  But those graphics changes where made in "multiple" places to support those changes- grub, kernel, xorg and in the proprietary drivers.

The first major change was from Legacy Grub to Grub2.  I really liked those changes... and besides and the capabilities it added, I think it really made things much easier for users.

The kernel added a lot of internal graphics module support and parallel adding KMS (kernel mode switching) support.  The KMS support means that it started adding a technology to take a graphics call from grub (or externally) and pass it on the Xorg, to affect the graphical session.

Xorg added support for newer technologies and the ability to take external calls during it boot (kms).

Each newer version of Linux (not just Ubuntu) implemented these changes.  You will not excape these changes by going to another distribution of Linux or Unix, as these changes are all upstream to these OS bases.

Yes- between 8.04, there are also some changes in syntax and in some applications.  Starting in low=graphics mode or failsafe mode, some applications will not be available.

Yes, your equipment should run 11.04, albeit 8.10 through 10.10.
> Asus P5PE-VM
Core 2 Duo 2.21Ghz (I think..)
2GB RAM DDR1
PCIE 3850 HIS (AGP Edition)
DVD, Harddisk..etc etc..Ideas? What I would do?

If 8.04 is stable for you, diagnose your hardware from that.  If your hard disk has room, resize your first partition to have at least 10 GB space between it and the Linix Swap partition.  Use that partition as a tempary test area to see if newer versions are going to work okay on your hardware... and you can make chages without affecting what is stable for you.

I think if you could get at least 10.04 working stable, looking ahead with things that affect current versions- then it should dist-upgrade from there fine.

One factor that might help is the proprietary drivers... during dist-upgrades, these are not changed... So if they are working and current, then dist-upgrades usually don't break them as bad... (LOL).

Sound Okay as a plan?

---

### Post by MAFoElffen on 2011-06-28
> **Panties said:**
> epic fail..

okay, this what I have done so far...

I have install and update all through MinimalCD.

After installation completed, it still hang/stuck at Ubuntu splash screen.

Unfortunately, Ctrl-Alt F1-F7 do not work at this point!

[B]<Ctrl><Atl><Backspace> also no go.

[/B]
[B]<Alt>-<SysReq>-<k> doesn't work either.


[/B]At this point, even if I remove the splash screen, I cannot see the error. The screen was too fast! 

Any idea what el[B]se I miss?
[/B]
At the grub menu... Press "e" (puts in edit mode) > Move to the linux boot line > remove "quiet splash"  > go the the end of that line and add " radeon.mode=1 --verbose text " > press <cntrl><X> 

It should boot in a text console.  With the verbose switch, it should turn on verbose boot messages for you to review.  It "will" wiz by, but...  Once it starts scrolling by, you can review it by holding down the <Shift> key and another key, navigating a screen up or down by <Shift><Page Up> or <Shift><Page Down> .

That should let you review all that and leave you in a text console to be able to review logs and try other stuff...

Edit--  I did I forget to mention that one of the reasons that I keep telling "you" to remove the "splash" switch from your boot line, is that it was found that that boot switch had problems with your video card?  Well now you do know...

---

### Post by MAFoElffen on 2011-06-28
Please post your /var/log/xorg.0.log. Remember when posting this to use the forum post toolbar and press the " # " icon, then paste the text within the CODE tags.

---

### Post by Panties on 2011-06-29
I tried ur method below and it didn't work. (Honest, I know what you're saying, i even tested this method below on my laptop and it works like a charm...)

My desktop, didn't wanna work. I froze the moment i press Ctrl-X to began booting.

-------------------------------------------------------


At the grub  menu... Press "e" (puts in edit mode) > Move to the linux boot line  > remove "quiet splash"  > go the the end of that line and add "  radeon.mode=1 --verbose text " > press <cntrl><X> 

It should boot in a text console.  With the verbose switch, it should  turn on verbose boot messages for you to review.  It "will" wiz by,  but...  Once it starts scrolling by, you can review it by holding down  the <Shift> key and another key, navigating a screen up or down by  <Shift><Page Up> or <Shift><Page Down> .

That should let you review all that and leave you in a text console to be able to review logs and try other stuff...

Edit--  I did I forget to mention that one of the reasons that I keep  telling "you" to remove the "splash" switch from your boot line, is that  it was found that that boot switch had problems with your video card?   Well now you do know... 		                   		  		  		 		 			 				__________________
				Multi-Boot= Various flavours of Windows, Linux and Unix... Ubuntu user # 33563, Linux user # 533637
[Boot Info Script]("http://bootinfoscript.sourceforge.net/") courtesy of community member meierfra

---

### Post by Panties on 2011-06-29
I think I did resolve my issue.

What I did was I took out the Graphic Card and enable the internal Graphic card.
It didn't work well and froze just now.

I now tried to disable 32MB Transfer rate of the Harddisk and tried again.

Woha, it boot up and install.

I'm installing it right now.

Lets hope and pray that it will go further!

---

### Post by Panties on 2011-06-29
...

---

### Post by Panties on 2011-06-29
Issue Resolved Ubuntu 10.10!

continue from above...
Thanks guys for being supportive!

What happen is, Right after installation and boot, it froze again!

BUT, Ctrl-Alt F1-F7 Works! 

Immediately 

login,
sudo apt-get update
sudo apt-get upgrade
restart


than after that, I can login! I immediately run terminal sudo update-manager -d, update everything and managed to land my OS till 10.10.

I did not upgrade to Natty, coz of FEAR & don't wanna waste time on kernel issues. Now, I turn off the machine. Enable back 32 Transfer rate in BIOS and clean my Gcard Fan, and plug my AGP card back in!

IT booted, but nothing on screen.But WAIT, I can login ( coz I type my username and password in blank/black screen, I can hear the login sound coming out from my soundcard!).
I turn off the machine, went to the Computer shop and got myself DVI - VGA converter. 
Turn it back on, and YEAH! i could see my login screen. So, Now, Updated my Hardware Driver, detected my ATI and install appropriately/automatically.

Upon restart, I switch back to DVI-HDMI Converter, because my Monitor support HDMI. YES! I can see and its crystal sharp.

For now, 10.10 is enough for me.

I would really want to say thanks for all your time and appreciated your advice/knowledge! It may not be "big" for you guys, but your suppose, make 1 happy noob ubuntu, a LIFETIME!. 

Thanks you Thank you THANK YOU! I share my love to all! <Resolved> :)

---

### Post by mörgæs on 2011-06-29
Good, please mark the thread 'solved' using 'thread tools'.

---

