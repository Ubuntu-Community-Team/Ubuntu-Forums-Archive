---
title: "Grub, Ubuntu, XP &amp; 7 !!"
date: 2010-03-04
forum: Installation &amp; Upgrades
---

### Post by Tom_T on 2010-03-04
Hi

I've had Windows XP and Ubuntu installed as a dual boot for a while.
This has been working fine !

Yesterday I decided to add Windows 7 (only because I need to test some software)

So I decreased the XP and Linux partitions, installed 7 into the new space, rebooted and got the 7 boot menu.

Using Parted Magic I managed to get grub back and working as before 7 was installed.

Now when I select XP from grub, I get the option of 7 or an earlier version (XP).

What I would like to do is add 7 to the grub menu, so I boot straight in to either Ubuntu, XP or 7, with out have dual boot menu's for windows.

This is my menu.lst:

```
title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		eb523de9-88a4-41a8-b377-483df12e3900
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=eb523de9-88a4-41a8-b377-483df12e3900 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		eb523de9-88a4-41a8-b377-483df12e3900
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=eb523de9-88a4-41a8-b377-483df12e3900 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, memtest86+
uuid		eb523de9-88a4-41a8-b377-483df12e3900
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
rootnoverify	(hd0,1)
savedefault
chainloader	+1
```

The vista option above is a the netbooks recovery process.

This is the output from fdisk -l:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb9bac821

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         784     6297448+  12  Compaq diagnostics
/dev/sda2   *         785        4838    32563755    7  HPFS/NTFS
/dev/sda3            4839        8671    30787584    7  HPFS/NTFS
/dev/sda4            8672       19457    86638545    5  Extended
/dev/sda5            8673       19086    83650455   83  Linux
/dev/sda6           19087       19457     2980026   82  Linux swap / Solaris

Disk /dev/sdb: 7948 MB, 7948206080 bytes
4 heads, 16 sectors/track, 242560 cylinders
Units = cylinders of 64 * 512 = 32768 bytes
Disk identifier: 0x000311aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      242560     7761912    c  W95 FAT32 (LBA)

```

I've also attached a grab from gparted !

Any advice or help would be great :)

Thanks

---

### Post by oldfred on 2010-03-04
The only way windows can dual boot is to combine its boot loaders into the install with the boot flag (active partition).

It is easier to do before you install as you can move the boot flag and it will make two independant installs.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

You may be able to move the boot flag (gparted will do this) and run the repairs on the windows install. You will then have to reinstall grub.

---

### Post by meierfra. on 2010-03-04
To be able to boot XP and Win 7 directly from the Grub menu, you have separate their boot loaders. Here are the instructions:

** Step 1 Edit the Win7 boot loader, so that it also will work once you moved it to Win 7 partition **

Boot into Window 7

Go to "Start". Type "cmd" and press "Ctrl+Shift+Enter". This will open a command line as an administrator. (If this did not open the command line: Go to Start->Program Files->Accessories, Right Click "Command Prompt", Choose "Run as administrator")

Type


```
  
bcdedit /set {bootmgr} device boot

```


** Step 2 Add Win 7 to "menu.lst": **

 Boot into Ubuntu  and open a terminal (Applications->Accessories->Terminal) 

Open menu.lst via

```
gksudo gedit /boot/grub/menu.lst
```
Add this to the end of the file

title		Windows 7
rootnoverify	(hd0,2)
chainloader	+1

Save the file.

** Step 3  Copy  the Windows 7 boot files from the XP  partition to the Window 7 partition **

In a terminal in Ubuntu:

```
cd /mnt
sudo mkdir 2 3 
sudo mount /dev/sda2 2
sudo mount /dev/sda3 3 
sudo cp 2/bootmgr 3
sudo cp -R 2/[Bb][Oo][Oo][Tt] 3/

```

Reboot. Choose  Window 7 at the Grub menu.  The Window 7 boot menu should appear. Make sure you can boot into Win 7  and XP before continuing.

** Step 4 Fix the Window XP boot sector **

Boot from your Window XP CD (if you don't have one, you can get repair CD from [here]("http://www.webtree.ca/windowsxp/tools/bootdiscs/xp_rec_con.zip"))
Press "R" to get to the repair console 
If asked  type the number  for your  Windows XP operating system
Just press "enter" if asked for a password. 

Type

```
map
```

and determine the drive letter for your XP partition.
Type

```
fixboot C:
```
but replace "C" by the drive letter of your  XP partition.

Reboot and choose "XP" at the  Grub menu. Make sure you can boot into XP before continuing.


** Step 5 Edit the Win7 boot loader, so that it boots directly into Win 7**

Reboot.
Choose the Win 7 entry at the Grub menu and  boot into Win 7  Open the Win 7 command line as in Step 1 and type

```

bcdedit /set {bootmgr} default {current}
bcdedit /set {bootmgr} timeout 0

```


Next time you choose Win 7 at the Grub menu, you should boot directly into Win 7.


If you run into problems, follow these [instruction]("http://bootinfoscript.sourceforge.net") to run the Boot Info Script and post the RESULTS.txt

---

### Post by Tom_T on 2010-03-07
Thanks to both !

I'll look at doing this shortly..
Hopefully I'll post back happy results !
Only concern is the repairing XP. The XP I have installed, was pre supplied.

So I'm not sure how I can run a repair. Any ideas ??
I do have a full MS partner XP CD,but would that work ?

Many Thanks :)

---

### Post by meierfra. on 2010-03-07
> So I'm not sure how I can run a repair. Any ideas ??
I do have a full MS partner XP CD,but would that work ?

Just follow the instruction from my post. Don't do any other repairs. To run "fixboot" the "MS partner XP CD" should work, or you can use the XP repair CD I linked.

---

### Post by Tom_T on 2010-03-07
Thanks:)
Will try to do this tonight !

---

### Post by Tom_T on 2010-03-08
Hi
Followed your post exactly..

Couple of slight issues !!

On my Grub Menu I have:

```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
rootnoverify	(hd0,1)
savedefault
chainloader	+1

# on /dev/sda3
title Microsoft Windows 7
rootnoverify (hd0,2)
chainloader +1

```

When I select the XP Grub option, I get a fully working Windows 7 Booting straight in with no menu..

If I select the Windows 7 Grub option, I get the 7 Bootmenu, offering XP & 7.

7 works, XP won't boot.

If I try to boot again from my XP CD, I get a blue screen !!  Yet it worked before !

Any ideas ?? Ideally I'd like not to re install any of the OS's !

Thanks for your help.

---

### Post by meierfra. on 2010-03-08
> XP won't boot.

What happens when you try to boot XP?  
Were your able to boot XP via "Window 7 on Grub Menu"-> "Window XP on Window 7 menu" after Step 3?
Did you had any error messages while following my  instruction?

Lets check out your situation: 

Boot into Windows 7. Go Start->Computer and determine the drive letter of  your XP partition and your Win 7 partition  Then open the command line as before.

```
bcdedit /store C:\boot\bcd >C:\bcd_win7.txt
```
But replace "C:" by the drive letter of your Windows 7 partition
```
bcdedit /store D:\boot\bcd >C:\bcd_xp.txt
```
But replace "D:" by the drive letter of your Windows XP partition.

Post the content  of the two files bcd_win7.txt and bcd_xp.txt on your C:drive.

Boot into Ubuntu and follow these [instructions ]("http://bootinfoscript.sourceforge.net/")run the boot info script and post the RESULTS.txt

---

### Post by Tom_T on 2010-03-08
Hi
before I start.. Thanks for helping me with this :)

OK..

Trying to boot Windows XP from the '7' Boot menu, results in Boot.ini error,not found c:\windows etc..

I can't remember if it worked earlier sorry !

I've attached the 3 files as requested.

Thanks again :)

---

### Post by meierfra. on 2010-03-08
A couple of things did go wrong.

[list=1]
[*] The timeout of Win7 boot loader on the XP partition was set to zero, rather than the timeout of the Win 7 boot loader on the Win 7 partition.

[*] "fixboot" did not change the boot sector of the  XP partition.
[/list]

Also I do not fully understand why you can't boot  XP from the Win 7 boot menu.

#1 is not a big deal. We can take care of that once we get XP to boot.

For #2, since you can't boot your XP CD, lets see whether we can get the Win 7 boot loader on the XP partition to boot XP:

```

cd /mnt
sudo mount /dev/sda2 2
sudo mount /dev/sda3 3 
sudo cp  3/BOOT/BCD 2/BOOT/

```

Reboot, choose XP at the Grub menu and then XP at the Win7 boot menu.

Hopefully this will boot XP.

---

### Post by Tom_T on 2010-03-08
Had to change the last command to:
sudo cp  3/Boot/BCD 2/Boot/

just rebooting to see if that works for XP !
Thanks :)

---

### Post by Tom_T on 2010-03-08
Results..

Grub XP menu -> goes to 7 boot menu -> XP Option works.

Grub 7 menu -> goes to 7 boot menu -> XP Option failes.

Both options have 7 Boot Menu !

What next ? :)

thanks again

---

### Post by meierfra. on 2010-03-08
> Had to change the last command to:
sudo cp 3/Boot/BCD 2/Boot/

Weird. I used the same capitalization as listed in RESULTS.txt.

> Grub XP menu -> goes to 7 boot menu -> XP Option works.
Good.

> What next ? 

Boot into Window 7. Open a  command line just as before.


```

bcdedit /store C:\Boot\BCD  /set {bootmgr} timeout 0
bcdedit /store D:\Boot\BCD  /set {bootmgr} default {ntldr}
bcdedit /store D:\Boot\BCD  /set {bootmgr} timeout 0

```

Reboot.  Now the XP entry on the Grub menu, should boot you directly into XP and the Win7 entry into Win7

---

### Post by Tom_T on 2010-03-08
RESULT.

Both Grub options work, very quick flash of the 7 boot menu, then straight into either7 or XP !

Thank you very much for your help & advise :)

---

### Post by oldfred on 2012-12-16
Thread closed. Some info still ok for some Windows. But some is grub legacy. A lot has changed so better to start new thread.

---

