---
title: "How best to go from 8.1 to Ubuntu dual boot Win 10"
date: 2015-10-21
forum: Installation &amp; Upgrades
---

### Post by Odyssey1942 on 2015-10-21
I have a new Dell XPS 8700 with Win 8.1 Home edition installed, 1 TB hdd.

I want to update to Windows 10 and to have a dual boot option to Ubunutu.

Ubunutu is my preferred platform, but there are still a few things that seem to be much easier on Windows (home security camera systems, etc.) and some hardware that the producer just has not yet adapted to Linux. Even if I am mistaken on this, I have a valid Windows 8.1 license which I can upgrade to 10 without cost, so want to keep it available.

Boot up should default to Ubunutu.

I have a 120GB SSD that I would like to use for the system/s, ideally for both OS's, but no big deal if Win has to boot from the hdd

So seeking general guidance and the order in which things should be done.

Starting with Windows 8.1, are there updates to 8.1 and related that should be done before upgrading to 10?

Should 8.1 be installed on the SSD before upgrading to 10? I have ordered the 8.1 install/re-install disks from Dell and they should be here in a few days if needed for this exercise.

Or should Ubunutu be installed first on the SSD?

Are there (Windows related) BIOS issues when installing dual booting? I am thinking of UEFI (or others that I do not know the name of)?

Finally my old computer runs Ubunutu 12.04 because: (1) LTS, (2) I can use the GUI that was in place before (Classic?) and (3) lack of (the considerable) time I need to upgrade. Anyway it is now time to update Ubunutu and the question is to what? I want the latest LTS that I can use the Classic GUI on.

So I am putting all the issues I can think of out there for guidance on how the above might best be done, and am grateful for any advice.

---

### Post by grahammechanical on 2015-10-21
I am not completely clear on the situation.

1) Do you have an existing dual boot between Windows 8.1 and Ubuntu? There are several threads on this forum where users of a dual boot system have upgraded to Windows 10 and found that the dual boot is then broken.

2) Is the machine without any OS? Or are you intending to fresh install both Windows and Ubuntu and so wipe whatever is on the disk? There are threads on this forum where uses have installed Windows after installing Ubuntu and its breaks the loading of Ubuntu.

I would say, install Windows 8.1 first; upgrade to Windows 10 and then install Ubuntu. But you need to take precautions. I cannot give best practice advice on upgrading a Microsoft OS.

a) Use Windows utilities to defrag Windows. Do it more than once and check that Windows loads after each defrag.
b) Use Windows utilities to create unallocated space on the disk for Ubuntu. Check that Windows loads after the re-size operations.
c) Have a means to restore/reinstall Windows.
d) Read and follow this guide when it comes to installing Ubuntu.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

The latest LTS is 14.04. There will not be another until 16.04 is released. To get the so-called classic look install gnome-session-flashback. That will give you 2 additional login options. Gnome Flashback (Metacity) and Gnome Flashback (Compiz). In Ubuntu 12.04 people installed gnome-fallback. In 14.04 it is gnome-session-flashback. Do not install gnome classic. That is an extension of Gnome 3 shell and it will also install Gnome 3 shell. Unless, of course, you like the way Gnome 3 shell works. In that case I suggest that you install Ubuntu Gnome to start with.

If you are upgrading 12.04 and not intending to fresh install 14.04 then revert 12.04 to as close to defaults as possible. Uninstall gnome-fallback. Revert to using an open source video driver. These are things that will avoid complications that could break the upgrade.

Regards

---

### Post by yancek on 2015-10-21
If you install 8.1 and then upgrade to 10, my understanding is that you have 30 days to go back to 8 if you don't like 10.  If you have the windows 8 install media I guess this isn't a problem.  In regard to updates to 8.1 before upgrading to 10, I would suggest that a better source of info would be the microsoft site or a windows forum.

Generally it is better to install windows first and from what I have read, even with UEFI this is still best.  Best to install 8 on the SSD and then upgrade to 10 before installing Ubuntu as the upgrade to 10 will mess up the bootloader.  There are a number of posts here related to that problem.

If you use UEFI for windows, you should also use UEFI when installing Ubuntu or you will have serious boot problems.  If you do an MBR install of windows, do the same with Ubuntu.   It would probably be helpful to read a little about UEFI before beginning.  A couple of links below should provide useful information. 

 
[http://ubuntuforums.org/showthread.php?t=2277628](http://ubuntuforums.org/showthread.php?t=2277628)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Odyssey1942 on 2015-10-21
Apology for any confusion.

It is a new computer.

It came with Windows 8.1 installed. I am using it with Win 8.1 as the OS now installed on the hdd.

I have used it for about an hour so far (so hopefully defragging, even multiple times, will be quick.)

*Edit: Just figured out the source of confusion. The 12.04 computer is 3 1/2 years old and getting tired. Time for new hardware which is the Dell XPS described in the original post.*

So here is what I synthesize:

Add the SSD and then install 8,1, bring 8.1 current on all updates (I am assuming that the DVD that Dell sends me will allow a fresh install onto the SSD, but please advise if you think this might not be the case)

Upgrade to 10

Do a UEFI install of 14.04 as a dual boot

Would it be recommended to remove the original 8.1 from the hdd after installing 8.1/10 to avoid possible conflicts?

I am unsure of the guidance on the Classic view.

> To get the so-called classic look install gnome-session-flashback. That will give you 2 additional login options. Gnome Flashback (Metacity) and Gnome Flashback (Compiz). In Ubuntu 12.04 people installed gnome-fallback. In 14.04 it is gnome-session-flashback. Do not install gnome classic. That is an extension of Gnome 3 shell and it will also install Gnome 3 shell. Unless, of course, you like the way Gnome 3 shell works. In that case I suggest that you install Ubuntu Gnome to start with.

I have 12.04 now booting into the Classic view and it is just fine for me. However I installed it 3 1/2 years and am unsure of the correct name (whether Flashback or gnome-fallback, but the latter seems familiar). I don't know about Gnome 3 shell. 

From Graham's post, I see there is a version of Ubuntu (Ubuntu Gnome) that perhaps just comes up in the Classic view without having to go through the additional steps of changing the 14.04 over to the Classic view.

Are there any disadvantages in terms of normal updates, using most software for Ubunutu (I understand that Unity packages would not work, but I don't have that now and don't want Unity), etc. I have done some googling/reading but don't find much discussion about disadvantages/issues.

---

### Post by oldfred on 2015-10-22
I got a Dell SFF small form factor system with Windows 8. I did not plan on using Windows but do not need a lot of space on hard drive, so shrank Windows a lot, like to 50GB.
But when booting Dell it wanted to make a Dell backup, a Windows backup and I also then used Macrium to make a full backup. It took several flash drives and multiple DVDs to make all those backups. It then asked after each backup if I wanted to delete backup partitions and I said no, but should have said yes.
While doing other things and having to buy more DVDs & flash drives it took 3 days to do all the backups. Probably half a day total time. It took me a bit to figure out Windows 8 enough to get to screens to turn off fast start up and shrink system. I created Linux partitions with gparted.
Then actual Something Else install with high speed Internet took less than 10 minutes. Another hour to do some of configuration and copy data from desktop.

Not sure what you get from Dell. Normally it is just the image copy of drive, just as you get when you make the image copy from hard drive onto flash drive or DVDs. But it now may be the upgrade to Windows 10? If the upgrade it probably needs to see the Windows 8 to install, but if an image it may not?

I am running gnome-panel or flashback on 14.04 on my desktop. 
        
 fred@trustyDT:~$ sudo apt-get install gnome-session-flashback
It installed a lot and suggested even more packages.

More info on gnome-panel/flashback
[http://www.omgubuntu.co.uk/2014/04/ubuntu-14-04-classic-gnome-flashback-session](http://www.omgubuntu.co.uk/2014/04/ubuntu-14-04-classic-gnome-flashback-session)
Flashback/fallback in 14.04 Kansasnoob
Installing the package 'gnome-session-flashback' does exactly the same thing as installing the package 'gnome-panel'.
[http://ubuntuforums.org/showthread.php?t=2220264](http://ubuntuforums.org/showthread.php?t=2220264)
[http://ubuntuforums.org/showthread.php?t=2090021&p=12994477#post12994477](http://ubuntuforums.org/showthread.php?t=2090021&p=12994477#post12994477)
[http://ubuntuforums.org/showthread.php?t=2184682&p=12986002#post12986002](http://ubuntuforums.org/showthread.php?t=2184682&p=12986002#post12986002)
[http://ubuntuforums.org/showthread.php?t=2184682&p=12971487#post12971487](http://ubuntuforums.org/showthread.php?t=2184682&p=12971487#post12971487)

---

### Post by grahammechanical on 2015-10-22
Ubuntu Gnome comes with Gnome 3 shell which is many ways is similar to Ubuntu Unity. Or, perhaps to put more accurately, Unity is in many ways similar to Gnome 3 shell.

 There is an extension to Gnome 3 shell called Classic that gives the old Gnome 2 panel menus. But in my opinion it looks like something sitting on top of Gnome 3 shell. Whereas, installing gnome-session-flashback on 14.04 and later does give the ideas that the Gnome 2 panel look was meant to be there.

This is Gnome 3 shell. Not to be confused with Gnome 3 the desktop environment which is also used by Ubuntu.

[https://www.gnome.org/gnome-3/](https://www.gnome.org/gnome-3/)

This is Gnome Classic on Gnome 3 shell.

[https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/7/html/Desktop_Migration_and_Administration_Guide/what-is-gnome-classic.html](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/7/html/Desktop_Migration_and_Administration_Guide/what-is-gnome-classic.html)

This is Gnome Session Flashback

[https://wiki.gnome.org/Projects/GnomeFlashback](https://wiki.gnome.org/Projects/GnomeFlashback)

My advice if anyone wants the old Gnome 2 panel look is to install Gnome Classic extension when running Ubuntu Gnome. And to install Gnome Session Flashback when running Ubuntu + Unity 14.04 and later. Gnome Fallback was fine for 12.04 but I would not install it on Ubuntu 14.04 because there have been many changes to the desktop environment (Gnome 3) used in 14.04. Flashback is more up to date with those changes than Fallback. I think you will find them similar.

Personally, I would not install Gnome Classic on Ubuntu + Unity 14.04 because it will bring in Gnome 3 shell because Gnome Classic is an extension ( = plugin) of Gnome 3 shell and needs it to run.

Regards.

---

### Post by ubfan1 on 2015-10-22
I recently used the latest Macrium Reflect (free as in beer) to set up a 60G SSD to replace a 160G hard disk containing a current UEFI Windows 8.1.  Just dragged and dropped the EFI and Windows partitions onto the new SSD.  Initially, tried to let the partitions be created at the same time, but my lack of experience with Macrium might have caused some failure -- creating the partitions first, then copy worked just fine.  Replaced the hard disk with the SSD, and it booted just fine.  Then did Microsoft's update to Win 10 with no problems.  The most work was cleaning up the existing Win 8 to fit onto a smaller disk.  Macrium claims to do the SSD setup and UEFI setup, and as far as I can see, they do it right.  I use a flash USB3 to run Ubuntu on this system (netbook), but would think if you have the room on your SSD, you should have no problem installing Ubuntu.

---

