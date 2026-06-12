---
title: "[SOLVED] Problem while install, or run Live Ubuntu 7.10, please help!"
date: 2008-04-08
forum: Installation &amp; Upgrades
---

### Post by ngduonglam on 2008-04-08
When I started booting from Ubuntu 710 CD, then choose to install, or even run on LiveCD, got the following error:
[B][COLOR="Red"]checksum for device 1 is not valid (0x89)
checksum for device 2 is not valid (0xbe)[/COLOR][/B]

Then, I tried with the ** i8042.noloop** option, but still the same. Can anyone help me to solve this?

_P/S_: I'm using Lenovo 3000 n200 laptop with Windows Vista Ultimate installed on it.

---

### Post by zvacet on 2008-04-08
Check [md5sum](https://help.ubuntu.com/community/HowToMD5SUM) and check disc integrity.If md5sum is not correct download same iso with  torrent and point download to the folder where is existing iso.hat way torrent will just check your iso and replace corrupted files.When it is finish check md5sum again.If is correct now burn iso on disc and check CD integrity.If everyhing is O.K. go for install.

---

### Post by Partyboi2 on 2008-04-08
Are you trying to install ubuntu as a virtual machine?

---

### Post by ngduonglam on 2008-04-08
**[COLOR="Blue"]To zvacet:[/COLOR]** 
I checked to md5sum, and they're different. Now, I'm trying to download another one. I will keep posting here if still can not work with the new download. Thanks for your quick response.

[COLOR="Blue"]**To Partyboi2:**[/COLOR]
I installed to my laptop as a secondary OS. I want to play dual OS.

---

### Post by ngduonglam on 2008-04-09
> **zvacet said:**
> Check [md5sum](https://help.ubuntu.com/community/HowToMD5SUM) and check disc integrity.If md5sum is not correct download same iso with  torrent and point download to the folder where is existing iso.hat way torrent will just check your iso and replace corrupted files.When it is finish check md5sum again.If is correct now burn iso on disc and check CD integrity.If everyhing is O.K. go for install.

I tried to download a new ISO file of Ubuntu 7.10, then check md5sum as well as CD intergrity check. Both of them are ok. Then I boot from CD to start from CD but I got the same error as I said before :(.

Could you please give me some other advices?

---

