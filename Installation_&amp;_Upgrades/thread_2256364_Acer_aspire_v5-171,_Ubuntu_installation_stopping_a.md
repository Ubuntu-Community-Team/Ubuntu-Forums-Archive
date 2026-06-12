---
title: "Acer aspire v5-171, Ubuntu installation stopping at &quot;Wireless&quot;"
date: 2014-12-11
forum: Installation &amp; Upgrades
---

### Post by bweiss22 on 2014-12-11
Hello I just got an Acer aspire v5-171 that I was planning on putting ubuntu on. It came with no hard drive so I put a toshiba hardrive that I had laying around into it and it seemed to fit and work, although I have never changed a harddrive so I am not even sure what else I need to do. Anyways after some reading I got the ubuntu disk to boot (had to disable secure boot) and start installing but it always freezes at the "wireless" part very early in the installation. It happens when I click continue and I am pretty sure the reason might have to do with the toshiba harddrive I put into it, because the part after "wireless" is the partitioning (If I remember correctly). I took it into a computer shop today and the guy mentioned some stuff about the legacy vs uefi but he was going a bit quick for me to comprehend it all. So if there is anyone out there that could give me an opinion it would be much apprecaited!

---

### Post by oldfred on 2014-12-12
If installing to a blank drive, you can install in UEFI or BIOS boot mode. But you have to change some settings in UEFI/BIOS. 
And how you boot installer, UEFI or BIOS is how it installs.
Do you have wired Ethernet connection? Many systems have issues with wireless and you may need to download a wireless driver. Where almost every system will work with wired driver on installer for install.

 [http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)

      How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)

 Acer V5-571P-6815 secure boot off worked Shows Diskpart
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)

 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by bweiss22 on 2014-12-12
I ended up figuring it out myself. All I had to do was run the ubuntu live cd and use the disk utility to format the hard drive. Oddly gparted didnt see it but the disk utility did. After I formatted it the installation worked.

---

