---
title: "GRUB problem"
date: 2011-05-04
forum: Installation &amp; Upgrades
---

### Post by jeshrel on 2011-05-04
Hi,

I have a very big problem, i had dual booted ubuntu 10.10 and windows 7, and then decided to delete ubuntu, so i formated the drive that had ubuntu in it and restarted my laptop now i am unable to access my Operating Sysytem. When i boot my laptop all it says is "grub rescue>". Kindly help

---

### Post by YesWeCan on 2011-05-04
The problem is probably that the Ubuntu installer overwrote the Windows bootloader rather than putting the Ubuntu bootloader on the Ubuntu disk. This is an ancient abuse that never gets sorted out for reasons that I try never to contemplate as it causes me mental trauma.

The Grub bootloader is not in one piece, some is on your Windows disk and some was on your Ubuntu disk. When you run Grub it fails to find its files and bombs to the prompt.

The only way to fix this is to reinstate the original Windows bootloader. You will need your Windows OS disk to do this. There may be other ways that I am not aware of.

Next time you do a dual boot you need to keep your eye open for the easy to miss bit in the Ubuntu installer that lets you change where Grub is put. Easier is to physically discnnect the Windows disk during the install to make sure it cannot be corrupted and to give Ubuntu no choice of where to put Grub. After the install you reconnect Windows drive, boot the Ububtu drive and run 'sudo update-grub' to add Windos as an entry to the boot menu. :)

---

### Post by satanselbow on 2011-05-04
As above - you need to boot into the "Startup Rescue" option on the W7 DVD - do be aware that you may have to run it several times (typically at least 3) before the Windows utility actual fixes the problem.

There is some good info here that should help you along ;)

[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by Quackers on 2011-05-04
Or you could re-install Ubuntu :-)

---

### Post by satanselbow on 2011-05-04
Yeah... I forgot to mention that... Format c: anyone?

---

### Post by kansasnoob on 2011-05-04
> **jeshrel said:**
> Hi,

I have a very big problem, i had dual booted ubuntu 10.10 and windows 7, and then decided to delete ubuntu, so i formated the drive that had ubuntu in it and restarted my laptop now i am unable to access my Operating Sysytem. When i boot my laptop all it says is "grub rescue>". Kindly help

If you have no Windows recovery disc, as is often the case now, and if your laptop has only one physical hard drive, you can use either an Ubuntu Live CD or Live USB and then just run these commands from terminal in the live desktop:

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sda mbr
```

That should get you booting :)

---

### Post by jeshrel on 2011-05-05
thank a lot guys ill try i and lett u knw in a while...

---

### Post by wilee-nilee on 2011-05-05
> **YesWeCan said:**
> The problem is probably that the Ubuntu installer overwrote the Windows bootloader rather than putting the Ubuntu bootloader on the Ubuntu disk. This is an ancient abuse that never gets sorted out for reasons that I try never to contemplate as it causes me mental trauma.

The Grub bootloader is not in one piece, some is on your Windows disk and some was on your Ubuntu disk. When you run Grub it fails to find its files and bombs to the prompt.

The only way to fix this is to reinstate the original Windows bootloader. You will need your Windows OS disk to do this. There may be other ways that I am not aware of.

Next time you do a dual boot you need to keep your eye open for the easy to miss bit in the Ubuntu installer that lets you change where Grub is put. Easier is to physically discnnect the Windows disk during the install to make sure it cannot be corrupted and to give Ubuntu no choice of where to put Grub. After the install you reconnect Windows drive, boot the Ububtu drive and run 'sudo update-grub' to add Windos as an entry to the boot menu. :)

Wow lol is all I can say.

---

### Post by frequentsource on 2011-05-05
Read this,it will easily solve your issue..
There are 3 ways by which you can easily remove GRUB from your existing hard drive. I will start with the most easiest one: [U][B][COLOR=#008000]Method 1: Use a MS-DOS disk or Windows 9x floppy[/COLOR]
[/B][/U]
 Get hold of a MS-DOS 6.22 disk or a Windows 9X start-up disk. Boot  from the floppy drive on your system with the hard drive attached and  give the following command:
 # fdisk /mbr
 The above command will over-write the MBR meaning that GRUB will now disappear and you will most likely have your Windows XP boot menu back or DOS will book.

[COLOR=#008000]_**Method 2: Use a Windows XP installation CD/DVD**_[/COLOR] Grab a Windows XP installation CD and boot from the CD with the hard drive attached and select the **“Repair”**  (choose “R”) option when it is presented to you. After that you will  taken a common prompt. Once you get to the command prompt give the  following command after selecting **“1&#8243;** for :
 1) C:\WINDOWS
and now type the following commands:
 C:\WINDOWS> CD ..
C:\> FIXBOOT C:
C:\> FIXMBR
C:\> BOOTCFG /rebuild
 The last command (BOOTCFG) will rebuild your boot.ini as per your hard drive partition table and will put appropriate entries for Windows XP. Also this command will most likley add a new entry to your Windows XP boot menu. You can easily delete the old entry by modifying the *C:\boot.ini* file once you successfully boot into Windows using the newly created entry.
 **_Note:_**  You will need to know the “Administrator” password before you can enter  into the command prompt. If you don’t have one, just press “Enter” key.
 [COLOR=#008000]_**Method 3: Use Linux dd command**_[/COLOR]
 Lastly you can use the powerful “dd” comamnd in Linux. For this the  best thing to do is to boot from a LiveCD with your hard drive attached  and give the following command:
 # dd if=/dev/null of=/dev/sd[COLOR=#0000ff]**X**[/COLOR] bs=446 count=1
 Where
 [COLOR=#0000ff]**X**[/COLOR] = *Your hard drive device name*
 You can use the following command to find your hard drive letter:
 # fdisk -l
 Output:
 Disk /dev/sda: 750.1 GB, 750155292160 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90ee8262
 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18237   146488671    7  HPFS/NTFS
/dev/sda2           18238       67366   394628692+   5  Extended
/dev/sda5           18238       66880   390724866   83  Linux
/dev/sda6           66881       67366     3903763+  82  Linux swap / Solaris
 That’s it. Hopefully by using any one of the above 3 methods you should be able to get your Windows booting back.
 Happy GRUB-erasing!

---

### Post by jeshrel on 2011-05-05
> **kansasnoob said:**
> If you have no Windows recovery disc, as is often the case now, and if your laptop has only one physical hard drive, you can use either an Ubuntu Live CD or Live USB and then just run these commands from terminal in the live desktop:

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sda mbr
```

That should get you booting :)



the first command did work and it downoaded lilo but the second command didnt work?

---

### Post by jeshrel on 2011-05-05
> **frequentsource said:**
> read this,it will easily solve your issue..
There are 3 ways by which you can easily remove grub from your existing hard drive. I will start with the most easiest one: [u][b][color=#008000]method 1: Use a ms-dos disk or windows 9x floppy[/color]
[/b][/u]
 get hold of a ms-dos 6.22 disk or a windows 9x start-up disk. Boot  from the floppy drive on your system with the hard drive attached and  give the following command:
 # fdisk /mbr
 the above command will over-write the mbr meaning that grub will now disappear and you will most likely have your windows xp boot menu back or dos will book.

[color=#008000]_**method 2: Use a windows xp installation cd/dvd**_[/color] grab a windows xp installation cd and boot from the cd with the hard drive attached and select the **“repair”**  (choose “r”) option when it is presented to you. After that you will  taken a common prompt. Once you get to the command prompt give the  following command after selecting **“1&#8243;** for :
 1) c:\windows
and now type the following commands:
 C:\windows> cd ..
C:\> fixboot c:
C:\> fixmbr
c:\> bootcfg /rebuild
 the last command (bootcfg) will rebuild your boot.ini as per your hard drive partition table and will put appropriate entries for windows xp. Also this command will most likley add a new entry to your windows xp boot menu. You can easily delete the old entry by modifying the *c:\boot.ini* file once you successfully boot into windows using the newly created entry.
 **_note:_**  you will need to know the “administrator” password before you can enter  into the command prompt. If you don’t have one, just press “enter” key.
 [color=#008000]_**method 3: Use linux dd command**_[/color]
 lastly you can use the powerful “dd” comamnd in linux. For this the  best thing to do is to boot from a livecd with your hard drive attached  and give the following command:
 # dd if=/dev/null of=/dev/sd[color=#0000ff]**x**[/color] bs=446 count=1
 where
 [color=#0000ff]**x**[/color] = *your hard drive device name*
 you can use the following command to find your hard drive letter:
 # fdisk -l
 output:
 Disk /dev/sda: 750.1 gb, 750155292160 bytes
255 heads, 63 sectors/track, 91201 cylinders
units = cylinders of 16065 * 512 = 8225280 bytes
disk identifier: 0x90ee8262
 device boot      start         end      blocks   id  system
/dev/sda1   *           1       18237   146488671    7  hpfs/ntfs
/dev/sda2           18238       67366   394628692+   5  extended
/dev/sda5           18238       66880   390724866   83  linux
/dev/sda6           66881       67366     3903763+  82  linux swap / solaris
 that’s it. Hopefully by using any one of the above 3 methods you should be able to get your windows booting back.
 Happy grub-erasing!
  thank to you i freaking lost all my data...thank you>>f***

---

### Post by jeshrel on 2011-05-05
> **frequentsource said:**
> read this,it will easily solve your issue..
There are 3 ways by which you can easily remove grub from your existing hard drive. I will start with the most easiest one: [u][b][color=#008000]method 1: Use a ms-dos disk or windows 9x floppy[/color]
[/b][/u]
 get hold of a ms-dos 6.22 disk or a windows 9x start-up disk. Boot  from the floppy drive on your system with the hard drive attached and  give the following command:
 # fdisk /mbr
 the above command will over-write the mbr meaning that grub will now disappear and you will most likely have your windows xp boot menu back or dos will book.

[color=#008000]_**method 2: Use a windows xp installation cd/dvd**_[/color] grab a windows xp installation cd and boot from the cd with the hard drive attached and select the **“repair”**  (choose “r”) option when it is presented to you. After that you will  taken a common prompt. Once you get to the command prompt give the  following command after selecting **“1&#8243;** for :
 1) c:\windows
and now type the following commands:
 C:\windows> cd ..
C:\> fixboot c:
C:\> fixmbr
c:\> bootcfg /rebuild
 the last command (bootcfg) will rebuild your boot.ini as per your hard drive partition table and will put appropriate entries for windows xp. Also this command will most likley add a new entry to your windows xp boot menu. You can easily delete the old entry by modifying the *c:\boot.ini* file once you successfully boot into windows using the newly created entry.
 **_note:_**  you will need to know the “administrator” password before you can enter  into the command prompt. If you don’t have one, just press “enter” key.
 [color=#008000]_**method 3: Use linux dd command**_[/color]
 lastly you can use the powerful “dd” comamnd in linux. For this the  best thing to do is to boot from a livecd with your hard drive attached  and give the following command:
 # dd if=/dev/null of=/dev/sd[color=#0000ff]**x**[/color] bs=446 count=1
 where
 [color=#0000ff]**x**[/color] = *your hard drive device name*
 you can use the following command to find your hard drive letter:
 # fdisk -l
 output:
 Disk /dev/sda: 750.1 gb, 750155292160 bytes
255 heads, 63 sectors/track, 91201 cylinders
units = cylinders of 16065 * 512 = 8225280 bytes
disk identifier: 0x90ee8262
 device boot      start         end      blocks   id  system
/dev/sda1   *           1       18237   146488671    7  hpfs/ntfs
/dev/sda2           18238       67366   394628692+   5  extended
/dev/sda5           18238       66880   390724866   83  linux
/dev/sda6           66881       67366     3903763+  82  linux swap / solaris
 that’s it. Hopefully by using any one of the above 3 methods you should be able to get your windows booting back.
 Happy grub-erasing!

thanks a lot for ur help..i lost all my data...

---

### Post by Anger 2 on 2011-05-05
Restore MBR back to Windows
Use Super Grub disk Live CD.See [http://en.kioskea.net/faq/2677-super-grub-disk-live-cd](http://en.kioskea.net/faq/2677-super-grub-disk-live-cd)

---

### Post by kansasnoob on 2011-05-05
> **jeshrel said:**
> the first command did work and it downoaded lilo but the second command didnt work?

Did you copy-n-paste the commands?

---

### Post by kansasnoob on 2011-05-05
> **jeshrel said:**
> thanks a lot for ur help..i lost all my data...

Which method did you use?

You should be able to recover most, or maybe even all of your data using TestDisk:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by jeshrel on 2011-05-05
> **kansasnoob said:**
> Which method did you use?

You should be able to recover most, or maybe even all of your data using TestDisk:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Thanks for your help, i jus did a clean ubuntu 10.10 installation

---

