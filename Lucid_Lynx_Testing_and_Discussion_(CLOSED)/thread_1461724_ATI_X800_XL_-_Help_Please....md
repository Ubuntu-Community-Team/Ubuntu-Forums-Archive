---
title: "ATI X800 XL - Help Please..."
date: 2010-04-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by crjackson on 2010-04-24
Ubuntu will only boot into Low Graphics mode for me due to this video card.

I've installed the xorg-edgers PPA and got no joy with that.

Can someone tell me how to make the default boot a Low Graphics session every time (so my kids don't have to use rescue mode to boot)?  Or does anyone have any idea how to make this card work normally?

All help is welcome.

---

### Post by Yellow Pasque on 2010-04-24
You could just make a simple /etc/X11/xorg.conf to force vesa:
```
Section "Device"
	Identifier	"Configured Video"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video"
EndSection
```

It would be nice to see the /var/log/Xorg.0.log when you try to boot with the radeon driver.

---

### Post by crjackson on 2010-04-24
> **Temüjin said:**
> You could just make a simple /etc/X11/xorg.conf to force vesa:
```
Section "Device"
	Identifier	"Configured Video"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video"
EndSection
```

It would be nice to see the /var/log/Xorg.0.log when you try to boot with the radeon driver.

Okay, I'll give this a try.

Tell me how to get the log information and I'll show it to you.  Remember it hard locks when I try to do a regular boot.

---

### Post by crjackson on 2010-04-24
Okay, so I booted using the xorg.conf file as posted.  It then gives me a warning about low graphics mode and I have to confirm to continue.

If I click ANYTHING else (i.e. configure hardware). It keeps looping through the same menu and won't let me either configure or continue booting.  I have to hard reboot to get out of this.

If I confirm that it's just for one session, then it will continue to boot to a normal desktop.

---

### Post by crjackson on 2010-04-24
Okay, I've attached all the log files in the previous post.

---

### Post by NoVista on 2010-04-24
Just making sure you uninstalled xorg-edgers PPA properly >>
Uninstalling:
Use ppa-purge or remove any references (in sources.list) to this PPA and run:
sudo apt-get install libgl1-mesa-dri/lucid libgl1-mesa-dri-dbg/lucid libgl1-mesa-glx/lucid libgl1-mesa-glx-dbg/lucid libglu1-mesa/lucid mesa-utils/lucid

---

### Post by crjackson on 2010-04-24
> **NoVista said:**
> Just making sure you uninstalled xorg-edgers PPA properly >>
Uninstalling:
Use ppa-purge or remove any references (in sources.list) to this PPA and run:
sudo apt-get install libgl1-mesa-dri/lucid libgl1-mesa-dri-dbg/lucid libgl1-mesa-glx/lucid libgl1-mesa-glx-dbg/lucid libglu1-mesa/lucid mesa-utils/lucid

I'm not sure I understand why I'm now uninstalling the PPA and updates I just added.  Please elaborate...

I see that you are using the All in wonder x800 xt.  Can you tell me what special steps you took (if any) to get your system to boot in normal graphics mode?

---

### Post by clhsharky on 2010-04-24
HI crjackson

Is your card AGP type?

Sharky

---

### Post by crjackson on 2010-04-24
> **clhsharky said:**
> HI crjackson

Is your card AGP type?

Sharky

No.  PCIe

---

### Post by clhsharky on 2010-04-24
HI crjackson

Radeon module might not have been built right or started at right time.

Check firmware 'R420_cp.bin' is in /lib/firmware/radeon/ and in /lib/firmware/"your kernel"/radeon/ . Might want to use newer kernel on OSS drivers, when radeon is working.

also that /etc/modprobe.d/radeon-kms.conf has 'options radeon modeset=1' 

Now put radeon back in xorg.conf instead of vesa.

And now Edit /etc/initramfs-tools/modules and add radeon. Run update-initramfs -k all -u 
Reboot

Sharky


From 'man radeon' might be relevant to turn this option on for your card and Lucid

Option "R4xxATOM" "boolean"
              This  option  enables  modesetting on R/RV4xx chips using atombios.  The default is
              off.

What Is AtomBIOS & These Different Drivers?
[http://www.phoronix.com/forums/showthread.php?t=7032](http://www.phoronix.com/forums/showthread.php?t=7032)

lots of info
Open-Source AMD/ATI Linux 
[http://www.phoronix.com/forums/forumdisplay.php?f=43](http://www.phoronix.com/forums/forumdisplay.php?f=43)

---

### Post by crjackson on 2010-04-24
> **clhsharky said:**
> HI crjackson

Radeon module might not have been built right or started at right time.

Check firmware 'R420_cp.bin' is in /lib/firmware/radeon/ and in /lib/firmware/"your kernel"/radeon/ . Might want to use newer kernel on OSS drivers, when radeon is working.

also that /etc/modprobe.d/radeon-kms.conf has 'options radeon modeset=1' 

Now put radeon back in xorg.conf instead of vesa.

And now Edit /etc/initramfs-tools/modules and add radeon. Run update-initramfs -k all -u 
Reboot

Sharky

Okay, I'll try this and report back.

---

### Post by clhsharky on 2010-04-24
HI crjackson

Please check my previous post I have added more info.

Sharky

---

### Post by crjackson on 2010-04-24
> **clhsharky said:**
> HI crjackson

Please check my previous post I have added more info.

Sharky

Already did but thanks.  I'm drinking a beer and watching Star Trek.  As soon as it goes off I'll go play and see what happens.

---

### Post by crjackson on 2010-04-24
Made all the suggested changes.  Sadly it's still not booting unless I go to recovery mode and select low graphics.

---

### Post by Yellow Pasque on 2010-04-24
Can you test other LiveCD distros on USB sticks? At this point, I'm thinking hardware problem.

---

### Post by crjackson on 2010-04-25
> **Temüjin said:**
> Can you test other LiveCD distros on USB sticks? At this point, I'm thinking hardware problem.

Ubuntu 8.10 is the last distrobution that fully loaded.  It works flawless with compiz and everything and is very fast.  It's not defective hardware.

I just popped in an 8.10 LiveCD and bang!  Everything works fine!  It's using the standard OSS driver, but shows the FGLRX proprietary driver is available from the Hardware Driver Applet.

---

### Post by crjackson on 2010-04-25
Well, I guess my choices are to either run 8.10 or buy as new video card. I prefer option 2, but I lost my job 2 months ago and spending money right now is a problem.

---

### Post by crjackson on 2010-04-25
I've got to say I'm pretty unhappy at this point.  I've been working with this all damned day, and I'm not making any progress at all.

Anyone else care to take a shot at it?

---

### Post by clhsharky on 2010-04-25
HI

Put 
```
radeon.modeset=0
```
in the boot string, will give you UMS 'user mode setting' in stead of KMS. Seem to help on some old radeons.

Sharky

---

### Post by crjackson on 2010-04-25
> **clhsharky said:**
> HI

Put 
```
radeon.modeset=0
```
in the boot string, will give you UMS 'user mode setting' in stead of KMS. Seem to help on some old radeons.

Sharky

Do I put this in a file, or hit a key in Grub and make the entry?

---

### Post by crjackson on 2010-04-25
okay, so I rebooted, hit the e key, added radeon.modeset=0 on an empty line near the top and continued to boot.

System locked up at the purple screen with the progress dots as usual.  Did I put this in the wrong place?

---

### Post by clhsharky on 2010-04-25
HI crjackson

Go to
/etc/default/grub
then to 
GRUB_CMDLINE_LINUX_DEFAULT=
add " radeon.modeset=0"
It should look like this.
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.modeset=0"

I would remove splash for now, plymouth been known to cause boot problems.
GRUB_CMDLINE_LINUX_DEFAULT="quiet radeon.modeset=0"

update  '  update-grub  '

Might even want to remove splash first, at least you can see what is going on at boot,don't forget to update grub after a boot line change.

Sharky

You sure got me  with this radeon thing!

---

### Post by crjackson on 2010-04-25
> **clhsharky said:**
> HI crjackson

Go to
/etc/default/grub
then to 
GRUB_CMDLINE_LINUX_DEFAULT=
add " radeon.modeset=0"
It should look like this.
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.modeset=0"

I would remove splash for now, plymouth been known to cause boot problems.
GRUB_CMDLINE_LINUX_DEFAULT="quiet radeon.modeset=0"

update  '  update-grub  '

Might even want to remove splash first, at least you can see what is going on at boot,don't forget to update grub after a boot line change.

Sharky

You sure got me  with this radeon thing!

Okay, made all the edits/updates.  It doesn't HARD lock (mouse still moves) but it stops booting before I can ever see a desktop.

---

### Post by clhsharky on 2010-04-25
HI crjackson

Can you still start in safe mode 'vesa'?

Have you try'ed ' startx ' in start up terminal
or
```
sudo /etc/init.d/gdm restart
```
?

Sharky

---

### Post by clhsharky on 2010-04-25
crjackson

What kernel are you on?

Sharky

---

### Post by crjackson on 2010-04-26
> **clhsharky said:**
> HI crjackson

Can you still start in safe mode 'vesa'?

Have you try'ed ' startx ' in start up terminal
or
```
sudo /etc/init.d/gdm restart
```
?

Sharky

VESA works but I have to go through the annoying Safe Graphics Menu to boot.

Once it locks during a normal attempt to boot, you can't get to a terminal.

---

### Post by crjackson on 2010-04-26
> **clhsharky said:**
> crjackson

what kernel are you on?

Sharky

2.6.32-21

---

### Post by Hairy_Palms on 2010-04-26
could try removing plymouth, i know that caused non-boots early in the cylce with my nvidia card.

---

### Post by ljrmorgan on 2010-04-26
I have the same card, running Lucid flawlessly, I haven't had to muck about with drivers, using the OSS ones. I upgraded from Karmic which was a clean install (and also worked fine) - did you upgrade directly from the last LTS? Could that be the problem?

Is there anything I can do to help? (post config files, etc...)

---

### Post by crjackson on 2010-04-26
> **ljrmorgan said:**
> I have the same card, running Lucid flawlessly, I haven't had to muck about with drivers, using the OSS ones. I upgraded from Karmic which was a clean install (and also worked fine) - did you upgrade directly from the last LTS? Could that be the problem?

Is there anything I can do to help? (post config files, etc...)

I really can't understand what is going on with this.  It was a clean install.  Intrepid was the last release that worked flawlessly on this machine.  The problem with this card started with Jaunty.  It wasn't until Lucid that I decided to try with low graphics mode and found that it works fine.

Mainboard: MS-7145

CPU:       AMD Athlon 64 3200+ Socket 754

Memory:    512MB Crucial

Video:     ATI X800 XL 256MB  PCIe

HD:        100GB PATA SEAGATE

DVD:       Dual Layer DVD Burner (LG or Liteon)

---

### Post by ljrmorgan on 2010-04-26
I should add that my card is also 256MB PCIe. Might it be a hardware problem?

---

### Post by crjackson on 2010-04-26
No, it works perfectly fine with Ubuntu 8.10 and lower as well as other OS's.

---

### Post by clhsharky on 2010-04-26
HI crjackson


Have you put all your settings back to original or where are you now?

> Once it locks during a normal attempt to boot, you can't get to a terminal.

Sorry I meant at startup choose shell, it might be recovery mode or something like that, instead of safe graphics.

After looking at your Xorg. logs it seems to be ignoring your xorg.conf file that points to radeon.

On desktop 'safe mode' right, check your xorg.conf file, heres mine, make sure radeon is there correctly. 
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"radeon"
        Option          "ColorTiling"           "on"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

Then pull up terminal and run

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

then recheck that radeon is still in xorg.conf
Restart into 'recovery mode' shell not safe graphics, and run code, might need to login.

```
startx
#or if that dont work
sudo /etc/init.d/gdm restart

```


Seeing your on OSS drivers install " Well not yet hopefuly soon " try latest stable kernel 2.6.33.2
The Ubuntu patched .32 is more problematic and less stable then the newer kernels. .34rc5 is very good also.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Sharky

---

### Post by crjackson on 2010-04-26
> **clhsharky said:**
> HI crjackson


Have you put all your settings back to original or where are you now?



Sorry I meant at startup choose shell, it might be recovery mode or something like that, instead of safe graphics.

After looking at your Xorg. logs it seems to be ignoring your xorg.conf file that points to radeon.

On desktop 'safe mode' right, check your xorg.conf file, heres mine, make sure radeon is there correctly. 
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"radeon"
        Option          "ColorTiling"           "on"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

Then pull up terminal and run

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

then recheck that radeon is still in xorg.conf
Restart into shell not safe graphics, and run

```
startx
#or if that dont work
sudo /etc/init.d/gdm restart

```


Seeing your on OSS drivers install " Well not yet hopefuly soon " try latest stable kernel 2.6.33.2
The Ubuntu patched .32 is more problematic and less stable then the newer kernels. .34rc5 is very good also.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Sharky

I'll have to get back at it tomorrow.  I got frustrated with it and pulled the tower. I replaced it with a much newer system I had sitting on the sidelines.  It needed to be tested with Lucid too.  It performed well.

I can't understand why Intrepid has no problems on this machine and anything newer does.

I even doubled the memory to see if it could have been that the older distro needed less memory and the newer distros needed more.  It made no difference.

I just don't get it. 

If I can't work it out, I'll install Intrepid.

---

### Post by NoVista on 2010-04-27
I can only say what I would do.
I hate to see you not being able to use the card.
This card has worked fine here since I first installed it on Ubuntu Edgy.
Obviously, it is not a hardware problem, as you have demonstrated.
I am currently running the xorg-edgers drivers, but let's get you back to square one first.

This card has worked on any version of Ubuntu I throw at it, (x800xtAIW, the 'xt' meaning an AGP card,
 and the AIW meaning "All In Wonder", since it is also a TV/Radio Tuner, which works here also).
In Lucid, I did nothing special.
No changing of grub, or adding lines to the boot string.
So, I would put all those things back to default.
My .xorg is at the end of this post, you should install it.
You have PCI-E, but our cards are identical, only the interface is different, mine being AGP.
You should remove the line:
Option "AGPMode" "4" option.

Go to your software sources list and remove
any references to xorg-edgers.
Reload the software sources and close it.

Open Synaptic, and remove anything listed under "Broken Packages".
If you have none the option will not appear.
Close Synaptic.

Open a terminal, and run this command:
sudo apt-get install libgl1-mesa-dri/lucid libgl1-mesa-dri-dbg/lucid libgl1-mesa-glx/lucid libgl1-mesa-glx-dbg/lucid libglu1-mesa/lucid mesa-utils/lucid

When finished, enter this command:
sudo apt-get autoclean
If you need to answer 'yes', do so.

Now run this command:
sudo apt-get autoremove:
If youi need to answer 'yes', do so.

Now open up synaptic once more and install:
gtkorphan

You will find it in System/Administration/Remove Orphaned Packages.
When it opens, remove all files listed under the "Orphaned packages' tab.
When that is done, click on "Options", located near the bottom, and tick the box that says:
"Show uninstalled packages with orphaned configuration files"
Keep on removing any files it finds. It may find more after you remove the first ones.

Now open up and run Update Manager.
Click the "Check" box, and install whatever it finds.

Now reboot.

===============================
Section "Device"
    Identifier    "Configured Video Device"
Option "RenderAccel" "on"
Option "AccelMethod" "XAA"
Option "AGPMode" "4"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
================================

---

### Post by crjackson on 2010-04-27
> **NoVista said:**
> I can only say what I would do.
I hate to see you not being able to use the card.
This card has worked fine here since I first installed it on Ubuntu Edgy.
Obviously, it is not a hardware problem, as you have demonstrated.
I am currently running the xorg-edgers drivers, but let's get you back to square one first.

This card has worked on any version of Ubuntu I throw at it, (x800xtAIW, the 'xt' meaning an AGP card,
 and the AIW meaning "All In Wonder", since it is also a TV/Radio Tuner, which works here also).
In Lucid, I did nothing special.
No changing of grub, or adding lines to the boot string.
So, I would put all those things back to default.
My .xorg is at the end of this post, you should install it.
You have PCI-E, but our cards are identical, only the interface is different, mine being AGP.
You should remove the line:
Option "AGPMode" "4" option.

Go to your software sources list and remove
any references to xorg-edgers.
Reload the software sources and close it.

Open Synaptic, and remove anything listed under "Broken Packages".
If you have none the option will not appear.
Close Synaptic.

Open a terminal, and run this command:
sudo apt-get install libgl1-mesa-dri/lucid libgl1-mesa-dri-dbg/lucid libgl1-mesa-glx/lucid libgl1-mesa-glx-dbg/lucid libglu1-mesa/lucid mesa-utils/lucid

When finished, enter this command:
sudo apt-get autoclean
If you need to answer 'yes', do so.

Now run this command:
sudo apt-get autoremove:
If youi need to answer 'yes', do so.

Now open up synaptic once more and install:
gtkorphan

You will find it in System/Administration/Remove Orphaned Packages.
When it opens, remove all files listed under the "Orphaned packages' tab.
When that is done, click on "Options", located near the bottom, and tick the box that says:
"Show uninstalled packages with orphaned configuration files"
Keep on removing any files it finds. It may find more after you remove the first ones.

Now open up and run Update Manager.
Click the "Check" box, and install whatever it finds.

Now reboot.

===============================
Section "Device"
    Identifier    "Configured Video Device"
Option "RenderAccel" "on"
Option "AccelMethod" "XAA"
Option "AGPMode" "4"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
================================

Thanks for your reply.  I'll give this a shot shortly and report the results.

---

### Post by crjackson on 2010-04-27
Okay, so this didn't work either but I have a junk theory about the problem.

I put the card in another identical box and guess what.  It did the same thing there with Karmic.  I also noticed that the GPU fan would not spin constantly on that machine as well.

Now here is my "Junk Theory".

The card is fairly heavy-duty. The eMachines box is fairly lightweight.  I checked the PSU and found it's only a 280w PSU. 

I think the PCIe isn't supplying the heavy card with enough power to get the job done once sophisticated graphics are piped in and more processing power is needed.

You see, the 2nd machine has much memory than the 1st. I suspect that the PSU is so marginal, that the memory in that machine gets so much of the power that the video card fan can't even spin up.

On the 1st machine, the video card spins up just fine but it has half the memory.

Next week when I have more time, I'll throw in one of my old PSU's (which I considered underpowered, but still 2 times more powerful than the stock eMachines PSU).

If that works, I'll have found a use for some of these spare PSU's laying around here.

Here's "Hummmmm" factor.  If the above proves to be true, why does Intrepid Ibex run so dandy?

---

### Post by clhsharky on 2010-04-27
crjackson

You may be on to something!

Sharky

---

### Post by crjackson on 2010-04-28
> **clhsharky said:**
> crjackson

You may be on to something!

Sharky

Seems like it was a JUNK theory.  I tried a 350w Antec.  No Dice!  Then a 550w Antec.  No Dice!  Then an 850w Corsair. No Dice! Then a 1KW Corsair still no Dice!

It's not power, but something about 8.10 compared to anything newer won't let me get to a desktop.  Wasn't there a big change in the xorg versions starting with 9.10?  Could that be it?

---

### Post by NoVista on 2010-04-28
The change from 8.10 that I remember was that I used ATI proprietary drivers. :) or :(, take your pick.

Going back to your debunking of the 'junk theory,' on my agp version, there is a separate power cord that plugs into the card. If it makes a poor contact, it will not work properly, but my bios usually will catch it before it continues a boot. (A spray of Deoxit fixed it).
Unsure if the pci-e versions have a separate power requirement too, as I don't have that style.
I am at a loss as to why it does not work for you.
Would be nice if someone with the PCI-E version would chime in,
especially since this forum is closing in a day.. ..

---

### Post by crjackson on 2010-04-28
> **NoVista said:**
> The change from 8.10 that I remember was that I used ATI proprietary drivers. :) or :(, take your pick.

Going back to your debunking of the 'junk theory,' on my agp version, there is a separate power cord that plugs into the card. If it makes a poor contact, it will not work properly, but my bios usually will catch it before it continues a boot. (A spray of Deoxit fixed it).
Unsure if the pci-e versions have a separate power requirement too, as I don't have that style.
I am at a loss as to why it does not work for you.
Would be nice if someone with the PCI-E version would chime in,
especially since this forum is closing in a day.. ..

Prolly not many users out there still using this card.  I too have used it with most versions of Ubuntu on a different system.  It was removed and replaced when during 8.04.

I have 2 identical systems (except for memory upgrade, and believe it or not an X300 video card upgrade). This is the lesser of the 2 systems and I wanted to give it a little life.

I'm about to buy another crappy X300 video card and give up on the X800 card.  The X800 card wouldn't work in the other system either.

I'm starting to think a bios upgrade (which isn't available) would be needed, or perhaps the PCIe slot on this board just isn't compatible with some PCIe cards.

Oh, there is no extra power connector on the PCIe version of the X800 card.

---

### Post by crjackson on 2010-04-28
Is there a utility or a commandline instruction that will report how much video memory a particular card has on it?

---

### Post by clhsharky on 2010-04-28
HI crjackson

In your log at
Xorg.O.Log 
line
41] (--) PCI:*(0:1:0:0) 1002:71cd:174b:0840 ATI Technologies Inc rev 0, Mem  
 I/O @ 0x0000d000/256

that what mine reports see what yours reports, and what does your BIOS say?

Sharky

HardInfo in repos can show video card memory. Shows up in applications/system tools/system profiler and benchmark.

---

### Post by ljrmorgan on 2010-04-28
> **NoVista said:**
> Would be nice if someone with the PCI-E version would chime in,
especially since this forum is closing in a day.. ..
As I said before, I have this card (256MB PCIe), working perfectly with the open source drivers that ship with Lucid. I'm happy to post any configs or anything - just let me know what you want!

---

### Post by crjackson on 2010-04-28
> **ljrmorgan said:**
> As I said before, I have this card (256MB PCIe), working perfectly with the open source drivers that ship with Lucid. I'm happy to post any configs or anything - just let me know what you want!

Thanks.  I'm thinking now there is a compatibility problem between the mainboard's PCIe capabilities and some PCIe video cards.

I just purchased a X300SE 128MB card from eBay to put in this machine.  It's the same card I have working in it's sister machine so hopefully it'll work out.

It disappoints me that I have a perfectly fine X800 XL, and an nVidia 7900 GTO that won't work on that machine when running Junty/Karmic/Lucid.

I find it so damned strange that Intrepid runs fine with those cards in the vary same machine.  I just don't get it!!!

---

### Post by crjackson on 2010-04-28
> **clhsharky said:**
> HI crjackson

In your log at
Xorg.O.Log 
line
41] (--) PCI:*(0:1:0:0) 1002:71cd:174b:0840 ATI Technologies Inc rev 0, Mem  
 I/O @ 0x0000d000/256

that what mine reports see what yours reports, and what does your BIOS say?

Sharky

HardInfo in repos can show video card memory. Shows up in applications/system tools/system profiler and benchmark.

Okay, I'll check this out tomorrow.  The kids are doing homework on the machine right now.

---

