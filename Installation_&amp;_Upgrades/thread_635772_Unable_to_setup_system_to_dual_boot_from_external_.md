---
title: "Unable to setup system to dual boot from external USB HDD"
date: 2007-12-09
forum: Installation &amp; Upgrades
---

### Post by nogoodatcoding on 2007-12-09
I'm trying to setup dual booting on my system with Ubuntu 7.10 booting from an external USB HDD but my laptop doesn't support booting from USB devices. I've looked around the forums and gone through some of the topics and seen [a HOWTO on the community documentation]("https://help.ubuntu.com/community/BootFromUSB") for exactly this case but I haven't been able to make much headway.

**Here's my configuration:**

- HP dv1000 series laptop 
- 1GB RAM 
- 80GB internal HDD (hd0 under grub, I believe. Shows up as sda under GParted)
- 80GB external USB HDD (hd1 or sdb)

**My partition setup:**

```
hd0 or sda or internal HDD:
- **sda1** - Win 98
- **sda2** - Extended Partition
    - **sda5 **- Win XP
    - **sda6** - Data partition
    - **sda7** - Data partition
    - **sda8** - Data partition
    - **sda9** - ext3, 100 MB boot partition, 
                            for booting from internal drive 
                            as the HOWTO suggested

hd1 or sdb or external USB HDD:
- **sdb1** - Ubuntu 7.10
- **sdb2** - Extended Partition
    - **sdb5** - Swap, 1GB
    - **sdb6** - Data partition
    - **sdb7** - Data partition

```
What I want: My current Windows setup remains untouched and I want to be able to run Ubuntu off the external HDD.

What happens: I had initially tried the Live CD but the installation used to freeze at 15%. A search through the forum suggested using the alternate CD and I was able to install using that. On rebooting, however, I simply reach the NTLDR selection screen. My reasoning is because the laptop doesn't support booting from the USB HDD.

I also tried installing grub to the internal HDD (not the partition hd0,1 but hd0) and I get an Error 21 on booting. I used the Win XP installation CD to fixmbr and restore the NTLDR but that gets me back to being unable to boot Ubuntu.

The topics I've seen and the HOWTO suggest ways out with grub already installed and modifications to the menu.lst. But I'm lost there, I don't understand where to find those files. If I install grub to the MBR of the internal HDD, where do I find them?

[B]_Currently, as I understand it, I'm supposed to do this:_
1. Install Ubuntu - Done
2. Install GRUB - Where? To the MBR of hd0? How? Where do the config files go?
3. Copy initrd and vmlinuz to the boot partition so that GRUB can load the kernel from the internal HDD and then that should be able to load the USB filesystem
4. Modify grub's configuration so it knows to look in the boot partition for these files - Where would I find the files (menu.lst etc. )?[/B]

Could someone please point in the right direction on how to do all this? I'm fairly competent with computers but a complete Linux newbie and a lot of the terminology is incomprehensible to me and I'm unaware of most commands. I think I've used the partition names correctly but I might be wrong!

Thank you for your patience :)

---

### Post by confused57 on 2007-12-09
You might want to see if Super Grub Disk can boot Ubuntu on your external drive:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

If you're able to boot Ubuntu, using SGD, you might want to consider WinGrub:
[http://users.bigpond.net.au/hermanzone/p9.html](http://users.bigpond.net.au/hermanzone/p9.html)
I've never personally used WinGrub, but it could be an option or it might not be capable of booting Ubuntu on a 2nd hard drive.

The easiest way would be to use SGD when you want to boot into Ubuntu.

---

### Post by logos34 on 2007-12-09
This can be a hard one.

You could certainly try using SGD, as confused57 suggested.  

I think you may have gone wrong here:
> I also tried installing grub to the internal HDD (not the partition hd0,1 but hd0) and I get an Error 21 on booting.

If you wrote grub to the mbr pointing to the root partition on the usb drive, it won't work.  It needs to point to the menu.lst on the boot partition sda9.

Try this:
Boot from the ubuntu live cd and click on sdb1 in nautilus file manager (Places>computer) to mount.  It should do so at '/media/disk'.  Then click on sda9 to mount--it should do so at '/media/disk1'.  Copy the whole /boot folder (including grub subdirectory) from the usb to sda9. 

sudo cp -r /media/disk/boot /media/disk1

Reinstall grub to the mbr (hd0), using [this guide]("http://ubuntuforums.org/showthread.php?t=224351"):

>find /boot/grub/stage1

[should output two locations: (hd1,0) and (hd0,8 ).  You want the latter.]

EDIT: the 'smilies' are getting in the way.  that's **hd0,8**

>root (hd0,8)  
>setup (hd0)
>quit

Edit menu.lst on the boot partition sda9.  

sudo gedit /media/disk1/boot/grub/menu.lst

Change the ubuntu entry to this:

> title  Ubuntu 7.10
root   (hd0,8)  [-->again, **hd0,8**]
kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/sdb1 ro splash [or just keep the 'root=UUID=...' format]
initrd /boot/initrd.img-2.6.22-14-generic 

The windows entry at the bottom should look like this:

> title		Windows 98
root		(hd0,0)
savedefault
makeactive
chainloader	+1

If it works and you would prefer to use the windows booloader (NTLDR) to boot linux, you could try using wingrub as confused57 suggested--again, make sure to point it to the boot partition on sda9.

Give that a shot.  Hope i got the paths right.  This can be a tricky one when it works at all.  

If you get it working you might also [add an fstab entry]("http://www.psychocats.net/ubuntu/mountlinux") for the boot partition sda9 so you can access it in ubuntu.

Good luck.

---

### Post by nogoodatcoding on 2007-12-10
Thank you confused57 and logos34, I'll give your suggestions a shot.

Unfortunately though, I only have time on weekends and since it's just the start of the week, it's going to be long wait for me before I can try my hand at anything :(

If I do manage something, I'll post back. Otherwise it's the Live CD for me!

---

### Post by nogoodatcoding on 2008-01-04
Well, I finally got around to trying out the suggestions here and, yay!, got Ubuntu up and running with logos34's steps. So thank you logos34!

I did face a problem after this though, the start up would just freeze with only a fraction of the progress bar 'lit up'. I then booted with the safe mode which showed the system stopping at these lines:

```
8139cp 0000:06:00.0 This (id 10ec:8139 rev 10) is not an 8139c+ compatible chip
8139cp 0000:06:00.0: Try the "8139too" driver instead
sd 2:0:0:0: [sdb] Assuming drive cache: write through
```

I Google'd "***is not an 8139c+ compatible chip***" and I reached [this page on the Ubuntu forums]("http://ubuntuforums.org/showthread.php?t=599364") which further led me to [this page on an OpenSuse wiki]("http://en.opensuse.org/SDB:Realtek_8139_Driver_Problem"). I didn't have the problem of the network not working (as I couldn't get Ubuntu to boot in the first place!) but this bit at the bottom of the page caught my eye:

***As of 27 May 2007, in kernel 2.6.21.3, you may experience the issues with the r8169 driver if you dual boot Windows on some systems. Windows by defaults disables the NIC at Windows shutdown time in order to disable Wake-On-Lan, and this NIC will remain disabled until the next time Windows turns it on. The r8169 driver in the kernel does not know how to turn the NIC on from this disabled state; therefore, the device will not respond, even if the driver loads and reports that the device is up. To work around this problem, simply enable the feature "Wake-on-lan after shutdown." You can set this option through Windows' device manager.***

So I went to Device Manager on Win XP and modified a few of the wake up settings (wasn't sure which one exactly) and voila! Everything worked great!

Another problem I had was that I copied some stuff around in Windows and when I booted up Ubuntu, fsck declared those newly copied files as corrupted or some such and truncated them! And later, in another session, I created a folder in Linux which was invisible in Windows :/ A little Google'ing points towards improperly unmounting of filesystems but I'm not well-versed enough to be able to recreate or figure out the problem as of now.

Apart from this, I've had no further problems, my NIC and wireless card both work, audio is great, resolution is perfect... Everything seems to be going fine for now :)

So again, thanks guys. Hope this post helps out someone else sometime.

---

