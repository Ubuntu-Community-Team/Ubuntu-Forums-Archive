---
title: "12-10 update wont boot"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by kevron2020 on 2009-12-10
When I did todays update and rebooted, Ubuntu won't boot up.  I am severely new to ubuntu.  Running 9.10 Dual Boot with Vista.  It wont let me select a kernel, and it says there is no kernel. It would "boot" but display alot of characters then would tell me there is no kernel.  Any help would be helpful.  I am gonna try and reboot again and see if I can Pause Break while it scrolls all the characters.

---

### Post by kevron2020 on 2009-12-10
I get a syntex error then  it says invalid command 20times. 

Then it goes to 

GNU Grub Version 1.97~beta4
[Minimal BASH-like line editing is supported]

---

### Post by grubdude on 2009-12-10
Keep in mind that I am in no way an expert yet but it sounds like you did a Wubi install. There appear to be some issues using that method versus a clean install off the liveCD.
 
This is probably due to the fact that you are running Ubuntu sitting on top of a NTFS partition. I had this same problem originally with a security update.I reinstalled using a clean partition without Wubi and all security updates etc. now work fine......I am sure someone with more detailed info will chime in here...
 
Good luck...;)

---

### Post by rappscal on 2009-12-10
I'm having a similar problem. I installed Ubuntu Net remix with WUBI in windows XP and after today's update 12/10 I select UNR from the windows boot list, and instead of being given another list of .. (kernels? images? modules?) that I usually get, I have a grub prompt.

I've tried loading a config file from /boot/grub, but I'm swimming in the dark here. I don't know how to get it back the way it was.

---

### Post by kevron2020 on 2009-12-10
yes I installed Via wubi inside windows, as I am not comfortable enough to do it via install disk and possibly destroy windows. I still need it for a few programs, at least till this years taxes are done.

---

### Post by grubdude on 2009-12-10
Do you have enough space on your hard drive to create a second partition to separate the Windows and Ubuntu installs?

---

### Post by Naphrys on 2009-12-10
I am having the same problem with my Toshiba L45 series Satellite laptop.
Also extreamly new to linux I am compleatly lost on how to procede, I also need windows for the time being so I can't kill it off to to a disk install.

---

### Post by kevron2020 on 2009-12-10
I have plenty of room left, I have 10gigs left in my ubuntu partition.  I have been scrictly booting ubuntu for over a week now.

---

### Post by kevron2020 on 2009-12-10
bump???

---

### Post by rappscal on 2009-12-11
I managed to boot back into an earlier version of the kernel (-14-generic) using the following command when the grub command line appears:

linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /boot/initrd.img-2.6.31-14-generic
boot

.. if sda2 doesn't work, try sda1, sda3 etc.

This got me into the GUI. Then I went into the console and typed:

sudo update-grub

.. this gave me the grub menu back. When clicking on kernel vmlinuz-2.6.31-16, I get an error: kernel not loaded. But 15 and 14 will load you into linux.

The update manager has given me a big list of updates again, I'm doing the update and It might get me back into the same situation. I'll try the sudo update-grub before rebooting after update, and post the results.

---

### Post by grubdude on 2009-12-11
You would really be better off downloading the live cd iso burn to CD, then select install Ubuntu. This will create a "real" install versus one sitting on top of a NTFS partition.
 
Just make sure you select something like use contiguous empty space on the hard drive so you don't overwrite anything in your Windows partition. Very easy install.
 
The Wubi install is really designed more to try it out. If you really want the full functionality you need to run under the ext4 file system. After this, you will not have anu more problems installing security updates, etc.

---

### Post by rappscal on 2009-12-11
After installing the updates again, I couldn't get the grub boot menu back, even when reproducing my original method of sudo update-grub after booting manually at the grub command line.

I really don't want it to have to type both linux and initrd commands every time I boot. So I'll have to keep working on it.

---

### Post by rappscal on 2009-12-11
I had also considered doing what grubdude suggests, installing ubuntu properly. I went with wubi because I don't have a usb stick for my netbook yet and it has no cd drive.

---

### Post by rappscal on 2009-12-11
Just an update on my situation.I decided to install ubuntu on a separate partition. Wanting to do it without having to use a cd or any external media, I'm using the netboot approach described in detail [here]("https://help.ubuntu.com/community/Installation/FromWindows") (section title: Manual Process - Netboot approach)

A sidenote: my laptop has a rescue partition, so in menu.lst (described in the above link) I would have had to change (hd0,0) to something else, but was not successful, I just took this out completely as I noticed the windows partition was set as root by default, allowing me to simply use: "linux /boot/vmlinuz..."

---

### Post by Naphrys on 2009-12-11
Yeah that little bit of script did nothing for me, kept saying there was no file by that name....
 
I really like having both Windows and Linux, as there are a few prgrams I prefer over it's linux counterpart. Sadly I am too poor the have two computers at this time.

---

### Post by rappscal on 2009-12-12
Keep at it. Which bit of script didn't work? The linux command from the grub menu?

If it tells you the filename doesn't exist directly after typing linux or initrd, then the grub root location might be wrong.

use your tab button to see what is in the current root of the grub command line. type "linux /" or even "ls /" and then hit tab, and it should show you a list of folders

If root is set to the correct directory it should have a boot folder and a bunch of linux type folders (etc, usr)

if it's say.. windows folders, type set root=(loop0)

type "linux /boot/vml" and hit tab, and it will show you a list of kernels,.. assuming they're there, it will autofill your command line up to a certain point where the filenames differ, and you have to fill out the rest.

If the file not found error is after you try and boot, maybe try changing sda2 to sda1.

.....

But anyway, I gave up on trying to fully fix this problem (i.e. restoring the menu). I successfully installed ubuntu into another partition. The link I gave in my last post can guide you through that, if you're interested.

---

