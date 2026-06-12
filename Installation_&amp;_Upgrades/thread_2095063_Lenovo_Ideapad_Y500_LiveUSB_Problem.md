---
title: "Lenovo Ideapad Y500 LiveUSB Problem"
date: 2012-12-15
forum: Installation &amp; Upgrades
---

### Post by haspelbein on 2012-12-15
I am trying to use the Ubuntu 12.10 Secure Remix to install Ubuntu on a Lenovo Ideapad Y500. My goal was to install a dual boot option alongside Windows 8. This was my first attempt at installing Ubuntu in a UEFI configuration.

After creating the bootable USB stick, I disabled the Secure Boot option in the BIOS.

I was able to boot from the USB stick and got the GRUB menu. Both the installation and boot w/o installation options resulted in a blank screen.

During the next boot attempt I used the "e" option to edit the kernel boot parameters.

Removing "quiet splash" and adding "text" I hoped to see text command line interface. Instead it seemed that the text output was compressed in the top 1/6th of the screen, rendering it unreadable. 

Unfortunately, without a command line interface I don't have many options. Anybody had similar results on a Lenovo Ideapad Y500?

---

### Post by y400 on 2012-12-15
I just recently set up Arch Linux in dual boot with Windows 8 on my y400 and installed using a CD.

Being squeezed up in the top portion of the screen seemed to happen when I would choose to boot from the CD from the menu instead of automatically on reboot after moving the optical drive to the top of the boot order list in the BIOS.

As for boot parameters, I had to add nomodeset or else the screen would freeze, although it would still boot up.

---

### Post by haspelbein on 2012-12-16
> **y400 said:**
> I just recently set up Arch Linux in dual boot with Windows 8 on my y400 and installed using a CD.

Being squeezed up in the top portion of the screen seemed to happen when I would choose to boot from the CD from the menu instead of automatically on reboot after moving the optical drive to the top of the boot order list in the BIOS.

As for boot parameters, I had to add nomodeset or else the screen would freeze, although it would still boot up.

Thanks a lot for the feedback. Changing the boot order in the BIOS setup instead of the boot menu indeed restored the text mode. I don't think I would have made that connection, thank you.

At least I can not experiment with display modes and try my luck. Did you have to through this or did the LiveCD / Live USB work for you right away?

Additional info: When running the "nomodeset" kernel parameter the following error will appear:

Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.

I am still researching, but not sure where to go from here, atm.

---

### Post by y400 on 2012-12-16
With my Arch Linux install, it doesn't use a GUI and couldn't get X going until I installed the nvidia drivers. These laptops don't have Optimus so they only use the Nvidia GPU and don't access the integrated intel graphics. I'm thinking that would explain why you can get into Ubuntu's text mode but not to the GUI.

You could try the boot parameter acpi=off but I'm thinking you'll probably have to do a non-GUI install.

---

### Post by haspelbein on 2012-12-17
> **y400 said:**
> With my Arch Linux install, it doesn't use a GUI and couldn't get X going until I installed the nvidia drivers. These laptops don't have Optimus so they only use the Nvidia GPU and don't access the integrated intel graphics. I'm thinking that would explain why you can get into Ubuntu's text mode but not to the GUI.

You could try the boot parameter acpi=off but I'm thinking you'll probably have to do a non-GUI install.

Yes, you may be right. I know that the Intel HD4000 is present, but it is not even visible as an option in the BIOS. So you are right, they are using the Nvidia by default. I think the problem is not so much that the Nvidia card is present, but that the Ubuntu install detects both GPUs. (I've been able to successfully install Ubuntu on Nvidia-only laptops in the past.)

I haven't tried ArchLinux before, but I know that it is more of an expert Linux system. Yet the way things are, I may have to read up on text-based installs, as I don't see a work-around either.

I will give acpi=off a try though, as one last effort. ;)

Thanks a lot for your feedback.

---

### Post by oldfred on 2012-12-17
Some now older info on switchable graphics:
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)

       Optimus
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
12.10 with bumblebee
[http://ubuntuforums.org/showthread.php?t=2077451](http://ubuntuforums.org/showthread.php?t=2077451)
NVIDIA Confirms It's Working On Optimus Linux Support - Aug 31, 2012
[http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY](http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY)

---

### Post by y400 on 2012-12-17
While the i7 does have the integrated intel graphics, it is disabled/bypassed on my y400 at least. I can only see the discrete Nvidia GT650M through lspci. I know there has been confusion about whether these laptops have Optimus or not and from what I can tell, there is no way to use or access the intel gpu.

I'm not sure what options there are for installing Ubuntu outside of the GUI so I can't help you there.  I hope this isn't frowned upon and feel free to mod edit if so, but if Ubuntu isn't feasible under this situation, here's the Arch beginners' guide:
[https://wiki.archlinux.org/index.php/Beginners'_Guide](https://wiki.archlinux.org/index.php/Beginners'_Guide)

---

### Post by oldfred on 2012-12-17
I link to Arch regularly, but it is more technical.

I have a nVidia discrete card, but have to use nomodeset to install and on first boot until I get proprietary driver installed. And with 12.10 I could not get driver installed until I installer kernel header first.

       [http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)
            Fix for nVidia with 12.10 missing kernel dpkg reconfigure:
[http://ubuntuforums.org/showthread.php?t=2072862](http://ubuntuforums.org/showthread.php?t=2072862)

    
       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by haspelbein on 2012-12-18
> **y400 said:**
> While the i7 does have the integrated intel graphics, it is disabled/bypassed on my y400 at least. I can only see the discrete Nvidia GT650M through lspci. I know there has been confusion about whether these laptops have Optimus or not and from what I can tell, there is no way to use or access the intel gpu.

I'm not sure what options there are for installing Ubuntu outside of the GUI so I can't help you there.  I hope this isn't frowned upon and feel free to mod edit if so, but if Ubuntu isn't feasible under this situation, here's the Arch beginners' guide:
[https://wiki.archlinux.org/index.php/Beginners'_Guide](https://wiki.archlinux.org/index.php/Beginners'_Guide)

Thanks a lot for the guide, I will look into it. And yes, I only see my NVidia card with this laptop. It does not appear to be an Optimus configuration. But somehow this configuration confuses Ubuntu upon install.

---

### Post by haspelbein on 2012-12-18
I'm getting a little closer. acpi=off got around the boot process hanging on the dual cards, however since I booted from a USB stick it turned off the USB port it was booting from, and was not able to mount the partitions to continue the installation.

I have yet to get the Ubuntu 12.10 to boot on this particular machine. (It boots just fine on others, and my disk imaging CD boots on the Y500.)

At this rate, I may eventually give ArchLinux a try.

@oldfred
Thanks a lot for your reference. Unfortunately I'm not far along enough in the install process to give them a try.

---

### Post by gabriele.lanaro on 2012-12-21
I'm having the same problem on my Y500. I'm going to try booting Ubuntu liveusb in text mode (nomodeset) and from there installing nvidia drivers and proceeding with installation. Do you think this would work? Has anybody tried that?

---

### Post by stevejluke on 2012-12-21
I had a similar problem booting from a LiveUSB and the USB losing power on my Sony Vaio.  It ended up being a combination of things:

1) The first USB drive I used seemed slow, and was prone to lose power on all USB ports.  This same drive worked on other computers, I believe it was specific to UEFI not liking it.

2) After switching to a different USB (Staples Relay), I found that one of the laptop's USB ports worked, and the other did not.

So my suggestion would be try using a different brand of USB drive, and try different ports to see if you have better luck.

---

### Post by gabriele.lanaro on 2012-12-21
I found a way to boot ubuntu with graphics.

1)in the BIOS at the boot section change UEFI to Legacy, and select the options that says to boot Legacy first.
2) It will automatically boot from the pendrive (I've used unetbootin) and it will be OK with graphics and all.
3) In this way you will have problems to boot into windows, simply turn on the computer while pressing F12 (it will make a lot of beeps but it's OK) and select windows. Or simply setup in the BIOS to boot UEFI first...

BTW Fedora 16 boots in graphics mode, even though both ethernet and wireless card don't work!

---

### Post by y400 on 2012-12-22
The Atheros AR8161 needs the alx driver from compat-wireless. This post may help: [http://ubuntuforums.org/showpost.php?p=12372946&postcount=2](http://ubuntuforums.org/showpost.php?p=12372946&postcount=2)

In my Arch install I didn't have problems with the wireless connection so I didn't get the alx driver going for the ethernet card until later.

Edit: glad to hear you found a way to get it booting up properly.

---

### Post by gabriele.lanaro on 2012-12-22
> **y400 said:**
> The Atheros AR8161 needs the alx driver from compat-wireless. This post may help: [http://ubuntuforums.org/showpost.php?p=12372946&postcount=2](http://ubuntuforums.org/showpost.php?p=12372946&postcount=2)

In my Arch install I didn't have problems with the wireless connection so I didn't get the alx driver going for the ethernet card until later.

Edit: glad to hear you found a way to get it booting up properly.

Thank you for your explanation! Can you suggest me a good partition setup? I'm a bit worried about deleting/shrinking some important partition and mess up the windows 8 installation (I'm going to keep this for games). Do you think it's OK to shrink the windows 8 partition?

---

### Post by oldfred on 2012-12-22
Use Windows to shrink the Windows partition and reboot a couple of times to let Windows run chkdsk and make whatever fixes it wants for its new size.

Then backup efi & Windows partitions.

       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

    Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

The installer will use your existing efi partition and you do not need the bios_grub.  With Windows 8 you just about have to have the shared NTFS data partition and set Windows 8 partition as read only in Ubuntu.
       
For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
If gpt(not MBR) partitioning include these two first - all partitions with gpt are primary
    250 MB efi FAT32  (for UEFI boot or future use for UEFI)
    1 MB bios_grub  no format (for BIOS boot)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by Y500user on 2012-12-28
> **haspelbein said:**
> I am trying to use the Ubuntu 12.10 Secure Remix to install Ubuntu on a Lenovo Ideapad Y500. My goal was to install a dual boot option alongside Windows 8. This was my first attempt at installing Ubuntu in a UEFI configuration.

After creating the bootable USB stick, I disabled the Secure Boot option in the BIOS.

I was able to boot from the USB stick and got the GRUB menu. Both the installation and boot w/o installation options resulted in a blank screen.

During the next boot attempt I used the "e" option to edit the kernel boot parameters.

Removing "quiet splash" and adding "text" I hoped to see text command line interface. Instead it seemed that the text output was compressed in the top 1/6th of the screen, rendering it unreadable. 

Unfortunately, without a command line interface I don't have many options. Anybody had similar results on a Lenovo Ideapad Y500?
I have been able to successfully dual boot with Ubuntu 12.1 and Win 8. I had the blank screen issue that you mentioned when trying to install/boot from a liveUSB but getting into the BIOS and modifying the bios to have "Legacy Support" instead of UEFI  did the trick. With that change, I was able to gui install from the USB. However, GRUB was not loading the correct UEFI bootloader for win 8 but was able to boot ubuntu OK. Installing and running the boot-repair tool with the default settings resolved the issue.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Installing the nVidia drivers (which had dependencies on linux-generic..sigh) was the next step. I'm yet to be able to control backlight or use the webcam but hope to get there...

---

### Post by peterpm on 2012-12-29
One important issue in 12.10 Xubuntu (also in 12.10 Ubuntu?): could not control brightness, probably another problem of the nouveau driver. I installed the nvidia driver and it gives me the nvidia-settings to control brightess.

Y400, see below, is right. I assumed this was brightness control. I  installed nvidiabl and now can control brightness with my Y500 Fn keys!   See also:

[http://askubuntu.com/questions/150601/why-nvidiabl-module-is-not-working-in-precise](http://askubuntu.com/questions/150601/why-nvidiabl-module-is-not-working-in-precise)

---

### Post by y400 on 2012-12-29
With my Y400 running Arch I'm using the nvidia driver and needed the [[COLOR="Blue"]nvidiabl driver[/COLOR]]("https://github.com/guillaumezin/nvidiabl") to be able to change the brightness.  With the module loaded, it adds an interface at /sys/class/backlight/nvidia_backlight where you should be able to change the brightness parameter.  To get the fn keys to change the brightness, I'm using the acpi scripts from [[COLOR="Blue"]here[/COLOR]]("https://github.com/guillaumezin/nvidiabl/tree/master/scripts/etc/acpi") with the sony events changed for this laptop.

---

### Post by rorschachwalter on 2012-12-30
Could you fill us in on how to capture those key events so that we can modify the script to run on our laptops? I'm trying to get the function keys working on a Y500.

---

### Post by y400 on 2012-12-30
You'll need to have the ACPI daemon, acpid, running to be able to check the key events and to run those event scripts. You can then run:
```
acpi_listen
```
Now press fn+up and fn+dn and it should give you the associated events.  For me, they are:
```
video/brightnessup BRTUP 00000086 00000000
video/brightnessdown BRTDN 00000087 00000000
```

The only other thing that comes to mind right now is to make sure the scripts are executable. Oh and probably need to restart acpid.

---

### Post by Y500user on 2012-12-31
> **y400 said:**
> With my Y400 running Arch I'm using the nvidia driver and needed the [[COLOR="Blue"]nvidiabl driver[/COLOR]]("https://github.com/guillaumezin/nvidiabl") to be able to change the brightness.  With the module loaded, it adds an interface at /sys/class/backlight/nvidia_backlight where you should be able to change the brightness parameter.  To get the fn keys to change the brightness, I'm using the acpi scripts from [[COLOR="Blue"]here[/COLOR]]("https://github.com/guillaumezin/nvidiabl/tree/master/scripts/etc/acpi") with the sony events changed for this laptop.
Wow! Thank you very much for the response.. I am able to control the backlight using the function keys now!

---

### Post by rorschachwalter on 2012-12-31
Could you post a step-by-step of how you named and edited and placed the scripts? I thought I had everything set to go, but then the keys still don't work. I'm working with a Y500, so your results should be repeatable.

What I tried:
I put a file 'nvidia-brightness-up' into /etc/acpi/events
Its contents were:
```
event=video LCD 00000000 00000086
action=/etc/acpi/nvidia_backlight_up.sh
```

Because acpi_listen gave me "video LCD 00000086 00000000" when I did Fn + Up.

I made a file 'nvidia_backlight_up.sh', chmod +x'd it, then placed it into /etc/acpi with the contents:
```
#!/bin/sh

test -f /sys/class/backlight/nvidia_backlight/brightness || exit 0

VAL=`cat /sys/class/backlight/nvidia_backlight/actual_brightness`
MAX=`cat /sys/class/backlight/nvidia_backlight/max_brightness`
STEP=10

VAL=`expr $VAL + $STEP`

if [ $VAL -gt $MAX ]; then
	VAL=$MAX
fi

echo -n $VAL > /sys/class/backlight/nvidia_backlight/brightness
```

And that doesn't produce any results.

---

### Post by Y500user on 2013-01-01
> **rorschachwalter said:**
> Could you post a step-by-step of how you named and edited and placed the scripts? I thought I had everything set to go, but then the keys still don't work. I'm working with a Y500, so your results should be repeatable.

What I tried:
I put a file 'nvidia-brightness-up' into /etc/acpi/events
Its contents were:
```
event=video LCD 00000000 00000086
action=/etc/acpi/nvidia_backlight_up.sh
```

Because acpi_listen gave me "video LCD 00000086 00000000" when I did Fn + Up.

I made a file 'nvidia_backlight_up.sh', chmod +x'd it, then placed it into /etc/acpi with the contents:
```
#!/bin/sh

test -f /sys/class/backlight/nvidia_backlight/brightness || exit 0

VAL=`cat /sys/class/backlight/nvidia_backlight/actual_brightness`
MAX=`cat /sys/class/backlight/nvidia_backlight/max_brightness`
STEP=10

VAL=`expr $VAL + $STEP`

if [ $VAL -gt $MAX ]; then
	VAL=$MAX
fi

echo -n $VAL > /sys/class/backlight/nvidia_backlight/brightness
```

And that doesn't produce any results.
I am working with a Y500 also. I basically did precisely what you have mentioned and it is working. Did you restart acpid? Also, make sure that the driver module is indeed being loaded on boot up, i.e by adding nvidiabl to /etc/module on a new line and rebooting. If the driver is indeed being loaded, then editing /sys/class/backlight/nvidia_backlight/brightness (which you should have if the driver is loaded) to  a different value should change the screen brightness in real-time.  If that is working, then try running your nvidia_backlight_up.sh file from the terminal to see if the brightness indeed goes up by 10.
   I guess all of this assumes that you are using the nVidia driver (nvidia-current-updates) for your display to begin with.

---

### Post by Y500user on 2013-01-01
Has anyone managed to get their Webcam working on the Y400/Y500 ?

---

### Post by y400 on 2013-01-01
> **Y500user said:**
> Has anyone managed to get their Webcam working on the Y400/Y500 ?

I haven't played around too much with it besides getting it to work in guvcview. The webcam in my Y400 is listed as the following from lsusb:
```
Bus 002 Device 002: ID 04f2:b331 Chicony Electronics Co., Ltd
```

It uses the linux-uvc driver and after it not working I sent a message to the linux-uvc mailing list and got pointed in the right direction. It tries to request too much bandwidth on the usb bus causing it to fail. I finally realized that changing the resolution to 320x240 in guvcview, closing it, and the restarting guvcview gets it working.  Since then, I haven't done anything else with it like trying to get skype going.

---

### Post by Y500user on 2013-01-01
> **y400 said:**
> I haven't played around too much with it besides getting it to work in guvcview. The webcam in my Y400 is listed as the following from lsusb:
```
Bus 002 Device 002: ID 04f2:b331 Chicony Electronics Co., Ltd
```

It uses the linux-uvc driver and after it not working I sent a message to the linux-uvc mailing list and got pointed in the right direction. It tries to request too much bandwidth on the usb bus causing it to fail. I finally realized that changing the resolution to 320x240 in guvcview, closing it, and the restarting guvcview gets it working.  Since then, I haven't done anything else with it like trying to get skype going.
Thank you very much! I'll give it a try... On the Y500 the webcam seems to be listed by lsusb to be "Realtek Semiconductor Peripheral".

---

### Post by greybeard62 on 2013-01-02
> **Y500user said:**
> I am working with a Y500 also. I basically did precisely what you have mentioned and it is working. Did you restart acpid? Also, make sure that the driver module is indeed being loaded on boot up, i.e by adding nvidiabl to /etc/module on a new line and rebooting. If the driver is indeed being loaded, then editing /sys/class/backlight/nvidia_backlight/brightness (which you should have if the driver is loaded) to  a different value should change the screen brightness in real-time.  If that is working, then try running your nvidia_backlight_up.sh file from the terminal to see if the brightness indeed goes up by 10.
   I guess all of this assumes that you are using the nVidia driver (nvidia-current-updates) for your display to begin with.

I am struggling with a new Y500 also trying to get brightness FN keys to work.  I have installed the latest driver from nvidia, 310.19 I believe and nvidia Xserver Settings is running and to prevent blindness I turn brightness down in color correction.

OK, I have installed nvidialbl.  Module is loaded on restart.  I have the directory /sys/class/backlight/nvidia_backlight installed.  When I do a sudo gedit the brightness file I simply get an error "can't create a backup file", won't save it or change the value of 127 which is the same as max_brightness.

It appears I might have a different nvidia driver installed.  When I tried to install nvidia_current (three times) the display went wild, into low res, could not see anything on screen (it was there just spread out beyond ability to see anything).  So this is the fourth clean install of Ubuntu 12.10.  

Yeah and I can't get the brightness to change with any of these scripts or instructions, I can change the color brightness as noted.

I certainly didn't want W8 but I have ordered a copy of Win7 just in case but then I can't find the drivers at Lenovo for Win7 either.  Anyone know how to find Win7 drivers for the Y500?

On the last Lenovo, U160, it took about four months to get support for the display and I had to revert to Win7 on that one until the i914 stuff supported it (something about reversed polarity screen).  It is beginning to look that way here except it appears nvidia and Linux just don't mix - something I'll long remember.  This is perhaps the worst case install I've ever had and six laptops now running Linux, either Ubuntu or Mint(wife loves Mint).

Well, not whining;) but certainly would like help.  This is the Y500 from Lenovo, i7-3630, 1TB, geforce gt 650M-2GB.  The current nvidia driver is displaying a beautiful 1920x1080 screen, a few other minor issues like no awake on lid open and the cam not funtional, all minor compared to brightness.

---

### Post by greybeard62 on 2013-01-02
Hey, apparently screaming and pulling hair and learning the right commands to change the value of "brightness" in /sys/class/backlight/nvidia_backlight was the right approach.

Now, the command issued:
echo nn | sudo tee brightness

where nn is a value between 0 and 127 in my case.  By decrementing "10" in value down to 57 I get a good brightness.

OK, sorry about the frustration guys but after 5 years of Linux I still feel like I don't know anything sometimes.  The forum helps a lot and the command is from Toz in the Hardware section of forum where I initially went with post.  It appears this is the most active discussion on the Y500.  Now, down to nitty on those scripts, I'll keep playing but nice if someone will post the exact scripts and placement which tie the FN keys to the brightness file in the thing.  Oh yeah, I'm about out of hair to pull:lolflag:

---

### Post by rorschachwalter on 2013-01-02
> **greybeard62 said:**
> 

It appears I might have a different nvidia driver installed.  When I tried to install nvidia_current (three times) the display went wild, into low res, could not see anything on screen (it was there just spread out beyond ability to see anything).

Well, not whining;) but certainly would like help.  This is the Y500 from Lenovo, i7-3630, 1TB, geforce gt 650M-2GB.  The current nvidia driver is displaying a beautiful 1920x1080 screen, a few other minor issues like no awake on lid open and the cam not funtional, all minor compared to brightness.

The resolution issue is because the driver didn't properly install. Make sure you have "dkms" installed first as well as "linux-headers-`uname -r`" first. If you have "linux-headers-generic" installed, the nvidia driver will not work. So if you're still in that boat, you don't have to reinstall Ubuntu. Just remove the nvidia driver (and linux-headers-generic just for the heck of it), install linux-headers-`uname -r` first, then reinstall nvidia. Everything should work fine.

First, make sure nvidiabl is being loaded automatically by adding a line saying simply "nvidiabl" to /etc/modules.

The scripts I posted above weren't quite right, but they were really close. Here's what they should be:
/etc/acpi/nvidia_backlight_up.sh:
```
#!/bin/sh

test -f /sys/class/backlight/nvidia_backlight/brightness || exit 0

VAL=`cat /sys/class/backlight/nvidia_backlight/actual_brightness`
MAX=`cat /sys/class/backlight/nvidia_backlight/max_brightness`
STEP=10

VAL=`expr $VAL + $STEP`

if [ $VAL -gt $MAX ]; then
	VAL=$MAX
fi

echo -n $VAL > /sys/class/backlight/nvidia_backlight/brightness
```
/etc/acpi/nvidia_backlight_down.sh:
```
#!/bin/sh

test -f /sys/class/backlight/nvidia_backlight/brightness || exit 0

VAL=`cat /sys/class/backlight/nvidia_backlight/actual_brightness`
MIN=0
STEP=10

VAL=`expr $VAL - $STEP`

if [ $VAL -lt $MIN ]; then
	VAL=$MIN
fi

echo -n $VAL > /sys/class/backlight/nvidia_backlight/brightness
```
/etc/acpi/events/nvidia-brightness-down:
```
event=video LCD 00000087 00000000
action=/etc/acpi/nvidia_backlight_down.sh
```
/etc/acpi/events/nvidia-brightness-up:
```
event=video LCD 00000086 00000000
action=/etc/acpi/nvidia_backlight_up.sh
```

Then you have to make sure those scripts are executable:
```
sudo chmod +x /etc/acpi/nvidia_backlight_up.sh
sudo chmod +x /etc/acpi/nvidia_backlight_down.sh
```

You also need to have permissions to edit the brightness file itself (this was one of the problems I ran into -- the keys were running the script, but I didn't have permission to change the file so nothing happened). I'm not sure if this is the "proper" way to do things, but it at least works. Someone can correct me if I'm wrong and I'll edit this post:
```
sudo chown YOURUSERNAME /sys/class/backlight/nvidia_backlight/brightness
```

That should work for a Lenovo Y500. It's not quite a perfect workaround -- the brightness actually increases and decreases slightly past what the indicator shows, but it basically works and I think you'll be quite happy with it.

If it works for you exactly as I've written it up, please report back. If there was anything I didn't quite explain or that didn't quite work, please report back so I can edit this post for others as well.

---

### Post by greybeard62 on 2013-01-02
"If it works for you exactly as I've written it up, please report back. If there was anything I didn't quite explain or that didn't quite work, please report back so I can edit this post for others as well."

Thank you so much! Your scripts worked perfectly just as posted.  Can't tell you how much I appreciate your help. This forum is a great resource.

This is a great timesaver and help for those just getting the Y500 or Y400.  I get to save about six hairs on top of my head now and I can put up my big Linux books again, things are heavy.  It helps to remember how to do stuff and learn new things though, fertilizer for the brain.

Of course for a plain newb or an old geezer like me, create the scripts in your home dir or a work dir, then sudo cp to appropriate directories as listed.  The absolute beginner will need to know how to cat the files but you can't do everything.  Everything worked perfectly after reboot.  I'm gonna go get a shot of Knob Creek - you earned it, I'll drink it to you, cheers!

---

### Post by greybeard62 on 2013-01-03
One more thing, about the generic headers.  I followed the guide on this forum at:
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)

to install the .bin driver from nvidia web site.

The driver is installed and works, current 64 bit for this card 310.19 but I have produced a bug report on the nvidia driver, crashed.

So now I am 3.5.0-21-generic.

Apparently you are suggesting the nvidia-currrent driver works without the generic headers?  There are many different guides available and the one above did work so there I was on the fourth install with generic headers.  

Just a little dream but is there consensus about this and perhaps a complete Y500 install guide..and finally, are you 12.10 64 bit desktop?

Before I get back to that crazy screen and try to remove generic headers and install 3.5.0-21-64bit and have to start all over I'll listen to advice.

---

### Post by oldfred on 2013-01-03
I do not have the Lenovo, but do have nVidia.

If you install the nVidia driver direct from nVidia, you have to reinstall with every new kernel as part of the install step is recompiling the init or boot files.

The experimental files from Ubuntu are just the newer versions of the nVidia. After nVidia messed up with the older .40 version not working with some nVidia cards I think Ubuntu wants to wait and see if the newer version really works before truly recommending it. Before they used to only offer one version.

If you download the Ubuntu versions, then with every kernel update it automatically is recompiled & works.

Some very new versions of Nvidia cards or chips may need the very newest driver, so then you cannot use the Ubuntu provided ones. But if not bleeding edge, it is a lot easier just to use the Ubuntu provided ones.

---

### Post by rorschachwalter on 2013-01-03
> **greybeard62 said:**
> One more thing, about the generic headers.  I followed the guide on this forum at:
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)

to install the .bin driver from nvidia web site.

The driver is installed and works, current 64 bit for this card 310.19 but I have produced a bug report on the nvidia driver, crashed.

As pointed out in the comment above, using the Ubuntu-provided driver makes upgrades seamless and also protects against regressions and instability. It's recommended that you stick with installing using the nvidia-current package. Lots of people have complained about updates and experimental drivers not working, and then things being fixed when reverting to nvidia-current.

And nvidia-current works fine on my Lenovo Ideapad Y500 with a 650m -- no crashes yet even after gaming for a while.

> Apparently you are suggesting the nvidia-currrent driver works without the generic headers?  There are many different guides available and the one above did work so there I was on the fourth install with generic headers.

Yes, I'm a bit dismayed at how difficult it is to find consistent and verified documentation on installing the nvidia driver. But again, the recommended installation procedure is to use nvidia-current. This is how Ubuntu installs it if you install and invoke jockey (Ubuntu's tool for installing proprietary drivers and firmware).

I am not exactly sure what the issue with the headers and the nvidia-current package is. But if you had resolution problems or if your desktop wouldn't boot or something after trying the nvidia-current package, it has to do with the headers. Normally, linux-headers-generic should work (and I'm guessing it does with the driver provided on nvidia's site), but there's some bug causing it to not work now. The other command I provided fixes the headers issue and allows a very quick and easy installation of the nvidia drivers. Install dkms, install the headers, install nvidia-current, then reboot and everything should be perfect.

No messing around with other commands to install the driver from nvidia's site, and for me, no crashes.

> Just a little dream but is there consensus about this and perhaps a complete Y500 install guide..and finally, are you 12.10 64 bit desktop?

The consensus is that, at least for this Ubuntu release, you should use nvidia-current, which means not installing linux-headers-generic, but installing linux-headers-`uname -r` and dkms first.

> Before I get back to that crazy screen and try to remove generic headers and install 3.5.0-21-64bit and have to start all over I'll listen to advice.

I think you can fix your situation fairly easily. Give this a shot, and if it doesn't work, then a rebuild might be easier:

Just uninstall the nvidia driver you installed from their website using this command:
```
sudo ~/installation_file.run --uninstall
```

Replace the filename above with whatever the actual filename is, and make sure the file is in your home directory.

Then uninstall the headers you installed before (you can probably leave them installed, but just incase):
```
sudo apt-get remove linux-headers-generic
```

I'd reboot at this point just to be sure nothing is sitting around that might cause problems with the new driver installation. After a reboot, just install dkms and linux-headers-`uname -r`, then after those install nvidia-current. Reboot and you should be good to go.

---

### Post by greybeard62 on 2013-01-03
OK,

I'm hosed again.

First uninstalled the nvidia driver as noted - done.
Then uninstalled generic headers - done.
Reboot.
Screen hosed.  Can't see anything except the spread out background.

Can get a terminal going in low-res.
Can't install "uname-r"
Don't have a clue but probably can't see everything out there.
dpkg --list shows two images, 3.5.0-17.28 and 3.5.0-21.32 as well as their linux-image-ex and thelinux-image-ge.

So, please give command to install the headers.
Tried sudo apt-get install linux-headers(all combinations I could think of).

---

### Post by rorschachwalter on 2013-01-03
Sorry to hear you're having troubles.

I think the problem is that you're typing the package name wrong. It's
```
linux-headers-`uname -r`
```The uname -r text is enclosed by the little apostrophe-type thing (called a grace accent) below the tilda. The command will NOT work with quotes or single quotes -- you must use the grave accent. Also make sure it has a space before the between the "uname" and the "-r" ending.

```
sudo apt-get install linux-headers-`uname -r`
```I didn't add any special repositories to my install, so the package should be there for you. Doing "apt-cache search linux-headers-`uname -r`" shows
```
linux-headers-3.5.0-19-generic - Linux kernel headers for version 3.5.0 on 32 bit x86 SMP
```
You probably won't see exactly that version since I'm typing this from another computer, but you should be able to install the package once it's typed properly.

---

### Post by greybeard62 on 2013-01-03
Yes, I understand.  However this results in 3.5.0-21-generic showing installed.  Perhpas I misunderstood thinking I was removing (I did execute the command and reboot) the generic headers and reverting.  So, after executing the code I still show generic installed, ie, uname -r returns 3.5.0-21-generic.

Yes, am using the correct character under the tilda not quotes, just typed it wrong here.

Anyway, same thing, after reboot and sudo apt-get install .....am still running generic, still have nvidia-current drivers so good there and still immediately after reboot have system program problem (it is an nvidia crash).

So, either I am extremely dense or simply don't understand what you are telling me or I need to re-install and start over to get rid of the generic headers.  They remain.

---

### Post by greybeard62 on 2013-01-03
It is late, not sure if my response was clear enough.
OK, did this all again before last post.
1. Uninstalled the 310.19 64 bit run file - OK
2.removed linux-headers generic
3. rebooted.
4. Installed sudo apt-get install linux-headers-`uname -r`
5. Installed sudo apt-get install nvidia-current
6. reboot

All commands work properly but I still am generic, 3.5.0-21-generic
I definitely am running the nvidia-current driver, from repository not nvidia.  Definitely getting nvidia crash on reboot (still works just cancel out).

---

### Post by rorschachwalter on 2013-01-04
I guess I wasn't understanding your problem then. Sorry!

I think the best solution would just be to reinstall. At least, that's the best solution I've got, because if we're running the same machine, I have no idea why the steps that worked for me wouldn't also work for you, unless something during the initial nvidia install messed with something.

Regarding having the generic headers installed, that's the way it should be -- just NOT from the linux-headers-generic package. Only from the uname -r command.

Your configuration includes an nVidia 650m?

---

### Post by oldfred on 2013-01-04
these are the commands I ran. I did not put version number into headers install and it installed the current head that I needed.

       [http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)
# You may need headers - meta package for current version:
sudo apt-get install linux-headers-generic
# only reason to purge is there are several versions, if you know you have different nVidia use that:
#To see available  versions:
dpkg -l | grep -i nvidia*
apt-cache search nvidia-sett*
# I used nvidia-current-updates & nvidia-settings-updates, example below is just nvidia-current, use version you prefer
sudo apt-get purge nvidia*
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot
May want nvidia-current, nvidia-current-updates or nvidia-current-experimental-XXX for most recent testing version.
apt-cache search nvidia-sett*

---

### Post by Y500user on 2013-01-04
> **rorschachwalter said:**
> The resolution issue is because the driver didn't properly install. Make sure you have "dkms" installed first as well as "linux-headers-`uname -r`" first. If you have "linux-headers-generic" installed, the nvidia driver will not work. So if you're still in that boat, you don't have to reinstall Ubuntu. Just remove the nvidia driver (and linux-headers-generic just for the heck of it), install linux-headers-`uname -r` first, then reinstall nvidia. Everything should work fine.

First, make sure nvidiabl is being loaded automatically by adding a line saying simply "nvidiabl" to /etc/modules.

The scripts I posted above weren't quite right, but they were really close. Here's what they should be:
/etc/acpi/nvidia_backlight_up.sh:
```
#!/bin/sh

test -f /sys/class/backlight/nvidia_backlight/brightness || exit 0

VAL=`cat /sys/class/backlight/nvidia_backlight/actual_brightness`
MAX=`cat /sys/class/backlight/nvidia_backlight/max_brightness`
STEP=10

VAL=`expr $VAL + $STEP`

if [ $VAL -gt $MAX ]; then
	VAL=$MAX
fi

echo -n $VAL > /sys/class/backlight/nvidia_backlight/brightness
```
/etc/acpi/nvidia_backlight_down.sh:
```
#!/bin/sh

test -f /sys/class/backlight/nvidia_backlight/brightness || exit 0

VAL=`cat /sys/class/backlight/nvidia_backlight/actual_brightness`
MIN=0
STEP=10

VAL=`expr $VAL - $STEP`

if [ $VAL -lt $MIN ]; then
	VAL=$MIN
fi

echo -n $VAL > /sys/class/backlight/nvidia_backlight/brightness
```
/etc/acpi/events/nvidia-brightness-down:
```
event=video LCD 00000087 00000000
action=/etc/acpi/nvidia_backlight_down.sh
```
/etc/acpi/events/nvidia-brightness-up:
```
event=video LCD 00000086 00000000
action=/etc/acpi/nvidia_backlight_up.sh
```

Then you have to make sure those scripts are executable:
```
sudo chmod +x /etc/acpi/nvidia_backlight_up.sh
sudo chmod +x /etc/acpi/nvidia_backlight_down.sh
```

You also need to have permissions to edit the brightness file itself (this was one of the problems I ran into -- the keys were running the script, but I didn't have permission to change the file so nothing happened). I'm not sure if this is the "proper" way to do things, but it at least works. Someone can correct me if I'm wrong and I'll edit this post:
```
sudo chown YOURUSERNAME /sys/class/backlight/nvidia_backlight/brightness
```

That should work for a Lenovo Y500. It's not quite a perfect workaround -- the brightness actually increases and decreases slightly past what the indicator shows, but it basically works and I think you'll be quite happy with it.

If it works for you exactly as I've written it up, please report back. If there was anything I didn't quite explain or that didn't quite work, please report back so I can edit this post for others as well.
Thanks for posting in detail.... The graphical brightness indicator seems to have a fixed number of steps I.e hotkey presses between min and max... If you increase your STEP size in the script so that the number of STEPs between 0 and max_brightness is the same as the number of steps the graphical indicator has, that might fix this minor issue.

---

### Post by greybeard62 on 2013-01-04
Yes, have 650M with 2GB, lspci so we can compare models:

00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GK107 [GeForce GT 650M] (rev a1)
01:00.1 Audio device: NVIDIA Corporation Device 0e1b (rev a1)
02:00.0 Ethernet controller: Atheros Communications Inc. AR8161 Gigabit Ethernet (rev 10)
03:00.0 Network controller: Intel Corporation Centrino Wireless-N 2230 (rev c4)
04:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 30)
04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 30)
04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 30)
04:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 30)

And, oldfred, yes, that is the install procedure I used but first time around I did the latter part and installed the most current driver downloaded from nvidia site, 64bit 310.19.  It worked except for occasional crash.

OK, where I am now is repeated the steps in that post and did first part and installed nvidia-current-updates.

All is well except I get a "system problem" shortly after reboot.  Telling it to report gives the nvidia crash report, stored in home dir.  Purge should have cleared any old stuff but who knows.

It's not the "end of the world" as we know it, just annoying.  I'll leave it this way a while and perhaps an update will clear it or perhaps there is a driver/hardware bug.  I am running generic as noted with nvidia-current-updates.

If we have a difference in the models, ie, lspci shows something different than my model please advise.

Thanks to you for patience and assistance.  At least with this driver from repository I won't have to do it manually in future.  But, just in case, I saved the scripts on my backup drive so won't have to recreate that.

---

### Post by Y500user on 2013-01-04
> **y400 said:**
> I haven't played around too much with it besides getting it to work in guvcview. The webcam in my Y400 is listed as the following from lsusb:
```
Bus 002 Device 002: ID 04f2:b331 Chicony Electronics Co., Ltd
```It uses the linux-uvc driver and after it not working I sent a message to the linux-uvc mailing list and got pointed in the right direction. It tries to request too much bandwidth on the usb bus causing it to fail. I finally realized that changing the resolution to 320x240 in guvcview, closing it, and the restarting guvcview gets it working.  Since then, I haven't done anything else with it like trying to get skype going.
Thanks.. Just wanted to report back that setting the frame rate and/or frame size to low values like you suggested helped and am able to see the video using guvcview.

On my Y500, the webcam is listed under lsusb as:

```
Bus 004 Device 002: ID 0bda:58dd Realtek Semiconductor Corp.
```Also, I get the following:
```
dmesg | grep uvc
[   19.388144] uvcvideo: Found UVC 1.00 device Lenovo EasyCamera (0bda:58dd)
[   19.398276] usbcore: registered new interface driver uvcvideo
```

---

### Post by kranthipls on 2013-01-31
Hi Even I am having the  problems for installing ubuntu  along side windows with a dual boot option for Lenovo Y 500. Can anyone give me a procedure for installing ubuntu in lenovo Y500

Thank you

---

### Post by oldfred on 2013-02-01
@kranthipls
I have not seen anyone with the Lenovo summarize the install details. If you start at the first post and follow thru all the details are there, just may take a bit to sort thru.

Also important to backup first both Windows & efi partition as one user in another thread used the overwrite entire drive option and erased Windows totally.

If you like keep track of what you do and document in one post like these have done.
       Installing Ubuntu 12.10 x64 on Dell XPS 13 Alongside Windows from USB New user with Details
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)

There are only a few UEFI/BIOS vendors so your screens may be similar?
Sony VAIO E Series Windows 8/Ubuntu 12.10 Dual Boot, EFI help UEFI screens shown
[http://ubuntuforums.org/showthread.php?t=2087991](http://ubuntuforums.org/showthread.php?t=2087991)

You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by binarydomain on 2013-02-04
Hi! Could anyone please give me a full alghorithm for successfull Ubuntu 12.10 install on Y500?

What i've done:
1. Enabled Legacy support
2. Made a 500gb partition for Linux
3. Installed Ubuntu there with default settings
4. After it Ubuntu is runable only in legacy mode. And Win8 only in UEFI. It is pretty annoying
5. I've booted from liveUSB, launched boot-repair with recommended settings
6. Changed BIOS settings to UEFI and boot point to Ubuntu.
7. It starts GRUB Menu. When i start Win8 from it - it can't launch it. When i start Ubuntu - only something like a quater of screen gows pure purple and nothing more happens.

I've tried some magic with EasyBCD under Win8 and other stuff, but nothing helped. Default Win8 UEFI boots well and nothing more( In legacy mode nothing is launchable at all, i am getting grub rescue menu.

I would appreciate any help, i'm pretty noob in linux and in disk partitioning and boot problems.

Thanks in advance!

---

### Post by oldfred on 2013-02-04
Have you turned off quick boot in Windows. Seem lots of issues with Windows hibernation.
       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
    
You can only boot Windows with the new entries added by Boot-Repair not from grub.
       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
    
What video chip do you have? Or is it Optimus?
Does system have Intel SRT?
       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by jowsingchue on 2013-02-22
My y500 can now adjust brightness. The next problem is the maximum brightness I can reach is very low.

When I boot up, this is my brightness level.
```

$ cat /sys/class/backlight/nvidia_backlight/brightness
2340
$ cat /sys/class/backlight/nvidia_backlight/actual_brightness
2339
$ cat /sys/class/backlight/nvidia_backlight/max_brightness
2339
```Ater I adjust brightness, my "max_brighness" was changed
```

$ cat /sys/class/backlight/nvidia_backlight/max_brightness
127
```and I cannot increase brightness beyond this value.

Any idea please?

---

### Post by beatgeek on 2013-02-23
> **rorschachwalter said:**
> The resolution issue is because the driver didn't properly install. Make sure you have "dkms" installed first as well as "linux-headers-`uname -r`" first. If you have "linux-headers-generic" installed, the nvidia driver will not work. So if you're still in that boat, you don't have to reinstall Ubuntu. Just remove the nvidia driver (and linux-headers-generic just for the heck of it), install linux-headers-`uname -r` first, then reinstall nvidia. Everything should work fine.

First, make sure nvidiabl is being loaded automatically by adding a line saying simply "nvidiabl" to /etc/modules.

The scripts I posted above weren't quite right, but they were really close. Here's what they should be:
/etc/acpi/nvidia_backlight_up.sh:
```
#!/bin/sh

test -f /sys/class/backlight/nvidia_backlight/brightness || exit 0

VAL=`cat /sys/class/backlight/nvidia_backlight/actual_brightness`
MAX=`cat /sys/class/backlight/nvidia_backlight/max_brightness`
STEP=10

VAL=`expr $VAL + $STEP`

if [ $VAL -gt $MAX ]; then
	VAL=$MAX
fi

echo -n $VAL > /sys/class/backlight/nvidia_backlight/brightness
```
/etc/acpi/nvidia_backlight_down.sh:
```
#!/bin/sh

test -f /sys/class/backlight/nvidia_backlight/brightness || exit 0

VAL=`cat /sys/class/backlight/nvidia_backlight/actual_brightness`
MIN=0
STEP=10

VAL=`expr $VAL - $STEP`

if [ $VAL -lt $MIN ]; then
	VAL=$MIN
fi

echo -n $VAL > /sys/class/backlight/nvidia_backlight/brightness
```
/etc/acpi/events/nvidia-brightness-down:
```
event=video LCD 00000087 00000000
action=/etc/acpi/nvidia_backlight_down.sh
```
/etc/acpi/events/nvidia-brightness-up:
```
event=video LCD 00000086 00000000
action=/etc/acpi/nvidia_backlight_up.sh
```

Then you have to make sure those scripts are executable:
```
sudo chmod +x /etc/acpi/nvidia_backlight_up.sh
sudo chmod +x /etc/acpi/nvidia_backlight_down.sh
```

You also need to have permissions to edit the brightness file itself (this was one of the problems I ran into -- the keys were running the script, but I didn't have permission to change the file so nothing happened). I'm not sure if this is the "proper" way to do things, but it at least works. Someone can correct me if I'm wrong and I'll edit this post:
```
sudo chown YOURUSERNAME /sys/class/backlight/nvidia_backlight/brightness
```

That should work for a Lenovo Y500. It's not quite a perfect workaround -- the brightness actually increases and decreases slightly past what the indicator shows, but it basically works and I think you'll be quite happy with it.

If it works for you exactly as I've written it up, please report back. If there was anything I didn't quite explain or that didn't quite work, please report back so I can edit this post for others as well.

I have a y400 and have tried to follow these instructions for changing the screen brightness, but I run into a few snags. The first is that nvidiabl doesn't seem to install properly - in fact the most recent version on github seems to be corrupt, so I installed the .deb of version .74 which appeared to work, except that after a reboot it never loaded, and typing "sudo modprobe nvidiabl" gives me "Error blahblah: No such device". It isn't listed in lsmod.

And then when doing "sudo chown YOURUSERNAME /sys/class/backlight/nvidia_backlight/brightness" it says there's no such file, and likewise  cat /sys/class/backlight/nvidia_backlight/brightness returns nothing.

---

### Post by MrMemou on 2013-02-24
Hi, did you get Ubuntu on your Lenovo Y500?. I'm trying whith mine but without luck the problem is the same as yours, the blank screen after hit on "try ubuntu" in the GRUB menu. how did you fix it?

---

### Post by beatgeek on 2013-03-02
I installed version .76 of nvidiabl and this solved the problem. Ah my eyes can finally take a rest!

---

### Post by kranthipls on 2013-03-16
Even I am facing the same problem. Did you find a solution.

---

### Post by Bushido Samurai on 2013-03-18
> **jowsingchue said:**
> My y500 can now adjust brightness. The next problem is the maximum brightness I can reach is very low.

When I boot up, this is my brightness level.
```

$ cat /sys/class/backlight/nvidia_backlight/brightness
2340
$ cat /sys/class/backlight/nvidia_backlight/actual_brightness
2339
$ cat /sys/class/backlight/nvidia_backlight/max_brightness
2339
```Ater I adjust brightness, my "max_brighness" was changed
```

$ cat /sys/class/backlight/nvidia_backlight/max_brightness
127
```and I cannot increase brightness beyond this value.

Any idea please?



find a solution?? I have the same error but I have searched for 2 days without any solution!

---

### Post by Bushido Samurai on 2013-03-18
> **rorschachwalter said:**
> The resolution issue is because the driver didn't properly install. Make sure you have "dkms" installed first as well as "linux-headers-`uname -r`" first. If you have "linux-headers-generic" installed, the nvidia driver will not work. So if you're still in that boat, you don't have to reinstall Ubuntu. Just remove the nvidia driver (and linux-headers-generic just for the heck of it), install linux-headers-`uname -r` first, then reinstall nvidia. Everything should work fine.

First, make sure nvidiabl is being loaded automatically by adding a line saying simply "nvidiabl" to /etc/modules.

The scripts I posted above weren't quite right, but they were really close. Here's what they should be:
/etc/acpi/nvidia_backlight_up.sh:
```
#!/bin/sh

test -f /sys/class/backlight/nvidia_backlight/brightness || exit 0

VAL=`cat /sys/class/backlight/nvidia_backlight/actual_brightness`
MAX=`cat /sys/class/backlight/nvidia_backlight/max_brightness`
STEP=10

VAL=`expr $VAL + $STEP`

if [ $VAL -gt $MAX ]; then
    VAL=$MAX
fi

echo -n $VAL > /sys/class/backlight/nvidia_backlight/brightness
```
/etc/acpi/nvidia_backlight_down.sh:
```
#!/bin/sh

test -f /sys/class/backlight/nvidia_backlight/brightness || exit 0

VAL=`cat /sys/class/backlight/nvidia_backlight/actual_brightness`
MIN=0
STEP=10

VAL=`expr $VAL - $STEP`

if [ $VAL -lt $MIN ]; then
    VAL=$MIN
fi

echo -n $VAL > /sys/class/backlight/nvidia_backlight/brightness
```
/etc/acpi/events/nvidia-brightness-down:
```
event=video LCD 00000087 00000000
action=/etc/acpi/nvidia_backlight_down.sh
```
/etc/acpi/events/nvidia-brightness-up:
```
event=video LCD 00000086 00000000
action=/etc/acpi/nvidia_backlight_up.sh
```

Then you have to make sure those scripts are executable:
```
sudo chmod +x /etc/acpi/nvidia_backlight_up.sh
sudo chmod +x /etc/acpi/nvidia_backlight_down.sh
```

You also need to have permissions to edit the brightness file itself (this was one of the problems I ran into -- the keys were running the script, but I didn't have permission to change the file so nothing happened). I'm not sure if this is the "proper" way to do things, but it at least works. Someone can correct me if I'm wrong and I'll edit this post:
```
sudo chown YOURUSERNAME /sys/class/backlight/nvidia_backlight/brightness
```

That should work for a Lenovo Y500. It's not quite a perfect workaround -- the brightness actually increases and decreases slightly past what the indicator shows, but it basically works and I think you'll be quite happy with it.

If it works for you exactly as I've written it up, please report back. If there was anything I didn't quite explain or that didn't quite work, please report back so I can edit this post for others as well.




Hello, first thank you very much, I followed your instructions and it works, but my problem now is the maximum I can reach brightness is very low.

(Then copy and paste the error of someone that MS is the same one I have!)

When I boot up, this is my brightness level.


```

$ cat /sys/class/backlight/nvidia_backlight/brightness
 2340
$ cat /sys/class/backlight/nvidia_backlight/actual_brightness 
2339
$ cat /sys/class/backlight/nvidia_backlight/max_brightness
2339

```

After I adjust brightness, my "max_brighness" was changed

```

$ cat /sys/class/backlight/nvidia_backlight/max_brightness
127

```

and I cannot increase brightness beyond this value.

I tried changing the file permissions with various commands from shell but not let me change that value. I also disabled the nvidiabl but once I do I can not find again the path (Of course because I've disabled).

No more to do with this problem, can you help me?

---

### Post by jowsingchue on 2013-03-24
> **Bushido Samurai said:**
> find a solution?? I have the same error but I have searched for 2 days without any solution!

Not yet, I think I spent too much time solving this problem, and because I'm a beginner, I cannot code it myself. The brightness problem for this machine happened to occur on windows and was fixed by a newer driver, so right now I'm just laying down waiting for the new driver and use Virtualbox on windows instead. (though the performance is a bit unpleasant)

Hope to see the solution soon.

---

### Post by jowsingchue on 2013-03-25
I've finally found my solution. [**[COLOR=#000000]beatgeek[/COLOR]**]("http://ubuntuforums.org/member.php?u=79892") gave a clue for me.

> **beatgeek said:**
> I installed version .76 of nvidiabl and this solved the problem. Ah my eyes can finally take a rest!


Now I'm using "nvidiabl-dkms_0.76_all.deb" and it works now.

---

### Post by b3nj4m on 2013-04-21
> **jowsingchue said:**
> I've finally found my solution. [**[COLOR=#000000]beatgeek[/COLOR]**]("http://ubuntuforums.org/member.php?u=79892") gave a clue for me.




Now I'm using "nvidiabl-dkms_0.76_all.deb" and it works now.

I'm still having the same problem with the maximum brightness being limited to 127 on the Y500. I've tried version 0.76 and version 0.80. Does anyone know how I might solve this problem?

---

### Post by jowsingchue on 2013-04-22
> **rorschachwalter said:**
> The resolution issue is because the driver didn't properly install. Make sure you have "dkms" installed first as well as "linux-headers-`uname -r`" first. If you have "linux-headers-generic" installed, the nvidia driver will not work. So if you're still in that boat, you don't have to reinstall Ubuntu. Just remove the nvidia driver (and linux-headers-generic just for the heck of it), install linux-headers-`uname -r` first, then reinstall nvidia. Everything should work fine.

First, make sure nvidiabl is being loaded automatically by adding a line saying simply "nvidiabl" to /etc/modules.

The scripts I posted above weren't quite right, but they were really close. Here's what they should be:
/etc/acpi/nvidia_backlight_up.sh:
```
#!/bin/sh

test -f /sys/class/backlight/nvidia_backlight/brightness || exit 0

VAL=`cat /sys/class/backlight/nvidia_backlight/actual_brightness`
MAX=`cat /sys/class/backlight/nvidia_backlight/max_brightness`
STEP=10

VAL=`expr $VAL + $STEP`

if [ $VAL -gt $MAX ]; then
    VAL=$MAX
fi

echo -n $VAL > /sys/class/backlight/nvidia_backlight/brightness
```
/etc/acpi/nvidia_backlight_down.sh:
```
#!/bin/sh

test -f /sys/class/backlight/nvidia_backlight/brightness || exit 0

VAL=`cat /sys/class/backlight/nvidia_backlight/actual_brightness`
MIN=0
STEP=10

VAL=`expr $VAL - $STEP`

if [ $VAL -lt $MIN ]; then
    VAL=$MIN
fi

echo -n $VAL > /sys/class/backlight/nvidia_backlight/brightness
```
/etc/acpi/events/nvidia-brightness-down:
```
event=video LCD 00000087 00000000
action=/etc/acpi/nvidia_backlight_down.sh
```
/etc/acpi/events/nvidia-brightness-up:
```
event=video LCD 00000086 00000000
action=/etc/acpi/nvidia_backlight_up.sh
```

Then you have to make sure those scripts are executable:
```
sudo chmod +x /etc/acpi/nvidia_backlight_up.sh
sudo chmod +x /etc/acpi/nvidia_backlight_down.sh
```

You also need to have permissions to edit the brightness file itself (this was one of the problems I ran into -- the keys were running the script, but I didn't have permission to change the file so nothing happened). I'm not sure if this is the "proper" way to do things, but it at least works. Someone can correct me if I'm wrong and I'll edit this post:
```
sudo chown YOURUSERNAME /sys/class/backlight/nvidia_backlight/brightness
```

That should work for a Lenovo Y500. It's not quite a perfect workaround -- the brightness actually increases and decreases slightly past what the indicator shows, but it basically works and I think you'll be quite happy with it.

If it works for you exactly as I've written it up, please report back. If there was anything I didn't quite explain or that didn't quite work, please report back so I can edit this post for others as well.

Hi, [**[COLOR=#000000]b3nj4m[/COLOR]**]("http://ubuntuforums.org/member.php?u=225739").
Base on the above, what I do is:

1. Uninstall all nvidia components and linux-headers-generic
2. Install neccesery things
```

sudo apt-get install dkms linux-headers-`uname -r`
sudo apt-get install nvidia-current-updates
sudp dpkg -i nvidiabl-dkms_0.76_all.deb
```
3. Add "nvidiabl" (without quotes) to /etc/modules 
4. Edit the script files above and make them executable

Reboot, and that should do it.
Bad English, sorry.

---

### Post by beatgeek on 2013-04-22
For those who are having a problem with maximum brightness, which version of the NVIDIA driver are you using? When I tried the most recent version (313.26 I think), I had problems with the brightness being too low (and it kept switching between high and low brightness on its own for no reason). I switched back to version-current-updates (304.88... I'm actually running linux mint 13, based on ubuntu precise) and it works perfectly.

---

### Post by jowsingchue on 2013-04-23
Hi, **beatgeek**.

Do you have any issue with Lenovo Easycamera?
Mine when black for no reason, I have to reinstall OS in order to use it again.

---

### Post by jonashendrickx on 2013-04-23
This my personal work. It's clearly based upon the idea in this thread. My script is synchronized with the brightness slider. This is the final and correct solution what we needed ;) I am still looking for a way to do it without nvidiabl. I believe we dont need nvidiabl at all since I can control brightness from nvidia-settings. Don't forget to give me credits for my solution if you post it elsewhere :)!

**How it works?** */sys/class/backlight/nvidia_backlight/brightness* contains the brightness value when the brightness keys are pressed. But the brightness doesn't change. I noticed this value has a range of 0-15. But the range of the nvidiabl is  0- 127. with some quick math I came with a formula y=15+8x where x represents the brightness value of the keys, and y is the actual brightness.*/sys/class/backlight/nvidia_backlight/max_brightness contains the maximum brightness, actually I can use this in my script and use remainders and few other things to make my script universal. It's very easy actually. I did not make it universal since I like to have every bit of performance.*





[LIST=1]
[*] Install latest nvidiabl debian package from [https://github.com/guillaumezin/nvidiabl/downloads](https://github.com/guillaumezin/nvidiabl/downloads)
[*] Now open the terminal and type
```
$ sudo gedit /etc/acpi/events/lenovo_backlight_up
```
Enter
```
event=video LCD 00000086 00000000
action=/etc/acpi/lenovo_backlight.sh
```
And now save and close the file.


```
$ sudo gedit /etc/acpi/events/lenovo_backlight_down
```
Enter
```
event=video LCD 00000087 00000000
action=/etc/acpi/lenovo_backlight.sh
```
And now save and close the file.


```
$ sudo gedit /etc/acpi/events/lenovo_backlight.sh
```
Enter
```
#!/bin/bash
test -f /sys/class/backlight/nvidia_backlight/brightness || exit 0
NEW_VALUE=`cat /sys/class/backlight/acpi_video0/brightness`
let BRIGHTNESS=$NEW_VALUE*8+7
echo -n $BRIGHTNESS > /sys/class/backlight/nvidia_backlight/brightness
```
And now save and close the file.
[*] Now let's set the necessary permissions for all the files we need to access
```
$ sudo chmod +x /etc/acpi/lenovo_backlight.sh
sudo chown YOURUSERNAME /sys/class/backlight/nvidia_backlight/brightness
```
[*] Now let's load nvidiabl at boot time, in terminal type:
```
sudo gedit /etc/modules
```
add to the bottom:
```
nvidiabl
```
close and save.
[*] reboot
[/LIST]



This is the best method, Now the brightness is synchronized with the brightness slider applet.


[SIZE=4][COLOR=#ff0000]**Don't forget to buy me a beer if you like it ;)**[/COLOR]
[COLOR=#ff0000]**[donation link]("https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=W38WJQJL358JQ")**[/COLOR][/SIZE]

---

### Post by b3nj4m on 2013-04-26
> **beatgeek said:**
> For those who are having a problem with maximum brightness, which version of the NVIDIA driver are you using? When I tried the most recent version (313.26 I think), I had problems with the brightness being too low (and it kept switching between high and low brightness on its own for no reason). I switched back to version-current-updates (304.88... I'm actually running linux mint 13, based on ubuntu precise) and it works perfectly.

I'm using version 313.30. I'll try downgrading the nvidia driver.

---

### Post by b3nj4m on 2013-04-28
> **b3nj4m said:**
> I'm using version 313.30. I'll try downgrading the nvidia driver.

Downgrading to the 304 series does make the max brightness issue go away. However, I wouldn't consider this a fix since I'm now stuck with an old display driver :/

Is there any hope of nvidiabl being updated to work with the 313 series?

---

### Post by T2Small on 2013-05-03
Thanks for the brightness fixes guys!  For those that can't get the Ubuntu to install via USB (original topic), here is what I did:

Edit the boot/grub/grub.conf:

1) Change where it says "set gfxmode=auto" to "set gfxmode=1920x1080"
2) Under "Install Ubuntu", change "quiet splash" to "nomodeset=1"

Use UEFI, but disable secure boot, and hold F12 while booting to choose the USB disk.  Ubuntu should show up at the proper size.  (If your display is lower resolution adjust the "1920x1080" to something more appropriate.)

---

### Post by T2Small on 2013-05-06
For a complete solution to the install: [http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358)

Worked great for me.

---

### Post by gentix on 2013-05-06
I'm still having trouble getting the nvidiabl module to work. I have tried a couple different versions of the Nvidia driver (310 and 304 I think), and various versions from 72 to most recent of the nvidiabl module but
```
sudo modprobe nvidiabl
```
still gives
```
ERROR: could not insert 'nvidiabl': No such device
```
and
```
/sys/class/backlight/nvidia_backligh/brightness
```
still does not exist


```
/sys/class/backlight/acpi_video/brightness
```
Does exist, but of course it doesn't do anything as it seems that is the file that gets changed by default.

P.S. I have the gt 750m card. Maybe that's the problem?

---

### Post by gentix on 2013-05-07
GUYS GUYS! I found something else that works for me!

xbacklight

```
sudo apt-get install xbacklight
```

I haven't tried hooking it up to the slider with your scripts yet, but I think it will work :D

(Not sure if this will work for the 650m. I currently have the 750m with the 310 driver installed

Hmmm trying to get a script going for xbacklight. Seems that /etc/acpi/events is not hearing my "video LCD 00000086 00000000" signal because the script I connected it to isn't running (I did mark it executable). But I know that the signal is being picked up _somehow_ because it changes the Ubuntu brightness indicator thing.

---

### Post by wikihunter on 2013-05-20
Any updates on brightness control for GT750M?  The most recent nvidia drivers (319.17?) work perfectly except for brightness control.  Same thing for most recent nouveau driver, actually.
I've tried putting acpi_osi=Linux, acpi_osi="!Windows 2012", acpi_backlight=vendor as kernel parameters.  Tried xbacklight too.  As it is, the battery runs out way too quickly due to max brightness.

---

### Post by wikihunter on 2013-05-20
I managed to successfully load nvidiabl.  I thought I had done so earlier.  Saw a message at boot that no supported graphics card was detected.  So, I checked the nvidiabl-gpu.h file at the github page, and can confirm that GT650M is listed there, but not the GT750M.  All that is needed is to add this line:


```

NVIDIABL_DECLARE_GPU_MODEL(0x0fe4, nv5x_driver_data),


``` 



to make it work!  Dont have time or know-how to recompile with that line, so will have to wait for now.

---

### Post by colby2 on 2013-09-06
> **beatgeek said:**
> For those who are having a problem with maximum brightness, which version of the NVIDIA driver are you using? When I tried the most recent version (313.26 I think), I had problems with the brightness being too low (and it kept switching between high and low brightness on its own for no reason). I switched back to version-current-updates (304.88... I'm actually running linux mint 13, based on ubuntu precise) and it works perfectly.
OK I was having the low-brightness problem too. I'm on 319.49 and nvidiabl 0.81. Anyways, to get my brightness back up, try experimenting with the max:

sudo modprobe -r nvidiabl #removes the module
sudo modprobe nvidiabl max=20000 #experiment with this number

then:
cd /sys/class/backlight/nvidia_backlight
echo 127 | sudo tee brightness

If it's bright enough, then great. Otherwise, start at the beginning, and up the max. It takes some experimenting; for me, I had to put like 100000 to get the brightness up.

---

### Post by ngthnhan93 on 2013-09-08
> **jonashendrickx said:**
> This my personal work. It's clearly based upon the idea in this thread. My script is synchronized with the brightness slider. This is the final and correct solution what we needed ;) I am still looking for a way to do it without nvidiabl. I believe we dont need nvidiabl at all since I can control brightness from nvidia-settings. Don't forget to give me credits for my solution if you post it elsewhere :)!

**How it works?** */sys/class/backlight/nvidia_backlight/brightness* contains the brightness value when the brightness keys are pressed. But the brightness doesn't change. I noticed this value has a range of 0-15. But the range of the nvidiabl is  0- 127. with some quick math I came with a formula y=15+8x where x represents the brightness value of the keys, and y is the actual brightness.*/sys/class/backlight/nvidia_backlight/max_brightness contains the maximum brightness, actually I can use this in my script and use remainders and few other things to make my script universal. It's very easy actually. I did not make it universal since I like to have every bit of performance.*





[LIST=1]
[*] Install latest nvidiabl debian package from [https://github.com/guillaumezin/nvidiabl/downloads](https://github.com/guillaumezin/nvidiabl/downloads)
[*] Now open the terminal and type
```
$ sudo gedit /etc/acpi/events/lenovo_backlight_up
```
Enter
```
event=video LCD 00000086 00000000
action=/etc/acpi/lenovo_backlight.sh
```
And now save and close the file.


```
$ sudo gedit /etc/acpi/events/lenovo_backlight_down
```
Enter
```
event=video LCD 00000087 00000000
action=/etc/acpi/lenovo_backlight.sh
```
And now save and close the file.


```
$ sudo gedit /etc/acpi/events/lenovo_backlight.sh
```
Enter
```
#!/bin/bash
test -f /sys/class/backlight/nvidia_backlight/brightness || exit 0
NEW_VALUE=`cat /sys/class/backlight/acpi_video0/brightness`
let BRIGHTNESS=$NEW_VALUE*8+7
echo -n $BRIGHTNESS > /sys/class/backlight/nvidia_backlight/brightness
```
And now save and close the file.
[*] Now let's set the necessary permissions for all the files we need to access
```
$ sudo chmod +x /etc/acpi/lenovo_backlight.sh
sudo chown YOURUSERNAME /sys/class/backlight/nvidia_backlight/brightness
```
[*] Now let's load nvidiabl at boot time, in terminal type:
```
sudo gedit /etc/modules
```
add to the bottom:
```
nvidiabl
```
close and save.
[*] reboot
[/LIST]



This is the best method, Now the brightness is synchronized with the brightness slider applet.


[SIZE=4][COLOR=#ff0000]**Don't forget to buy me a beer if you like it ;)**[/COLOR]
[COLOR=#ff0000]**[donation link]("https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=W38WJQJL358JQ")**[/COLOR][/SIZE]

AND

> [IMG]http://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG][COLOR=#000000] Originally Posted by [/COLOR]**beatgeek**[[IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("http://ubuntuforums.org/showthread.php?p=12614556#post12614556")[COLOR=#000000][I]For those who are having a problem with maximum brightness, which version of the NVIDIA driver are you using? When I tried the most recent version (313.26 I think), I had problems with the brightness being too low (and it kept switching between high and low brightness on its own for no reason). I switched back to version-current-updates (304.88... I'm actually running linux mint 13, based on ubuntu precise) and it works perfectly.

[/I]
[/COLOR]
[COLOR=#000000]OK I was having the low-brightness problem too. I'm on 319.49 and nvidiabl 0.81. Anyways, to get my brightness back up, try experimenting with the max:[/COLOR]

[COLOR=#000000]sudo modprobe -r nvidiabl #removes the module[/COLOR]
[COLOR=#000000]sudo modprobe nvidiabl max=20000 #experiment with this number[/COLOR]

[COLOR=#000000]then:[/COLOR]
[COLOR=#000000]cd /sys/class/backlight/nvidia_backlight[/COLOR]
[COLOR=#000000]echo 127 | sudo tee brightness[/COLOR]

[COLOR=#000000]If it's bright enough, then great. Otherwise, start at the beginning, and up the max. It takes some experimenting; for me, I had to put like 100000 to get the brightness up.[/COLOR]



I just can't thank all of those who help to answer in this thread, and especially to both of those quoted. You guys just make my day.
So here is how I combine the work and finding of both the guys above and get a decent solution to Fn key to adjust brightness in the IdeaPad Y500

As first, I followed **[COLOR=#000000]jonashendrickx [/COLOR]**[COLOR=#000000]for his guide and set up the event-listeners and the .sh file. It would work okay at first since the brightness did change accordingly and it utilised the indicator at the top right corner. But I find that, since he used the relation between the brightness in acqui-video to give a new value of brightness in nvidia_backlight, I thought to myself why not do the same. I also found out that the value of brightness in folder acpi_video0 varies from 0 to 100 with an interval of 6, while the brightness in folder nvidia_backlight has a maximum value of 127. So I changed his formula inside the lenovo_backlight.sh as followed:
```
let BRIGHTNESS=$NEW_VALUE*8+7
```
into
```
let BRIGHTNESS=$NEW_VALUE*127/100
```
I know this would give me integer division but the number should be close enough to be functional. Then I combine the condition of comparison for the BRIGHTNESS value with the value stored in nvidia_backlight/max_brightness and set it to be equal to that value if it gets bigger (which is not likely according to the formula). And so with that I had a smooth change of brightness with the Fn key. 

But then the issue hasn't stopped. The maximum brightness is capped and to some people, the screen is just not bright enough. Here's where [/COLOR]**[COLOR=#000000]colby2 [/COLOR]**[COLOR=#000000]comes to save the day with his findings.

By experimenting with the value, I obtain 143000 to be a suitable max, since when the brightness indicator gets to 94%, 1 more increment (1 more hit of Fn+Up) doesn't change the brightness anymore. That's when I know the brightness is maxed out.

And so I have for myself a smooth change in brightness with maximum range (as I like to convince myself that).

With credits to [/COLOR]**[COLOR=#000000]jonashendrickx [/COLOR]**[COLOR=#000000]and [/COLOR]**rorschachwalter **here is the code for lenovo_backlight.sh:
```
#!/bin/bashtest -f /sys/class/backlight/nvidia_backlight/brightness || exit 0
NEW_VALUE=`cat /sys/class/backlight/acpi_video0/brightness`
MAX=`cat /sys/class/backlight/nvidia_backlight/max_brightness`
let BRIGHTNESS=$NEW_VALUE*$MAX/100
if [$BRIGHTNESS -gt $MAX]; then
    BRIGHTNESS=$MAX
fi


echo -n $BRIGHTNESS > /sys/class/backlight/nvidia_backlight/brightness
```

Then after that I ran snippet from [B]colby2
[/B]
[COLOR=#000000]sudo modprobe -r nvidiabl #removes the module[/COLOR]
[COLOR=#000000]sudo modprobe nvidiabl max=143000 #actually the calculated value was 142880[/COLOR]

[COLOR=#000000]then:[/COLOR]
[COLOR=#000000]cd /sys/class/backlight/nvidia_backlight[/COLOR]
[COLOR=#000000]echo 127 | sudo tee brightness


[B][SIZE=4]HOWEVER, I still haven't been able to make this permanent, since everytime I reboot, the maximum brightness is reset and I have to do the above to get the max brightness right again. So how can I make it permanent, how do I change the setting of nvidiabl?
[/SIZE][/B][/COLOR][COLOR=#000000]

[SIZE=2]Edit2: I figured that if I wrote in /etc/modules with the line[/SIZE]
[/COLOR][COLOR=#000000][B][SIZE=4]
[/SIZE][/B][SIZE=4]nvidiabl max=143000
[/SIZE][/COLOR]
then when I reboot I can have the max brightness as I wanted. 
------
I'm using driver 3.13 nvidia with kernel 3.8.0.30-generic.
Y500, SLI GT650M with 16Gb SSD and 1Tb HDD
I can boot to Ubuntu and Window 8. But my Boot Mode is set to LEGACY MODE with UEFI FIRST and I use GRUB as default bootloader.

I just used Ubuntu approximately 24 hours, but I had tried and failed for like 3 days in a row. Thanks to these posts and contributions I was able to dual boot and enjoy Ubuntu while still having Win 8 for gaming (which to me is a BIG achievement since I'm super new to Linux)

---

### Post by colby2 on 2013-10-03
[COLOR=#DD4814][COLOR=#000000][ngthnhan93]("http://ubuntuforums.org/member.php?u=1858533"),
[/COLOR][/COLOR]

Thank you for your detailed analysis of the brightness issue. It sounds like you fixed your problem by adding that line to /etc/modules (sorry I didn't mention that in my post). 

I'm just curious: do you also have a problem keeping the brightness down when you open certain applications? For example, I like to keep my screen around 50% brightness. When I open some applications (like iceweasel or gnome settings), it resets my brightness to max, and blinds me! I have to re-run the sudo tee command to get it back down.

My other question: how are you able to edit the nvidia_backlight/brightness file with your user? When I first log in, and try to reduce the brightness, of course I can't. I have to first chown the file before changing the value. Have you found a solution to this?

Thanks!! I'm really hoping nVidia gets their act together and releases a new driver that 'just works' with brightness control. Also, have you got the 319.49 driver to work with any kernels newer than 3.9? I think I'm stuck on 3.9 until they update.

---

### Post by ngthnhan93 on 2013-10-06
> **colby2 said:**
> [COLOR=#DD4814][COLOR=#000000][ngthnhan93]("http://ubuntuforums.org/member.php?u=1858533"),
[/COLOR][/COLOR]

Thank you for your detailed analysis of the brightness issue. It sounds like you fixed your problem by adding that line to /etc/modules (sorry I didn't mention that in my post). 

I'm just curious: do you also have a problem keeping the brightness down when you open certain applications? For example, I like to keep my screen around 50% brightness. When I open some applications (like iceweasel or gnome settings), it resets my brightness to max, and blinds me! I have to re-run the sudo tee command to get it back down.

My other question: how are you able to edit the nvidia_backlight/brightness file with your user? When I first log in, and try to reduce the brightness, of course I can't. I have to first chown the file before changing the value. Have you found a solution to this?

Thanks!! I'm really hoping nVidia gets their act together and releases a new driver that 'just works' with brightness control. Also, have you got the 319.49 driver to work with any kernels newer than 3.9? I think I'm stuck on 3.9 until they update.

Yup, I also experience the problem of having brightness set back to default when I open certain applications (in my case, they are nvidia-settings and thunderbird.). However, since I have the Fn key that can adjust the brightness, it's not a problem for me. 

For the other question: I have to chown the file before I can actually modify the file. Since I'm only using 1 account, I am okay with doing that command chown once and for all.

Right now, I'm using Ubuntu 13.10 with kernel 3.11.0-11-generic and nvidia driver 331.13 (I install from [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa). Just added the repository and go to Software Center to update my driver.)  The driver works just fine for me so far. I haven't tested any graphic-heavy app yet (just updated to 13.10 this afternoon), however, before updating to Saucy, I was able to play dota 2 on my Lenovo Y500 smoothly with driver 325.15 with 3.8.0.31 kernel. Hope this information help!

---

### Post by BDNiner on 2014-04-05
Wow this is a wealth of information. Currently I have Ubuntu running off a persistent 32GB thumb drive. I have been reluctant to take the plunge on my Y400 and wiping win8 and installing Linux.

---

