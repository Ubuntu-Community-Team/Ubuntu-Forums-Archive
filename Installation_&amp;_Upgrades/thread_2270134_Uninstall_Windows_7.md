---
title: "Uninstall Windows 7"
date: 2015-03-20
forum: Installation &amp; Upgrades
---

### Post by Lori_Imel on 2015-03-20
So I just installed ubuntu a couple of days ago.  Then I went and backed up all of my windows files etc.  So I want to get rid of Win7.....  How do I do it?  I found instructions, but it is for an older version of Ubuntu (not 14.04).  I even tried to get os-installer, but it said "unable to lockate"  in a terminal.  

So how can I uninstall windows now?

Thank you

---

### Post by Impavidus on 2015-03-20
Are you sure? To reinstall Windows later you need a Windows install disk, a backup of the files is not enough.

But it's quite easy. You need the program gparted. You can install it from the software centre, or use a live disk, which has gparted installed by default. Use that to remove the Windows partition and then do something to reuse the disk space in whatever way you want to reuse it. Then (back on your installed system, if you used the live disk), run```
sudo update-grub
``` to get rid of the Windows entry in the grub menu.

I don't think these instructions have ever changed as long as Ubuntu exists.

---

### Post by Lori_Imel on 2015-03-20
oh well.....  I went ahead and did a clean install and wiped everything clean.... probably needed it anyways....  I had not done too much in ubuntu anyways....

I do have backup discs for windows - I used them when I installed a new harddrive on my laptop....

---

