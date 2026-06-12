---
title: "Installing difficulties."
date: 2014-09-27
forum: Installation &amp; Upgrades
---

### Post by bryan30 on 2014-09-27
I just decided to switch to Ubuntu from a windows 8.1 computer (brand new hard drive, so no 8.1 info on it).  I booted from a USB drive, and it asked me if I wanted to try it or install it, so I clicked install.  went through the entire installation process, finished, rebooted 'no boot disc found' So I installed again. same thing.  I went into bios, turned off secure boot.  tried again.  still no boot drive.  turned on secure boot, installed again.  still no boot drive.  Though various changes here and there, so many I have no clue which did anything, but under the secure boto (efi is it?) it lists ubuntu, but if I select that, it gives me the 'no boot disc'.  I've found if I turn the computer on, escape to the start up menu, then select boot efi selection (or something to that effect) I can select various different start up options, such as MokManager.efi, grubx64.efi, and shimx64.efi.  grubx64 and shimx64 will boot me into ubuntu, but MokManager wants to do some other stuff.

So, I'm booted into ubuntu, and I I played around a bit, then I wanted to lock the computer.  I hit log off, and nothing happened.  I tried clicking on a few different things, and nothing happened.  Eventually, a menu popped up asking me if I wanted to log off, lock, etc.  Really seems weird that a brand new clean install takes that log for a menu to pop up....

But, moving on, I tried to install some software.  If failed saying it didn't have permission the the /usr directory.  I'm the only user, as which I should be admin and have access to everything, right?  Ok, so I went in and changed my account, which apparently was not set for admin.  I added the software, no shortcuts on the desktop, no entry's in the start menu, so I searched the drive, saw a copy, and ran it, it ran find.  I then came back and tried to create a short cut.  There's no menu item or shortcut key go create a new shortcut.

So, I went in to Apps I think it was, and created a new subdirectory, then went into that, the only opens were create a folder or am empty file.  no short cut.

Ok, maybe if I select the program, I can past a short cut back in here :)  Nope, pasted a full copy, which won't run without the other files, so......

Ok, then I looked at the path to the file....
/dev/fd/14/dev/fd/14/dev/fd/14/dev/fd/14/dev/fd/14/dev/fd/14/dev/fd/14/dev/fd/14/dev/fd/14/dev/fd/14/dev/fd/14/dev/fd/14/dev/fd/14/dev

WHAT THE?!  and as I start from the top and dig in, each directory along the way looks to be and exact copy of the one above it

I (apparently used to be) am VERY computer literate.  Though, apparently like most of the population, I've become brain dead on windows ways....

I'm thinking, because everything so new and I don't have a lot of stuff installed on here yet, I might just want to start over, but it would be really nice to figure out how to get the computer to boot into the OS without having to go into set up each time and select the program to start.  I probably WILL eventually want a dual boot with windows 8.1, do I need the 8.1 boot screen, or will it install to the ubuntu start up?

So, for others, any idea what would cause the slowness in logging out, and excessive recursion in those directories?

And finally, what's the best way to instaill ubuntu on a new system from a usb drive? on a computer with the efi secure boot (HP pavailion t20 all in one)

---

### Post by yancek on 2014-09-27
I don't use windows 8 or UEFI so can't help you with that.  You don't need to turn off Secure boot to install Ubuntu.  It isn't clear to me whether you still have windows 8 on the computer on another or the same drive?  If you have windows 8 on another drive it will make a difference if it was pre-installed or whether you installed it.  Did you use UEFI method during the Ubuntu install?  Secure Boot is just a part of the UEFI which is used mostly because windows uses it.

The permissions error you got has to do with the system and has nothing to do with the fact that you are the only user of the computer.  On a Linux system, the only directories/files a normal user will have read/write access to are in the /home/user directory.  Files elsewhere are system files and you need root/admin permissions.  You need to prefix a command with sudo in a terminal and and you will be prompted for your primary user password. 

There are no shortcuts placed on the Desktop everytime you download some software.  You can create them if you want.

I think you jumped in without doing much research.  The way Linux systems work is a lot different than windows.  I would suggest you do some reading before trying again.  You could start with the Ubuntu beginners manual which you can download at the link below.

[https://ubuntu-manual.org/](https://ubuntu-manual.org/)

---

### Post by bryan30 on 2014-09-27
you are correct, I definitely jumped in with no research, I figure I'll learn as I go :)

The computer had nothing on it.  I even pulled the bios battery.  new, unformatted hard drive, USB flash drive with ubuntu 14.whatever the current version is.

Then, where did my program that I just installed go?  The copy I found was a back up (I have since pulled everything from the old drive I could.  nothing is installed from it, it's just a copy of the files.)

Any idea on buried directory problem?  ([COLOR=#000000]/dev/fd/14/dev/fd/14/dev/fd/14/dev/fd/14/dev/fd/14/dev/fd/14/dev/fd/14/dev/fd/14/dev/fd/14/dev/fd/14/dev/fd/14/dev/fd/14/dev/fd/14/dev)  

I'm thinking I may just reformat it all again just to ensure everything is done properly, could someone please give me the proper steps to install from a flash drive?  I suppose at this point I could even burn a DVD, would that be a better choice?
(I've heard a lot of 'boot from a linux live cd, then install from there' is that what I'm doing with the download from ubuntu?)[/COLOR]

---

### Post by sudodus on 2014-09-28
Welcome to the Ubuntu Forums :-)

The first steps:

1. Download an iso file

2. Check that it is correct with ***md5sum***

3. Burn it to a DVD disk or flash it to a USB pendrive.

I find the method to flash to a pendrive better (unless the computer is very old, and does not boot from USB). See this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

4. Make the computer boot from DVD or USB and [try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

5. Run the installer which is rather straight-forward with a clean disk.

*. If you wish, you can make partitions and file systems before starting the installation. That way you can prepare for future tests with other versions or flavours of Ubuntu and other linux distros.

---

### Post by yancek on 2014-09-28
The link below is another tutorial specifically on installing Ubuntu 14.04.  The installation process is the same whether you are using a DVD or flash drive.  The link below also has some additional information at the beginning that would be useful if you are new to Linux.  Additionally, several links to other pages including one on partitioning.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

