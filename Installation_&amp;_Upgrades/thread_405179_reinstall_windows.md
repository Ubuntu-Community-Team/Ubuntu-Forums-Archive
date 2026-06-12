---
title: "reinstall windows"
date: 2007-04-09
forum: Installation &amp; Upgrades
---

### Post by onefallinghope on 2007-04-09
Hello, this is my first post in the Ubuntu forums, so if this has already been addressed, my apologies.

I have been using Ubuntu for a while on several machines, and it has been the easiest to use and install distro that I have ever used over the past 6 years or so that I've been playing with Linux.

Saturday I built a new Dual Boot box.

First I installed Windows Small Business Server 2003 to a raw drive.  The drive was 160GB, during windows partiton I chose to give 40GB to windows and format as NTFS, i left the rest of the disc as unallocated space.  After the windows install finished, I popped in my 6.10 CD and went through the install, telling it to use the rest of the space on the drive.  During the install process GRUB detected my Windows installation and put it into the bootloader.  Then I updated Ubuntu to 7.04 by going to terminal and typing "update-manager -d"  All went well, and I have a wonderful dual boot system.

Except that I have no idea why I installed Windows Server 2003, when I really want XP.  So, I grabbed my XP disc and booted up with that, when it gets to the installation screen Windows setup only sees one large unallocated drive.  I had hoped it would see the 40GB that windows is already installed onto, and that I could just install a different version of windows.  

Can anyone tell me what I need to do to replace my Server 2003 installation with XP, while retaining my 7.04 install and still have GRUB work?  Or would I be better off wiping the whole drive and starting over?

Thanks,
Bill

---

### Post by LukeCarrier on 2007-04-09
Hi Bill,

Personally I would recommend you format the drive and start a fresh, as from past experience I have found that Windows always seems to edit the boot record, preventing Grub from starting, this has occurred every time I re-installed XP.

That does not mean you can't try simply upgrading to XP the way you normally would, after all if Grub fails to start after installing XP you'll have to start from scratch, but if it works you won't have to do the full format again. You never know, it might work.

As you probably know, it's best to avoid having Windows and GNU / Linux on the same hard disk, or even the same computer. If you can, have one box for Ubuntu and another for Windows. That way you never have to worry about this sort of problem.

Good luck,
Luke Carrier.

---

### Post by bulldog on 2007-04-09
Reinstalling GRUB is the least of your problem.:) 

You can try the GParted live cd ,to see if this program recognize the partitions as they should be.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
Just burn the ISO as an image on a cd-r and boot from it.

If you can see your partitions reformat the 40GB server partition and try to reinstall XP on that partition.
This woul remove GRUB but that's easy to solve with the live cd. [any live cd will do]
Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```

It's not a problem to have a dual boot machine,or even install Ubuntu and windows on the same hdd,just try to install windows on the first primary partition.

---

### Post by onefallinghope on 2007-04-09
Thanks Bulldog, Ill give that a shot.  In my past experience its not a big deal to have Windows and Linux on the same box, usually not to probematic.  Last year I had a triple boot machine that was doing Ubunut, XP and OSX86, that also was problem free.

Like I said, Im going to give what bulldog said a try...  It's really no big deal if i have to reformat this machine. I just thought that I shoudl know how to do what I was trying to do.  I DO have another machine with windows on it.  4 of them in fact, and 7 Macs running different flavors of OSx, and another few old SE's running system 7, another machine running strictly ubuntu, a box running Solaris (meh...) and my old (OK, ANCIENT) North*Star Horizon and its 8inch floppies.  Amongst other Atari, Amiga and Commodore machines. 

I just would like to reinstall windows to take the "Lazy man route" because I have Feisty configured JUST how I like it.  but, that only took about a day so if i cant get it going then I'll just reinstall.

The reason for the dual boot is to prove to a group of naysayers that I know that with the limited specs of this machine (AMD Athlon 1.3, 384 MB ram, Creative live Multi channel sound card, 9in1 media card reader, DVD drive, and BFG NVidia Radeon 7300 OC graphics card) That I am able to:

A- Run warcraft through WINE in Linux

B-Warcraft through WINE on this machine runs BETTER and with DOUBLE the FPS than it does on an Actual Windows box of the same hardware.  And,

C-That Beryl, Ubuntu, and Warcraft through WINE all work perfectly on this "old junk" machine - allowing people to rotate the cube and check for stuff on the web.

So, really its a tech demo - plus this machine has the best GFX card I have, so I also play FFXI and I was going to install that in the windows partition of this machine - since FFXI does not work with WINE.

I'll follow up and let everyone know what worked or didn't work for me a bit later.

Thanks again.

/Bill

---

### Post by onefallinghope on 2007-04-09
OK, just a follow up.

I didnt bother with the gparted iso that bulldog mentioned, I just grabbed a more recently pressed XP Pro install disc (I have a MSDN subscription) and booted off of that.

The new XP disc saw all of my partitions as they should have been.
I selected the partition that had Server 2003 on it, deleted that partition, then let the windows installer reformat that partition NTFS and installed XP Pro to it.

This of course DID overwrite GRUB  so, I popped my Edgy Live CD into the drive booted off of that and followed Bulldogs instructions from above.

as Emeril would say, BAM!!, everything was back as it should be.

Now when I boot GUB shows all of my different kernels, and my Windows installation - and they all work.

The only small hang up now is that my Windows partition is still called Server 2003 on the grub menu.  But i think that cant be too hard to change...  I'll see what google has to say on THAT subject.

Thanks again everyone, my problem has been cleared up!!

/Bill

---

### Post by chollis888 on 2007-04-09
well that's easy enough to fix:

```
 sudo gedit /boot/grub/menu.lst
```Look for the Title Server 2003 and change it, save and exit. It should be last or atleast toward the bottom.

---

