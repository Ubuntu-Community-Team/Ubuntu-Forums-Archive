---
title: "Ubuntu Installation"
date: 2010-12-03
forum: Installation &amp; Upgrades
---

### Post by Mukundav on 2010-12-03
Dear All,

 I am a new Ubuntu user and I want to use both Windows XP and Ubuntu in my laptop. I have seen ubuntu notebook version to download in ubuntu website.

 I have very less memory space in C drive however I do have 25 Gb and 40 Gb disk space in other two drives. i.e. in E and F.


 Is it possible to install the ubuntu in other drives other than C. 

 How can I install and use GNE GRUB to use Multi OS.

 Can I incorporate the my docs, my music foldres etc.., from XP to Ubuntu even if they located in different drives? eg: c and E

 Also if I incorporate does it replicate the files or just map the storage?

Thanks in advance for your views and advise. 

Regards,
Mukundan

---

### Post by sikander3786 on 2010-12-03
Welcome to Ubuntu and Welcome to the forums :-)

Regarding your query of dual booting Ubuntu and Windows, I would suggest that you please read this page.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Then you must have some queries and we would be able to answer them more appropriately.

Yes you can install Ubuntu to any other partition rather than C:, Ubuntu can boot from an extended/logical partition as well and a primary partition is not necessary.

Regarding Grub, if there is only one HDD present in your system, don't change any settings for the installation of Grub during Ubuntu installer. It would itself get installed in the MBR of your HDD and will be readily dual-boot ;-)

You can use an NTFS partition to share data between Ubuntu and Windows. Linux can read/write to  NTFS quite efficiently. I would advise to use your E: drive as a data sharing partition between Ubuntu and Windows rather than mounting the C: drive itself.

Which version of Ubuntu do you plan to install?

It is advised that you first boot from the Live CD, select the Try mode and test all your hardware with that version of Ubuntu. If all works, install it. If something doesn't, try some different version. 10.10 and 10.04 are the choices these days.

Feel free to post back and ask any further :-)

---

### Post by Mukundav on 2010-12-04
Thanks a ton sikkander. Surely I will try and get back to u, in the mean time can if I try dowload the above said versions and is it possible to burn as an image file. Also will ununtu installation hav the GRUB or should I have to download it seperately. 

Many thanks & Kindest regards,
Mukundan

---

### Post by dino99 on 2010-12-04
grub is proposed automaticaly during installation

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

