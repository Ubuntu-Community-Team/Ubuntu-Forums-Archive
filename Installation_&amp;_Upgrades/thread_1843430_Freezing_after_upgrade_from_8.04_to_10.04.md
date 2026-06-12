---
title: "Freezing after upgrade from 8.04 to 10.04"
date: 2011-09-13
forum: Installation &amp; Upgrades
---

### Post by jdneate on 2011-09-13
***** see post 24 for solution ****

sorry if I am not too techy .... I finally upgraded to 10.04 today .... and as I feared, the system is freezing - sometimes almost immediately ( i only hope i can get this request for help before it freezes again)

The upgrade produced at two points (1) a warning on config settings for evolution-alam-notify may not work properly and (2) a number (5?) CUPS server errors "client error bad request".

I had to find a driver for my Samsung ML2010 printer initially which would not print - I suppose this might be a result of one of the CUPS errors.

The system now runs for varying times up to 10 mins; seems to hang if I click on any buttons; I can access OpenOffice, Evolution and Firefox/Google plus web when it is working  - but very delicate.

When it freezes there is no response to mouse clicks anywhere. I have to hold power down button. The only clue is that the disk light is flashing about once every 4 secs. 

Any suggestions as to what to look for gratefully received

---

### Post by mörgæs on 2011-09-13
Is the system stable if you run 10.04 from a live CD?

---

### Post by jdneate on 2011-09-13
Thanks for taking an interest; I ran the system for a short time from a 10.04 dvd about 6 months ago; I had to use the "nomodeset" option to get it to run but once I had sussed this, it appeared to be stable.
I haven't tried running it  since - I was hoping to upgrade from 8.04 from the internet. ( 8.04 was wonderfully stable - never crashed - hence my reluctance to upgrade in any case).
I am wondering if it could be something to do with the Gnome desk top. I have looked at the system log file and there are some error messages relating to various gnome progs; it most often hangs up when doing desktop things although it has hung at start up once.

---

### Post by jdneate on 2011-09-13
Further update - the system has now crashed  at the user log in stage upon restart.First time this has happened.

I assume the hardware is ok because 8.04 was running well and without problems but may run memory test later.

I am wondering whether I am going to have to reload the system from dvd....

---

### Post by mörgæs on 2011-09-13
That is also what I would suggest. Remember to have wired internet access while installing.

---

### Post by jdneate on 2011-09-13
Thanks for your advice. In the absence of any other suggestions I suppose I will have to install from cd and hope that works.
Since my last message, I have successfully run one pass of the memory test programme on the computer and run 10.04.1 from cd without problems.
Any idea why these systems do not upgrade from one version to the next ?
Also why do I have to select "nomodereset" to get the cd to run ? and what is nomodereset and will it affect the download from cd ?

thanks

---

### Post by mörgæs on 2011-09-13
There is an ongoing debate in the fora about fresh installs versus upgrades. My opinion is clearly in favour of a fresh install, simply because I have had too many bad experiences with failed upgrades, like yours. I wrote a little about it here:
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

If you want to know more about nomodeset, this is a good beginning:
[URL="http://ubuntuforums.org/showthread.php?t=1580857"]http://ubuntuforums.org/showthread.php?t=1613132
[/URL]

---

### Post by Olivia Wagner on 2011-09-14
Have you run all the updates of your current version of ubunto before the upgradation? Also you should keep in mind that for all the versions of Ubuntu, you should always run a supported release of Ubuntu in order to receive  security bug fixes and other related problems. And also if you are using old hardware, you should not stick  to unsupported releases to keep you system fast and it is better to install  a lighter distro like that of lubunto.

---

### Post by jdneate on 2011-09-14
Thanks for guidance so far but I am still running Ubuntu 10.04 on cd.

I did clean loads of both 10.04.01 and 10.04.03 but experienced similar freezes as with upgraded systems with both loaded systems. The 10.04.01 was from a  purchased cd; the 10.04.03 I made myself at low speed but did not do an MD5SUM check. I have followed the excellent guidance except I left an HP scanner/printer and Samsung ML2010 printer left connected through USB ports. 

In both cases the load seems to go perfectly to completion; it then asks whether to carry on running from cd or to restart the system. When I select restart the monitor initially shows messages which appear to be ok but then ends with a screen full of messages similar to ( different numbers/ addresses) ...

(2782.848874) end request: I/O error, devsr1.sector 525264

The computer hangs at this point; after a couple of minutes I force the power off to restart. Mostly ( not always) Ubuntu starts up  but freezes when Mozilla etc are selected.

It is an old computer but was running 8.04 quite happily ! In the last 3 years I have changed the hardware (1) added a dvd drive (2) added additional memory and (3) changed the monitor. The resolutions of the latter were different from the original and there were problems with the display at power up/down until I edited /etc/x11/xorg.conf and /etc/usplash.conf. I didn't change the BIOS - should I ?

I take your point about Lubuntu but wonder if I might get the same problem with that ?

---

### Post by jdneate on 2011-09-14
I forgot to mention in previous post that the cd tray opens at the point at which the system hangs during the restart during the load procedure.

---

### Post by mörgæs on 2011-09-14
There seems to be a number of error reports indicating that this bug appeared first time in 10.04, and that it is related to the CD/DVD-drive.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/577465](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/577465) (and more)


If your computer supports it, I would try booting Xubuntu 11.04 from USB.

---

### Post by jdneate on 2011-09-14
As ever, thanks for prompt reply. 

I don't think I can boot from usb on this computer - but will confirm tomorrow.

I will also investigate (1) whether it is possible to run/reboot the computer with only one cd/dvd drive connected and (2) confirm the integrity of the data on the Ubuntu discs.

Any reason why you recommended xubuntu ?

I have had more than enough of computers for today - so am shutting the system down now to go to bed ..... good night !

---

### Post by jdneate on 2011-09-15
I was running 10.04.03 from cd last night; I then shut the system down after my last post.

When I selected the shutdown option shutdown proceeded as expected and the cd was ejected.

The computer just hung at this point and did not power down; the  monitor showed a screen full of I/O error messages as previous posts.

If there is an issue with some cd/dvd drives puzzled why it should have affected my first attempt at the upgrade process which did not use these drives.

For information, when do a clean install how does Ubuntu determine computer configuration, display driver,  display resolution and other parameters? When reload the system where is this information held ?

What is role of BIOS, MBR, and Grub loader in storing/getting this info ? Or where can I find this info in understandable form. 

I seem to have read a lot of bumf on Ubuntu but yet to find this spelled out

---

### Post by mörgæs on 2011-09-15
I don't think that you need more theory, but experiments.

As before, try Xubuntu 11.04, preferably from USB but a CD test is also interesting, if USB does not work.
Try upgrading the BIOS and / or disabling one or more drives here.

Xubuntu is my favourite simply because it is way more stable than Ubuntu and works on more hardware. When it runs, you can consider other Buntus.

---

### Post by jdneate on 2011-09-15
As ever thanks for comments .....

I have been doing plenty of practical today ..... but without success. Plenty of reloads. I have been exchanging hardware - cd / dvd drives. The only thing I have found so far is that after the error messages, if I closed the cd drive door and pressed enter then the computer did shut down.

The existing cd/dvd drives are not always repeatable - the boot cd does not always display the language/options selction screen when ctrl F pressed  at the start of the boot.

I am now trying a pair of new dvd drives and will load off these and see how that goes.


I have just acquired a further pair of dvd drives - and am running cd system off these. Obviously I am still using the same scsi controller on the motherboard.

I am about to reload 10.04.03 ....... again

---

### Post by jdneate on 2011-09-15
Same problem with replacement optical drives as before.

I think I have an alternative display driver; I don't know if it is worth trying this? 

Otherwise, I will have a look at BIOS options and xubuntu tomorrow.

Can I use Evolution email with Xubuntu ?

---

### Post by mörgæs on 2011-09-15
I don't think it pays to swap hardware, since 8.04 worked well. 

Yes, you can install all the applications you are used to in Xubuntu.

---

### Post by jdneate on 2011-09-16
I have tried everything I can think of now - without success.
Today I have tried Ubunutu 10.04.03 and 11.04 and Xubuntu 10.04 and 11.04. They all run fine from the cd but will not install to produce a working system.

I changed the BIOS settings this morning; they were for booting in order cdrom,cdrom, hard disk. They were changed to cdrom, hard disk, floppy disk. There is no option to boot from usb.

I noticed that when booting Ubuntu 10.04 and XUbuntu 10.04 at the initial load screen it stilled showed the option of loading from two cdroms. But Ubuntu 11.04 and Xubuntu 11.04 only showed a single cdrom option.

Ubuntu 10.04 and Xubuntu 10.04 both showed I/O error messages when the restart was pressed after the load and the computer was powering itself down, whereas neither  11.04s showed errors at this point.

Ubuntu 11.04 seemed to work ( not perfectly) before I downloaded all the updates. I tried two loads of 11.04 and the faults on the two final systems were not identical. The first time I got the purple wall paper screen and movable cursor but no sign of a system. The second time I got the drums, logged in, the music and purplish  wall paper but no cursor. 

Xub 10.4 would not restart after installation; 11.04 got to login display; I selected myself but the system did not ask for my password; the cursor could be moved but I could not select other.

It seems like a loading/booting problem but don't see where ?

---

### Post by jdneate on 2011-09-17
I feel a bit brain dead.

This morning i found that the loaded version of Xubuntu 11.04 would run for a short time but crashed soon after starting Mozilla ..... so having been unable to find any ubuntu or xubuntu that will load and run I thought I would concentrate back on Ubuntu 10.04.03.

From the number of reloads and restart I have done I have found that 10.04.03 freezes at different points - somtimes at log in and once or twice I have had it running and it has crashed running Mozilla. When it crashes the mouse freezes and the clock stops updating.

I have to use NOMODESET option to run from the cd so I thought I would include this in the GRUB configuration as recommended in one of the Forum posts;  so I loaded the system from cd but before restart I reran the cd and to edit the configuration file.

When I ran the sudo update-grub command the following came back ....

/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

Any help gratefully received - this is my third day trying to get a running Ubuntu and i am running out of ideas

---

### Post by mörgæs on 2011-09-17
If you don't start Firefox, for how long time is Xubuntu 11.04 stable?

While experimenting you don't need to add Nomodeset permanently to Grub. The boot screen gives you the option of adding it for the particular session.

---

### Post by MAFoElffen on 2011-09-17
> **jdneate said:**
> I forgot to mention in previous post that the cd tray opens at the point at which the system hangs during the restart during the load procedure.
May I be of assistance on this?  There is differences in the way graphics works (Through Grub/Kernel?Xorg) since version 8.04 that have to do with KMS.  Once you can work these these changes in, you should have few future graphics problems with current and future releases.

Please use the first 3 posts of this sticky to use as refrence:
**[B]Sticky:**[/B]                                      [COLOR=#008C00]**[all variants]**[/COLOR]                          [Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535") 

I have a few questions that should help mörgæs and I to assist you.

Can you get to a Grub Boot Menu?  If so (press shift key repeatedly during boot), will it boot in rescue mode?
Is ubuntu the only opeating system installed on this PC?  
How much memory is installed on this PC?

I am assuming, even though you haven't mentioned it, that you are using a "nomodeset" boot option because you have  an NVidia chipset for video?

To help provide some of this info, please post the output to:
```

lspci -v | grep VGA

```And then boot on a livecd (using a nomodeset boot option ( main menu > F6/Boot Options > select nomodeset > escape > try ) and when it boots, mount the partition that your install is on to post the /var/log/xorg.o.log that is from your install.

That should be enough to get us started.

---

### Post by rolfisrolf on 2011-09-18
I upgraded from 10.10 to 11.04 last night and I am getting a frozen white screen about every 10 minutes. I have to reboot via the power button, get the white screen again, reboot, white screen, eventually it lets me in, but not for long. I might try a fresh install as this is far too annoying, but just to put it out there, has anyone else had it this bad?

---

### Post by mörgæs on 2011-09-18
> **rolfisrolf said:**
> I might try a fresh install as this is far too annoying

That is a good idea. More advice here:
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)
If that does not work, please open a new thread.

---

### Post by jdneate on 2011-09-18
:D
Firstly - thanks to everybody ( especially Morgraes and now Mafollffen) who have taken an interest and offered guidance.

Now the good news - about 3 hrs ago I installed Ubuntu 10.04.03. The system has been running Mozilla and some games since then and has not frozen; I have restarted it successfully twice; so it looks extremely promising. 

It needs tuning now such as incorporating NOMODESET in the GRUB start up, display resolution, getting printing, email to address etc etc which I can address in time. ( if I need assistance I will start separate threads for these).

How did I get it going ?

Previously all the Ubuntu/Xubuntu systems ran fine on the livecd but froze at log in or within 5 minutes after installation. I spent yesterday re-reading Morgraes' excellent reply and all the associated links.

On the Ubuntu page on how to load the system, it said if the livecd  gave problems then try the Alternate downloads.

So I burned an Alternate cd and installed from this - and it works fine.

The Alternate cd asks the same questions as those asked by the livecd at installation. But in addition it asked if I wanted to install the GRUB loader into the MBR - which I did because I run a single operating system. Could this have been the answer ? 

I will answer Mafollffen's questions later on.

I was going to close the thread but I notice that rolfisrolf has a problem. Should I leave it open ?

---

### Post by jdneate on 2011-09-18
In response to MAFoElffen's questions if you want to consider the (solved?) problem further

1)   jdn@jdneate:~$ lspci -v | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX200] (rev b2)

2)   Pressing shift did not get me into the GRUB Boot Menu when booting from the liveCD. I haven't tried it on the working system

3)   I only have a single operating system installed ( Ubuntu 10.04.03) and the disk is partitioned only to the extent required by this operating system.

4)   The computer has 1.5  MB of RAM

5)   I haven't tried 

"And then boot on a livecd (using a nomodeset boot option ( main menu > F6/Boot Options > select nomodeset > escape > try ) and when it boots, mount the partition that your install is on to post the /var/log/xorg.o.log that is from your install."

Thanks for taking an interest !

---

### Post by MAFoElffen on 2011-09-18
> **jdneate said:**
> In response to MAFoElffen's questions if you want to consider the (solved?) problem further

1)   jdn@jdneate:~$ lspci -v | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX200] (rev b2)

2)   Pressing shift did not get me into the GRUB Boot Menu when booting from the liveCD. I haven't tried it on the working system

3)   I only have a single operating system installed ( Ubuntu 10.04.03) and the disk is partitioned only to the extent required by this operating system.

4)   The computer has 1.5  MB of RAM

5)   I haven't tried 

"And then boot on a livecd (using a nomodeset boot option ( main menu > F6/Boot Options > select nomodeset > escape > try ) and when it boots, mount the partition that your install is on to post the /var/log/xorg.o.log that is from your install."

Thanks for taking an interest !
On #2. that would have been somethig your want to try as you try to boot from the install on your hard disk...  If you can get to a Grub Boot menu from your install, you have gotten passed a few things (ruled out some things) and have some options to try.

"nomodeset" is a temporary NVidia GPU fix, usually added in until a video card driver is installed. Once the driver is installed, then that kernel boot switch should nolonger be needed.  nomodeset tells NVidia GPU to use VESA mode settings, which is something it doesn't do from it's native mode.  It gets a little confused without it, without an NVidia driver installed to use it's native modes.

With an Nvidia GPU, usually a fresh install would mean install, reboot, boot rescuemode to get to the Additional Drivers applet to install the respective NVidia driver (or to do it from the command line.  With NVidia GPU's, 75% of the time, getting a purple screen on boot up usually just means that either a driver is not loaded or that the wrong driver is loaded.

Once a correct driver driver is loaded, there may be some other tweaks or workarounds needed, but usually loading the correct driver is all that's needed.  I believe that the driver that will show up for your GPU in the additional driver app will be the nvidia-96 driver.

---

### Post by jdneate on 2011-09-18
Hi MAFoElffen

I tried nvidia-96 driver; but I have a problem with screen resolution - basically the monitor is not recognised; I can't select an appropriate resolution for the displays which are too large to fit the screen. It is annoying but after the last 4 days I am  grateful to have a robust system and I haven't had time to investigate.

The nvidia-96  made the screen resolution issue worse so I have removed the driver for the time being. It demonstrates the system is robust; having loaded and removed drivers it hasn't crashed. 

I need to tell the system the permitted screen resolutions ...... do you know how/where to do this ? .... I don't want to take up any more of your time but if you knew I would be grateful ; if not I will start reading the literature etc.

Thanks

---

### Post by MAFoElffen on 2011-09-18
> **jdneate said:**
> Hi MAFoElffen

I tried nvidia-96 driver; but I have a problem with screen resolution - basically the monitor is not recognised; I can't select an appropriate resolution for the displays which are too large to fit the screen. It is annoying but after the last 4 days I am  grateful to have a robust system and I haven't had time to investigate.

The nvidia-96  made the screen resolution issue worse so I have removed the driver for the time being. It demonstrates the system is robust; having loaded and removed drivers it hasn't crashed. 

I need to tell the system the permitted screen resolutions ...... do you know how/where to do this ? .... I don't want to take up any more of your time but if you knew I would be grateful ; if not I will start reading the literature etc.

Thanks
I have 2 test boxes that use older legacy NVidia GPU's like yours... (They are running dev versions of Ubuntu)  The best I got out of them using Ubuntu packaged drivers is using the Nvidia/nouveau Experimental 3D video driver.  It would show up in your Additional Drivers appplet if you were running 11.04, but you are not...  

Even if you are not using an NVidia driver for your NVidia GPU, you can create an xorg.conf to tell it to use an Xorg VESA or Nouveau driver... as it's driver and not have to use nomodeset as a boot switch --OR-- use nomodeset )and create xrandr profile to set your resolution)... 

As for setting resolutions... If resolutions are not showing up in NVidia Settings applet (nvidia-settings) or in the Monitor Setting applet (if you are not using aan NVidia Driver -> nouveau or vesa drivers) Then, if you install hwinfo:
```

sudo apt-get install hwinfo

```then run 
```

sudo hwinfo --monitor
sudo hwinfo --framebuffer

```To check for a resolution that both your GPU and monitor shares and manually set these in your Xorg.conf file.  If your system does not have an xorg.conf fle present, one can be generated to do this. If this is something your what to try, just tell me and I'll give your instructions.

If it's an older monitor and does not store that EDID data, driver's also get confuse on what resolutions to use with it.  I have work-arounds for that also.

---

### Post by jdneate on 2011-09-18
Again thanks - I will investigate in the next few days and let you know the outcome.

---

### Post by rolfisrolf on 2011-09-18
> **mörgæs said:**
> That is a good idea. More advice here:
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)
If that does not work, please open a new thread.

Just a quick update - I am convinced now that it is NOT an Ubuntu problem but rather an issue with my laptop's screen as it happened when I was attempting to do a fresh install, and I get the white screen as I turn on my computer. It's a Dell that's about a year old, and I bought it while in China (which I mention because of the rumours that the Chinese computer dealers replace parts of computers with cheaper parts, no idea if it is true or not). Thanks for reading.

---

### Post by jdneate on 2011-09-19
hi RolfisRolf

I know a few years ago when I was using Windows I had an unstable system; I found it by running the memory test on the Ubuntu liveCD. I gave up Windows at that point and went to Ubuntu.
I was extremely happy with 8.04 and now I think I will be the same with 10.04 once I get my resolution issue resolved.

I will close this thread once the resolution issue is finished with.

Best of luck with your laptop

---

### Post by jdneate on 2011-09-19
Hi MAFoEllfen

1  I printed out the display/driver configurations ....
 ----------------------------------------------------------------------------
jdn@jdneate:~$ sudo hwinfo--monitor                                                                                  26: None 00.0: 10000 Monitor
  [Created at fb.71]
  Unique ID: rdCR.EY_qmtb9YY0
  Hardware Class: monitor
  Model: "Generic Monitor"
  Vendor: "Generic"
  Device: "Monitor"
  Resolution: 640x480@60Hz
  Driver Info #0:
    Max. Resolution: 640x480
    Vert. Sync Range: 50-70 Hz
    Hor. Sync Range: 31-33 kHz
  Config Status: cfg=new, avail=yes, need=no, active=unknown

  jdn@jdneate:~$ sudo hwinfo --framebuffer
                                                                                         02: None 00.0: 11001 VESA Framebuffer
  [Created at bios.464]
  Unique ID: rdCR.9X2tz5+Fif6
  Hardware Class: framebuffer
  Model: "NVidia NV11 (GeForce2) Board"
  Vendor: "NVidia Corporation"
  Device: "NV11 (GeForce2) Board"
  SubVendor: "NVidia"
  SubDevice: 
  Revision: "Chip Rev B2"
  Memory Size: 32 MB
  Memory Range: 0xe0000000-0xe1ffffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown
jdn@jdneate:~$ 
-------------------------------------------------------------------------------
2  The display I am trying to use has max resolution of 1024x768 at 75Hz.
Horizontal frequency 31 - 60 kHz
Vertical frequency 60 - 75 Hz

--------------------------------------------------------------------------------

3  I listed files in /etc/X11/ but no xorg.conf shown. So I attempted to generate one without success 

-------------------------------------------------------------------------------
jdn@jdneate:~$ sudo Xorg -configure
[sudo] password for jdn: 

Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 

 ddxSigGiveUp: Closing log
jdn@jdneate:~$ 
------------------------------------------------------------------------------------

I am out of my depth ..... your previous offer of help welcomed !

---

### Post by jdneate on 2011-09-23
I still haven't got the display resolution sorted out after 3 days - so I have decided to close this thread and open a new one ..... thanks to those contributed to this thread.

---

### Post by mörgæs on 2011-09-23
If the topic is unchanged, please keep writing here rather than opening a new thread. It is a great help to people helping you that they can see the previous advice.

---

### Post by jdneate on 2011-09-23
Hi    I think the topic has changed because it has changed from getting Ubuntu to run to changing the monitor resolution.

If you want to follow new thread the title is ....

[ubuntu] 10.04 unable to set resolutions on non-EDID monitor

---

