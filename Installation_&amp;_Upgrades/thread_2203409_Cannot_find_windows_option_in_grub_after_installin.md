---
title: "Cannot find windows option in grub after installing unbuntu 13.10?"
date: 2014-02-03
forum: Installation &amp; Upgrades
---

### Post by josh32 on 2014-02-03
I have just installed unbuntu 13.10 alongside windows 7. In order to do this i made the HP TOOLS and Backup partitions logical then just did the intall alongside option.

Now windows is not an option in Grub, unbuntu works fine though. It seems it may have deleted windows but i don't know how?

Is there any way of finding this out and if not a way of recovering form this?

I am a total newbie to unbuntu I may add.

Thanks

---

### Post by oldfred on 2014-02-03
How did you install? Manual or Something Else or an auto option?

run this first from inside your install:
sudo update-grub

If that does not work we need details.
       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by josh32 on 2014-02-03
Thanks I have already done this getting [B]paste.ubuntu.com/6867467/

And i used the auto option: Install alongside windows
[/B]

---

### Post by oldfred on 2014-02-03
You show no Windows, are you sure you used the along side option, not install to entire drive option?

This only is for re-installs. But if you reinstalled also say this bug applies to you.
       Reinstall says overwrite Ubuntu but it also erases existing Windows.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

You did backup Windows or make the vendor recovery DVD set before install? You would have to recreate a NTFS primary partition with the boot flag to restore your Windows.

---

### Post by josh32 on 2014-02-03
No rather stupidly I din't back it up. If I performed this would I get my old files back? What was it that I did wrong with the installation?

Thanks

---

### Post by oldfred on 2014-02-03
There is no way to get everything back. Parts of Ubuntu have overwritten parts of Windows. But Ubuntu is relatively small.
You can try testdisk and see if it shows old partitions and data in old partitions, probably not.

Then you can try tools that scan drive for anything that looks like a file. They take very long & you need enough space on another drive to store all the recovered files. With photorec it even found every verson files I deleted many times, so I had lots of issues sorting thru to see if I could get the latest info.

       [URL="http://www.cgsecurity.org/wiki/TestDisk"]http://www.cgsecurity.org/wiki/TestDisk
      [/URL]
 [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

Part of testdisk is photorec. Not just for photos

 [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

   Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)

      
 NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - Getdataback often recommended
[http://www.runtime.org/data-recovery-products.htm](http://www.runtime.org/data-recovery-products.htm)
Also this one:
Then, I settled on Recuva, which isn't as pretty as the others, but it does the job well and is completely free. 

     
 
    [URL="http://www.cgsecurity.org/wiki/TestDisk"]
[/URL]

---

