---
title: "Ubuntu Nvidia 304 driver not working"
date: 2015-04-25
forum: Installation &amp; Upgrades
---

### Post by nilandj-nilandsplace on 2015-04-25
I have spent 3 weeks worth posts trying to get the nvidia drivers to work. I can now do the install blindfolded with one hand tied behind my back in every method.
This all went to hell when my motherboard blew up. I am not joking! I replaced 13 capacitors, 2 SATA connectors, 2 sticks of Corsair 1 gig memory and a hard drive (tetra byte) after an ice storm here in the south when the power came back on. The motherboard is repaired and tested.
The Motherboard is a Intel D865GLC (32-bit) with 4 gig's of corsair matched memory and a pentium 4 CPU 3.00GHz × 2. The hard drive is one of the better Western Digital 1 teta-byte, SATA with cache. I can't remember if it was the highest or 2nd highest grade. I know I paid a premium for it.
Any way I had the bright Idea of installing 12.04.5 LTS over my 12.04 LTS and nothing worked since. I ended up purging everything, reinstalling 12.04 and reloading my home directory from backup. I am back to the linux-3.2.0-80-generic kernel. Seems once you install 12.04.5 you are stuck with 3.13 something with no more updates.
_The nivida driver installs without any errors_, but when my gnome desktop loads, (system settings >> details) says Graphics: Unknown and Experience: Fallback. The Nouveau drivers are purged and blacklisted. the xorg config is correct as far as I can tell. Without the drivers working things like Firefox or Chrome are slooow to start and run as I have no GPU acceleration on my GeForce 6200 AGP x8 video card. Nouveau is a little better but only marginally as it does not use the 256 mega byte memory on the card. setting the BIOS for 256 MB video does not help. Using 64 MB is just the same and gives me more memory for the system (3.3MB as compared to 2.9MB). Installing from Terminal boot or Synaptic make no difference and the Extra drivers in the system panel does not any longer seek the right drivers. It use to say Nvidia...version (304) [recommended], but after this last install for terminal (i.e. cntr+alt+F2) it says this driver is activated and currently in use, BUT it is not? so why is Graphics Unknown and Fallback?
I do not like the Unity desktop at all, it is too hard to access things. So I use Gnome classic with no effects. I also set up a different User/desktop to test in, but is all the same as far as video goes.

Also I have multiple folders under file system for home like
 /home/james/...Desktop, Documents, Music, pictures, .config files and so forth (has files)
/home/...Desktop, Documents, Music, pictures, .config files and so forth (empty except for .config files)
/root/...Desktop, Documents, Music, pictures, .config files and so forth (empty except for .config files)
The .config file are not the same or equal in the different directories?  _I don't know if this is part of the problem?_
I don't have enough infor to know what should exist in each folders? I can't find a list of what generic file should be there? So I have not deleted anything. This seem to come about in the Ubuntu 12.04 LTS reinstall. I am scared to update to version 14.04 untill they are done fixing it and I am too pressed for time as it is to workout bugs. It is already updated twice (14.04.1 and 14.04.2).

I have attached data files and some screenshots

I hate to say it, but I am now using Windows again[IMG]http://ubuntuforums.org/images/icons/icon8.png[/IMG], GOD help me![IMG]http://ubuntuforums.org/images/icons/icon9.png[/IMG] I friken hate windows crap!!! [IMG]http://ubuntuforums.org/images/icons/icon13.png[/IMG]

---

### Post by ubfan1 on 2015-04-25
Did you try the xorg-edgers version of the driver?
[http://www.ubuntuupdates.org/package/xorg-edgers/vivid/main/base/nvidia-graphics-drivers-304](http://www.ubuntuupdates.org/package/xorg-edgers/vivid/main/base/nvidia-graphics-drivers-304)
I found that worked better for the 304 drivers on an old system I no longer have.
Add their repository, update, then add nvidia-current (I think, or just the explicit 304 latest driver, which may be one version number higher than the one in the standard repos). NO CUT and PASTE on the ppa line since an extra space was added after the colon to squash the emoticon nonsense).
> sudo add-apt-repository ppa: xorg-edgers/ppa 
sudo apt-get update
sudo apt-get install <package name>

---

### Post by grahammechanical on 2015-04-25
I would like to make a couple of points.

1) An fresh install Ubuntu 12.04.5 will come with the hardware enablement stack that is in 14.04 and that includes the Linux kernel 3.13 which is supported until 12.04 reaches end of life in April 2017.

> The 14.04 HWE stack will remain supported in 12.04 for the life of the 12.04 LTS release.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

2) The manufacturers of proprietary video drivers often drop support for what they consider obsolete video cards. Newer drivers such as nvidia 304 may not have support for that video adapter. You may have to look in software centre for an older (legacy) driver. The Nvidia web site shows the newest driver supporting ypour adapter is 304

[http://www.nvidia.co.uk/Download/Find.aspx?lang=en-uk](http://www.nvidia.co.uk/Download/Find.aspx?lang=en-uk)

3) It is normal for Details on 12.04 to say Graphic Unknown. Things are a lot better in later versions of Ubuntu

4) It is common to run in a fall back mode if there are conflicts with proprietary video drivers

5) I am not sure that purging nouveau is a good idea as it is the default video driver. Without nouveau installed and without a proprietary video driver installed the system has no choice but to run in some kind of fall back mode, even fail safe mode.

6) with that video adapter you would be using Unity 2D. 

7) If we re-install Ubuntu over an existing install without formatting the partition we do not lose data in our /home partition but then again we do not start with fresh configuration files.

My advice would be to backup your data and fresh install of 12.04.5 and stay with it until it reaches end of life in April 2017. I do not think that machine will run 14.04. You will have to investigate Xubuntu or Lubuntu as an alternative.

Regards.

P.S. The software centre has nvidia 96 and nvidia 173. Either of those might support your video card.

---

### Post by nilandj-nilandsplace on 2015-04-30
Hello 
First thanks for the fast reply. Sorry for not getting back right away, I was unable to get through the SSO/Ubuntu one login for a while. The Ubuntu one always gives me fits. Sometimes I get the bad bot thing for awhile.
Anyway I tried the xorg-edgers update, but no joy. I don't know why but I cannot revert back to the nouveau drivers now, well I can but it will no longer load my Dell ST2220M monitor 22" 1920x1080 resolution any longer. Maybe because of getting burned so many times by Microsoft I am not willing to try Ubuntu 14.xx yet.
If I could afford it right now I would give away this computer to someone in need and join the new age of 64-bit processors. My biggest gripe is without the GPU acceleration my web pages load real slow in firefox. That an I need to run multiple sites for my web stores. I use Gnome cause the new unity desktop limits me in screen switching. I like my dozen at the bottom and I hate the menu in Unity. I bring it up because I wonder if I have a problem because of Gnome? Nvidia 96 and 173 will not install any more since moving to 12.04, and I don't have much time of late to figure it out. Backup and reinstall...yikes 465 gig's of data. At this point I suspect Nvidia 304.125 just does not want to play nice with something any more, and it seems I can only get a graphic screen with Nvidia. Hard to view web pages in tty. I have multiple configuration files in multiple directories, but witch ones are being used? Any Ideas?
Thanks again
James Niland
nilandsplace.com

---

