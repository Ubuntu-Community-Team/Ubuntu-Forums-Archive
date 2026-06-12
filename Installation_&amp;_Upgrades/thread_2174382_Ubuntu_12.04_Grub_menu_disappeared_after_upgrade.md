---
title: "Ubuntu 12.04: Grub menu disappeared after upgrade"
date: 2013-09-14
forum: Installation &amp; Upgrades
---

### Post by stovebolt_824 on 2013-09-14
Hi,

I had a working dual boot configuration with Vista and Ubuntu 11.10.  I upgraded to 12.04 and I no longer get the grub menu on startup - Ubuntu is booted automatically.

I've tried updating and reinstalling grub and I think this all looks ok:

```
stuart@HOME-PC:~$ sudo apt-get clean
stuart@HOME-PC:~$ sudo apt-get autoclean
stuart@HOME-PC:~$ sudo apt-get autoremove

stuart@HOME-PC:~$ sudo update-grub2
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-53-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-53-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-52-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-52-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-51-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-51-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-49-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-49-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-48-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-48-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-45-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-45-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-44-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-44-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-43-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-43-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-41-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-41-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-40-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-40-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-39-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-39-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-38-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-38-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-37-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-37-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-36-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-36-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-35-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-35-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-29-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-29-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda2
done

stuart@HOME-PC:~$ sudo grub-install /dev/sda
Installation finished. No error reported.


```

Here is my fdisk and blkid output. 

```


stuart@HOME-PC:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb37a81e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    14329979     7164958+  12  Compaq diagnostics
/dev/sda2   *    14329980   131648916    58659468+   6  FAT16
/dev/sda3       131649534   163814804    16082635+   5  Extended
/dev/sda4       163814805   312576704    74380950    7  HPFS/NTFS/exFAT
/dev/sda5       131649536   162367487    15358976   83  Linux
/dev/sda6       162369018   163814804      722893+  82  Linux swap / Solaris

Disk /dev/sdb: 2000.4 GB, 2000396746752 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907024896 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00197fcd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048  3907024895  1953511424    7  HPFS/NTFS/exFAT

stuart@HOME-PC:~$ sudo blkid
/dev/sda1: LABEL="PQSERVICE" UUID="E6E41B2116D9B5D2" TYPE="ntfs" 
/dev/sda2: LABEL="ACER" UUID="2ED4F4AED4F47A03" TYPE="ntfs" 
/dev/sda4: LABEL="DATA" UUID="7E784B2D784AE40D" TYPE="ntfs" 
/dev/sda5: UUID="ad31f9e6-a6e6-409a-ae75-25512a4300c1" TYPE="ext4" 
/dev/sda6: UUID="7718f28a-65b3-41e6-8113-78907074b5d8" TYPE="swap" 
/dev/sdb1: LABEL="WD-Elements" UUID="80EC-F7EB" TYPE="vfat" 


```

I've tried a BootRepair from a LiveCD but it didn't make any difference.  The report is [here]("http://paste.ubuntu.com/6105454/").

I think I've exhausted my (fairly limited) expertise, so any tips or suggestions would be very much appreciated. 

Stuart

---

### Post by ajgreeny on 2013-09-14
Unfortunately I can not really help with the non-booting windows problem, or lack of grub menu other than suggesting you hold shift at boot to get the grub menu to show, then try booting windows from that, though it looks as if your grub.cfg file does not include a normal menuentry for windows, and that os-prober is having some problems finding windows properly.

Can you quickly check the output of ```
ls -l /usr/bin/os-prober
``` and report back here what it says.

---

### Post by stovebolt_824 on 2013-09-14
Hi,

Thanks for the response.  The output of the command is:

```

stuart@HOME-PC:~$ ls -l /usr/bin/os-prober
-rwxr-xr-x 1 root root 4198 Apr  4  2012 /usr/bin/os-prober

```

I tried holding shift during the boot, and I briefly saw a message saying "Loading GRUB" but then the input to the monitor was lost for a period (I got the monitor message saying "input not supported") before it booted into Ubuntu.  Note I also get this behaviour during a normal boot (without holding shift), just without the "Loading GRUB" message. Is it maybe attempting to display the grub menu but having some sort of display problem, then choosing the default Ubuntu boot option?  

Thanks,
Stuart

---

### Post by grahammechanical on 2013-09-14
You should be getting a Grub  menu because Boot Repair reset the Grub menu timeout back to 10 seconds. Setting the Grub menu timeout to 0 seconds will stop the Grub menu from appearing. You can check this by opening /usr/share/grub/default/grub and looking for the line

> GRUB_TIMEOUT=10

If it is zero ( o ) then there will not be a Grub menu. But I suspect that the reason why you are not getting a Grub menu now is because Ubuntu is the only OS found on the hard disk. Go to the end of that boot repair report where you see

> generating grub.cfg

in the printout you will not see any mention of a Windows OS. Yet in your printout of generating grub.cfg we see

> Found Windows Vista (loader) on /dev/sda2

Try running

```
sudo update-grub
```

again and see if Windows is detected. If it is then run again
```
sudo grub-install /dev/sda
```

Oh, by the way, update-grub and update-grub2 do the same thing. They are just scripts that launch the same Grub utility.

Regards.

---

### Post by oldfred on 2013-09-14
Your sudo update-grub showed you found Windows, but you have to lot of kernels. Only so many are shown on first grub menu screen. If you have a tiny (really tiny) arrow at bottom right then you have more entries and can just scroll down to Windows entry at bottom.

Probably best to houseclean old kernels. I like to keep one old one, but if you just upgraded all the old versions may not work anyway.

       
Determine your current kernel:
uname -a
uname -r
In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
cd /boot
ls vmlinuz*
sudo apt-get purge  linux-image-[version]-generic linux-image-[version]-generic
Multiples, just be sure not to delete your current kerne.:
sudo apt-get purge linux-image-3.5.0-{XX,XX,XX,XX,XX,XX}-generic
Example:
sudo apt-get purge linux-image-3.5.0-{17,18,19,21,22,23,24}-generic

---

### Post by stovebolt_824 on 2013-09-14
OK I'll try and address all of the points above. My /usr/share/grub/default/grub contains the following, so think the timeout is ok.

```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

My kernel version is as follows:
```
uname -a
Linux HOME-PC 3.2.0-53-generic-pae #81-Ubuntu SMP Thu Aug 22 21:23:47 UTC 2013 i686 athlon i386 GNU/Linux
uname -r
3.2.0-53-generic-pae
```

I cleaned down the previous kernel versions as advised and re-ran update-grub, output as follows:
```

sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-53-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-53-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda2
done
```

So looks like it found Windows as expected. I reinstalled grub as follows:

```
sudo grub-install /dev/sda
Installation finished. No error reported. 
```

But on reboot I still don't get any grub menu.  It seems to sit on "Attention: Input not supported" for almost 30 seconds now before booting into Ubuntu.  Is it worth re-running boot repair?

---

### Post by oldfred on 2013-09-14
Perhaps a video mode not supported? Grub has this setting. You can uncomment the gfxmode. And you can at grub menu by going to grub command line if you get menu to show, so you can use a better setting.

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

---

### Post by stovebolt_824 on 2013-09-14
Hurrah it works!  As suggested, I uncommented the GRUB_GFXMODE then ran update-grub and it fixed it. 

```
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=640x480 
```

Note I had to update /etc/default/grub rather than /usr/share/grub/default/grub as the latter seemed to have no effect.  Can anyone explain the difference between these two files?

Thanks for all the help anyway, much appreciated. 
Stuart

---

### Post by Quackers on 2013-09-14
I think what happened is that you ran update-grub then re-installed grub, so effectively got a default grub back.
Once you subsequently ran update-grub again your Windows system appeared again.

And yes, you needed to change /etc/default/grub not /usr/share/grub/default/grub.

---

### Post by stovebolt_824 on 2013-09-15
Ok that makes sense. Thanks all.

---

