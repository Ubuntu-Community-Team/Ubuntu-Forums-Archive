---
title: "Display problem with Trident Cyberblade Ai1"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by MonkeyPlus on 2008-05-25
I've put Xubuntu on an old Toshiba Satellite but cannot seem to increase the screen resolution past 800x600 which is very annoying as it means I can only use a very small box in the middle of an already small screen.

I've tried specifying a higher resolution in /etc/X11/xorg.conf but with no success. Can anybody help?

---

### Post by Pumalite on 2008-05-25
Post:
lshw

---

### Post by MonkeyPlus on 2008-05-25
> **Pumalite said:**
> Post:
lshw

The relevant bit for the graphics card:

```
*-display UNCLAIMED
description: VGA compatible controller
product: CyberBlade XPAi1
vendor: Trident Microsystems
physical id: 0
bus info: pci@000:01:00.0
version: 82
width: 32 bits
clock: 66MHz
capabilities: agp agp-2.0 pm vga_controller bus_master cap_list
configuration: latency=8
```

---

### Post by Pumalite on 2008-05-25
Bad news. The kernel does not recognize it and does not load the module.

---

### Post by MonkeyPlus on 2008-05-25
> **Pumalite said:**
> Bad news. The kernel does not recognize it and does not load the module.

Is there nothing that I can do?

---

### Post by Pumalite on 2008-05-25
You could try this at your own risk:
sudo apt-get install linux-backports-modules-generic
Do this first:
sudo apt-get update
sudo apt-get upgrade
Try again and if still having problems, try the above command.

---

### Post by MonkeyPlus on 2008-05-25
Its a hardy build downloaded and installed today, so I can't see it needing upgrading.

I couldn't find the module you suggested.

---

### Post by Pumalite on 2008-05-25
Open up all your repos.

---

### Post by MonkeyPlus on 2008-05-25
> **Pumalite said:**
> Open up all your repos.

Theres "linux-backports-modules-2.6.24" and "linux-backports-modules-hardy" but no generic

I've enabled all the repositories I can and I still can't find it.

---

### Post by Pumalite on 2008-05-25
sudo apt-get install linux-backports-modules-`uname -r`

---

### Post by MonkeyPlus on 2008-05-25
Unfortunately there appears to be no change with that module.

---

### Post by MonkeyPlus on 2008-05-25
I have managed to resolve this issue.

For anyone else who has the problem, the key seems to be to add the following to your xorg.conf

```
Section "Device"
  Identifier "Trident Microsystems CyberBlade XPAi1"
  Driver "trident"
  BusID "PCI:1:0:0"
EndSection

Section "Monitor"
  Identifier "Generic Monitor"
  Option "DPMS"
  HorizSync 28-51
  VertRefresh 43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Generic Monitor"
	Device		"Trident Microsystems CyberBlade XPAi1"
	SubSection "Display"
		   Depth 8
		   Modes "1024x768"
	EndSubSection
	SubSection "Display"
		   Depth 16
		   Modes "1024x768"
	EndSubSection
	SubSection "Display"
		   Depth 24
		   Modes "1024x768"
	EndSubSection
	SubSection "Display"
		   Depth 32
		   Modes "1024x768"
	EndSubSection
EndSection
```

This I established through trial and error, so there may be a more efficient way to do the same thing

---

### Post by iahim on 2008-06-12
> **MonkeyPlus said:**
> I've put Xubuntu on an old Toshiba Satellite but cannot seem to increase the screen resolution past 800x600 which is very annoying as it means I can only use a very small box in the middle of an already small screen.

I've tried specifying a higher resolution in /etc/X11/xorg.conf but with no success. Can anybody help?

Hi there,

Just try : sudo displayconfig-gtk. You should have the chance to change the monitor, select 1024x768 and then change the resolution as well. It works for me :) so it should work for you too.

---

### Post by Canobuntu on 2008-06-14
I had a similar problem on a Tosh Laptop. In my case I think it was a new install of Ubuntu Hardy which caused the problem (an upgraded Hardy Kubuntu from Gutsy worked just fine). However, when I compared the xorg.conf files from the working and non-working installs it became obvious that there was a significant difference, so I copied the working xorg.conf file to the not-workling install and hey presto - no more problems.

Anyway, the answer was basically the same as stated above, albeit I got there by a slightly different route.

---

### Post by lantim on 2008-08-01
I success!
```
Section "Monitor"
	Identifier	"Configured Monitor"
      Option      "DPMS"  "true"
      HorizSync    30.0-60.0
      VertRefresh  50.0-70.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
      DefaultDepth      24
      SubSection "Display"
                  Depth         24
                  Modes         "1024x768" "800x600"
      EndSubSection
      
EndSection
```

---

### Post by fryman24 on 2008-11-03
> **MonkeyPlus said:**
> I have managed to resolve this issue.

For anyone else who has the problem, the key seems to be to add the following to your xorg.conf

```
Section "Device"
  Identifier "Trident Microsystems CyberBlade XPAi1"
  Driver "trident"
  BusID "PCI:1:0:0"
EndSection

Section "Monitor"
  Identifier "Generic Monitor"
  Option "DPMS"
  HorizSync 28-51
  VertRefresh 43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Generic Monitor"
	Device		"Trident Microsystems CyberBlade XPAi1"
	SubSection "Display"
		   Depth 8
		   Modes "1024x768"
	EndSubSection
	SubSection "Display"
		   Depth 16
		   Modes "1024x768"
	EndSubSection
	SubSection "Display"
		   Depth 24
		   Modes "1024x768"
	EndSubSection
	SubSection "Display"
		   Depth 32
		   Modes "1024x768"
	EndSubSection
EndSection
```

This I established through trial and error, so there may be a more efficient way to do the same thing

I am having this issue with a Toshiba Satellite 1800 (from Europe, the laptop has the exact same video card). I have tried the solution listed here:
[Thread 4772671]("http://ubuntuforums.org/showpost.php?p=4772671&postcount=1"), but gksudo (or sudo) displayconfig-gtk does absolutely nothing.

And I have added the above lines to my xorg.conf
After adding the above into xorg.conf, I get the following error on boot:
"Ubuntu is running in Low-Graphics Mode
(EE) Problem parsing the config file
(EE) Error parsing the config file"

Here is the relevant portion of 'lspci':
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)
and here is my xorg.conf:
Section "Device"
  Identifier "Trident Microsystems CyberBlade XPAi1"
  Driver "trident"
  BusID "PCI:1:00.0"
EndSection

Section "Monitor"
  Identifier "Generic Monitor"
  Option "DPMS"
  HorizSync 28-51
  VertRefresh 43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Generic Monitor"
	Device		"Trident Microsystems CyberBlade XPAi1"
	SubSection "Display"
		   Depth 24
		   Modes "1024x768"
	EndSubSection
EndSection

Any suggestions for a noob?
Thanks!

---

### Post by roger_1960 on 2008-11-30
Hi

Fryman24, your xorg.conf file is fine but I bet that when you cut and pasted it from the earlier post,you forgot to add a carriage return at then end after "Endsection".  This would cause the error you report!

---

### Post by albythom on 2009-01-04
hi i,m having the same problem with my toshiba satelite pro 6050 when i coppied your command into a terminal it came up endsection command not found,any idea's would be greatly appreciated as i'm a complete newbee and i've never used terminal before

---

### Post by roger_1960 on 2009-01-05
Hi Albython

I think you are a bit confused!  The "code" which ends with "EndSection" and a carriage return, has to be pasted into the system file /etc/X11/xorg.conf  Not into a terminal. To do this it is necessary to use a text editor with administrator rights:

In terminal enter:

gksudo mousepad /etc/X11/xorg.conf

(use gedit instead of mousepad in Ubuntu)

Then enter your password.  You should get a text editor with full editing rights - BE CAREFUL!  The "code" from fryman24's post above should be pasted into the xorg.conf file  (this may be the only thing there if you are using 8.10 Intrepid )  Save the file and reboot.

Hope that makes it clearer!

---

### Post by roger_1960 on 2009-01-05
Hi Albython

I think you are a bit confused!  The "code" which ends with "EndSection" and a carriage return, has to be pasted into the system file /etc/X11/xorg.conf  Not into a terminal. To do this it is necessary to use a text editor with administrator rights:

In terminal enter:

gksudo mousepad /etc/X11/xorg.conf

(use gedit instead of mousepad in Ubuntu)

Then enter your password.  You should get a text editor with full editing rights - BE CAREFUL!  The "code" from fryman24's post above should be pasted into the xorg.conf file  (this may be the only thing there if you are using 8.10 Intrepid )  Save the file and reboot.

Hope that makes it clearer!

---

### Post by albythom on 2009-01-06
hey thanks for that it works now i can stop pulling my hair outand get on  with setting up my system
again many thanks:D:popcorn:

---

### Post by albythom on 2009-01-06
thanks for the help now i know how it works.

---

### Post by CBJFanGirl on 2009-01-17
Thank you for this thread!!  I nearly gave up temporarily on ubuntu until I read this.  I have a Toshiba laptop with this video card and I was getting frustrated with the small screen.  I am completely new to Linux and didn't have the time to go through this until I found this and a few other threads.  Thank you!! 

:)

---

### Post by royrutter on 2009-03-25
thank you all for this. I'm totally new to ubuntu/linux and had the same Toshiba display problem, now it's fixed I'm so relieved and can get on learning how to use it.

---

### Post by steveeeee on 2009-04-16
> **MonkeyPlus said:**
> I have managed to resolve this issue.

For anyone else who has the problem, the key seems to be to add the following to your xorg.conf

```
Section "Device"
  Identifier "Trident Microsystems CyberBlade XPAi1"
  Driver "trident"
  BusID "PCI:1:0:0"
EndSection

Section "Monitor"
  Identifier "Generic Monitor"
  Option "DPMS"
  HorizSync 28-51
  VertRefresh 43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Generic Monitor"
	Device		"Trident Microsystems CyberBlade XPAi1"
	SubSection "Display"
		   Depth 8
		   Modes "1024x768"
	EndSubSection
	SubSection "Display"
		   Depth 16
		   Modes "1024x768"
	EndSubSection
	SubSection "Display"
		   Depth 24
		   Modes "1024x768"
	EndSubSection
	SubSection "Display"
		   Depth 32
		   Modes "1024x768"
	EndSubSection
EndSection
```

This I established through trial and error, so there may be a more efficient way to do the same thing

Thanks MonkeyPlus! I was stuck in 800x600 running Xubuntu 8.10 on a Thinkpad R30 with CyberBlade i1 and your xorg.conf has given me glorious full-screen 1024x768! :D

---

### Post by kimharding on 2009-04-27
At last a technique which works with my Toshiba Satellite Pro, thanks!!

---

### Post by musicatplay on 2009-05-06
Thanks so much!  This worked flawlessly on an old Toshiba laptop I had sitting around collecting dust!!

> **MonkeyPlus said:**
> I have managed to resolve this issue.

For anyone else who has the problem, the key seems to be to add the following to your xorg.conf

```
Section "Device"
  Identifier "Trident Microsystems CyberBlade XPAi1"
  Driver "trident"
  BusID "PCI:1:0:0"
EndSection

Section "Monitor"
  Identifier "Generic Monitor"
  Option "DPMS"
  HorizSync 28-51
  VertRefresh 43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Generic Monitor"
	Device		"Trident Microsystems CyberBlade XPAi1"
	SubSection "Display"
		   Depth 8
		   Modes "1024x768"
	EndSubSection
	SubSection "Display"
		   Depth 16
		   Modes "1024x768"
	EndSubSection
	SubSection "Display"
		   Depth 24
		   Modes "1024x768"
	EndSubSection
	SubSection "Display"
		   Depth 32
		   Modes "1024x768"
	EndSubSection
EndSection
```

This I established through trial and error, so there may be a more efficient way to do the same thing

---

### Post by smerf on 2009-05-23
Hi,

I had the same problem, I tried to load Ubuntu 8.04 on my machine, could only get 800X600 screen on my toshiba laptop, I next tried 7.04 and saw that it would give me 1024X768. Next I tried Ubuntu 7.10 and I received same results as Ubuntu 7.04 a 1024X768 screen but now I could upgrade to Ubuntu 8.04 through an upgrade package. so what the heck gave it a try, Ubuntu 8.04 upgraded giving me my right driver and a 1024 X 768 screen.

Good Luck this really works, hope you can get hold of Ubuntu 7.10.

smerf

Amiga is dead, dead dead, now we are all stuck with winblows.

Thank God for Ubuntu or if you are a non believer, thank the Ubuntu programmers.

---

### Post by stuart.reinke on 2009-06-21
Problem fixed on my Toshiba laptop also :D

what exactly did I do by changing the xorg.conf file and why did it have to be done manually?

---

### Post by wmichaelb on 2009-07-07
Monkeyplus: This worked perfectly on my Toshiba Satellite 1805-S204, thank you very much for your meticulous documentation and sharing!

---

### Post by Jonesy939 on 2009-08-04
It has to do with the integrated video chip in the laptop.  I've read up on it and it seems to be a unique case.  It's interesting that it doesn't have the problem when running from the live cd.  I am still working on getting mine to run correctly.  Wish me luck

---

### Post by wmichaelb on 2009-08-05
> **Jonesy939 said:**
> It has to do with the integrated video chip in the laptop.  I've read up on it and it seems to be a unique case.  It's interesting that it doesn't have the problem when running from the live cd.  I am still working on getting mine to run correctly.  Wish me luck
Jonesy: I found a link that helped, and edited my /etc/xorg/xorg.conf file with a text editor as follows:

> # xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Trident Microsystems CyberBlade XPAi1"
	Driver "trident"
	BusID "PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option "DPMS"
	HorizSync 28-51
	VertRefresh 48-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Generic Monitor"
	Device		"Trident Microsystems CyberBlade XPAi1"
	SubSection "Display"
		   Depth 16
                   Modes "1024X768"
	EndSubSection                 
EndSection


And now I have full 1028X760 screen operation. Maybe this will helpl

In passing, my machine is only a 1 GHz processor, so I also did two other things. I added a Task List to the bottom panel, Windows-style, so that I could be sure to shut off apps that I wasn't using, and then installed Opera as a browser. It's quicker than Firefox 3.0. Right now, the machine is at least usable.

Good luck!

---

### Post by littlematt on 2009-09-03
> **MonkeyPlus said:**
> I have managed to resolve this issue.

For anyone else who has the problem, the key seems to be to add the following to your xorg.conf

```
Section "Device"
  Identifier "Trident Microsystems CyberBlade XPAi1"
  Driver "trident"
  BusID "PCI:1:0:0"
EndSection

Section "Monitor"
  Identifier "Generic Monitor"
  Option "DPMS"
  HorizSync 28-51
  VertRefresh 43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Generic Monitor"
	Device		"Trident Microsystems CyberBlade XPAi1"
	SubSection "Display"
		   Depth 8
		   Modes "1024x768"
	EndSubSection
	SubSection "Display"
		   Depth 16
		   Modes "1024x768"
	EndSubSection
	SubSection "Display"
		   Depth 24
		   Modes "1024x768"
	EndSubSection
	SubSection "Display"
		   Depth 32
		   Modes "1024x768"
	EndSubSection
EndSection
```

This I established through trial and error, so there may be a more efficient way to do the same thing


Thanks for this.

Worked on my Toshiba Portege 3500 for Ubuntu Jaunty Jackalope.


littlematt

---

### Post by bruceo on 2009-11-14
Thanks this finally worked for me on a Toshiba Portege 3505.
I don't know how many of these 3505's were made.
Nice little laptop but... 
Guess it's no surprise that this has been the most painful Ubuntu install ever for me.
Windows XP Tablet version is no treat either... which is why I am going through the pain.
Anyway, I never would have gotten it working without your help.

---

### Post by black28 on 2009-12-04
i also have a Cyberblade il, did you guys post straight into the xorg.conf file? or did you guys change the device names to il and save? i did that and it left me in shell mode at boot up.

---

### Post by wmichaelb on 2009-12-04
Black28: What I did is copied and pasted into my post, which is above at no. 32. Try cutting and pasting that into your xorg.conf file; it worked for me. 

Did you back up your xorg.conf file before editing?

---

### Post by black28 on 2009-12-04
I tried that and rebooted and it says 'low graphics mode' my card is actually 1l and not A1l so I also tried to substitute that in and got the same message. anyone know how and what to paste in the xorg.conf file for Trident Microsystems Cyberblade 1l?

---

### Post by roger_1960 on 2009-12-06
Hi
There seems to be confusion on fonts.  The original solution was for the Ai1 (ay eye one) not an A1l.  Could simple misreading of fonts be the issue?

---

### Post by Mechageo on 2010-01-13
> **steveeeee said:**
> Thanks MonkeyPlus! I was stuck in 800x600 running Xubuntu 8.10 on a Thinkpad R30 with CyberBlade i1 and your xorg.conf has given me glorious full-screen 1024x768! :D
Thank you very much!
This helped me understand xorg.conf more and solved the issue on my Toshiba Portege 4010's.

:KS

---

### Post by Skip Da Shu on 2010-02-02
> **MonkeyPlus said:**
> I have managed to resolve this issue.

For anyone else who has the problem, the key seems to be to add the following to your xorg.conf

```
Section "Device"
  Identifier "Trident Microsystems CyberBlade XPAi1"
  Driver "trident"
  BusID "PCI:1:0:0"
EndSection

Section "Monitor"
  Identifier "Generic Monitor"
  Option "DPMS"
  HorizSync 28-51
  VertRefresh 43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Generic Monitor"
	Device		"Trident Microsystems CyberBlade XPAi1"
	SubSection "Display"
		   Depth 8
		   Modes "1024x768"
	EndSubSection
	SubSection "Display"
		   Depth 16
		   Modes "1024x768"
	EndSubSection
	SubSection "Display"
		   Depth 24
		   Modes "1024x768"
	EndSubSection
	SubSection "Display"
		   Depth 32
		   Modes "1024x768"
	EndSubSection
EndSection
```

This I established through trial and error, so there may be a more efficient way to do the same thing

I did the following after a fresh install of v9.10:

1) exit to tty (Ctrl-Alt-F1)
```
sudo service gdm stop
```
Then to create an xorg.conf (not in /etc/X11 by default in v9.10)
```
sudo Xorg -configure
```
Restarted: This thing will not reboot yet, have to power off, it will work using ```
sudo shutdown -P now
``` but not ```
sudo reboot
```... anyway, that's a different issue.

I copied the generated xorg.conf.new to /etc/X11/xorg.conf and rebooted.
Then copied and pasted the above over the entire generated xorg.conf.  I did edit out the depth 8 and depth 32 entries in "screen".

Save the updated xorg.conf and reboot again.  Excellence!  Well, almost.
If you putz'd around with System->Preferences->Display like I had before finding this, what will happen is that it'll reboot to a full 1024x768 login screen but while you login it'll pick up the (now) user based display preferences and switch you back to 800x600 during login.  All you need to do at this point is got back to System->Preferences->Display and you'll now have an option for 1024x768.  Select it as default and you're now good to go!

Thanx for the excellent xorg.conf fix that CAN be applied to Karmic with just a couple extra steps.

Skip

---

### Post by Skip Da Shu on 2010-02-02
BTW... This applies to UBUNTU as well as Xubuntu... could you retag it?

---

### Post by JPWhite on 2010-02-17
Thanks to MonkeyPlus. The Xorg changes work perfectly with Xubuntu 9.10.

Nice to see a full size screen!!:popcorn:

JP

Toshiba Satellite 1800-S208
512 MB Ram
20 GB HDD
1.1 Ghz CPU

---

### Post by dic amore on 2010-04-01
i'm having the same problem with my toshiba satelite 1805 S204.
Somebody can help me, how i can found xorg.conf?
then what should i do after that?
[-o<
this first time i installing linux.
i had install ubuntu 9.10. i'm a newbie.

---

### Post by pnguine on 2010-04-02
Thanks for this thread - it helped me set up xorg in (shhhh)-FreeBSD on a Satellite 1800. Only diff was that x said the trident driver didn't exist so I tried leaving the driver as 'vesa' and it worked.

---

### Post by goneplumcrazy on 2010-04-10
> **roger_1960 said:**
> Hi Albython

I think you are a bit confused!  The "code" which ends with "EndSection" and a carriage return, has to be pasted into the system file /etc/X11/xorg.conf  Not into a terminal. To do this it is necessary to use a text editor with administrator rights:

In terminal enter:

gksudo mousepad /etc/X11/xorg.conf

(use gedit instead of mousepad in Ubuntu)

Then enter your password.  You should get a text editor with full editing rights - BE CAREFUL!  The "code" from fryman24's post above should be pasted into the xorg.conf file  (this may be the only thing there if you are using 8.10 Intrepid )  Save the file and reboot.

Hope that makes it clearer!

ubuntu 9.10

I know  this thread is old but I could really use some help.  I've got a Toshiba Satellite Pro 4600 with the Trident Cyberblade XP graphics card. I copied the code exactly as above in the earlier post which it did successfully gave the bigger screen resolution but I'm also getting the "ubuntu is running in low-graphics mode  The following error was encountered.  You may need to update your configuration to solve this.  (EE) Problem parsing the config file (EE) Error parsing the config file."

I followed the steps, but what  do you mean by  carriage return at then end after "Endsection"?  Just a regular enter after "Endsection"?  If so then I tried adding that also and it did not work.  Help.

---

### Post by pnguine on 2010-04-10
Sometimes you can get errors like that from simple typo's, like a spelling mistake or using a ' where it should be a ". All I can suggest is that you check the file carefully for that. As for the carriage return I think that is right - you just need to make sure you enter one at the end of the last line (the cursor will be at the beginning of the line underneath the last line of text before you save it).

HTH

---

### Post by roger_1960 on 2010-04-14
Hi Goneplumcrazy

Yes, I literally meant check that there is a carriage return as per pnguine's post above.  If you just copy and paste text from a post its easy to miss this.

The Trident Cyberblade XP is not the same card so not sure I can help further.

---

### Post by goneplumcrazy on 2010-06-03
> **roger_1960 said:**
> Hi Goneplumcrazy

Yes, I literally meant check that there is a carriage return as per pnguine's post above.  If you just copy and paste text from a post its easy to miss this.

The Trident Cyberblade XP is not the same card so not sure I can help further.

ty 4 replying gonna test out more stuff when i get a chance

---

### Post by MJR22 on 2010-07-02
thanks - after a couple of hours driver searching - this was all I needed to do, worked great :)

---

### Post by compiz addict on 2010-07-21
Thanks a million MonkeyPlus! I also have a Toshiba Satellite which is really old and crappy, but this method worked well on Lubuntu 10.04. I had to create the /etc/X11/xorg.conf file myself because it wasn't there, but all worked well in the end.

---

### Post by jhunterb18 on 2010-07-26
> **lantim said:**
> I success!
```
Section "Monitor"
    Identifier    "Configured Monitor"
      Option      "DPMS"  "true"
      HorizSync    30.0-60.0
      VertRefresh  50.0-70.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
      DefaultDepth      24
      SubSection "Display"
                  Depth         24
                  Modes         "1024x768" "800x600"
      EndSubSection
      
EndSection
```

I just wanted to say thanks. This is the very first time using ubuntu and I hated the small screen but this fixed my problem and gave me full screen. However, I am still looking up how to get visual effects...

---

### Post by roger_1960 on 2010-07-26
Hi jhunterb

You're not going to get any visual effects if you are using a Trident Cyberblade!  Its too old and basic.

---

### Post by jhunterb18 on 2010-07-27
> **roger_1960 said:**
> Hi jhunterb

You're not going to get any visual effects if you are using a Trident Cyberblade!  Its too old and basic.

Well that hurts... lol Guess I'll need to upgrade to a better laptop. Either way, after only using Ubuntu for a day now I prefer it over windows already, and have already formatted my HDD and and am now just running Ubuntu. 

Think theres a way to get videos to play better? Thats really my only other concern right now.

---

### Post by roger_1960 on 2010-07-27
Hi

Have a look at this link (a sticky from multimedia and video forum)  It gives precise instructions on how to optimise playback.  My 900MHz Celeron laptop with Trident Cyberblade just about plays Videos.  

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by tony1212 on 2010-08-25
Hi Just like to thank MonkeyPlus for the xorg.conf script with a bit of a tweak (puting a line space in before each of the 'end section') this also worked on my Toshiba Portege 2010 laptop and I now have a full 1024x768 screen and a fully working Ubuntu 10.04 system running.

Not bad for a P3 866 with only 256mb Ram (additional 256mb now on order)

---

### Post by herrdeh on 2010-09-02
Hello everybody you happy fellows,

I wasted half a night to make a Toshiba Satellite 1800-750 work on xubuntu 10.04 - and do not get it. - It worked without any glitch on 7.10.

I tried as stated above, but my Toshi gets stuck at various states - according to various findings these messages are irrelevant, as all has to do with X11 not working. 

I found that inserting

GRUB_cmdline_LINUX="i915.modeset=0"

into /etc/defaults/grub

gets me a bit forward, but when doing startx, the machine gets stuck with a dark screen, and I do not even find a way to terminate it than with a brutal hard reset.

I'd be grateful if some helpful fellow would take me by the hands.

Yours, Wolf

 PS.: "*.txt" extensions at the attachments are just for uploading

---

### Post by herrdeh on 2010-09-04
I copied the xorg.conf data on a Mac and didnt realize, that in this way there were tabstops in the xorg.conf file. Removing the tabstops made the machine work.

It works like Michael Minn describes here:

[http://michaelminn.com/linux/toshiba1800/]("http://michaelminn.com/linux/toshiba1800/")

in addition I had to add to modify /etc/default/grub:

```

GRUB_cmdline_LINUX="i915.modeset=0"

```

Greetings,

herrdeh

---

### Post by donc786 on 2010-09-25
> **MonkeyPlus said:**
> I have managed to resolve this issue.

For anyone else who has the problem, the key seems to be to add the following to your xorg.conf

```
Section "Device"
  Identifier "Trident Microsystems CyberBlade XPAi1"
  Driver "trident"
  BusID "PCI:1:0:0"
EndSection

Section "Monitor"
  Identifier "Generic Monitor"
  Option "DPMS"
  HorizSync 28-51
  VertRefresh 43-60
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Generic Monitor"
    Device        "Trident Microsystems CyberBlade XPAi1"
    SubSection "Display"
           Depth 8
           Modes "1024x768"
    EndSubSection
    SubSection "Display"
           Depth 16
           Modes "1024x768"
    EndSubSection
    SubSection "Display"
           Depth 24
           Modes "1024x768"
    EndSubSection
    SubSection "Display"
           Depth 32
           Modes "1024x768"
    EndSubSection
EndSection
```This I established through trial and error, so there may be a more efficient way to do the same thing

Worked great for me on a Toshiba Portege 3500 running Xubuntu 10.04 in XFCE.  Thanks a lot, I am much happier with this computer now that all my systems are running Ubuntu in one form or another.

---

### Post by majorw00dy on 2010-10-01
If none of those options work edit/create the xorg.conf and add this under device/card0 section:
```
Option   "NoDDC"
```

---

### Post by NotWindows on 2010-10-31
Hello, I need to put this code into my XORG file but not sure how it is to be done. Can someone tell me how to open the file and with what program so I can add the code.

I am running Ubuntu 9.10

Thanks,
Kevin

---

### Post by pnguine on 2010-11-05
There's probably a million ways to do this - someone please correct this if it's wrong.

First back up the original: open a terminal -> do 'sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.back'

then do -> sudo gedit /etc/X11/xorg.conf

make your changes

save the file

post back later to find out what went wrong  8-[

---

### Post by NotWindows on 2010-11-17
This did the trick but I only had to use the 2nd instruction in Terminal then put the code in and save it. I rebooted and right there it was all filled out!!!!!!!!!!!!!!

Thanks Guys!
Kevin

---

### Post by prince5325 on 2010-11-18
1. Define your NON PCI device model.
                
                2. Define your operating system to install your NON PCI device.
                
                3. Browse PCI Drivers.
                
                4. Find NON PCI Drivers.
                
                5. Select Trident Video Accelerator CyberBlade-Ai1.
                
                6. Download Trident Video Accelerator CyberBlade-Ai1. Note: you can update all Drivers automatically with [RadarSync]("http://www.*****************/radarsync/") (Freeware) or [**DriverScanner**]("http://www.liutilities.com/affcb/?id=DSdownloadatoz&aff=2010&xat=atozDS2") (Shareware).
                
                7. Install Trident Video Accelerator CyberBlade-Ai1.
                
                8. Restart or reboot your computer to finish your driver installation. Note: you can [backup your computer drivers]("http://tutorial.*****************/backup-computer-drivers-with-driver-detective.html") before updating.

---

### Post by gjosef on 2010-11-21
Worked on a Toshiba Portégé 7100 running Xubuntu 10.04.

---

### Post by gjosef on 2010-11-21
> **gjosef said:**
> Worked on a Toshiba Portégé 7100 running Xubuntu 10.04.

That is, Skip Da Shu's routine based on MonkeyPlus' conf file.

---

### Post by mike_burkholder on 2011-04-12
Hello,

I'm new to forums but not to Linux. I've installed Xubuntu 10.10 on a friends TE2000 which has the TRident card. I also had problems with the screen which led me to here and I changed my Xorg.conf to the one Xorg.conf posted in this forum. It runs, and I was excited that it did however, the screen and system seems to lock up at random times. I'm just wondering if anyone else has experienced this issue?

Regards,

Mike

---

### Post by gjosef on 2011-04-13
By now, I've run this trick on three or four laptops.
Only one of them has a hangup problem like you describe, the Toshiba Portégé 7100. But this computer would freeze with any windows version newer than windows 98, so I think it's a hardware issue, not linux. Fortunately it only freezes on startup, so if I reboot a couple of times, I can usually make it work.

---

### Post by wmichaelb on 2011-04-13
Periodically, I found the Toshiba mentioned in the posting above running Xorg at 100% CPU for long periods. I never did figure out exactly what it was doing, but it led me to put Puppy Linux on that machine, and that runs much better. The Puppy 5.11 version runs a bit better on this machine than the subsequent 5.20, and there is a MacPup 5.11 version that uses the Enlightenment desktop, rather than the default Fluxbox, and that's the one I'm running. The Xorg problem went away, and this particular distro detects the Trident chip set and audio flawlessly, and boots quickly. I installed the Iron browser, which is Google Chrome without all the tracking bits, and that makes this old machine pretty usable. Check it out, puppylinux.org or puppylinuxfaq.org.

---

### Post by mike_burkholder on 2011-04-13
Thanks fellow Michael B,

I had tried Puppy Linux as well and discovered the same thing detecting and everything. I was hoping to get Xubuntu going to take advantage of the ubuntu educational software packages because my friend has two girls in elementary school that would be the primary users.

I may have to revisit the puppy trail. I think they'll probably use it mostly for internet browsing anyways. 

Thanks for your help.

Mike

---

### Post by wmichaelb on 2011-04-13
Did I mention that the newest 5.x versions of Puppy are binary-compatible with Ubuntu? Check out the Puppy Lucid repositories; you may yet get the educational packages to work.

---

### Post by mike_burkholder on 2011-04-17
I had a look at Macpup 5.11 and changed the video driver with the wizard to Xorg_high to get the 1024 x 746. I went into the xorg.conf file and notice that its very similar to my configuration for xubuntu even using the trident driver. I just wondering what the difference is and will Macpup have the same problem of the locking screen as xubuntu?

Mike

---

### Post by wmichaelb on 2011-04-17
Mike: all I can tell you is that I haven't had the xorg problem with MacPup on the machine I'm typing on now, and I did have that problem with Xubuntu on the same machine. I can't get any newer Debian-related distro to boot on this machine at all, but any and all versions of Puppy that I've tried have worked fine. I'm running Macpup 5.2 right now, and I'm usint the Macpup modified Xorg_high driver version. It's available for download from macpup.org/runtt21. 

Good luck!

---

### Post by mike_burkholder on 2011-05-09
Hey Michael, I was wondering if you had any issues with setting up the wireless using pup? I know I didn't get it going under xubuntu ... too focused on fixing the screen issue.

---

### Post by cuyabro on 2012-03-26
Hi guys, 

I am running Puppy 5.20 on a Toshiba Satellite 204-S177 which uses the Trident Cyberblade Ai! graphics card mentioned here. Screen resolution is working fine for me however I want to use 2 monitors to extend my desktop onto the external LCD I have.  I've spent countless hours trying to get this to work but I just can't get it working.  When I connect the external monitor to my laptop and turn it on, the same screen is displayed on both monitors after using the function key to toggle between my laptop screen and the external LCD but it never extends my desktop.  I tried using Grandr but it only detects one output identified as 'default'.

I've tried editing the xorg.conf as well. Looking at the /etc/X11 directory I see other xorg files xorg.conf.Trident_CYBER_8820ToshibaInte and Xorg.Conf.Trident_CYBER_8820Westinghouse.  I made backups and tried editing them to coincide with xorg.conf but nothing seems to work.  I have attached the xorg.conf mentioned above.  Any help is appreciated.

---

