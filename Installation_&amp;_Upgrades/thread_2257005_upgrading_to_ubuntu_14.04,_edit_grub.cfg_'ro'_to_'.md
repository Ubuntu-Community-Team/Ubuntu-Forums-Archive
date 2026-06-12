---
title: "upgrading to ubuntu 14.04, edit grub.cfg 'ro' to 'rw' everywhere?"
date: 2014-12-16
forum: Installation &amp; Upgrades
---

### Post by riva2 on 2014-12-16
I was upgrading my ubuntu 13.10 to 14.04 and was having this exact [Ubuntu 14.04 doesn' t boot after upgrade from 12.04 installed inside Windows 8.1]("https://askubuntu.com/questions/452631/ubuntu-14-04-doesn-t-boot-after-upgrade-from-12-04-installed-inside-windows-8-1") problem, the sysytem was not starting after upgrading so as was suggested in the link, I entered the grub menu (holding down the shift key) then selected edit boot commands and changed the 'ro' flag to 'rw'. I have been able to start my system but it is a temporary work around and I need to edit my grub.cfg file to permanently set 'ro' to 'rw'.


  I want clarify that should I  change all the occurrences of 'ro quite splash' to 'rw quite splash' in  grub.cfg? There are two places that 'ro quite splash' occurs in grub.cfg  file. I also downloaded grub customizer because I read that you can edit boot commands and set flags more easily but I have not been able to work that out too.
 I am very new with ubuntu. Please help.

---

### Post by ibjsb4 on 2014-12-17
I guess that you know that wubi is no longer supported.
[https://wiki.ubuntu.com/WubiGuide#What_about_Windows_8.3F](https://wiki.ubuntu.com/WubiGuide#What_about_Windows_8.3F)

And grub.cfg is not a good file to edit.
[http://www.dedoimedo.com/computers/grub-2.html#mozTocId920681](http://www.dedoimedo.com/computers/grub-2.html#mozTocId920681)
> grub.cfg is overwritten by certain Grub 2 package updates, whenever a kernel is added or removed, or when the user runs update-grub.
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Is dual boot an option?

---

### Post by hakuna_matata on 2014-12-17
> **riva2 said:**
> 
  I want clarify that should I  change all the occurrences of 'ro quite splash' to 'rw quite splash' in  grub.cfg?

My suggestion: Try to change **/etc/grub.d/10_lupin** instead: [http://ubuntuforums.org/showthread.php?t=2217829&p=13039623#post13039623](http://ubuntuforums.org/showthread.php?t=2217829&p=13039623#post13039623)

---

### Post by riva2 on 2015-01-08
@Hakuna_matata
Hello. Sorry for such a late response. Thanks for the link. 
Should i just write the code you mentioned -
sudo sed -i s/' ro '/' rw '/g /etc/grub.d/10_lupin
sudo update-grub

in the terminal and everything will get fixed ? I am very new with ubuntu and just want to be sure that I don't break anything.

---

### Post by riva2 on 2015-01-08
@ibjsb4
Hello. Sorry for such a late response.
I didn't know that wubi is no longer supported in the newer versions when I ran that upgrade. I guess a sort of warning should be given along with the update message. 
Yes I am using dual boot.

---

### Post by hakuna_matata on 2015-01-08
> **riva2 said:**
> @Hakuna_matata
Should i just write the code you mentioned -
sudo sed -i s/' ro '/' rw '/g /etc/grub.d/10_lupin
sudo update-grub

in the terminal and everything will get fixed ?
Yes, you should. The easiest and safest way is to copy and paste the commands to terminal.

---

### Post by riva2 on 2015-01-08
> **hakuna_matata said:**
> Yes, you should. The easiest and safest way is to copy and paste the commands to terminal.

Thank you so much. Problem fixed!

---

