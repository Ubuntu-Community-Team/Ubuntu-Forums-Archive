---
title: "[SOLVED] Dual-boot Ubuntu/Xp (Ubuntu first)"
date: 2008-09-12
forum: Installation &amp; Upgrades
---

### Post by Farajamo on 2008-09-12
I'd like to start by saying I used the guide at:
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5)

So first, I booted live cd, and partitioned my HD fine.  I went about installing XP, and that worked too.  I boot into XP, and everything was fine. Then, I followed step 5 of the guide.  When I go into grub and select Windows XP I get the following error:

Windows could not start because the following file is missing or corrupt:
<Windows root>\system32\ntoskrnl.exe.
Please re-install a copy of the above file.

Any ideas?

---

### Post by Pumalite on 2008-09-12
That's a Windows known bug.

---

### Post by Farajamo on 2008-09-12
I don't suppose you know how to fix it? Should I just reinstall windows?

---

### Post by oilchangeguy on 2008-09-12
> **Pumalite said:**
> That's a Windows known bug.

i've done many windows installs over the years, and never had an error message pop up during the course of setting it up. where do you get your information that this is a known bug? the op could have done something during step five of whatever guide they are following. don't blame the operating system for operator error.

---

### Post by Pumalite on 2008-09-12
There is a thread by mierfra in this forum on how to fix Windows. Use Search: mierfra

---

### Post by Farajamo on 2008-09-12
I followed a tutorial by him that didn't really help... I'm still missing a file, or it's corrupted.

---

### Post by Pumalite on 2008-09-12
Known bug in dual boot.

---

### Post by Farajamo on 2008-09-12
Do you have any suggestions?

---

### Post by Pumalite on 2008-09-12
I am not a Windows user, but my impresion is that the file is not missing and that you should try Super Grub and see if you can boot Windows. In general Windows does not like this kind of arrangement.
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)
Burn to disk and boot from it.

---

### Post by Farajamo on 2008-09-13
Okay, I found out that it has something to do with the partition (I think).  I loaded the Windows boot cd, went into recovery, and did "fixmbr".  That got rid of grub and I can now boot into windows fine.

---

### Post by Farajamo on 2008-09-13
I don't know why, but this is the second time I've attempted dual-booting, and I had problems last time too....

---

### Post by Farajamo on 2008-09-14
Right now I've come up with a temporary fix... If I want to go on windows, I boot their CD, and fixmbr.  If I want to go on Ubuntu, I load up the LiveCD and restore grub. It's really a nuisance and would dearly appreciate if someones knows a fix. Thanks.

---

### Post by Pumalite on 2008-09-14
Post:
sudo fdisk -lu

---

### Post by Farajamo on 2008-09-14
Result is:

```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcb76f3cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   294535709   147267823+  83  Linux
/dev/sda2   *   294535710   468616049    87040170    7  HPFS/NTFS
/dev/sda3       468616050   488392064     9888007+   5  Extended
/dev/sda5       468616113   488392064     9887976   82  Linux swap / Solaris

```

---

### Post by Farajamo on 2008-09-20
Shameful bump.

---

### Post by meierfra. on 2008-09-20
You can add Ubuntu to the Windows boot loader:

Boot into Ubuntu or the Ubuntu Live CD.

Step 1 Install Grub to the boot sector of the Ubuntu Partition:


```
sudo grub
```
and at the grub prompt:

```
root (hd0,0)
setup (hd0,0)
quit
```


Step 2 Copy the Ubuntu boot sector to a file on your Windows partition:

```
sudo mount /dev/sda2 /mnt

sudo dd if=/dev/sda1 of=/mnt/ubuntu.bin bs=512 count=1
```
(be very careful with the "dd" command)

Step 3 Edit boot.ini:

```
sudo nano /mnt/boot.ini
```

Add this to the end of the file  (start a new line, but to not leave a blank line)

C:\ubuntu.bin="Ubuntu"

Save the file. Run "fixmbr" for the Windows CD (if needed). You should now get a boot menu allowing you do choose between "windows" and "ubuntu"

---

### Post by Farajamo on 2008-09-22
Since my Local Disk on Windows XP is K:\ instead of C:\, is there anything I should change?

---

### Post by meierfra. on 2008-09-22
> Since my Local Disk on Windows XP is K:\ instead of C:\, is there anything I should change?  
Yes, use


```
K:\ubuntu.bin="Ubuntu"
```

in boot.ini.

---

### Post by Farajamo on 2008-09-22
I did the code you presented, and did FIXMBR again in the recovery console.  Now when I boot, it looks like a menu appears for only a split second, then boots into windows... is there any way to make that last longer?

---

### Post by meierfra. on 2008-09-22
Probably you just need to edit the timeout in "boot.ini"
Change "timeout=?" to something like "timeout=10"

This link shows you how to edit "boot.ini" from XP
[http://support.microsoft.com/kb/289022]("http://support.microsoft.com/kb/289022")

---

### Post by Farajamo on 2008-09-22
When I attempt to boot Ubuntu, I get the following error:

```
Windows could not start because of a computer disk hardware configuration problem.
Could not read from the selected boot disk. Check boot path and disk hardware.
Please check the windows documentation about hardware disk configuration and your hardware reference manuals for additional information.
```

---

### Post by meierfra. on 2008-09-22
Try C:\ubuntu.bin="Ubuntu"  in place of K:\ubuntu.bin="Ubuntu"


If this does not solve your problem, post your "boot.ini"

---

### Post by Farajamo on 2008-09-22
It works! Thanks a lot for your time and patience, I really appreciate it!

---

### Post by meierfra. on 2008-09-22
> Thanks a lot for your time and patience, I really appreciate it!

You are welcome. Have fun with XP and Ubuntu.

---

