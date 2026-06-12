---
title: "How do I do reinstall Ubuntu/Kubuntu Partition? (step by step)"
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by Shinobi326 on 2007-05-30
OK... with all of this kernel upgrade stuff + downloading/installing a million packages I think I want to wipe out my existing partition and start over with a fresh Ubuntu/Kubuntu partition.  Currently I cannot get into a graphical Xserver session without logging in as root and doing a dpconfigure-xorg command.

My current hardware:
AMD64 3200
Dual Nvidia 8800GTS's
Dual Raptor 74gig drives (one is Windows XP drive the other is Ubuntu/Kubuntu
Dell 30" LCD screen
One NAS mount via samba

My questions:

1.  What is the exact sequence of events I need to accomplish to wipe out my existing Ubuntu/Kubuntu partition, make Grub work correctly (right now it has the .15 & .16 kernel options and the default is the memory test instead of my windows partition like it used to be before the .16 upgrade), get my NAS remounted, get Kubuntu installed?

2.  This time, from a fresh install, what is the preferred way to get my Nvidia drivers to work properly with my 8800gts's?... I've read everything from 'Use Envy', 'Use Restricted Drivers', 'Recompile them using the tarball from Nvidia', etc.... When I did my original install I tried the Envy first and that didn't work for some reason (I get the blue screen failed to start xserver screen), I tried using the restricted drivers and that didn't appear to work either, I then did the manual recompiling using the .9755 drivers from Nvidia and I finally got something to work.  So my main question is for someone with 8800GTS video cards, what is the method you used to get them to work?

3.  Can someone post their Xorg.conf file so I can see your settings you use for the Dell 30" LCD monitor (specifically the 'Modeline') as well as your settings for these 8800GTS video cards.  For some reason I just never seem to really get the same performance from these cards in Ubuntu than I do in WindowsXP (using Firefox, gaming, screensavers, scrolling).  What are some of your 'magic tricks' you use to get performance out of your video cards?

4.  What are the commands & steps to load and use Kubuntu?

5.  Does someone have a good guide of steps to take to mount a NAS drive using samba over ethernet (looking for a step-by-step procedure... I remember it's a little involved). 

Well thanks in advance for reading this long post but given the numerous packages I've installed, especially through the evil Automatix2 (which I will not be reinstalling), the break down from the .16 upgrade, and my ongoing performance issues, I simply want to start over again.

---

### Post by Shinobi326 on 2007-05-31
Please....anyone.......

I really would like to do this tonight but I'm afraid if I put in the Ubuntu disk to try to reinstall I'm going to mess up Grub or something where I won't be able to get to my WinXP partition.

---

### Post by confused57 on 2007-05-31
> **Shinobi326 said:**
> Please....anyone.......

I really would like to do this tonight but I'm afraid if I put in the Ubuntu disk to try to reinstall I'm going to mess up Grub or something where I won't be able to get to my WinXP partition.
First thing I would suggest is to download & burn a copy of the Super Grub Disk(5-7 Mb download):
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

SGD download mirrors:
[http://ubuntuforums.org/showthread.php?t=419598](http://ubuntuforums.org/showthread.php?t=419598)

About all I can help you with is the reinstall of (K)Ubuntu...you would need to select "Manual" partitioning, then use your current Ubuntu partitions to reinstall...(/), swap, /home(if you have a separate partition).
set the mountpoints accordingly, be sure to format / as ext3, swap as swap.  Your Window's partition shouldn't  be affected as long as you select not to format.  You probably will need to set the boot flag on for your root partition?  The new install should install grub & recognize & add an entry to boot Windows.

From reading other posts, your video card would need to use the "vesa" driver until you can install  nvidia drivers.
Sorry I can't help you more.

Added:  I just noticed that you have 2 hard drives, you might want to consider this method:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

Are you booting from your Window's drive first?  If so, that's where grub is installed, but you could use the SGD to restore Window's IPL code to your Window's mbr.  Then with the method in the last link, grub would be installed to the Ubuntu drive, then you could add an entry to boot Windows to your menu.lst...this method might be more effort than you're willing to put into it, but thought I'd mention it as an option.

---

### Post by Shinobi326 on 2007-06-02
Well when I dug my teeth into this a bit more I decided to go with the 'guided' partition install.  Since I'm running two HD's I just had to make sure I was selecting my Linux drive and not my Windows drive.  Everything went without a hitch.  I was concerned my Grub wasn't going to be correct but apparently the reinstall also redid GRUB correctly and I was able to get into either partition right off the bat.

I haven't installed Kubuntu because, frankly, I've learned a lot more about Gnome and I can nearly do anything in Gnome that I wanted to do in KDE so I think for now I'm going to stick with Gnome.

The series of things I did upon a reinstall are:
- Get the Nvidia drivers to work with dual 8800gts (these are still finicky cards for Ubuntu!) This is a daunting and a PITA because not only do I have difficult cards to work with but I also have a 30" screen that I need to get 2560x1600 going.
- Get my Nexstar NAS mounted and working
- Get my Network Printer going.  This is probably the easiest thing to get working in Ubuntu.  All I do is simply put in the IP address and Printer model ID and it simply WORKS!
- Tweak a few things to get "Desktop Effects" to work correctly (Love the cube!) (like fixing disappearing titlebar bug)
- Get Medibuntu and all of the necessary libraries to run MP3's, watch DVD's, and burn DVD's.
- Get additional Firefox Extensions squared away to make more enjoyable

Some things I still [COLOR="Red"]wish would work[/COLOR]:
- Watch videos on Foxnews (grrr....still apparently not compatible with Linux)
- Is there a good ICON based login window (Like WinXP) where you can simply click your name/icon and it logs you in?
- Good 'behind the scenes' music player that will integrate well with Foxytunes.
- Get some more good Themes, Pointers, etc. (what I have works good, I just want more variety.

---

