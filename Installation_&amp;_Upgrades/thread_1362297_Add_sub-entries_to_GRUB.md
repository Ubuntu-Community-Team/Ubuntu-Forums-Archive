---
title: "Add sub-entries to GRUB"
date: 2009-12-23
forum: Installation &amp; Upgrades
---

### Post by xsever on 2009-12-23
Hello everyone,

I am currently triple-booting, XP-32, Windows 7 64-bit, and Ubuntu 9.04.

I had 7 and XP installed with 7 as my default OS to load. After installing Ubuntu, GRUB took over which is normal.

Now I only have one entry in GRUB saying Windows Vista (loader). If I press enter with it highlighted, I can see the sub-entries (Windows 7 and Windows XP).

What I would like to do is have GRUB include these sub-entried in its initial display without having to go through "Windows Vista (loader)" and then choose.

I will really appreciate your help and I am willing to supply all information needed.

Thank you,

---

### Post by oldfred on 2009-12-23
You cannot easily, grub just chainboots to a working windows normally with the boot flag on:

Vista/win7 copies boot manager to one 
[http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing](http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing)
Moral of the story - look on other NTFS partitions for the missing bootmgr and Boot directory.

Windows combines its boot loaders so you can choose which to boot. Some boot files are moved from the second install to the first. If installing the second windows there is a work around but once installed I do not know if  you can separately repair them and get the same result. You could try moving the boot flag and running the repairs on each windows separately check that it boots ok by itself, then reinstall grub.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by meierfra. on 2009-12-23
Edit:  The same instruction work for Windows 7. Just replace Vista by "Window7" everywhere.

Try this
[SIZE="3"][COLOR=blue] Boot into Vista.[/COLOR][/SIZE]

[B]Step 1 Edit the Vista boot loader
[/B]
Go to "Start". Type "cmd" and press "Ctrl+Shift+Enter". This will open a Vista commandline as an administrator. Type

```
  
bcdedit /set {bootmgr} device boot
bcdedit /set {bootmgr} timeout 0
bcdedit /delete {ntldr} /f

```
(don't close the command line)

**Step 2 Fix the XP bootsector.**

Insert your Vista DVD in the DVD drive and wait for a few second. (If you don't have a Vista DVD/CD let me know and I can show you different ways to accomplish this step)
At the command line: 
```

E:\boot\bootsect  /nt52 D: /force

```

Here "E" needs to be replaced by the drive letter of your DVD drive and "D" by the drive letter of your XP partition. (Just look in "My Computer" to determine the drive letters. Even if you know the drive letters, I suggest to double check. Vista and XP probably use different drive letters. You need to use the drive letters used by Vista)


[SIZE="3"][COLOR=blue] Boot into Ubuntu.[/COLOR][/SIZE] 
and open a terminal (Applications->Accessories->Terminal) 


** Step 3 Add Vista to "menu.lst" **

Open menu.lst via


```
gksudo gedit /boot/grub/menu.lst
```

Your current entry for Vista will later actually boot XP. So you might want to edit the title. Also you should create a similar entry for Vista. (if you need help with that post the output of "sudo fdisk -lu")



** Step 4  Move the boot files from XP to Vista **

Type 

```
 sudo fdisk -lu
```

and determine the device name of the XP partition and the device name of the Vista parition.
In the following I assume that  XP is on /dev/sda1 and Vista is on /dev/sda2. 

```
 sudo mkdir /mnt/{XP,Vista}
sudo mount /dev/sda1 /mnt/XP
sudo mount /dev/sda2 /mnt/Win
sudo mv /mnt/XP/{Boot,bootmgr} /mnt/Vista

```
Of course you need to  replace  /dev/sda1 by the device name of the XP partition and /dev/sda2 by the device name of the Vista partition. 
Sometimes the directory  Boot  is called BOOT instead. Use  "ls -l /mnt/XP" to determine the correct spelling. 


Reboot and hopefully you will be able to boot into all your OSs from the Grub menu.

---

### Post by xsever on 2009-12-23
@ meierfra.

As mentioned in my thread I have Windows 7 installed and not VISTA.

Would your instructions still apply or some modifications are needed to be suitable for 7?

Thank you,

---

### Post by meierfra. on 2009-12-23
Sorry, I got confused with the "Windows Vista (loader)". But the same instructions work for Windows 7.

---

### Post by xsever on 2009-12-23
I do not know which of your commands caused it, but one of my hard drive shows as RAW in Windows now. I am in the process of recovering.

I highly suggest you look into your books since something is majorly wrong!!

---

### Post by meierfra. on 2009-12-23
I never had any problems with these instruction before (and I used them several times). Did you use the wrong  drive for "E:\boot\bootsect  /nt52 D: /force"? 

If you would like some help recovering, boot into ubuntu, run the boot info script

[http://ubuntuforums.org/showthread.php?t=1291280]("http://ubuntuforums.org/showthread.php?t=1291280")

and post the RESULTS.txt

What partition is showing as raw?   Are you able to boot into all your OS's?

---

### Post by xsever on 2009-12-23
I was not wrong about drive letters. I double checked before proceeding. I am not sure why it happened.

I am using GetDataBack for NTFS right now to copy all my data to another HD before reformatting. I trying TestDisk first with no luck. It was not able to find anything.

An entire second HD is showing as raw. It is a 750GB HD that I use for data storage. After your instructions, I can boot either XP or 7 but not both depending on which one I repair.

---

### Post by meierfra. on 2009-12-23
Could you run the boot info script so that I can figure out what is going on?

---

### Post by xsever on 2009-12-23
> **meierfra. said:**
> Could you run the boot info script so that I can figure out what is going on?

I have to wait for the other software to finish analysis.

How exactly can I run the boot info script?

Thank you,

---

### Post by meierfra. on 2009-12-23
> How exactly can I run the boot info script?

Download it to your Desktop from [https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Run it via

```
sudo bash ~/Desktop/boot_info_script*,sh
```

This creates the file RESULTS.txt on your Desktop. Post the content of RESULTS.txt (use the code tags: #)

Unless your problem is unrelated to my instruction, I would be very surprised if you  would have reformat or reinstall anything.

---

### Post by xsever on 2009-12-24
I recovered my files and deleted the Ubuntu partition since I do not want to use it anymore. I might give it a try on another PC.

I am fixing the boot loader now using Windows 7's disk and cmd.

---

