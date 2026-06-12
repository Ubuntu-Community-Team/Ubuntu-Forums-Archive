---
title: "Problem in dual booting"
date: 2010-08-04
forum: Installation &amp; Upgrades
---

### Post by Panos_Papajohn on 2010-08-04
Hello, 

I installed Ubuntu a couple days ago and shortly after Windows XP.
Without Windows everything was fine (as expected ;)) but after the installation I cant access which OS I'd like to work in. I tried fixing the problem from the terminal via the LiveCd but Windows don't even read it. Is there any way to fix dual booting through the Windows' command line? 

Thanks

---

### Post by dandnsmith on 2010-08-04
As stated, no - you'd need to do several things which are not possible to Windows before you get to a solution in which you can invoke linux from the Windows boot menu.
What you've done is clobbered the bootstrap code by installing WinXP, and you'd ideally have saved a copy of the code before you took that step.

---

### Post by oldfred on 2010-08-04
You do not access the liveCD from windows but boot the liveCD to repair the MBR. After you boot into Ubuntu run sudo update-grub and it should find your windows install and let you boot either. Be sure to reinstall the correct version of grub or grub2. 9.10 or later new installs use grub2.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you installed Ubuntu first it is probably not sda5 so you will have to adjust:
Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

Do not install to partitions. Drives are sda, sdb etc, Partitions are sda1, sda2 etc.

---

### Post by Panos_Papajohn on 2010-08-04
oldfred I did what you told me and my desktop appeared. But then I repeated the whole procedure (I don't know why) and now when I open my pc I receive the message: 

error: file not found
grub rescue>

I hope I'm not putting into trouble. Thanx.

---

### Post by oldfred on 2010-08-04
Post this so we can see what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by Panos_Papajohn on 2010-08-05
```
error: file not found
grub rescue>

```

This is what i get when i open my pc. A black screen. I can't even  boot Ubuntu from the LiveCd. Should I install Windows and then Ubuntu again and then repeat what you told me for the installation of grub?

---

### Post by oldfred on 2010-08-05
You should not have to reinstall. But if you have no data or time spent setting up systems reinstall may be faster. We like to spend days (weeks:)) fixing things just to fix them.

---

### Post by viriimind on 2010-08-05
> **Panos_Papajohn said:**
> ```
error: file not found
grub rescue>

```

This is what i get when i open my pc. A black screen. I can't even  boot Ubuntu from the LiveCd. Should I install Windows and then Ubuntu again and then repeat what you told me for the installation of grub?

Did you select CDROM as 1st boot from bios? if yes, you must be able to boot from liveCD. I also had the same trouble, now everything is OK,
```
h**p://h0w-t0.blogspot.com/2010/08/how-to-reinstall-grub2-after-installing.html
```

Reinstalling is not good idea.
Good luck.. :)

---

### Post by Panos_Papajohn on 2010-08-05
oldfred 
since you have knowledge of these things (far greater than mine:))
could you make a guess about what happened when I installed the grub second time in a row? When I saw the partitions in my pc (I installed windows again :() one partition was missing. It was like I had deleted the partition containing the ubuntu. Do you you have any references that I can read to expand my knowledge. I found great stuff in [https://help.ubuntu.com/]("https://help.ubuntu.com/") anything else?

Thanx

---

### Post by oldfred on 2010-08-05
If you installed grub from a working system, I would not expect the grub rescue. Did you try the manual boot procedure?

This page has solutions to many issues:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page)

Often you need to know where things are installed. I learned to read the details of this script. Especially important with multiple drives, or multiple systems. Actually combines many commands and some extra probing of MBR & PBR to see what is installed where into a nice report.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

Grub2 basics see section 15 on booting from rescue mode:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

