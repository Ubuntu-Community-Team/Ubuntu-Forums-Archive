---
title: "Install/Operation Problems - Computer Crashes after Install Ubuntu 14.10"
date: 2015-05-21
forum: Installation &amp; Upgrades
---

### Post by Chris_Sol_Gully on 2015-05-21
SOLVED! 
Update: Thanks to all who helped me out with this. The machine is running great now, stable and crash free for several days now. Below are steps that helped fix this, but main issue was related to NVIDIA drivers.

1) The main fix--> NVIDIA adapter updated and new/correct drivers installed. From terminal, enter: "sudo apt-get install nvidia-current"  
Again, thanks to SeijiSensei for that. OnCe updated and rebooted, seems to function like it's supposed to. Runs great!

2) Noticed that the little rubber spacers on bottom rear of this old laptop were missing and there was insufficient air space which was causing overheating and intermittent crashes. This HP tends to run hot and has crappy fan and venting to begin with... so this was pushing it over the edge. Temporarily have propped it up but plan to fabricate some new larger spacers and epoxy them where these little spacer feet should be. Will also clean fan and possibly dremel/cut some new larger openings so fan can breath better. Will also use laptop cooling stand when using its at home on desk. 

3) Have updated various other software just to make sure everything is up to date. For now sticking with Ubuntu 14.10 since seems to run fine now, will consider switching to 14.04LTS in future. 

So this crappy old laptop seems to have a new lease on life as a useful machine. Next steps are buy new battery, install Wine and see if can run SketchUp. 
Note: Posts edited to remove embedded images per oldfred's request to speed up viewing. Images now attached. Thanks again.
Chris

Original post:
Hello, new to forum. Used the search and viewed FAQ's but didn't see same scenario I'm dealing with so figured I'd post and ask for advice...

I'm an architect (building not software) with average computer skills. I've been wanting to switch to Linux (would have to run Wine for most of my arch related software) and figured my first project would be to convert an old laptop to run Ubuntu. This is a 10 year old throw-away HP Pavilion DV9500 laptop my wife had that ran Windows 32 bit Vista, horrible OS. The machine was barely functioning and super slow. However, the screen and speakers are relatively nice and it has a Turion 64 x2 1900MHz & upgraded to ~3.6MB RAM, which according to what I've read should be plenty to run Ubuntu 64 bit. (Was this my first mistake, installing Ubuntu 64 bit instead of 32?). I created a boot-from-USB and proceeded to install Ubuntu 14.10 and wiped out Vista completely since it's an older laptop w/ ~ 114 GiB harddrive (mostly free now) and wanted to maximize efficiency. 

From the little bit of functioning Ubuntu experience that I have gotten so far, I can see why people fall in love with Linux/Ubuntu etc and won't go back to Windows. It seems really sweet and the laptop runs way faster than it ever did when it's working. But... It won't work for very long and starts bogging down and freezing up and then crashes. So I really haven't been able to play with it or learn much so far. But at this point I'd like to move this forward and troubleshoot it, and either junk the laptop and get something that works, or preferably fix this laptop to have as an extra toy. I don't want to convert my other main work laptop to dual-boot Linux until I have a better handle on things and gain some more confidence in Linux. 

The install seemed to go well enough, but booted inconsistently and crashed off and on. Seemed to get a bit more consistent and work better after booting several times, including in safe-mode, but I really didn't change any configurations (although it did automatically update) and started running a bit smoother. But it's still not a functional laptop. It freezes up and crashes consistently. Using the 'search' button really agitates it and usually crashes shortly thereafter, while displaying odd pixalated screen graphics in variety of colors. Not sure if this is a processor issue, a graphics card issue, driver issues (I still can't quite understand how drivers work in Linux vs Windows). But there seems to be some sort of fundamental incompatibility in this application. Would it be better to run Mint, Manjaro or some other alternate version?

It won't always boot correctly from GRUB but when I then restart it, it usually will. Not sure why inconsistent. When it does start Ubuntu, it gives me several error messages, first during boot and then once running Ubuntu from the desktop. I ran some basic memory tests at boot and it passes them all so doesn't seem to be corrupt hard disk. Deciphering these errors is beyond my current skill set so would love some advice on how to go about fixing this. Here are some images that may help show what the issues are:










Anyways, thanks for reading along and I would be super appreciative of any help/advice in getting this sorted out. Hopefully will be off and running with Linux Ubuntu in near future.
Thank you!
Gully

---

### Post by oldfred on 2015-05-21
Please do not post screen shots in line. Attach them with the paperclip icon in the Advanced editor. Not all users have high speed Internet and you bog down their system.

I am running Ubuntu on my 2006 Toshiba with 1.5GB of RAM and use 64 bit version. But systems that old typically have limited video processors. On my system full Ubuntu runs so slow as to be unusable. But I install fall back which is similar to the older versions of Ubuntu with gnome2. When gnome3 came out Ubuntu switched to Unity, but Unity needs a newer system with good processor and a newer video card/chip.

I have fallback on my system with 12.04 and expect a new laptop before 12.04 expires. :)
Have not tried fallback on newer versions. Others often suggest Lubuntu or Xubuntu.

You have have an advanced install with LVM which I will not used as it is more complicated. But if you want full drive encryption, you have to use it. There have been some other posts on the encrypted swap mount issue, so it may be a bug, but have not followed that issue.

I think your issues are your limited video because it is an older system and use of LVM.
If just starting out better to use a standard partitioned install.

 Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)

      
 [https://wiki.gnome.org/action/show/Projects/GnomeFlashback?action=show&redirect=GnomeFlashback](https://wiki.gnome.org/action/show/Projects/GnomeFlashback?action=show&redirect=GnomeFlashback)
[http://www.omgubuntu.co.uk/2014/04/ubuntu-14-04-classic-gnome-flashback-session](http://www.omgubuntu.co.uk/2014/04/ubuntu-14-04-classic-gnome-flashback-session)
Flashback/fallback in 14.04 Kansasnoob
Installing the package 'gnome-session-flashback' does exactly the same thing as installing the package 'gnome-panel'.
[http://ubuntuforums.org/showthread.php?t=2220264](http://ubuntuforums.org/showthread.php?t=2220264)
[http://ubuntuforums.org/showthread.php?t=2090021&p=12994477#post12994477](http://ubuntuforums.org/showthread.php?t=2090021&p=12994477#post12994477)

---

### Post by Chris_Sol_Gully on 2015-05-21
Thanks for the repy, oldfred. I will read up on Fall Back and LVM. 

Also, roger that on posting inline images; I'll post images more sparingly and mostly attach them instead. 
Thanks!

---

### Post by grahammechanical on 2015-05-21
One of your images is showing 

> GPU lockup - switching to software fbcon

with further references to "nouveau" which is the open source video driver for Nvidia video adapters. I ran Ubuntu 14.10 on Nouveau all through its 26 week development period without getting that problem. Then when 14.10 was released I switched to the development release of 15.04 and sometime during its 26 week development I would get GPU lockup with the whole system freezing. This would happen when if I tried selecting large blocks of text in Libreoffice.

The solution? I activated the Nvidia Proprietary video driver. I have an Nvidia GT 220, by the way and I am now running the development version of 15.10 and I still get GPU lock up with Nouveau.

We change video drivers by going to System Settings>Software & Updates>Additional drivers tab. We need to be connected to the internet and allow the utility time to find drivers for our video adapter. You may see an Nvidia driver labelled "legacy." That may be the one to use as Nvidia has an habit of dropping support from its drivers for older hardware.

The latest Nvidia drivers do not support my GT 220. All Nvidia drivers have a version number that get higher the newer the driver. If you need an older driver than those in Additioanl Drivers you will find some legacy drivers in the Ubuntu Software Centre. Search for Nvidia and look for lower numbered versions.

That might solve one issue. Oh, by the way, when we get that "Sorry, Ubuntu has experienced an internal error" message we can untick the box to send a report and then click Details and we will get a bit more information as to what exactly has crashed. Which might be useful information.

Do you really need LVM? A re-install without might get rid of that message.

Regards.

---

### Post by Chris_Sol_Gully on 2015-05-21
Very interesting, sounds like may have a similar issue with Nvidia driver, I'll look for 'legacy' &/or other drivers relating to my graphics card and be sure to update. Thank you

---

### Post by Chris_Sol_Gully on 2015-05-22
Edit: deleted embedded image, consolidated above as attached.

---

### Post by SeijiSensei on 2015-05-22
I suggest trying a more "lightweight" flavor of Ubuntu like [Lubuntu]("http://lubuntu.net/").  You can boot from its installation disk and choose "Try Ubuntu" to see what it looks like.  It will be slow if it is running off the CD.  You can get better performance if you have a spare USB thumb drive around, and your machine supports booting off a USB device.  Use the [Startup Disk Creator]("https://help.ubuntu.com/community/Installation/FromUSBStick") to create a bootable USB drive and boot from that.

If you do have an NVIDIA adapter, you can install the proprietary driver by running the "Driver Manager" or "Additional Drivers" application. (It has different names in different releases.)  It will scan your hardware and install any matching proprietary drivers.  If you're comfortable typing commands, entering "sudo apt-get install nvidia-current" at the prompt will accomplish the same task.

Don't choose the LVM option if offered, and I'd avoid full-disk encryption as well.  Just start with a vanilla installation that uses the entire disk drive for Ubuntu.

Finally, as a new user, I strongly recommend you use a version of Ubuntu with long-term support like 14.04LTS.  14.10 will reach its "[end-of-life]("https://wiki.ubuntu.com/Releases")" in July.  LTS releases are supported for much longer periods of time; 14.04LTS will be supported until April, 2019.

---

### Post by oldfred on 2015-05-22
Please attach screen shots. And best if you go back and delete in line screen shots & reattach.

       If you use the advanced editor, you can use the paperclip icon to attach screenshots. Post #4
[http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

---

### Post by Chris_Sol_Gully on 2015-05-22
> **SeijiSensei said:**
> I suggest trying a more "lightweight" flavor of Ubuntu like [Lubuntu]("http://lubuntu.net/").  You can boot from its installation disk and choose "Try Ubuntu" to see what it looks like.  It will be slow if it is running off the CD.  You can get better performance if you have a spare USB thumb drive around, and your machine supports booting off a USB device.  Use the [Startup Disk Creator]("https://help.ubuntu.com/community/Installation/FromUSBStick") to create a bootable USB drive and boot from that.

If you do have an NVIDIA adapter, you can install the proprietary driver by running the "Driver Manager" or "Additional Drivers" application. (It has different names in different releases.)  It will scan your hardware and install any matching proprietary drivers.  If you're comfortable typing commands, entering "sudo apt-get install nvidia-current" at the prompt will accomplish the same task.

Don't choose the LVM option if offered, and I'd avoid full-disk encryption as well.  Just start with a vanilla installation that uses the entire disk drive for Ubuntu.

Finally, as a new user, I strongly recommend you use a version of Ubuntu with long-term support like 14.04LTS.  14.10 will reach its "[end-of-life]("https://wiki.ubuntu.com/Releases")" in July.  LTS releases are supported for much longer periods of time; 14.04LTS will be supported until April, 2019.
Okay, thanks Sensei, good to know and I will work on the driver manager stuff this weekend. Will consider reinstall with Lubuntu, will start using a supported version and will ditch the full-disk encryption. I didn't realize there were so many options and had just went with the default download from the Ubuntu website. I'll google these other options and figure out where to download. Hopefully will be up and running this weekend once have a chance to play around some more. Thanks you!

---

### Post by Chris_Sol_Gully on 2015-05-22
> **oldfred said:**
> Please attach screen shots. And best if you go back and delete in line screen shots & reattach.

       If you use the advanced editor, you can use the paperclip icon to attach screenshots. Post #4
[http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)
Okay I'll use the paperclip/attach instead. Didnt even see that and just used the image insert option.
Thank you!

---

### Post by Chris_Sol_Gully on 2015-05-29
My install and operational issues with Ubuntu 14.10 running on old laptop are SOLVED! Really loving Linux/Ubuntu now that I can fully use it. See top post #1 for update & more details. Thanks again guys!

---

### Post by Bucky Ball on 2015-05-29
Please see the second link in my signature to mark the thread as 'solved' correctly. Thanks and good luck. ;)

---

