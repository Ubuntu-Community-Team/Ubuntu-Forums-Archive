---
title: "Install/upgrade straight from downloaded file"
date: 2005-04-09
forum: Installation &amp; Upgrades
---

### Post by EndersGame on 2005-04-09
I'm not sure if I'm asking the impossible, but here goes:

I'm currently running an older array-cd release of Hoary.  Due to annoying firewall restrictions, I can't access any of the repositories.  Even worse, burning onto a cd isn't an option either.  Basically, all I have access to at this point is the ubuntu website.  Is there any way to install or upgrade to the final release of hoary after simply downloading the .iso.  Or are there other files I could download to make this work?  I realize I've limited my options substantially without a cd-burner or synaptic, but I thought I'd ask.

Thanks in advance.

---

### Post by az on 2005-04-09
You want to boot from the iso image, right?

Maybe this can help:

[http://www.knoppix.net/wiki/Poor_Mans_Install](http://www.knoppix.net/wiki/Poor_Mans_Install)

[http://www.knoppix.net/wiki/Win_Partition](http://www.knoppix.net/wiki/Win_Partition)

[http://www.knoppix.net/wiki/Hd_Based_HowTo](http://www.knoppix.net/wiki/Hd_Based_HowTo)

---

### Post by EndersGame on 2005-04-10
[QUOTE=azz]You want to boot from the iso image, right?

Maybe this can help:

[http://www.knoppix.net/wiki/Poor_Mans_Install](http://www.knoppix.net/wiki/Poor_Mans_Install)

[http://www.knoppix.net/wiki/Win_Partition](http://www.knoppix.net/wiki/Win_Partition)

[http://www.knoppix.net/wiki/Hd_Based_HowTo](http://www.knoppix.net/wiki/Hd_Based_HowTo)[/QUOTE]
 Thanks for the info.  The tutorials all describe cheatcodes such as 'toHD', which I'm wondering if these are knoppix specific.  Do you (or anyone else) know what the equivalents would be from the Ubuntu array-cds?

Thanks

---

### Post by az on 2005-04-10
[http://www.knoppix.net/wiki/Win_Partition](http://www.knoppix.net/wiki/Win_Partition)


There is no mention of that here.

---

### Post by EndersGame on 2005-04-10
[QUOTE=azz][http://www.knoppix.net/wiki/Win_Partition](http://www.knoppix.net/wiki/Win_Partition)


There is no mention of that here.[/QUOTE]
 "5. Now, open Notepad, and load the file C:/BOOT/GRUB/menu.lst. Check to make sure that each step matches your HD configuration. Exammine the boot stanzas **and add any cheatcodes for persistent home, saved configuration, or whatever you may use.**"

I'm not sure I completely understand, though.  Maybe this is beyond me and I should just wait until I can get my hands on a cd. :-/

---

### Post by az on 2005-04-10
That would be for running knoppix and taking advantage of the persistent home and other settings.   The point is, the grub installed under windows is able to access the iso image and boot it.

Lemme know if this works.

---

### Post by vegetto on 2005-04-10
Please can anyone explain what i should add to menu.1st to start install from the ubuntu iso.

---

### Post by EndersGame on 2005-04-11
Just to let you know, I chickened out on this one.  Thanks for the help though.

---

### Post by dubside on 2005-04-12
I'm bumping this because I also need help with editing menu.lst to access the ubuntu iso on my c:\ drive (the installer doesn't like my cd-rom drive).

I've pasted the text of the .lst file below, deleting additional titles that I'm pretty sure aren't needed (like options to boot from older kernels of knoppix). How should I edit this to boot from, say, C:\BOOT\Ubuntu 5.04.iso?

Sorry if this is basic stuff, but I'm entirely new at this...




######################################################
# GvR Dec 16th 2004
	color black/cyan yellow/cyan
	timeout=5
	default=0

title Default Boot on HD 0
	rootnoverify (hd0,0)
	chainloader +1
	boot

# Knoppix Boot from a single NTFS partition hda1:
# All the files within the directory "Root_Of_NTFS" of the grubd.zip
# have to be copied into the root of the NTFS hda1 partition c:\
# but the boot.ini file (which is just here as an example,
# the line "c:\grldr="Start Grub" has been added at the end of the boot.ini)
# Copy the also the 700MB knoppix ISO file into c:\boot\knoppix.37\ directory

title Knoppix 3.7 kernel 2.6 from NTFS hda1 ISO scan ramdisk=32MB
	kernel (hd0,0)/boot/knoppix.37/linux26 ramdisk_size=100000 init=/etc/init lang=us apm=power-off vga=791 nomce quiet bootfrom=/dev/hda1/boot/knoppix.37/*.iso config=scan home=scan ramdisk=32768 noprompt
	initrd (hd0,0)/boot/knoppix.37/minirt26_ntfs.gz
	boot

---

