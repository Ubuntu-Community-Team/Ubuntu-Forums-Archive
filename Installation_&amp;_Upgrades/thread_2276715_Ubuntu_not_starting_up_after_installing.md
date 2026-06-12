---
title: "Ubuntu not starting up after installing"
date: 2015-05-04
forum: Installation &amp; Upgrades
---

### Post by angel mike on 2015-05-04
I have installed Ubuntu 14.04 using a disc on my Gateway and deleted the Windows 7.
I get through the installation process which asks to restart. On restart the Ubuntu opening screen shows briefly but then 3 lines of error messages show up very briefly one of which says'no firmware' then the screen goes blank.
I have tried re-installing twice with the same result.

---

### Post by Bashing-om on 2015-05-04
angel mike; Hello;

Show us what we are working with here for partitioning and what is installed: Assuming a standard desk top install.

Boot the liveDVD(USB) to "try ubuntu" mode;
At the desktop key combo ctl+alt+t yields a terminal;
Post back the outputs - Between Code tags, please - of terminal commands:
```

sudo fdisk -lu
sudo parted -l
sudo blkid

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
With the goal to see if all that is required is to properly install grub (GRand Unified Bootloader).

look'n at the 
[INDENT][INDENT]simple things 1st
[/INDENT][/INDENT]

---

### Post by angel mike on 2015-05-05
> **angel mike said:**
> I have installed Ubuntu 14.04 using a disc on my Gateway and deleted the Windows 7.
I get through the installation process which asks to restart. On restart the Ubuntu opening screen shows briefly but then 3 lines of error messages show up very briefly one of which says'no firmware' then the screen goes blank.
I have tried re-installing twice with the same result.
The output requested by Bashing-om is as follows
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]> [/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]sudo fdisk -lu[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Disc/dev/sda:320.1 GB, 320072933376 bytes[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]255 heads, 63 sectors/track,38913 cylinders, total 625142448 sectors[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Units=sector of 1*512=512 bytes[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Sector size (logical/physical):512 bytes/512 bytes[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]I/O size (minimum/optional):512 bytes/512 bytes[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Disk identifier  0x000328d5[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]sudo parted -l[/FONT][/COLOR]
Model:ATA ST3320833AS(scsi)
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Disk/dev/sde:320GB[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Sector Size logical/physical):512B/512B[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Partition Table: msdos[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Number Start End Size Type File System Flags[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]1 1049KB 318GB 318GB primary ex14 boot[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]2 318GB 320GB 2136MB extended[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]5 318GB 320GB 2136MB logical linux-swap(v1)[/FONT][/COLOR]


[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Model:ATAPI DVD W DH16W1P(scsi)[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Disk/dev/sr0:4700MB[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Sector size (logical/physical):2048B/2048B[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Partition Table:msdos[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Number Start End Size Type File System Flags[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]1 131KB 4140MB 4140MB Primary boot,hidden[/FONT][/COLOR]


[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]sudo blkid[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]/dev/loop0:TYPE=”squashfs”[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]/Dev/sr0:LABEL=”Ubuntu 14.04.1 LTS i386” TYPE=iso9660[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]/dev/sda1:UUID=”6dbede84-8ad2-4cf5-697c-654ea8870f9c” TYPE=”ext14”[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]/dev/sda5:UUID=”1f0397ed-1e80-4e73-879f-9e2695e05700” TYPE=”swap”
Thanks Bashing-om for your help and guidance - the above is copied by hand from the screen - hope no typos !
The disc has been checked for errors using the Ubuntu startup.[/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif] [/FONT][/COLOR]

---

### Post by Bashing-om on 2015-05-05
angel mike; Hey ..

The partitioning looks OK. very small swap partition to small to allow hibernating the machine . Ubuntu boots so fast however that there is no loss with not having the ability to hibernate.

So let's see what results when we install the boot code directly.
Boot the liveDVD to "try ubuntu" mode;
at the desktop key combo ctl+alt+t yields a terminal:
execute:
```

sudo mount /dev/sda1 /mnt
sudo grub-install --boot-directory=/mnt /dev/sda
sudo umount /mnt

```
Reboot now and ->
reset in bios to boot from the hard drive as that 1st boot priority.
Boot up the install of ubuntu.
Now execute terminal command:
```

sudo update-grub

```

Advise on the result.

[INDENT][INDENT]are we buntu'n now ?
[/INDENT][/INDENT]

---

### Post by angel mike on 2015-05-06
[COLOR=#222222][FONT=Times New Roman, serif][SIZE=3]Here is results
> 
Sudo mount /dev/sdal /mnt[/SIZE][/FONT][/COLOR]



[COLOR=#222222][FONT=Times New Roman, serif][SIZE=3]Mount:special device /dev/sdal does not exist[/SIZE][/FONT][/COLOR]



[COLOR=#222222][FONT=Times New Roman, serif][SIZE=3]sudo grub-install &#8211;boot-directory=/mnt /dev/sda[/SIZE][/FONT][/COLOR]



[COLOR=#222222][FONT=Times New Roman, serif][SIZE=3]Installing forvi386-pc platform[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Times New Roman, serif][SIZE=3]grub-install:error: failedto get canonical path of '/cow'[/SIZE][/FONT][/COLOR]



[COLOR=#222222][FONT=Times New Roman, serif][SIZE=3]sudo unmount /mnt[/SIZE][/FONT][/COLOR]
umount: /mnt: not mounted


- - - - - - - - - -


Pressing ctlr+alt+F1 gives access to the terminal after restart with no Live DVD inserted. The screen is blank after startup.


- - - - - - - - - -


sudo update-grub


Generating grub configuration file....
Warning:Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported
Found Linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found memtest86+image: /boot/memtest86+.elf
Found memtest86+image: /boot/memtest86+.bin
done


- - - - - - -
Screen is still blank after restarting with no Live DVD inserted

Thanks

---

### Post by Bashing-om on 2015-05-06
angel mike; Hey hey;

Making progress here on several fronts.
Posting to the thread, once more for your reference:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

As to the mount command it is 'sda1' - a numeral one rather than the letter 'L' .
```

sudo mount /dev/sda1 /mnt
sudo grub-install --boot-directory=/mnt /dev/sda
sudo umount /mnt

```
Got to have a identified target - 'sda1' - for the command to work. (copy and paste commands work well ) 

[INDENT][INDENT]try try again
[/INDENT][/INDENT]

---

### Post by angel mike on 2015-05-06
Ok but cannot copy/paste as do not have system running unless there is a way of using a flash drive or erthenet and transferring info from another computer - likewise copying from screen.  
As for problems posting - for some reason there must be some characters outside the QUOTE marks - perhaps I missed that in the tutorial.
I have done the commands again as indicated below but I now cannot get into the terminal on re-booting. The opening screen showing ubuntu does not show up either. Could it be the installation of the i386-pc platform? No ubuntuing yet. By the way I did install ubuntu on my mini 10 Dell a couple of years ago without problems - maybe Dell has better architecture than Gateway.

> 
sudo mount /dev/sda1 /mnt


mount: /dev/sda1 already mounted or/mnt busy
mount:according to mtab, /dev/sda1 isalready mounted on  /mnt


sudo grub-install –boot-directory=/mnt/dev/sda


Installing for i386-pc platform
Installation finished, No errorsreported


sudo umount /mnt


(No output so entered command againwhich gave'umount: /mnt:not mounted )



---

### Post by Bashing-om on 2015-05-06
angel mike; OK;

This:
> 
installing for i386-pc platform
Installation finished, No errors reported

installed the boot code, and the system is happy with it. SO, what happens now when you boot ?
One may have reset in bios to boot from the hard drive  .
A system problem ??:
> 
The opening screen showing ubuntu does not show up either. Could it be the installation of the i386-pc platform? 

Possible, but I doubt it ; as the plymouth screen loads and runs after grub starts . If it is grub's splash screen we are talking about, that display is optional. We may play with that and see what is set .

And it is the "[code]" tag one uses to maintain the formatting of the relayed info.

[INDENT][INDENT]no sweating the small stuff
[/INDENT][/INDENT]

---

### Post by angel mike on 2015-05-07
I have done some more investigationwhich might givealead.

[LIST=1]	
[*]Starting computer and inserting	the disc the screen shows Ubuntu with the red dots until the	Try/Install screen comes up.
	
[*]Going into the 'Try' sequence	produces a blank screen. Pressing Ctrl+Esc keys accesses the	terminal screen which has the following messages
	* Starting Mount network file systems
	*Stopping Mount network file systems
	[384.219003] nouveau E [  DRM] GPU	lockup &#8211; switching to software fbcom
	
[*]Restarting and going into the	'Install'  &#8211; asks for location /who are you detail/choose delete	existing Ubuntu &#8211; then copies and installs files sand finally a	message saying 'Installation complete Restart'
	Restart and change BIOS to boot on	hard drive and continue with run. Screen is blank except for a brief	show of Ubuntu screen hidden except for a thin border.Then full	Ubuntu screen shows biefly and then screen goes blank.
	Pressing Ctrl+Alt+F2 gives a terminal	screen with various messages  'Welcome to Ubuntu 14.04 etc ' with a	login request then waits for a command. Pressing the keys again	gives '384 packages to be updated etc' other times it gives the	lockup message and then 'Failed to expire sync object before buffer	eviction'
[/LIST]


Hope all that helps

[LIST=1]		
[/LIST]

---

### Post by Bashing-om on 2015-05-07
angel mike; OK;

Now we are looking at a graphics driver issue. A number of ways we can look and check.
Let's examine the simpler way 1st ( for a new user that is).

Boot the install - no disk inserted in the DVD drive -  as soon as the bios screen clears depress and hold the right shift key  (for UEFI system repeatedly depress and release the escape key )-> grub boot menu ;
With the normal ubuntu kernel selected ( top entry ) press the 'e' key for edit mode -> boot options screen;
in this screen arrow down to the line similar to "linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=217ed9a7-e11a-4e32-8c05-992e8c8932b6 ro  quiet splash $vt_handoff" and arrow across to the terms "quiet splash" add the term "nomodeset" - without the quotes ;
Key combo ctl+x to continue the boot process. At this point degraded graphics is OK, we will fix that soon;
Login and at the desktop activate a terminal - key combo ctl+alt+t .
Post back the results of terminal commands:
```

lspci -vnn | grep VGA -A 12
sudo lshw -C display

```
to see what the graphics chip set is, and a bit of info as to how the graphics layer in the operating system is handling the display.

Now we have a bit more info to advise on the course of action to get a graphics driver installed.
----------------------
Off Topic:
Sorry for the delay in responding. I had a thermal event that shut my system down, In that cleanup process I guess I disturbed some connections as I lost hard drives. I am finally back up and operational .
-----------------

again;
[INDENT][INDENT][INDENT]it ain't nothing but a thing
[/INDENT][/INDENT][/INDENT]

---

### Post by undershepherd1 on 2015-05-07
I would like to "stick my nose" into this discussion and just say a big thank you to "Bashing-OM" for the patience, clear, precise and quick responses. For us amateurs who have a difficult time understanding "ubuntu-speak," your help is greatly appreciated! Thanks so much!

---

### Post by angel mike on 2015-05-12
Off Topic :Thanks Bashing - om for continuing support and apologise for late reply - away in London for VE celebrations. 
Results : See below for output. I can now use the computer programs like Libre/Firefox etc - fantastic !! Does it still need a fine tune ?
>  
michael@michael-GM5066B:~$ lspci -vnn | grep VGA -A 12
01:00.0 VGA  compatible controller [0300]: NVIDIA Corporation G72 [GeForce 7300 LE]  [10de:01d1] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Gateway, Inc. Device [107b:3a07]
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at 91000000 (32-bit, non-prefetchable) [size=16M]
    Memory at 80000000 (64-bit, prefetchable) [size=256M]
    Memory at 90000000 (64-bit, non-prefetchable) [size=16M]
    Expansion ROM at <ignored> [disabled]
    Capabilities: <access denied>

03:00.0  IDE interface [0101]: Marvell Technology Group Ltd. 88SE6101/6102  single-port PATA133 interface [11ab:6101] (rev b1) (prog-if 8f [Master  SecP SecO PriP PriO])
     Subsystem: Marvell Technology Group Ltd. 88SE6101/6102 single-port PATA133 interface [11ab:6101]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    I/O ports at 2018 [size=8]
michael@michael-GM5066B:~$ 
 sudo lshw -C display
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: G72 [GeForce 7300 LE]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:91000000-91ffffff memory:80000000-8fffffff memory:90000000-90ffffff
michael@michael-GM5066B:~$ 


---

### Post by Bashing-om on 2015-05-12
angel mike; Good Morning:

As we continue, making good progress.
Yeah, there still be tuning to be done:
> 
configuration: latency=0

does not show a graphics driver installed. That is an old card and I am not real sure Nvidia continues support for it as it takes the 304 driver. Let's check:
Open Software sources (Menu) from the Software Center -> last tab is "Additional Drivers"; is the 304 driver shown here as an option ? 
If so install this proprietary driver;

Else we will see what we can do to get the nouveau driver installed.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by angel mike on 2015-05-12
Hello Bashing-om

i think we are nearly there - Additional Drivers Tab gave 4 options.
NVIDIA Corporation: G72[GeForce 7300LE] - the current one was xserver(open source).
I installed the version 304.125 from nvidia-304(proprietary, tested).
The other two options were 304.125-304-updates(proprietary) and 173.14.39 .
Restarting gives the desktop screen ! It is not covering the landscape size of my screen - more portrait size.
Thanks

---

### Post by Bashing-om on 2015-05-12
angel mike; Well;

Wonders never cease .
OK, what can you do for:
> 
It is not covering the landscape size of my screen - more portrait size.

from the 'nvidia settings" utility ?

[INDENT][INDENT]poke and see
[INDENT][INDENT][INDENT]what bites
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

