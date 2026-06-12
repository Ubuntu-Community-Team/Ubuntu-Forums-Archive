---
title: "Installed XP after Karmic"
date: 2009-12-01
forum: Installation &amp; Upgrades
---

### Post by mateamargo on 2009-12-01
I have installed Windows XP after Karmic. Then, I have fixed the grub to load Ubuntu again but Windows is not recognized.

Both are installed on a IDE Hard Drive (I have another SATA disk), here is the fdisk -l output:

```

Disk /dev/sdb: 80.0 GB, 80026361856 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1088     8739328+   f  W95 Ext'd (LBA)
/dev/sdb2   *         965        1088      995998+  82  Linux swap / Solaris
/dev/sdb3            1089        5550    35841015   83  Linux
/dev/sdb4            5551        9729    33567817+   7  HPFS/NTFS
/dev/sdb5               1         964     7743235+  83  Linux

```

I'm not sure what should I put in the menu.lst file, because some settings trhows the grub's error 13.
I don't know if should be hd0,0 or hd0,1.

Is there a way to find out what to use?

---

### Post by oldfred on 2009-12-01
First use gparted to move the boot flag to sdb4 which looks like your windows partition.

If this is your sdb drive you probably need the map commands since windows wants to think it is first.

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb4
title        Microsoft Windows XP Professional
rootnoverify    (hd1,3)
savedefault
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

The above assumed you upgraded in place and still have old grub. 

If it is grub2 just run the updater

sudo update-grub

---

### Post by phillw on 2009-12-01
> **mateamargo said:**
> I have installed Windows XP after Karmic. Then, I have fixed the grub to load Ubuntu again but Windows is not recognized.

Both are installed on a IDE Hard Drive (I have another SATA disk), here is the fdisk -l output:

```

Disk /dev/sdb: 80.0 GB, 80026361856 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1088     8739328+   f  W95 Ext'd (LBA)
/dev/sdb2   *         965        1088      995998+  82  Linux swap / Solaris
/dev/sdb3            1089        5550    35841015   83  Linux
/dev/sdb4            5551        9729    33567817+   7  HPFS/NTFS
/dev/sdb5               1         964     7743235+  83  Linux

```I'm not sure what should I put in the menu.lst file, because some settings trhows the grub's error 13.
I don't know if should be hd0,0 or hd0,1.

Is there a way to find out what to use?

If you did a clean install of 9.10, then you would be on Grub2 - a quick 'heads-up' on win & both Grub and Grub2 can be found here -->  [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you have problems, head over there - but update-grub usually sorts things out - grub2 is a pretty intelligent beast ;-)

Phill.

---

### Post by mateamargo on 2009-12-01
> **oldfred said:**
> First use gparted to move the boot flag to sdb4 which looks like your windows partition.

First, thanks for the quick response.
The gparted shows me the disk space as unallocated :O 
[http://img22.imageshack.us/img22/833/screenshotdevsdbgparted.png](http://img22.imageshack.us/img22/833/screenshotdevsdbgparted.png)

I'll try with a live cd and post the results here.

---

### Post by mateamargo on 2009-12-01
Same problem.
I've just tried with the live cd and shows me the disk as unallocated.

How come this is even working?

---

### Post by presence1960 on 2009-12-02
> **mateamargo said:**
> I have installed Windows XP after Karmic. Then, I have fixed the grub to load Ubuntu again but Windows is not recognized.

Both are installed on a IDE Hard Drive (I have another SATA disk), here is the fdisk -l output:

```

Disk /dev/sdb: 80.0 GB, 80026361856 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1088     8739328+   f  W95 Ext'd (LBA)
/dev/sdb2   *         965        1088      995998+  82  Linux swap / Solaris
/dev/sdb3            1089        5550    35841015   83  Linux
/dev/sdb4            5551        9729    33567817+   7  HPFS/NTFS
/dev/sdb5               1         964     7743235+  83  Linux

```

I'm not sure what should I put in the menu.lst file, because some settings trhows the grub's error 13.
I don't know if should be hd0,0 or hd0,1.

Is there a way to find out what to use?

Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by darkod on 2009-12-02
Do what presence has asked you to do.
And just something for you to consider: How did you ever end up with only an extended partition on sdb? Did you use the guided option of Karmic and it creates extended by default? Then your XP is installed on logical partition. It might be even impossible to boot it like that, not XP.

---

### Post by mateamargo on 2009-12-15
I didn't reply before because I had a problem with my ISP.

This is what I got now:

[LIST]
[*] Windows working
[*] Karmic installed but not working.
[/LIST]

With no working I mean the grub menu doesn't show up.
I'll boot with Karmic live cd and post how I have my disks partitioned.

When I force grub to install in the Windows partition, it fails with "Wrong format" and when I install it in the Ubuntu partition, grub doesn't load.

Any idea?

---

### Post by darkod on 2009-12-15
> **mateamargo said:**
> I have installed Windows XP after Karmic. Then, I have fixed the grub to load Ubuntu again but Windows is not recognized.

Both are installed on a IDE Hard Drive (I have another SATA disk), here is the fdisk -l output:

```

Disk /dev/sdb: 80.0 GB, 80026361856 bytes

   Device Boot      Start         End      Blocks   Id  System
[COLOR=Red]/dev/sdb1               1        1088     8739328+   f  W95 Ext'd (LBA)
/dev/sdb2   *         965        1088      995998+  82  Linux swap / Solaris[/COLOR]
/dev/sdb3            1089        5550    35841015   83  Linux
/dev/sdb4            5551        9729    33567817+   7  HPFS/NTFS
/dev/sdb5               1         964     7743235+  83  Linux

```I'm not sure what should I put in the menu.lst file, because some settings trhows the grub's error 13.
I don't know if should be hd0,0 or hd0,1.

Is there a way to find out what to use?

I just picked up on this. How can /dev/sdb2 which is primary be inside /dev/sdb1 which is extended?

PS. Not to mention that the swap partition has the boot flag.

---

### Post by presence1960 on 2009-12-15
> **darkod said:**
> I just picked up on this. How can /dev/sdb2 which is primary be inside /dev/sdb1 which is extended?

PS. Not to mention that the swap partition has the boot flag.

Disk /dev/sdb: 80.0 GB, 80026361856 bytes

   Device Boot      Start         End      Blocks   Id  System
[COLOR="DarkRed"]/dev/sdb1               1        1088     8739328+   f  W95 Ext'd (LBA)[/COLOR]
/dev/sdb2   *         965        1088      995998+  82  Linux swap / Solaris
/dev/sdb3            1089        5550    35841015   83  Linux
/dev/sdb4            5551        9729    33567817+   7  HPFS/NTFS
/dev/sdb5               1         964     7743235+  83  Linux

sdb1 is extended. sdb 2 & sdb5 are inside that.
But the boot flag on swap? I would remove that from gparted on Live CD.
_**OP run that darn script I asked you to run so darko and I can see exactly what you have on your machine please!**_

---

### Post by presence1960 on 2009-12-15
> **mateamargo said:**
> I didn't reply before because I had a problem with my ISP.

This is what I got now:

[LIST]
[*] Windows working
[*] Karmic installed but not working.
[/LIST]

With no working I mean the grub menu doesn't show up.
I'll boot with Karmic live cd and post how I have my disks partitioned.

When I force grub to install in the Windows partition, it fails with "Wrong format" and when I install it in the Ubuntu partition, grub doesn't load.

Any idea?

**_DOWNLOAD & RUN THE SCRIPT you were asked to run please!_**

---

### Post by mateamargo on 2009-12-24
@presence1960 I'm attatching the results file from the script you asked me to run.

My current state is Windows XP giving me error 15 and Ubuntu booting fine.

Thanks.

---

### Post by mateamargo on 2010-02-02
Any ideas?
Did the RESULTS.txt file give any hint?

---

### Post by presence1960 on 2010-02-02
> **mateamargo said:**
> Any ideas?
Did the RESULTS.txt file give any hint?

Boot into ubuntu and open a terminal. Run ```
gksu gedit /boot/grub/menu.lst
```
That is a lowercase L in .lst
This command will open menu.lst with root priviledge to edit menu.lst, you want to edit your windows entry. Scroll down to this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

Change it to:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
chainloader	+1

```

Click Save on top toolbar & close file. reboot & choose windows.

You do not need the map lines, they are only needed when windows is not on the first hard disk that boots in BIOS. Your sdb is booting first in BIOS so that is actually (hd0) even though fdisk reports it as sdb.

---

### Post by mateamargo on 2010-02-04
> **presence1960 said:**
> 
Change it to:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
chainloader	+1

```


That made it work. Thanks a lot.
:popcorn:

---

### Post by presence1960 on 2010-02-05
> **mateamargo said:**
> That made it work. Thanks a lot.
:popcorn:

Glad you got it working! Enjoy your dual boot setup.

---

