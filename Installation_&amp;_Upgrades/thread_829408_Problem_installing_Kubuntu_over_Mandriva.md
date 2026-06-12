---
title: "Problem installing Kubuntu over Mandriva"
date: 2008-06-14
forum: Installation &amp; Upgrades
---

### Post by Sanfel on 2008-06-14
Hello everybody! :)

I had installed Mandriva 2008 Spring to dual-boot with Windows XP in my PC. (Before that I had tried with Kubuntu, Ubuntu and Xubuntu from Wubi installer).

Now I want to get rid of Mandriva and install Kubuntu onto the same partition Mandriva is currently using. I tried to do this from Kubuntu Live CD (first to boot from CD, and then clicking on the desktop icon to install on the hard drive). The problem is when the partition screen appears. Kubuntu's installer doesn't detect Mandriva partition. :( The partition table only has two blocks: Windows and "empty". That is, it only detects the Windows partition that the Mandriva installer had created.

How can I solve this? I've read that I can install Gparted Live CD and use it to solve this problem (If I understood correctly). But where shall I download it? In Mandriva or in Windows? Where should I run it?

BTW, in Mandriva I was able to access (with the root password) information regarding partitions and it seems that I can perform some tasks there (like erasing partitions or resizing). Could I thus change the size assigned to Mandriva from there? Or do something that heps me solve the problem?


AMD Athlon 64
HD: 80 GB
RAM: 1 GB
Nvidia GeForce FX 5500

Thanks in advance!

Santiago

---

### Post by Pumalite on 2008-06-14
Gparted Live CD: you have to burn the iso to disk and boot from it. It doesn't matter where you download it to.
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)

---

### Post by Sanfel on 2008-06-15
Thanks, Pumalite! I've used the Gparted and it detects the Mandriva partitions (the 3 partitions inside the partition for Mandriva)... but the problem is that I can't resize the whole partition, I can only resize the "sub-partitions" (/home, swap and the other one I don't remember the name). I can delete their contents too... But any resizing doesn't affect the overall partition for Mandriva. And that is what I want to do: to shrink, or better, to eliminate Mandriva with its 3 inner partitions in order to leave space for Windows again. That is, I want everything to be exactly as it was before I installed Mandriva. The wole hard drive for Windows. In this way, I think the Kubuntu installer will recognize thye whole hard drive, and will be able to create a partition in it for Kubuntu. Besides, I can't resize the whole Windows partition either.

Perhaps I could solve this by formatting the inner partitions for Mandriva into NTFS? I saw that the Windows partition is NTFS, and the other ones are a different type. Maybe if all of them are NTFS, the installer from Kubuntu will detect the whole hard drive... (I say this from my absolute ignorance, that's why I'm asking: does it make any sense to do this?)

PS: Also, I thought that maybe the problem was that all the partitions are mounted, and I read that to be able to edit them, they must be unmounted. However, when I click on one of them, the option "unmount" is disabled. :( Plus, there is no brown "lock" icon next to it.

Any help is greatly appreciated! 

Santiago

---

### Post by Pumalite on 2008-06-15
The partitions are unmounted. Maybe you are having a problem with an extended partition. Post a screenshot of Gparted and the offending partitions.

---

### Post by Sanfel on 2008-06-16
Well, as I couldn't capture the screenshots from Gparted (even though I read documentation on the net), I copied them by hand and then drew them with a CAD program. I attach the screenshots (what is in grey shading in the images is the disabled otpions). 

Screenshot 1 corresponds to the whole partition for Mandriva.
The other screenshots correspond to its inner partitions.

If other screenshots are necessary, I can do them right away (now it's a matter of copying and pasting and modifying what's needed, so it's very simple).

Thanks in advance!

Santiago

---

### Post by Pumalite on 2008-06-16
I need a picture of the entire drive with exact colors.
Also post:
sudo fdisk -lu

---

### Post by Sanfel on 2008-06-17
Thanks, Pumalite.
Here is the result of "sudo fdisk -lu":

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

Device Boot      Start        End    Blocks   Id  System 
/dev/hda1   *       63  112438934  56219436    7  HPFS/NTFS
/dev/hda2    112438935  156296384  21928725    5  Extended
/dev/hda5    112438998  128809169   8185086   83  Linux
/dev/hda6    128809233  135620729   3405748+  82  Linux swap/Solaris
/dev/hda7    135620793  156296384  10337796   83  Linux

And I attach two more screenshots: one of the Windows partition and the other of the whole drive. In the "Entire drive" screenshot, the black dots at the top are icons that I didn't draw to save time. :)

Thanks in advance!

Santiago

---

### Post by Sanfel on 2008-06-17
Excuse my ignorance, I'm trying to figure out how to post the output of sudo without it appearing so messy...

BTW, in the "Entire drive" screenshot, I forgot to mark in grey the optionsn that are disabled, but they are only "New", "Paste", "Undo", and "Apply", all of them at the top.

---

### Post by Pumalite on 2008-06-17
OK. I think you better use Gparted Live CD and delete everything right of sda1, including the extended partition. Make all of that one large 'free space'. Then format that in it's entirety, ext3. The installo, go Manual and choose that partition. You will have to delete it again to make 2 'New' partitions:
almost all of it for '/'
Save 1 GB for /swap (/swap=RAM in laptops)
Then press 'Forward'
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779&release_id=592033](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779&release_id=592033)
Burn to disk and boot from it.

---

### Post by Sanfel on 2008-06-17
Thanks, Pumalite! I'm doing as you said. I'm in the process of installing Kubuntu, at the partition screen of the Kubuntu installer. I deleted the partition that I had formatted as ext3, as you said. I'm about to create a new partition ('/'), and I have to choose whether it is a primary partition or a logical one. I suppose it's a logical partition, but I want to make sure it is.

Thanks!
Santiago

---

### Post by Pumalite on 2008-06-17
You could make it either one. Keep in mind rule of 4 primary partitions per drive. In doubt, make it logical. Ubuntu works fine in logical partitions.

---

### Post by Sanfel on 2008-06-17
Thanks so much, Pumalite! I was able to make it! I deleted Mandriva and now I have a dual boot system with Windows and Kubuntu... 

Thank you very much!

I'm glad we have the help of this community!

Santiago

---

### Post by Pumalite on 2008-06-18
You are welcome and good luck.

---

