---
title: "Booting from floppy to thumb drive (flash drive)."
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by theaceoffire on 2008-07-10
[SIZE="5"][COLOR="Blue"]Explination.[/COLOR][/SIZE]
So we have some old (OLD) computers that we were going to get rid of, and I decided to see if I could manage to scrap something useful out of them.

They are Hatachi's, with a 450MHz processor, 128MB of ram, a floppy drive, cd drive, and 2 usb slots. Fat 16 file system, and running Windows 2000. 

So I grab a copy of xubuntu and try to get em goin. Set the bios to boot floppy, cd, hard disk, and stick in the disk... nothing. 

Reburn the image, try again: nothing. 

Make a boot disk, choose CD, it works! (oops, forgot to alternative instal... it crashes). 

Try again, it tells me that it is getting an error (0x44 i believe, no cd inserted). This continues 99% of the time, randomly deciding to let me boot from a disk.

So I say to myself, "Self! I refuse to continue messing with this cd drive. Maybe there are other options". And indeed there were. 

This is the story of me, one computer, and pain. 

[SIZE="5"][COLOR="Blue"]The Battle Begins.[/COLOR][/SIZE]
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
[SIZE="4"][COLOR="DarkOliveGreen"]Attempt 1).[/COLOR][/SIZE] Insert disk. Can't read disk. Burn new disk, run disk check... no errors. Won't boot. 
[SIZE="4"][COLOR="DarkOliveGreen"]
Attempt 2).[/COLOR][/SIZE] Used [[COLOR="Red"]rawwritewin.exe[/COLOR]]("http://uranus.it.swin.edu.au/~jn/linux/rawwrite-old.htm") to burn a copy of [[COLOR="Red"]sbm.bin[/COLOR]]("http://www.filewatcher.com/m/sbm.bin.1474560.0.0.html") that I got from an Ubuntu install cd to a floppy. Its easy to use, just click the start, select the image (Had to choose "view all" since it is not an img file), and run. 

This worked by the way, it let me boot from the cd... but then my cd issues started up. It was not registering any cd being entered at all (God it is old hardware). So I moved on. 
[SIZE="4"][COLOR="DarkOliveGreen"]
Attempt 3).[/COLOR][/SIZE] Found an *awesome* program called [[COLOR="Red"]unetbootin[/COLOR]]("http://lubi.sourceforge.net/unetbootin.html"). Everything was going great, got all base files installed... when it hanged while installing software. (Again, I blame old computer.. can't believe it still runs). It worked great though... I am keeping a copy of this for the future. This program lets you install an OS to a hard disk or thumb drive, either from an ISO, a cd, or from a list that it will go online and download what you need. Then you reboot and select the second option, which does what you ask. Keep an eye on this.

[SIZE="4"][COLOR="DarkOliveGreen"]Attempt 4).[/COLOR][/SIZE] Started looking for more floppy images. Lots more. Some I found were [[COLOR="Red"]superGrubDisk[/COLOR]]("http://www.supergrubdisk.org/index.php?pid=6"), which didn't have usb support (sigh). Anywho, I probably didn't know enough to use it right (too complicated?)

[SIZE="4"][COLOR="DarkOliveGreen"]Attempt 5).[/COLOR][/SIZE] Tried to do a net install. Got the idea from [[COLOR="Red"]Ubuntu's installation[/COLOR]]("https://help.ubuntu.com/community/Installation") guides, the one about [[COLOR="Red"]netbooting floppies[/COLOR]]("https://help.ubuntu.com/community/Installation/WithFloppies"). 

Basically I used the same program as before ([[COLOR="Red"]rawwritewin.exe[/COLOR]]("http://uranus.it.swin.edu.au/~jn/linux/rawwrite-old.htm")) to create 3 floppies: [[COLOR="Red"]boot.img[/COLOR], [COLOR="Red"]root.img[/COLOR], [COLOR="Red"]net-drivers.img[/COLOR].]("http://ftp.egr.msu.edu/debian/dists/sarge/main/installer-i386/current//images/floppy/")

The idea is you boot from boot.img, then add the next two which enable your network, and then download your OS from online! However, it failed. The boot disk gave me an error (Something like "Booting linux: failed) so I had to move on. On a side note, that same image worked on a virtual computer at home later that day, go figure. 

[SIZE="4"][COLOR="DarkOliveGreen"]Attempt 6).[/COLOR][/SIZE] I grabbed an external hard drive, mounted [[COLOR="Red"]Xubuntu[/COLOR]]("http://www.xubuntu.org/get#hardy") in [[COLOR="Red"]deamon lite[/COLOR]]("http://http://www.daemon-tools.cc/dtcc/download.php?catid=5&mode=ViewCategory"), and copied all visible and hidden files to the root of the external hard drive. Moved to the computer, plugged it in, and tried to run [[COLOR="Red"]superGrubDisk[/COLOR]]("http://www.supergrubdisk.org/index.php?pid=6") to boot into it... but couldn't figure out how to access the usb hard drive. 

At this point, it was pretty clear I needed a floppy boot disk with usb drivers on it.

[SIZE="4"][COLOR="DarkOliveGreen"]Attempt 7).[/COLOR][/SIZE] Lucky (I hope, haven't done this yet). Found someone online who suggested using the [[COLOR="Red"]pendrivelinux floppy image[/COLOR]]("http://pendrivelinux.com/downloads/pdlfloppy.img.gz"). This lets you boot to a usb with the pendrive os on it, and it uses grub, so I figure I can modify its target to activate the "cd"'s I have stored on my 4GB, partitioned thumb drive (Got XP essentail and Xbuntu Alternate install on it). 


[SIZE="5"][COLOR="DarkRed"]To Be Continued...[/COLOR][/SIZE]
I will update as I keep trying... and I would love to have someone else swoop in with a bootable floppy that allows booting USB devices....

---

### Post by logos34 on 2008-07-11
> **theaceoffire said:**
> [SIZE=4][COLOR=DarkOliveGreen]
Attempt 3).[/COLOR][/SIZE] Found an *awesome* program called [[COLOR=Red]unetbootin[/COLOR]]("http://lubi.sourceforge.net/unetbootin.html"). Everything was going great, got all base files installed... when it hanged while installing software. (Again, I blame old computer.. can't believe it still runs). It worked great though... I am keeping a copy of this for the future. This program lets you install an OS to a hard disk or thumb drive, either from an ISO, a cd, or from a list that it will go online and download what you need. Then you reboot and select the second option, which does what you ask. Keep an eye on this.

What about this:

[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)
(-->'CD Approach')

Basically you start up from hard drive and it follows through on (Alternate) CD

It'll probably freeze just like unetbootin when it gets to installing part, but worth a shot.

---

### Post by theaceoffire on 2008-07-11
Thanks, but I think the cd drive is broken. 

Its ok, I figured out how to do it I think.. just need some more floppies to try my idea. 

[SIZE="5"][COLOR="Navy"]My game plan:[/COLOR][/SIZE]

[SIZE="4"][COLOR="DarkGreen"]1)[/COLOR][/SIZE] Get the following programs:
([[COLOR="Red"]rawwritewin.exe[/COLOR]]("http://uranus.it.swin.edu.au/~jn/linux/rawwrite-old.htm")) to create 4 floppies
[[COLOR="Red"]boot.img[/COLOR], [COLOR="Red"]root.img[/COLOR], [COLOR="Red"]net-drivers.img[/COLOR]]("http://ftp.egr.msu.edu/debian/dists/sarge/main/installer-i386/current//images/floppy/")
[[COLOR="Red"]sbm.bin[/COLOR]]("http://www.filewatcher.com/m/sbm.bin.1474560.0.0.html")

[SIZE="4"][COLOR="DarkGreen"]2)[/COLOR][/SIZE] In windows, use rawwritewin.exe to burn the floppy images to floppies (do it to two different floppies, cause at least one will be corrupt/missing files/etc). 

In linux, use the following command to make your floppies:
```
dd if=/path/to/floppy/images/boot.img of=/dev/fd0
```

[SIZE="4"][COLOR="DarkGreen"]3)[/COLOR][/SIZE] Insert the floppy containing boot.img into your drive, reboot. When it shows you a picture and a text input symbol, type "expert" and press enter.

[SIZE="4"][COLOR="DarkGreen"]4)[/COLOR][/SIZE] It will do some stuff, then say "insert root disk or usb". Swap out the boot.img floppy with the root.img one, and press enter. 

[SIZE="4"][COLOR="DarkGreen"]5)[/COLOR][/SIZE] A menu will show up, go down to the option that says something like "Get drivers from floppy".

[SIZE="4"][COLOR="DarkGreen"]6)[/COLOR][/SIZE] Swap out the root.img floppy with net-drivers.img, and press enter for it to be able to access your network stuff. 

[SIZE="4"][COLOR="DarkGreen"]7)[/COLOR][/SIZE] Go down to "detect network devices", run it. It will ask you if you want to give parameters, say no... it will ask if you want to turn on x, y, or z, and say what you want. I went with yes most of the time, although it wasn't needed.

[SIZE="4"][COLOR="DarkGreen"]8)[/COLOR][/SIZE] Go down to "setup network", let DHCP connect, let it remain "debian", make up a name to show the other computers (I went with "sigh"). Let it finish. 

[SIZE="4"][COLOR="DarkGreen"]9)[/COLOR][/SIZE] Go to "Partition hard drive", tell it to delete everything, and to make one partition. (These are default options). 

[SIZE="4"][COLOR="DarkGreen"]10)[/COLOR][/SIZE] Ether go to "go to console window" or press alt-f2 (Press alt-f1 to get back from this window). 

[SIZE="4"][COLOR="DarkGreen"]11)[/COLOR][/SIZE]Time for some code! If everything went right, there is a folder called /target that is the root of your file system. 

```
[COLOR="DarkSlateGray"][COLOR="DimGray"]
/////Make a temp directory//////[/COLOR]
mkdir tempstuff
[COLOR="DimGray"]
/////go there//////[/COLOR]
cd tempstuff[COLOR="DimGray"]

/////Get the file we need from online//////[/COLOR]
wget http://archive.ubuntu.com/ubuntu/pool/main/d/debootstrap/debootstrap_1.0.10_all.deb
[COLOR="DimGray"]
/////back up to the root folder again//////[/COLOR]
cd ..
[COLOR="DimGray"]
/////Extract the stuff from the deb file//////[/COLOR]
ar -x tempstuff/debootstrap_1.0.10_all.deb
[COLOR="DimGray"]
/////Install it.//////[/COLOR]
zcat < tempstuff/data.tar.gz| tar xv
[COLOR="DimGray"]
/////Run debootstrap, to grab the basics we need for ubuntu.//////[/COLOR]
debootstrap --arch i386 --foreign hardy /target http://archive.ubuntu.com/ubuntu
[COLOR="DimGray"]
/////It does stuff here, may take a bit//////[/COLOR]
[COLOR="DimGray"]
/////Now this is where I am still iffy. Here is what is suggested//////
/////By some tutorials: Change root. //////[/COLOR]
chroot /target /bin/bash
[COLOR="DimGray"]
/////Mount proc... don't know what this means, /////
/////but it is very important supposedly. //////[/COLOR]
mount -t proc proc /proc
[COLOR="DimGray"]
/////Edit network, don't know why.//////[/COLOR]
vim /etc/network/interfaces
[COLOR="DimGray"]
////Not sure if this goes in the interfaces, or if it is typed in...////[/COLOR]
auto lo iface lo inet loopback
auto eth0 iface eth0 inet dhcp
[COLOR="DimGray"]
////Change hostname... don't know if this is needed.////[/COLOR]
echo debian > /etc/hostname
[COLOR="DimGray"]
/////Add this to etc hosts:////[/COLOR]
vim /etc/hosts
[COLOR="DimGray"]
/////Stuff to add to the hosts file: not sure if second local host was////
////to be misspelled like that. I added localhost just in case./////[/COLOR]
127.0.0.1 localhost.localdomain locahost debian localhost
[COLOR="DimGray"]
/////Start ubuntu install!/////[/COLOR]
base-config new

[COLOR="DimGray"]
/////It (hopefullY) goes and does stuff! Takes a long time,/////
///// a couple of errors show up (fonts mostly), just let it run./////
///// Go have chocolate milk.////[/COLOR]
[COLOR="DimGray"]
/////Setup language.//////[/COLOR]
dpkg-reconfigure locales
[COLOR="DimGray"]
/////Update our cache./////[/COLOR]
apt-get update
[COLOR="DimGray"]
/////Search cache for a good linux kernel. I use generic myself./////[/COLOR]
apt-cache search linux-image
[COLOR="DimGray"]
/////get kernel so we can boot./////[/COLOR]
apt-get install linux-image-debug-2.6.24-18-generic
[COLOR="DimGray"]
////Get a boot loader////[/COLOR]
apt-get install grub
[COLOR="DimGray"]
////Install it.////[/COLOR]
grub-install /dev/hda
[COLOR="DimGray"]
////Generate it... ? Say "y" if it asks. ////[/COLOR]
update-grub

ctrl+d
reboot[/COLOR]

```

And that *should* be that. 

If anything is still missing after I got my os that far, I can simply run the command "sudo apt-get install ...... oh my god...

[SIZE="6"][COLOR="red"]
HANG ON.[/COLOR][/SIZE]

Found this thread, which is EXACTLY what I needed to know:
[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=213278[/COLOR]]("http://ubuntuforums.org/showthread.php?t=213278")

^_^ Hope this helps someone else!

---

