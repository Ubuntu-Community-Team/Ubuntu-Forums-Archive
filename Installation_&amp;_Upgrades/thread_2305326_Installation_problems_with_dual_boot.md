---
title: "Installation problems with dual boot"
date: 2015-12-04
forum: Installation &amp; Upgrades
---

### Post by Edison_James on 2015-12-04
Hello, I have an Acer Aspire M Laptop, 3 years old, originally came with Windows 8 recently upgraded to Windows 10. I have dual booted ubntu and windows before but never on this device  or using the UEFI, I have disabled secure boot. The issue is this. Using windows tools I created some unallocated space on the drive, (which is SSD). When I attempt to use GParted to create a logical partition in this unallocated space, I get the following message.
                       /dev/sda contains GPT signatures, indicating that it has a GPT table. However it does not have a valid fake msdos partition table, as it should. Perhaps it was corrupted by a program that doesn't understand GPT partition tables. Or perhaps you deleted the GPT table, and are now using an msdos partition table. Is this a GPT partition table  (yes) (no).

When I went ahead with an installation attempt anyway, Ubuntu did not recognize any OS on the Disk, and offered to install to the disk treating it as all unallocated. Which of course I can't do as I don't want to lose my Windows 10, which I like very much.  Any suggestions? Thank you for your time.

---

### Post by yancek on 2015-12-04
If you are using windows with UEFI then you are also using GPT.  With GPT there is no such thing as a logical partitions, they are all primary up to as many as 128 partitions.  Just create as a primary as that is what the message is telling you.

---

### Post by Edison_James on 2015-12-04
Thank you yancek. I will have another try with GParted.

Unfortunately, GParted does not give me the option suggested. It only recognizes my drive as entire unallocated space. It doesn't recognize any existing partitions, of which there are 3 plus the unallocated space I created earlier. I am using parted Magic which I have always had good success with, although my version is 3 years old, if that makes a difference?  
Edit I went back to Windows and used their tools to create a new simple volume. So I now have a partition instead of unallocated space, when I tried another install of Ubuntu it still does not recognize this partition nor any existing operating system on the disk. Attached is a screen shot of my partition table.

---

### Post by Geoffrey_Arndt on 2015-12-04
Seems there is some similarity to this thread (perhaps same fix too?):

See posts #5 thru #8

[http://ubuntuforums.org/showthread.php?t=2180625](http://ubuntuforums.org/showthread.php?t=2180625)

---

### Post by yancek on 2015-12-05
The image you posted in post #4 above from windows Disk Management shows 4 partitions, 3 ntfs and the first one which may be a boot partition.  Whatever it is, it's too small to install Ubuntu to.  Two partitions are 350MB and 450MB which are obviously both too small.  The only one on which you could install Ubuntu is the one referred to as E, 19GB.  Unfortunately, that has been formatted with an ntfs proprietary filesystem and you can't install any Linux on it, not Ubuntu anyway.  Creating the partition from windows should be OK but formatting it ntfs  won't work to install Ubuntu.

Which installation type option did you use?  I think it would be best if you selected the manual (Something Else) option.  If you did that and still have problems you might need to get the boot repair software and run it and post the output here as it will give a much more detailed look.

---

### Post by Edison_James on 2015-12-05
I did use the manual option on the install attempt. Puzzling over this issue, I do have a theory why this is not working. This Laptop has had Windows 8, reinstalled 3 times, once as a result of hacking, twice due to bugs and glitches. It is possible some of the manufacturer installed software has been deleted which would explain the GParted error message. I am not sure if I can recover the factory defaults myself or if I will have to go back to the Geek Squad at Best Buy where I bought it. At any rate, it may not be possible to install a dual boot until this has been resolved. Unless I can reformat partition E to ext 4. If windows tools won't do it, I will download Ease Us Todo and try that. Thanks for the help, the ntfs proprietary filesystem was something I was not aware of.

---

### Post by yancek on 2015-12-05
ntfs filesystem are only for windows.  You can format a partition during the install of Ubuntu although it usually works better to just leave the space unallocated and you can certainly delete that partition in windows.  You should select the Something Else option for installation type.  You need to also boot Ubuntu UEFI from the install medium.  I can't tell you how that is done as I don't use UEFI.  Your original post with the GPT error would mean you are using UEFI as my understanding is windows needs UEFI if using GPT.

---

### Post by al.coda on 2015-12-06
Has this issue been resolved yet?

---

### Post by oldfred on 2015-12-07
If you have gpt signatures, but now have BIOS/MBR install of Windows then you have the issue where Windows does not correctly convert a gpt partitioned drive from gpt to MBR. It leaves the backup gpt partition table. The Linux tools which now see both MBR & gpt get confused and only want to totally repartition drive.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sda

But you also are showing the MBR limit of 4 primary partitions. You need to convert one primary to an extended so then you can create logical partitions inside the extended.
      
 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

### Post by Edison_James on 2015-12-07
Thank you for your help here oldfred, your explanation makes sense to me. My antivirus program wouldn't let me download fixparts. So I will try as you suggested to convert a primary partition to logical and install to that.
Edit; Thank you for the links, very interesting stuff.

---

### Post by oldfred on 2015-12-07
Run fixparts from Ubuntu live installer. Inside that you should have no issue downloading it.

---

### Post by Edison_James on 2015-12-07
Thank you oldfred, I have success. I will relate the steps here in case anyone else needs it. I used easeUS to change my windows partition table. I downloaded a new version of Ubuntu 15.04 and burned  a CD. I installed with that and after a failure to boot using the something else option. I totally deleted all but 2 of my windows partitions. Then I reinstalled using the install alongside choice, which was easy to use and worked. The new version recognized my Windows OS both times. The first time I used boot repair but it wouldn't work as it recognized GPT signatures.
I now have my dual boot, Windows 10 and Ubuntu 15.04. Again my thanks for your expertise, your help and your patience.

---

### Post by Geoffrey_Arndt on 2015-12-07
Glad to read about your successful install, after do much effort (trial & error) . . . . HOWEVER . . . . keep your eyes open when doing major Windows 10 updates.    There are daily reports on these forums and others across the web about Win 10 ruining dual boot configurations.

---

### Post by Edison_James on 2015-12-08
> **Geoffrey_Arndt said:**
> Glad to read about your successful install, after do much effort (trial & error) . . . . HOWEVER . . . . keep your eyes open when doing major Windows 10 updates.    There are daily reports on these forums and others across the web about Win 10 ruining dual boot configurations.

Thank you for this insight.I really think that my problem stemmed from the fact of a corrupted GPT table, due to multiple reset and installs. I do have Windows 8 install media, which has been handy however it does have the potential to erase all of the manufacturer's software. Any way thank's again for the advice.

---

