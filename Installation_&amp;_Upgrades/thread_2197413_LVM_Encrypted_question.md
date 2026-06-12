---
title: "LVM Encrypted question"
date: 2014-01-03
forum: Installation &amp; Upgrades
---

### Post by ags40 on 2014-01-03
****I have installed from USB to my 160GB HDD, Kubuntu 13.10, choosing the 'Guided LVM Encrypted' option. Everything goes perfect until I have to enter the passphrase after reboot. It simply is not available  and the mouse is completely absent.
Any thoughts? Thanks.

---

### Post by ags40 on 2014-02-03
*bump*

---

### Post by Herman on 2014-02-04
Have you tried giving it some time and then simply typing your password at the blank screen and pressing enter?

---

### Post by ags40 on 2014-02-04
Your sarcasm is appreciated. Yes, I waited two hours the last time I installed for the second time. But, I do thank you for your answer. The only I got. I moved on and installed Sabayon for the time being. Thanks again.

---

### Post by sudodus on 2014-02-04
I have tested what I think is the corresponding Lubuntu encrypted system according to the following link, and it works.

[http://iso.qa.ubuntu.com/qatracker/testcases/1439/info](http://iso.qa.ubuntu.com/qatracker/testcases/1439/info)

---

### Post by Herman on 2014-02-04
I wasn't being sarcastic, I'm honestly trying to be helpful. It sometimes happens that the screen for unlocking the encrypted disk fails to appear during booting the encrypted installations. This has been either a problem or an added security feature (now I'm  being humorous), since as far back as I can remember with the encrypted  installations. Normally it is still possible to continue booting by typing the encryption password after waiting long enough for it to have appeared, even though you cannot see anything.

In the past I have been successful in dealing with problems which can occur in an incomplete installation. Sometimes the encrypted disk is just unable to be unlocked due to missing or misconfigured files in the operating system. That type of thing can happen sometimes when trying out pre-release versions of Ubuntu, or maybe I guess from corrupted packages downloaded from the internet during installation. Chrooting in from a Live CD or another Ubunutu installation, (in a USB drive maybe), I would try taking a look for the /etc/crypttab file to make sure it is present and looks right, possibly edit /etc/initramfs-tools/modules and maybe create a new initrd.img.

Useful links: 
 '[EncryptedFilesystemsViaUbiquity]("https://help.ubuntu.com/community/EncryptedFilesystemsViaUbiquity")' - Ubuntu Community Docs, 
'[Encrypted Filesystem LVM How-to]("https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto")' - Ubuntu Community Docs, see especially this part: [final preparation]("https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto#Final_preparation"). 
' [how to chroot, simple and fast]("http://ubuntuforums.org/showthread.php?t=1156240")', by taavikko - Ubuntu Web Forums
[How to Resize a LUKS Encrypted File System]("http://ubuntuforums.org/showthread.php?p=4530641") - bodhi.zazen - Ubuntu Web Forums 				

I am wondering if you can see the screen for unlocking the encrypted disk or not, from your first post it's hard to tell. Maybe you mean you can see it but cannot get the box activated where you type the encryption password. If that happened to me I would first try booting in safe mode, then switch to the desktop after booting up. I ahven not tried out the safe mode in 13.10 yet, so I hope I would be steering you in the right direction, (if you still had the problem system installed). Maybe this post will help someone else.

---

### Post by ags40 on 2014-02-04
Thanks you sudous. I will read it and giveit a try. Thanks again.

---

### Post by ags40 on 2014-02-04
.Thanks you Herman! That was a complete and great answer. I will through all of it in the next days and let you know. 
In regard to the screen: yes, I can see a perfectly formed screen with the rectangle to make the input of the passphrase but is grayed and the mouse was not responding and no HD activity apparent.

Since I had some pressing thing to do, I moved on and installed Sabayon. Everything appears to go well so far.

Thank you very again

---

