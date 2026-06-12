---
title: "New install; no drives for install..."
date: 2010-09-07
forum: Installation &amp; Upgrades
---

### Post by sinecosine314 on 2010-09-07
Hello all,

I just purchased an HP HPE-210f (AMD Phenom II quad core).  I would like to run Win7 and Ubuntu side by side.  However, at step 4 of the installation (from USB drive) where the installer is trying to repartition the drive, the installer does not seem to recognize the disk... very odd.  I've never had this problem before installing Ubuntu.  The drive does not "show up" on the list of possibilities.  There is simply nothing there!  Any ideas?!?

---

### Post by Mark Phelps on 2010-09-08
Could also be that HP formatted your drive with the maximum number of partitions, so the installer sees nowhere to create any partitions.

Boot into a LiveCD, open a terminal, run "sudo fdisk -lu" (that's a lowercase L, not a one) and post the results back here.

IF you already have all four primary partitions allocated, it is going to be a LOT of work to install Ubuntu.

---

### Post by sinecosine314 on 2010-09-08
I think you might be on to something here...  I will run the command later today when I get be to the machine and post the results.

Here is a little more info...  I booted the live usb stick and instead of running the installer, I went with the "Try Ubuntu" to get Ubuntu up.  I ran gParted to shrink the Win7 partition (which worked fine) to 300Gb leaving Ubuntu with 700Gb.  I then created a new partition as an ext4 filesystem and that seemed to work fine also.  My thought was the maybe now the installer would see the ext4 filesystem.  But, alas, to no avail...  Any thoughts on that?

Now, thinking about what you said in your post, it may be that there are more than 4 partitions because if I remember correctly, the was a Win7 partition, a "recover" partition and even another on that I cannot remember.  With the new ext4 filesystem, that makes 4... there may have another one yet, but I cannot remember.

---

### Post by lechien73 on 2010-09-08
It has been documented that the dmraid driver can cause problems with the installation - even if you don't have RAID installed. This prevents the installer from seeing your hard disks.

If you can boot in with the LiveCD, then try the following:

[LIST]
[*]Open a terminal window and type:

```
sudo apt-get remove dmraid
```

[*]Then try the installation again by double-clicking on the Install icon on the LiveCD desktop.
[/LIST]

---

### Post by ronparent on 2010-09-08
To clarify the issue. Dmraid usually is a problem if meta data has been written to the drive - often inadvertent or left over from a drives previous life. I don't personally recommend removal of dmraid unless meta data present has been erased. Otherwise the problem will return to haunt you if dmraid is reintroduced by an upgrade or reinstall, and, you probably won't remember the specifics well enough to cope with it then.

---

### Post by ahmed002 on 2010-09-08
I have the exact system i.e. HPE-210F and the same problem with 10.10 beta. ** Removing dmraid did the trick for me.** Otherwise the installer would not even see the disk although fdisk did.  I used fdisk before to create the extended partition once i had shrunk the Windows 7 partition.

Previously i played with all sorts of BIOS settings such as changing to AHCI and IDE but no joy.   I was about to give up and return the system when i maracously stumbled upon this thread!   The installation is happening as we speak, if something goes wrong (as suggested by ronparent)  after installation then i'll report back.

---

### Post by ahmed002 on 2010-09-08
So the install when just fine.  Grub installed fine.  However the system dropped to the initramfs prompt because it could not find the root device.  It was looking for the device via its UUID.  On the initramfs prompt i changed root=/dev/sda5 the old fashined way and the system booted fine.   I am going to make the corresponding change manually in grub.cfg via vi.  I am old fashioned guy.  Maybe there is a better way to solve all this and not touch grub.cfg?

Also the UUID's seem to work fine in /etc/fstab.

---

### Post by sinecosine314 on 2010-09-08
WOW!  You guys are all awsome!  Thanks much!  I have a working (almost) system by following everyones advise.  For future readers, here is what I've done so far:

1. Booted LiveCD.
2. Started a terminal
3. Removed dmraid with the command: **sudo apt-get remove dmraid**
4. Ran "Install Ubuntu 10.04 LTS" from the desktop icon, starting up the installer
5. Restarted when prompted
6. Selected Ubuntu from the GRUB menu
7. Boot dropped into initramfs
8. At (initramfs), I typed: **root=/dev/sda4**
9. At (initramfs), I typed, **exit**
10. Ubuntu boots

Yea!  amed002 talks about editing grub.cfg.  I'm not sure about this...  From what I see in the documentation, users are not supposed to edit grub.cfg as it is a generated config file.  The grub documentation look a bit complicated for an old guy like me! ;-)  How do I fix this initramfs issue at boot?

---

### Post by chrissk_2 on 2010-09-09
Removing dmraid also removes Ubiquity so the installation can not proceed. Is there a way around this ? 

Also how can we fix the disk metadata so that dmraid does not get confused ?

---

### Post by lechien73 on 2010-09-09
> **sinecosine314 said:**
> The grub documentation look a bit complicated for an old guy like me! ;-)  How do I fix this initramfs issue at boot?

When you have booted in to Ubuntu, does it make any difference after opening a terminal window and running:

```
sudo update-grub

```

You could always download and run Boot Info Script from [http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net). Then post the contents of the results.txt file here, so that we can see your Grub configuration.

Glad we're getting there :)

---

### Post by sinecosine314 on 2010-09-10
Actually, I have not had to do anything else!  After doing the procedure I wrote a few posts back, everything has been working fine.  The machine boots normally into either Ubuntu or Win7... not that I'm going to use Win7! :D  Thanks, again, everyone that helped!

---

### Post by lechien73 on 2010-09-10
Glad to hear it - you're welcome! Please could you use the **Thread Tools** menu at the top of the page and mark the thread as [SOLVED] when you get chance?

Thanks

---

### Post by oldfred on 2010-09-10
If the drive has raid meta data:

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discussion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by ahmed002 on 2010-09-13
Actually now i have a much better understanding.  There is no need to reconfigure grub or manually provide root=/dev/sda4 etc.  The whole issue is with "ata2 link is slow to respond" and Linux trying to set the BlueRay/DVD drive to 1.5mbs and then giving up.  This whole thing is taking so long that the system jumps to the initramfs prompt.  The workaround is to either wait about 30 seconds on initramfs and then just type exit OR disable the DVD/BlueRay drive in the BIOS.  Disabling obviously is not the desired solution however the boot is really fast after that.  Another thing, since i have disabled the DVD drive in the BIOS, my eth0 has stopped working.  It does show up under ifconfig but cant cant an ip via dhcp.  I manually configured it with IP and still i could not ping my router.  I don't know if this is just a co-incidence.  For now i am using the Wi-Fi connection.

I am sure there is a better workaround.  Maybe some kernel boot argument that i can give to ignore the DVD drive and  or

---

### Post by ahmed002 on 2010-09-14
So the plot thickens.  The Blue Ray/DVD drive model is  HP BDDVDRW CH20L.  After the ata timeouts it is actually totally disabled by Linux and it is not usable at all.  I am testing this on 10.10 Beta.  So it appears that this particular model is not supported yet by a Linux driver.  Not sure what is so unique about this Drive.   As a whole i would not recommend anyone to buy the HPE-210F if they are serious about running Linux on it.  I have also not been able to get Desktop Effects (Compiz) working both with the open sourced or the properiety driver from ATI :-(

---

### Post by nyteryder79 on 2010-10-31
Ubuntu 10.04 and 10.10 do not currently have support for your HP blu-ray drive.  I had to disable the SATA port in BIOS on my Pavilion Elite and install Ubuntu from a flash drive.  I submitted a bug and hopefully it gets looked at and addressed soon as this machine is a popular on as is this blu-ray drive.  Right now I'm using an external dvd-rw drive I had for my netbook.

---

