---
title: "Accidentally deleted all windows when installing ubuntu. Want dual boot?"
date: 2014-03-25
forum: Installation &amp; Upgrades
---

### Post by josh32 on 2014-03-25
So basically somehow or another i completed deleted all windows and have been using ubuntu for a few months. I now want windows 7 back, I have the installation cd. How do I sort the partition drives to have dual boot? 

Provided is a screenshot of Gparted if that helps at all. My laptop is HP G62, 64 bit.

[ATTACH=CONFIG]251473[/ATTACH]

Thanks

---

### Post by Mark Phelps on 2014-03-25
First of all, this may be a "terminology" difference, but Win7 does NOT come on a CD -- it is far too large for that; instead, it comes on a DVD.  So, if it's really a DVD, you're in good shape; if it's really a CD -- you're not.

Since you want Win7 in addition, then you need to do the following:
1) Boot from Ubuntu install media
2) Run GParted and shrink down the first partition to leave 50GB of room for Win7
3) Format the new unallocated space as NTFS
4) Reboot, from the Win7 DVD, select the NTFS partition you just created, and FORMAT it -- this is important.
5) When Win7 is done installing and you reboot, you'll probably just boot right into it -- as it overwrites the disk MBR in the process
6) To get Ubuntu access back, read the details in the link: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by josh32 on 2014-03-26
> **Mark Phelps said:**
> First of all, this may be a "terminology" difference, but Win7 does NOT come on a CD -- it is far too large for that; instead, it comes on a DVD.  So, if it's really a DVD, you're in good shape; if it's really a CD -- you're not.

Since you want Win7 in addition, then you need to do the following:
1) Boot from Ubuntu install media
2) Run GParted and shrink down the first partition to leave 50GB of room for Win7
3) Format the new unallocated space as NTFS
4) Reboot, from the Win7 DVD, select the NTFS partition you just created, and FORMAT it -- this is important.
5) When Win7 is done installing and you reboot, you'll probably just boot right into it -- as it overwrites the disk MBR in the process
6) To get Ubuntu access back, read the details in the link: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Thanks for the response, and yes i meant DVD. Is there anyway you can send me a link or give me more explicit instructions I'm not very experienced?

---

### Post by fantab on 2014-03-26
Go through this [Gparted tutorial]("http://www.dedoimedo.com/computers/gparted.html") and you will understand 2 and 3 steps mentioned by Mark.
Shrink=Resize.

Make a note of the 4th step. You have to reformat the partition (for Windows) with Windows installer with NTFS... so you will be formatting it twice.

---

### Post by josh32 on 2014-03-26
Thanks fantab :-)

---

