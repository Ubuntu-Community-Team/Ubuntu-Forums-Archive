---
title: "Help installing Ububtu from iso"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by Godismyrock on 2008-05-10
I need the files from this post please! The links in it aren't working and I can't find them in my .iso file. If anyone could please help by giving me links to them or sending them to me it would be GREATLY appreciated!

 "HOWTO: Install Ubuntu Linux without burning a cd
#EDIT: The automatic installer script included with this thread has been removed. The new version is available for Breezy and Dapper here: errr... waiting for the thread to be approved by a moderator... zzzz!

How to install Ubuntu Linux without having to burn the .ISO image to CD.

Why would you want to do this?
1 - you don't have a cd burner.
2 - you can't be bothered to wait for your pressed cd to arrive in the post.
3 - because you can...

-- The howto is mainly a simplification of this (Install GNU/Linux without any CD, floppy, USB-key, nor any other removable media) excelent guide for which i take no credit --

The hardware i used to sucessfully install Ubuntu without booting a CD:

Dell Inspiron 1100 2.2 Ghz laptop, 20GB hard disk, running Windows XP on a single NTFS partition. No other system has been tested ~ at least, not by me.


Brief overview of the steps:
1 - resize the c: windows partition
2 - get hold of the ubuntu kernel
3 - set up GRUB for NT
4 - install ubuntu

easy really! i should stop now, hehe


#1 ~ Resizing the partition
(I used Partition Magic 8.0)

Notes:

The trick is not to create specific Linux partitons, but to resize the Windows one leaving nothing but free 'unallocated' space. The ubuntu installer will be able to install itself to this space and do all the fancy partitioning stuff automatically without frightening us linux n00bs too much

In my case i redistributed my 20GB to 15GB for windows and 5GB of 'unallocated space'.

#2 ~ Setting up the kernel

We only need to download two files for the installer to work...

linux.bin
initrd.gz

both of these we could download from the ubuntu archive

place both of these files in C:\boot
- you'll probably have to create this directory yourself

#3 ~ Setting up GRUB for NT (a bootloader that will allow us to choose either the Ubuntu installer or to boot normally into Windows)

The files that we need for GRUB for NT actually contained in the GRUB for DOS package, but that's no problem, so download that:

from here: [http://newdos.yginfo.net/grubdos.htm](http://newdos.yginfo.net/grubdos.htm)
or here: [http://grub.linuxeden.com/](http://grub.linuxeden.com/)

The two files that we want are "menu.lst" and "gldr", you can delete the rest. Place "gldr" in the root of the hard disk (probably C:\) and make a new directory inside C:\boot called 'grub' (ie, C:\boot\grub) and put you menu.lst in there.

All we have to do now is edit the menu.lst to give an option to select the Ubuntu installer and to set the boot.ini to load GRUB.

A) ~ Editing menu.lst

open it with notepad and append right at the bottom of the file the following lines:

Quote:
title Ubuntu Installer (hd0,0)
kernel (hd0,0)/boot/linux vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --
initrd (hd0,0)/boot/initrd.gz

(a lot of the stuff in that file can be cut out, but it's no big deal, we'll leave it for now)

B) ~ editing the boot.ini

The problem here is that this particular file is not only write-protected but also hidden. So to undo all this open a command prompt (Start -> Run -> cmd.exe)

type:
Quote:
attrib -a -r -s -h c:\boot.ini
now open the boot.ini file with notepad and add this line on at the end:

Quote:
C:\grldr="Start GRUB"
...

That's it!


4 ~ Installing Ubuntu

Now when you reboot you should be presented with a screen offering you the choice to either boot into windows, or to 'Start GRUB'; choose 'Start GRUB' and then on the next menu choose 'Ubuntu Installer'.

The installer will run and download all the parts it needs for a while until you get to the partitioning stage... Ubuntu will ask you to install in on the whole of your drive - which obviously we do no want, so choose manage drives personally (or whatever the label is, i don't remember exactly :s) and then you will be able to tell it to install onto the 'unallocated space' we created earlier with Partition Magic. Ubuntu will then set its own ext3 and swap partitions from this space and continue to download and install itself to the empty half of the drive

After this (or maybe it was before?) you'll be prompted with the Ubuntu's own GRUB screen... It should have detected Windows, if so, just agree with it and allow it to install its own GRUB to the boot sector.

That's it!
Fin!

Sorry it's so badly written and all, but i've just done this and was pretty pleased so i thought it was important to share :P

***

Lastly, I have attached all the files needed to set this up in a .zip (EXCEPT FOR inird.gz and linux.bin ~ they're just too big, you'll have to download them yourself to the same folder where you extract this archive to) with this message, inside is a .bat file which can set the whole business up for you

IT IS NOT MY FAULT IF IT SCREWS EVERYTHING UP ~ sorry!

The .bat file expects to run on Windows XP (though i don't suppose it'll care what you run it on...) and will do the following:

create c:\boot
create c:\boot\grub
move grldr to c:\
move linux and initrd.gz to c:\boot
insert a pre-edited version of menu.lst into c:\boot\grub
unprotect the boot.ini
append data to the boot.ini
reprotect the boot.ini

effectively, you could extract the files, run the .bat and then reboot, and all's fine


One last thing, i take no responsibility for any ill effects caused by either your following of this guide, or by running my .bat file.

-ed.

Useful? Try here too: [http://www.ubuntuforums.org/showthre...618#post145618](http://www.ubuntuforums.org/showthre...618#post145618)

EDIT: (24/04/2005)
#1 - I forgot to type (hd0,0) after 'Unbuntu Installer' in the new c:\boot\grub\menu.lst file sorry! I've fixed the .zip package too.
#2 - Removed all the stuff about renaming linux to linux.bin ~ seems that was all pointless (archive updated accordingly).

(13/06/2005)
#3 - Finally fixed the "title Ubuntu Installer" line - sorry about that... I'll fix the archive soon too; just a little busy right now...

(27/06/2005)
#4 - Added wget.exe (command-line based download program) and set it up to download both the 'initrd.gz' and 'linux' and put them in the right place.

So... Now all you have to do is partition your hard disk, run 'install.bat' and reboot. Though - as always - I take NO responsiblity for whatever happens..."

I TAKE NO RESPONSIBLILTY FOR THIS POST! I just copied it because I needed the files so maybe someone could help! Thanks!

---

### Post by pytheas22 on 2008-05-10
An easier approach to installing without the CD would be to use [wubi]("http://wubi-installer.org/"), provided you have Windows already installed on that computer.

---

### Post by Godismyrock on 2008-05-10
wubi wouldn't work on my computer. I got windows 2000 installed on it and wouldn't work.

---

### Post by ChronoSphere on 2008-05-10
They're in the iso in the casper directory.

casper/initrd.gz
casper/vmlinuz (substitute linux.bin)

---

### Post by Godismyrock on 2008-05-10
what about the other files?

---

### Post by ChronoSphere on 2008-05-16
You can get WinGrub here: [https://gna.org/projects/grub4dos/](https://gna.org/projects/grub4dos/)

Another tutorial to install w/o a CD is here: [http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html)

---

