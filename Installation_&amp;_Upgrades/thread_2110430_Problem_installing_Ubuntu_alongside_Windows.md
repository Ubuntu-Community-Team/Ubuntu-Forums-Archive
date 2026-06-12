---
title: "Problem installing Ubuntu alongside Windows"
date: 2013-01-30
forum: Installation &amp; Upgrades
---

### Post by utkan on 2013-01-30
Hi, I'm new to Linux World, though I'm an Android user on mobile. I have downloaded Ubuntu 12.10 and burnt it onto a disc then restared computer. I chose the option to install it alongside Windows but when I click next, installation gets interrupted and my computer restarts, and on the screen says ***"Please remove the disk, close the tray (if any) and press ENTER to continue"*** I had Ubuntu 12.04 but same problem also occured with it as well. Any help would be greatly appreciated. I'm running Windows 8 32-bit.

---

### Post by omeomi on 2013-01-30
Try burning the ISO on the lowest speed or at least a very low speed. 

Does the installer give any error message or other output when it crashes?

---

### Post by utkan on 2013-01-30
> **omeomi said:**
> Try burning the ISO on the lowest speed or at least a very low speed. 

Does the installer give any error message or other output when it crashes?

No, just "Remove the CD" error and computer restarts.

Also I found this - I think that's the solution for my problem:
[B]
This is to remove the hard pause and the CD eject message when powering down Statler, running  from a persistent Live-USB key:

1) Browse (as root) to /etc/init.d/live-boot.[/B] [B]
2) Make backup copy of the file.
3) Open file with Gedit (right click and select "Open as root").
4) Remove EXACTLY these lines only: lines 150 - 177 (highlight them and delete).
5) Save file, you are done![/B]

[http://crunchbang.org/forums/viewtopic.php?id=9582](http://crunchbang.org/forums/viewtopic.php?id=9582)

How do I exactly browse? Something like command prompt on Windows? I have live CD on and trying Ubuntu now.

---

### Post by omeomi on 2013-01-30
> **utkan said:**
> Also I found this - I think that's the solution for my problem:
[B]
This is to remove the hard pause and the CD eject message when powering down Statler, running  from a persistent Live-USB key:

No that's not relevant for your situation. This solution is just to remove the message when you run from USB (not CD).

Have you tried running the installer after logging into the live session? Does it give the same result? (there should be a shortcut on the desktop saying 'Install Ubuntu ...')

---

### Post by utkan on 2013-01-30
> **omeomi said:**
> No that's not relevant for your situation. This solution is just to remove the message when you run from USB (not CD).

Have you tried running the installer after logging into the live session? Does it give the same result? (there should be a shortcut on the desktop saying 'Install Ubuntu ...')

I tried, but now it doesn't give me the option to install alongside Windows.

---

### Post by furything on 2013-01-30
Asking a daft question - Have you got any free space on your hard drive?

If not you need to boot into windows first and use the disk manager to shrink your volume to create the desired space.

Don't use linux Gparted on windows 8 you must free space inside from windows.

---

### Post by Mark Phelps on 2013-01-30
> **utkan said:**
> I tried, but now it doesn't give me the option to install alongside Windows.

Win 8 machines currently use UEFI BIOS -- which is very different from the former MBR BIOS.  I'm not an expert on EUFI but I believe that you have to disable that to use the installer.

But, before you do that, I would strongly urge that you go into Win8 and use the Backup feature to create and burn a Win8 Repair CD.  You may need that later to restore the Win8 boot loader from problems during the dual boot setup.

Also, do NOT, repeat NOT, use the Ubuntu installer to shrink the win8 OS partition to make room for Ubuntu.  That has a history of causing filesystem corruption and rendering Win8 unbootable.

Instead, use only the Win8 Disk Management utility to shrink Win8.

---

### Post by utkan on 2013-01-30
> **furything said:**
> Asking a daft question - Have you got any free space on your hard drive?
 
If not you need to boot into windows first and use the disk manager to shrink your volume to create the desired space.
 
Don't use linux Gparted on windows 8 you must free space inside from windows.
 
Yep, I have 92 gb's of free space shrinked for Ubuntu.

---

### Post by furything on 2013-01-30
I hope you did it from inside windows as you can see Mark and my post. 

Using a linux partitioner with a new unrecognized format **will corrupt your os**.

---

### Post by utkan on 2013-01-30
> **furything said:**
> I hope you did it from inside windows as you can see Mark and my post. 
 
Using a linux partitioner with a new unrecognized format **will corrupt your os**.
 
I used Windows' own disc manager to shrink the volume, yes. I'm always somewhat hesistant about using Ubuntu's disc manager for partition.

---

### Post by audiomick on 2013-01-30
> **utkan said:**
> I'm always somewhat hesistant about using Ubuntu's disc manager for partition.

It is just a matter of the right tool for the job in hand. The windows partitioning tool is better for windows partitions, the Linux tools (gparted, GNOME Disks, or whatever) are just fine for Linux partitions.

---

### Post by Soul-Sing on 2013-01-30
the gparted iso (live cd) will do the job for you.
don't touch the small part (50/100mb) of the windows boot loader.Gparted is the full version of the partionmanager within the ubuntu live cd. Get famil. with primairy and extended partions.

---

### Post by furything on 2013-01-30
> don't touch the small part (50/100mb) of the windows boot loader

Problem is I think this is exactly what most people do.

I prefer a seperate hard drive - can't go wrong that way although of course this is for desktops with more than one drive bay.

---

### Post by Bucky Ball on 2013-01-31
*Thread moved to **Installation & Upgrades***

---

