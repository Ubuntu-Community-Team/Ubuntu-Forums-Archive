---
title: "ATI no graphical display"
date: 2011-11-19
forum: Installation &amp; Upgrades
---

### Post by Maintech on 2011-11-19
Ok. I have waited many weeks for a resolution to the issue with AMD/ATI APU graphics. I have tried 'nomodeset', 'radeon mode=0', and 'radeon mode=1' with no video after booting from live disk. I have tried vesa mode, and 'mode=771'. I have tried combinations. I am running Ubuntu 11.04 now on the computer with the AMD/ATI APU graphics and making this post with it. No issues. What has been broken in all flavors of linux to cause the graphics display to no longer work??? No version of linux (new versions) will work anymore. Not Fedora, not SuSE, not Ubuntu, NOTHING......with the new kernels. My computer is a HP Pavilion dv6z quad-core APU with the built-in APU graphics adaptor from ATI. Only the **OLD** versions of linux will work with it. Will I have to give up using linux on it or use only MS???? I have been a long time user of linux and it is my preferred OS but I like to keep it current. I can continue to use 11.04 for a time but eventually there will be no support for it. Then what?  :confused:

---

### Post by efflandt on 2011-11-19
Do you know what specific video card or chip it has?  Or what does **sudo lspci -v** say about your video on a system that is working?

My old (circa 2004) single core early Athlon64 3200+ (2 GHz) 2 GB with legacy ATI X1300 boots 64-bit 11.10 without issues from install iso on USB.  The video card is somewhat newer than the computer, but from before AMD bought ATI.  Video is not fast enough for modern gaming, but appears to run Unity fine (and Firefox, etc.) with default drivers.

PS: I forget which Ubuntu version(s) I had to use "nomodeset" or "radeon mode=0" (when kms was first implemented), but currently I do NOT have to use any boot parameters.

---

### Post by Maintech on 2011-11-19
> **efflandt said:**
> Do you know what specific video card or chip it has?  Or what does **sudo lspci -v** say about your video on a system that is working?

My old (circa 2004) single core early Athlon64 3200+ (2 GHz) 2 GB with legacy ATI X1300 boots 64-bit 11.10 without issues from install iso on USB.  The video card is somewhat newer than the computer, but from before AMD bought ATI.  Video is not fast enough for modern gaming, but appears to run Unity fine (and Firefox, etc.) with default drivers.

PS: I forget which Ubuntu version(s) I had to use "nomodeset" or "radeon mode=0" (when kms was first implemented), but currently I do NOT have to use any boot parameters.



VGA compatible controller: ATI Technologies Inc Device 9641 (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Device 358b
	Flags: bus master, fast devsel, latency 0, IRQ 53
	Memory at e0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 3000 [size=256]
	Memory at f0300000 (32-bit, non-prefetchable) [size=256K]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx

---

### Post by MAFoElffen on 2011-11-19
> **Maintech said:**
> Ok. I have waited many weeks for a resolution to the issue with AMD/ATI APU graphics. I have tried 'nomodeset', '[COLOR=Red]radeon mode=0[/COLOR]', and '[COLOR=Red]radeon mode=1[/COLOR]' with no video after booting from live disk. I have tried vesa mode, and '[COLOR=Red]mode=771[/COLOR]'. I have tried combinations. I am running Ubuntu 11.04 now on the computer with the AMD/ATI APU graphics and making this post with it. No issues. What has been broken in all flavors of linux to cause the graphics display to no longer work??? No version of linux (new versions) will work anymore. Not Fedora, not SuSE, not Ubuntu, NOTHING......with the new kernels. My computer is a HP Pavilion dv6z quad-core APU with the built-in APU graphics adaptor from ATI. Only the **OLD** versions of linux will work with it. Will I have to give up using linux on it or use only MS???? I have been a long time user of linux and it is my preferred OS but I like to keep it current. I can continue to use 11.04 for a time but eventually there will be no support for it. Then what?  :confused:
Both of you had typo's in the KMS kernel boot mode switch? I understand if it was just in the post, but it really is as
```

radeon.mode=0

```Notice the period between radeon and mode? If you have that space there (instead), the kernel treats it as separate parameters. Next was mode=771... I believe you meant vga=xxx, where xxx is the VESA mode your card supports.

Next time please try "radeon.modeset=0 vga=791"... What using both of them together should do is turn KMS off and put the card into a VESA 1024x768x16 bit. That is fairly basic graphics for all the install disks.

Try it like this:
- Boot the ISO. 

- _T_he first Screen is the black screen with the person/keyboard screen > Press Escape.

- This will get you to a low-res language selection screen > Press Escape.

- This will get you to the Advanced Installation Menu 

- Press F6... it will bring up a dropdown boot option menu.  Press escape.

- That will close the dropdown, but now an editable boot line will be   displayed at the bottom of that screen. It you Arrow left a few times,   the cursor will diplay.  Move it to after the "--".

- Add the text "radeon.modeset=0 vga=791"

- Chose the try button.

* If that still doesn't work, then I reboot and get back to the Advanced menu... then

- Press Escape at the Advanced Menu Screen.

-  This will prompt a Message Box saying "Exiting- You are leaving the   graphical boot menu. You are starting the text mode interface."

- It should start a hardware probe to your video hardware to try to identify the graphics supported.  On some really older GPU chips, it will display a text message error   saying it couldn't "ID the mode: XXX", it then blinks, then displays a text menu   asking for a display mode type... I think I usually use VGA 640x480x16,   which I think I remember as menu item "7"...

- That starts the installer in a text mode.  I go through the install... After the reboot, it seems to work just fine.

*** Note- Sometimes the above, at the video probe, will dump you down to   a  text prompt saying "boot:"  Press enter and it will bring you back   to the Advanced Install Menu...

 At this point I change tactics.  Then I   use the Ubuntu Alternate Install ISO or the "Minimum" Install ISO. Which are text based installers.   On the Mini, when it gets to the Taskel Software Install screen, you have to select a desktop manager or you end up with a fragmented install. 

Your card is supported by the xserver.xorg.video.ati driver... although we all know we sometimes have to do things to get things right.

---

### Post by Maintech on 2011-11-19
> Next time please try "radeon.modeset=0 vga=791"... What using both of them together should do is turn KMS off and put the card into a VESA 1024x768x16 bit. That is fairly basic graphics for all the install disks.

I tried all of that. If you look at my first post the 'graphic card' is in the CPU and they are called APU. This is a new laptop from HP. When booting using the above suggestion it will eventually enter text mode. If you tell it to startx it will try then give reasons why it doesn't work. I can't do that with 'nomodeset' turned off because the screen is black and there is no text. With the 'nomodeset' turned on (KMS off) I get this error:

> Failed to load fglrx (module does not exist)
[KMS] drm report nomodesetting isn't supported
Radeon (0) Chipset "SUMO" (ChipID=0x9641) requires KMS
Screen found but none have a usable configuration

---

### Post by MAFoElffen on 2011-11-19
> **Maintech said:**
> I tried all of that. If you look at my first post the 'graphic card' is in the CPU and they are called APU. This is a new laptop from HP. When booting using the above suggestion it will eventually enter text mode. If you tell it to startx it will try then give reasons why it doesn't work. I can't do that with 'nomodeset' turned off because the screen is black and there is no text. With the 'nomodeset' turned on (KMS off) I get this error:
Ouch!  In the CPU? ...I don't have any experience with those yet.

Can you install with the Alternate Install CD, then install your drivers?  If it did get through the install, then you could get to a TTY Text console to install the driver that supports your APU? (reaching now...)

Let me do some digging for you...

---

### Post by darkod on 2011-11-19
And what APU/CPU model do you have? I guess it's the A series but it might be E too.

---

### Post by darkod on 2011-11-19
> **MAFoElffen said:**
> Ouch!  In the CPU? ...I don't have any experience with those yet.

Can you install with the Alternate Install CD, then install your drivers?  If it did get through the install, then you could get to a TTY Text console to install the driver that supports your APU? (reaching now...)

Let me do some digging for you...

It's the new AMD CPUs which are now called APUs and include the video INSIDE them. Earlier board with integrated graphics had it in the NB I believe. Now it's in the CPU.

The A series comes with Radeon 6550 or 6530, or similar depending on the exact model (that is for desktop, laptop is different). As soon as the OP gives the model of the CPU, we have the model of the video too. Not sure if the AMD/ATI driver for linux supports them yet though.

---

### Post by darkod on 2011-11-19
You must be joking, the AMD website has maintenance right now. :)
I wanted to check what ATI models are supported from that line.

---

### Post by Maintech on 2011-11-19
> **darkod said:**
> And what APU/CPU model do you have? I guess it's the A series but it might be E too.

AMD A8-3510MX APU with Radeon HD Graphics.

---

### Post by darkod on 2011-11-19
> **Maintech said:**
> AMD A8-3510MX APU with Radeon HD Graphics.

OK, according to Wikipedia the graphics inside is HD 6620G.

If only the AMD website comes back online to check driver support.

Another question: Can you boot the recovery mode entry from the grub menu? That should give you text mode system and possibly you can add the latest ATI driver, if this chip is hopefully supported.

---

### Post by Maintech on 2011-11-19
> **darkod said:**
> OK, according to Wikipedia the graphics inside is HD 6620G.

If only the AMD website comes back online to check driver support.

Another question: Can you boot the recovery mode entry from the grub menu? That should give you text mode system and possibly you can add the latest ATI driver, if this chip is hopefully supported.

I have not yet installed it. I will not install it until I am certain I can have a GUI. My days of text only is over. If no distribution of linux will allow an installation that completes with a GUI and without me having to spend hours over a terminal in text mode editing conf files and running commands to get a GUI then I guess my days of using linux is over. Ease of installation has been a great linux selling point. There have been a few little quirks over the years but nothing really major. Linux is still my favorite OS and as you can see I am using it right now. Someone 'broke' something (the kernel I think) since 11.04 works fine with no issues and 11.10 will not work at all.

---

### Post by collisionystm on 2011-11-19
> **Maintech said:**
> Ok. I have waited many weeks for a resolution to the issue with AMD/ATI APU graphics. I have tried 'nomodeset', 'radeon mode=0', and 'radeon mode=1' with no video after booting from live disk. I have tried vesa mode, and 'mode=771'. I have tried combinations. I am running Ubuntu 11.04 now on the computer with the AMD/ATI APU graphics and making this post with it. No issues. What has been broken in all flavors of linux to cause the graphics display to no longer work??? No version of linux (new versions) will work anymore. Not Fedora, not SuSE, not Ubuntu, NOTHING......with the new kernels. My computer is a HP Pavilion dv6z quad-core APU with the built-in APU graphics adaptor from ATI. Only the **OLD** versions of linux will work with it. Will I have to give up using linux on it or use only MS???? I have been a long time user of linux and it is my preferred OS but I like to keep it current. I can continue to use 11.04 for a time but eventually there will be no support for it. Then what?  :confused:

Boot with no mode set 
At command line login
Sudo apt-get remove xserver-xorg-video-radeon 
Sudo service lightdm start

---

### Post by collisionystm on 2011-11-19
(did previous post from my phone! Revising... )

I have a 6380G. I was frustrated to. 

Boot live CD.

Boot the system with nomodeset
At command line login
sudo apt-get remove xserver-xorg-video-radeon 
 sudo service lightdm --full-restart

You should now have the GUI. You can install.

Once installed, do the same thing. Download the latest Linux Catalyst drive which is 11.11. Install it.
Open a terminal
sudo aticonfig --initial -f 

reboot

You should be up and working.


OR if you choose not to install

Install the catalyst driver during your live session and instead of reboot just log out and back in

It is the version of Xorg that is shipping that is broken.
Apparently Suse 12.1 is using a different version than the others, however I have not tried it.

---

### Post by MAFoElffen on 2011-11-19
> **darkod said:**
> It's the new AMD CPUs which are now called APUs and include the video INSIDE them. Earlier board with integrated graphics had it in the NB I believe. Now it's in the CPU.

The A series comes with Radeon 6550 or 6530, or similar depending on the exact model (that is for desktop, laptop is different). As soon as the OP gives the model of the CPU, we have the model of the video too. Not sure if the AMD/ATI driver for linux supports them yet though.
Yes and lspci reports the OP's as an ATI 9641... I couldn't find info on an AMD w/ that as APU. 

I'm not sure on the recent linux support on APU's either. I also see the same on Fedora, Mint, etc.  I also see the OP has a dupe post "here" in Hardware and Laptops. 

This has been the 3rd person in a week asking here with an APU. But the 2 previous were E series and were supported by Catalyst (flgrx).  I see him using fglrx, but with his APU(?), I'm out of my experience on this.  I am really curious about this though.

---

### Post by darkod on 2011-11-20
Well, I can't try it but the website of AMD seems to have a driver that supports the A8-35xxM/MX APUs. It supports 32bit and 64bit versions of the driver.

The only problem might be if you need to add it manually.

---

### Post by Tuvoc on 2011-11-20
> **Maintech said:**
> Ok. I have waited many weeks for a resolution to the issue with AMD/ATI APU graphics. I have tried 'nomodeset', 'radeon mode=0', and 'radeon mode=1' with no video after booting from live disk. I have tried vesa mode, and 'mode=771'. I have tried combinations. I am running Ubuntu 11.04 now on the computer with the AMD/ATI APU graphics and making this post with it. No issues. What has been broken in all flavors of linux to cause the graphics display to no longer work??? No version of linux (new versions) will work anymore. Not Fedora, not SuSE, not Ubuntu, NOTHING......with the new kernels. My computer is a HP Pavilion dv6z quad-core APU with the built-in APU graphics adaptor from ATI. Only the **OLD** versions of linux will work with it. Will I have to give up using linux on it or use only MS???? I have been a long time user of linux and it is my preferred OS but I like to keep it current. I can continue to use 11.04 for a time but eventually there will be no support for it. Then what?  :confused:

I have the same issue but with a 2 year old ATI 3870. Ubuntu 8.10 and prior is fine. No modern distribution - and I've tried most of them - will run a LIVECD or even start the install process. Either a blank screen or graphical garbage. Of course it runs Windows perfectly. Dropped an ATI 5450 into the machine and now everything works fine. The 3870 is in another machine, and I get all the same issue now with that other machine. Windows fine, Linux is no-go. I want to replace the 3870 with a 6850, but now I see people having the same issue with that. What is it with Linux and ATI ?? Anyway, the solution to your problem is likely to be the same for me

---

### Post by darkod on 2011-11-20
@Tuvoc

It seems to me there were plenty of boot parameters suggested here to try. If that allows you to boot, you just need to add the ATI driver. I guess the driver should support 3870, you can check that in advance on the AMD website.

Did you ever try that?

---

### Post by Tuvoc on 2011-11-20
Yes I tried those boot options. As for the ati driver - how can I install an ATI driver if I can't even get the O/S installed ?

The Linux community need to solve these sorts of issues. How can you expect the average consumer to adopt Linux with issues like this ? Ordinary popular hardware that Linux just won't run with. Windows walks all over Linux in terms of hardware compatibility and driver support. If you are lucky enough to have supported hardware - and my other machines do - then great, otherwise tough

---

### Post by darkod on 2011-11-20
That depends whether some of the parameters worked or no. If a parameter worked, you can install and use the same parameter on first boot.
Another option is to install with the alternate cd, not the standard desktop cd. It has a text installer not GUI, but you end up with the same desktop system.

As for the hardware compatibility, that's the card MS is playing I guess. All manufacturers are pushed developing drivers well in advance, so it looks like windows is compatible with everything. Linux drivers on the other hand were left very much for the community to develop. It's a good thing that lately it seems manufacturers pay more attention to develop linux drivers too.

And even the compatibility doesn't help windows work more efficiently, not to crash, etc, right?

At the end of the day, use what ever is best for you. I strongly believe that you do need some basic understanding and a will to learn in order to install any OS. I don't believe in idiot-proof OS install. You need to learn and make an effort.

I remember a time when you couldn't install XP on a sata disk because it didn't have drivers by default. While linux could. So how did the XP install look like compared to linux then, easier or more complicated?

---

### Post by Tuvoc on 2011-11-20
I see one boot parameter there I haven't tried. I'll try that in a couple of days when my system becomes free to reboot. 

I'm no stranger to tinkering with an O/S, my old OS/2 Warp days were a lot of fun. But even that would always install. I disagree that an install should not be idiot-proof. That is exactly what they need to be for the consumer. In the server room a different story, but ironically Ubuntu server without a GUI is the one that would actually install perfectly.

I'll watch this thread for any solutions, and report back anything I find myself.

---

### Post by darkod on 2011-11-20
It looks like the server installs fine because it doesn't have any graphics. Likewise, as I said, the alternate install should work fine, and on first boot maybe try to enter in the recovery mode option, not the standard boot option.
That should also load text mode.
Have the ATI driver on a stick prepared in advance.
And just install it (yeah it sound easier said than done) :)

---

### Post by MAFoElffen on 2011-11-20
> **Tuvoc said:**
> Yes I tried those boot options. As for the ati driver - how can I install an ATI driver if I can't even get the O/S installed ?

The Linux community need to solve these sorts of issues. How can you expect the average consumer to adopt Linux with issues like this ? Ordinary popular hardware that Linux just won't run with. Windows walks all over Linux in terms of hardware compatibility and driver support. If you are lucky enough to have supported hardware - and my other machines do - then great, otherwise tough
There are things to try to get around this... I think darkod will agreed. I have to do these every once in awhile for some... If the boot options don't work--

Like I mentioned in Post #4: 
- You could try to get into the Text Mode Interface of the installer of the LiveCD...
- You could try to Install from  the Alternate Install CD...
- You could try to install from the Minimal CD and select the Ubuntu desktop...
- You could try to install from the Server CD and afterwards cli install ubuntu-desktop

Preferred you try in that order-- If any of them installed, then you could install the driver that supported it.

Another way, is to install an earlier version, install the driver, then either do incremental release upgrade (if really old version) or do-release-upgrade to current.

For some, that's an hour of ideas...  Even if you just install a Command Line sys (Minimal CD), at least you have something to work from / to build on.  If the Linux CLI has problems, because current also uses vga graphics, then theres going to be problems with Xorg, as it run above that layer.

EDIT-- Even the other-than-LiveCD  install options (even server) may need boot options... Example- Server changed to VGA graphics over straight text for server "theming"...

---

### Post by Maintech on 2011-11-20
> **collisionystm said:**
> (did previous post from my phone! Revising... )

I have a 6380G. I was frustrated to. 

Boot live CD.

Boot the system with nomodeset
At command line login
sudo apt-get remove xserver-xorg-video-radeon 
 sudo service lightdm --full-restart

You should now have the GUI. You can install.

Once installed, do the same thing. Download the latest Linux Catalyst drive which is 11.11. Install it.
Open a terminal
sudo aticonfig --initial -f 

reboot

You should be up and working.


OR if you choose not to install

Install the catalyst driver during your live session and instead of reboot just log out and back in

It is the version of Xorg that is shipping that is broken.
Apparently Suse 12.1 is using a different version than the others, however I have not tried it.

I followed your advice to the letter. Now my entire xorg for the radeon is gone from my installed 11.04 and the computer will no longer boot. By the way, there was no 'lightdm' on the CD. Well, now I am in a pickle. I have a laptop that no longer works and the latest versions will not install. GREAT!!  :-x

The previous post was because I used Lubuntu instead of Ubuntu because I had intended to install Lubuntu due to my extreme dislike of Unity. However, there was no way to get a GUI with the Lubuntu. I put in a regular Ubuntu disk and followed the instructions and I now have a GUI. Now I have to decide if I really want to install the Ubuntu with Unity or go find my old 11.04 disk and just re-install and keep my Gnome GUI.

---

### Post by MAFoElffen on 2011-11-20
> **Maintech said:**
> I followed your advice to the letter. Now my entire xorg for the radeon is gone from my installed 11.04 and the computer will no longer boot. By the way, there was no 'lightdm' on the CD. Well, now I am in a pickle. I have a laptop that no longer works and the latest versions will not install. GREAT!!  :-x
Just saw that... That was a bad idea... Now even if you had a backup xorg.conf, if it pointed to that radeon driver... Wait a minute, what did you say?  I'll get back to that later. Lets get you back up first.

Follow these instructions to boot your installed sys into a Command Line TTY console:
**[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1][[B]Temporalrily Booting Into a TTY Text Console**]("http://ubuntuforums.org/showpost.php?p=11383888&postcount=715")[/SIZE][/COLOR][/SIZE][/COLOR][/B]

Once you get logged in
```

sudo apt-get install xserver-xorg-video-radeon 

```If you continued to follow his instruction maybe while you're still in a cli you should do one of these two to get your driver straightened out:
[[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1][/SIZE][/COLOR][/SIZE][/COLOR]]("http://ubuntuforums.org/showpost.php?p=10950714&postcount=334")[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1][**Installing ATI Packaged Drivers**]("http://ubuntuforums.org/showpost.php?p=11467052&postcount=798")
[/SIZE][/COLOR][/SIZE][/COLOR][COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Installing ATI Binary Drivers]("http://ubuntuforums.org/showpost.php?p=10950714&postcount=334")** 
[/SIZE][/COLOR][/SIZE][/COLOR]
I saw you had flgrx before in earlier posts, so either should work right?  If you were using the opensourced radeon, pointed by a custom xorg.conf (or not), then when you executed the script, it made a backup of the old xorg.conf file.
```

ls /etc/X11/xorg.conf*

```You may see an xorg.conf.backup or some xorg.conf.dist-upgrade.[date_of_release_upgrade] files... copy with one you think was most right for you. Example:
```

sudo cp xorg.conf.backup xorg.conf

```
EDIT-- yes, lightdm started w/ 11.10. 11.04 is GDM.

---

### Post by Maintech on 2011-11-20
Well, after hours of trying to follow the instructions and get 11.10 ubuntu to run on my computer I ended up having to do a re-install of 11.04. I lost everything I had on it originally. This is why I dislike trying to install a system that won't run correctly from a live disk. I take full responsibility for my loss of data as I should have made a backup before starting anything. So, now I have a **_LOT_** of work to do getting the computer programs that I had to hunt down and install back on the computer. There is nothing I can do now for the data loss. And, I am back to 'square one' in that none of the 'new' linux OS of any flavor will run on my computer with a GUI. I guess I will have to continue to hunt for live CD's from different groups until maybe I find one that will run on my computer. For now, I am stuck with Ubuntu 11.04 (until it comes to the end of the support cycle). :(

---

### Post by Maintech on 2011-11-22
FYI:  Mint Debian base will boot live mode on this computer with no issues. In fact, it runs great and seems to have all the correct display drivers because it runs Gnome 3 with all the acceleration enabled. I tried Mint Ubuntu base and it is the same as Ubuntu in that I do not have a display after the initial boot screen. Kinda strange that Debian, which is the Ubuntu base, will correctly identify my video/display while Ubuntu and all it's derivatives will not (applies only to 11.10 release). And the Mint Gnome 3 is arranged in such a way that those who dislike Unity can feel comfortable because it is configured similar to Gnome 2. Since I have been using Ubuntu since 2006 I hope these issues are quickly resolved. I used Mandrake (Mandriva) prior to Ubuntu but had to permanently change linux distributions because of changes made to the OS which caused me issues. I hope Ubuntu is not following the same path.

---

