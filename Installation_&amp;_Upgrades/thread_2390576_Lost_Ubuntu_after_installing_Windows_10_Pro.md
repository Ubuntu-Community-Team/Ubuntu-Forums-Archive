---
title: "Lost Ubuntu after installing Windows 10 Pro"
date: 2018-04-30
forum: Installation &amp; Upgrades
---

### Post by rudibloes on 2018-04-30
Hello,

I did a clean install of Windows 10 Pro on the partition where my Windows 7 used to be.
But now I can not get to the partition where my Ubuntu 16 is installed. In fact, I can not get to any partitions at all. Windows 10 Pro starts immediately.
Is my Ubuntu lost for ever? Or can I get it back the way it was. How to solve this?

Thanks in advance,

---

### Post by yancek on 2018-04-30
Did you use the "Custom" install option with windows 10 and select the old windows partition?
Was your windows 7 install a Legacy/MBR install (that was the default)?
Is your hardware UEFI capable?
Is windows 10 installed using UEFI?
Is Ubuntu installed using Legacy/MBR?

If you have an Ubuntu disk/flash drive, boot it and run the following command and post the output.  That will show whether you have an EFI partition and Linux partiitions.  You might need to go to the site below with the Ubuntu install media if you have it and download and run boot repair according to the instructions on the page.  Make certain when you run boot repair to select the Create BootInfo Summary option.  That will output a link which you can post here that contains details needed for someone to help.

```
sudo parted -l
```  That's a lower case Letter L in the command.

  [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by oldfred on 2018-05-01
Windows in BIOS mode updates partition table.
And for many years it has had a bug (Windows feature to make Linux a problem) in that it forgets to include your Linux partitions in partition table. Data & partition are still there if you have not done anything to destroy it since shown as unallocated free space in Windows.

You should be able to use parted rescue or testdisk to update partition table.
       Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/m...de/rescue.html](http://www.gnu.org/software/parted/m...de/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/66544...rtition/665462](http://askubuntu.com/questions/66544...rtition/665462)

---

