---
title: "error partition doesn't exist"
date: 2011-07-02
forum: Installation &amp; Upgrades
---

### Post by PhilFox on 2011-07-02
Mitac 5033 laptop
Installing  Ubuntu 10.04.2 live CD
4 GB hardisk
96M ram
Clean install on previously formatted and cleaned down machine (done some years ago by someone else so no details)

When rebooting to hard disk...

while other things are happening...

> [COLOR="Red"]error partition doesn't exist!!![/COLOR]

after a pause

> error: no suitable mode found.
error: unknown command 'terminal'.
error: cannot allocate real mode pages.
error: you need to load the kernel first.
    Failed to boot both default and fallback entries.

Press any key to continue...

(if any key is pressed the later error messages are repeated.)

I replaced the CMOS battery and first got an error message

> CMOS checksum does not add up or something like that - the BIOS did not recognise hard disk, so I put the old battery back in and got the original red error message and the bios did work. So I put the new battery back in a second time and the CMOS error message stopped, but the red error message came back.

I have 3 partitions 1,2 and 5 which I could see via the live CD, but I do not know what to do next.  I tried to mount the file system using the live CD and a command line, following instructions from the forum. I did this by using repair from the live CD, then the install environment none of the 3 partition environments would work (not sure if that's the right terminology).  On the command line which I think involved a hash key, I typed mkdir ubuntu and could see that directory under the command ls. But I could not mount that directory. I could not see that directory from the command line by typing dir /. So I have given up on that set of instructions.

I've tried PLoP boot manager, but do not understand it.

I tried Smart Boot Manager sbm.bin but could not get the floppy drive to boot from it and I would not know how to sort out the partitioning or master boot record. I know the words and that is it.

I think this live CD has Grub 1.98 on it.

---

### Post by coffeecat on 2011-07-02
Welcome to the forum.

> **PhilFox said:**
> 
96M ram

Are you sure you mean 96MB? That is not nearly enough for Ubuntu with gnome.

You say you were using the live CD. Do you mean the live CD that takes you to a live Ubuntu GUI desktop, not the alternate CD with a text installer? I'd be very surprised if a live CD could even half boot up with only 96MB RAM.

---

### Post by PhilFox on 2011-07-02
yes 96MB RAM

I'm using the alternate CD

It's not getting far enough on boot to see if GNOME works.

---

### Post by coffeecat on 2011-07-02
> **PhilFox said:**
> yes 96MB RAM

I'm using the alternate CD

That would explain it. There's probably enough RAM for the alternate CD to do the install, but not nearly enough for the installed Ubuntu to boot into the GUI. My guess is that those error messages are spurious and caused by the system running out of memory and getting hopelessly confused.

Unless you can up the RAM to about 512MB, you'll never get the gnome desktop to run, I regret to say. You'll need a leaner distro for that machine. I don't have any experience of Lubuntu, but you could check its system requirements - its desktop is much less RAM-hungry than gnome. Or others may be able to recommend non-Ubuntu lean distros particularly suited to older hardware.

**EDIT**: no, sorry. The minimum RAM for Lubuntu 10.04 is 128MB:

[https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/LucidLynx](https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/LucidLynx)

Ditto for Lubuntu 11.04:

[https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/NattyNarwhal](https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/NattyNarwhal)

---

### Post by PhilFox on 2011-07-02
Some people have got it going on a puppy distro, so I'll give that a try. Thanks.

---

### Post by PhilFox on 2011-07-05
The instructions for a lean Ubuntu installation are here [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

I've installed ServerLinux (a version of Puppy) from a live CD and it installs very well, but the hard drive is still full of files from the previous failed installation of Ubuntu. It still won't boot from hard disk.  So the next plan is to follow the instructions in the link above. 

By toggling the various options in the bios menu I've managed to get rid of the "partition doesn't exist" error message, but the other error messages still come up on failed boot from hard disk.

---

### Post by PhilFox on 2011-07-05
It's worth saying that I've got a full installation of Lucid Lynx (Ubuntu 10.04.2) with Gnome working well on two other desktops with only 256M RAM. One was a bit slow until I re-installed it with a working internet connection during the installation. Suddenly it started working normally.

---

### Post by PhilFox on 2011-07-07
The problem is now solved with even the wireless adapter working straight out of the box, thanks to the very useful tools on Puppy Wary 5.1.2 - a lean distro designed for legacy machines based partly on Ubuntu Lucid Lynx 10.04.  This OS boots and runs from CD (i.e. it is a Live CD) - first step is to change the BIOS to boot from CD - press F2 while booting to get to the BIOS. The steps I followed thereafter were:

Next step to clear the partitions I used the Ubuntu 10.04 Alternate installation CD - reboot and run the installation until the partitioning stage - repartition to make sure that all old files are deleted and that there is a swap partition - preferably large.  Then I pulled out the power cord and killed the installation.

Then reboot the Puppy Wary 5.1.2 live CD. Allow the install - run the wireless wizard from desktop to apply the network wireless code.  Then reboot - this prompts for a location for the personal files and to install some of the OS files on the disk for faster loading and operation.  As the BIOS did not recognise the USB Flash Drive I could not get the promised boot from USB to work - but maybe there is a way. 

Reboot a couple of times as this will prompt more operations for faster install. You do end up with a machine that works probably a lot faster than it did when new with windose 95/98.

Now the bit that this is all about.  

menu>setup>Puppy universal installer
I opted for the frugal install as this allows many different versions of Puppy to be installed to one partition and many different users.  Keep a note of where the kernel is being installed as you will need it later.

Using the "grub legacy bootloader" applet from menu>system follow all the default settings and then the "bootmanager configure bootup" from the same place. Select the master boot record (MBR) when you get the chance. 

After one of these three utilities you will be advised to find menu.lst in the grub folder and add some code - I had to find a workaround for copy and paste because my left click button does not work (The workaround is to put the cursor at the begining of the text - by tapping the touch pad instead of left click. then hold shift and tap the end of the text and this works for selecting text!)  Find menu.lst by using the Graphical User Interface (GUI)  and clicking on the icon of the appropriate drive on the desktop and drilling down (or up to root and back down again)- you will have been prompted earlier for a location to put Grub so make a note of that too and find your way there. When there double click on the file (or double tap in my case!) and it will open an editor. Save menu.lst with another backup name e.g. menu.bak.lst . Then paste the code to the bottom of the file and save it back again to menu.lst. If you get very daring you might like to clean up some of the other entries which in my case referred to installations which did not exist, but I've left them in for another day.

Then reboot again, having removed the CD. You will get to a grub screen with various options. Highlight the one which includes the code you've just pasted to menu.lst and type b for boot and with any luck you are then booting up as normal. [http://ubuntuforums.org/images/smilies/icon_razz.gif](http://ubuntuforums.org/images/smilies/icon_razz.gif)

Solved

---

