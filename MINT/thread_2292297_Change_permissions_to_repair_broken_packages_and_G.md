---
title: "Change permissions to repair broken packages and Grub from a LiveCD"
date: 2015-08-26
forum: MINT
---

### Post by eric.lapoint on 2015-08-26
Hello,

I messed up my system. I can't boot anymore: broken packages and Grub not functionning.

I'm basically trying to follow the steps described by Wthlteh in this post:[http://ubuntuforums.org/showthread.php?t=1654368&page=2](http://ubuntuforums.org/showthread.php?t=1654368&page=2), hoping I can repair my system. When I do the chroot /media/XXXX     step in the terminal, I get a 'Permission denied". How can I change the permissions so that complete the steps in question? Will it work presumably? Anything missing?
 
Any help will be appreciated. Be detailed if possible as my knowledge are limited.

Some details, if needed, of my system can be found here: [http://paste.ubuntu.com/12197153/](http://paste.ubuntu.com/12197153/)

Thank you in advance,

Eric

---

### Post by yancek on 2015-08-27
The problem is not permissions but rather the fact that you have windows installed which you did not mention in your post as well as Ubuntu.  That in itself is obviously not the problem but the problem is that you have Grub installed to the master boot record (see the beginning of the boot repair output) and you are also using windows 8 or newer in UEFI.  You should not install any code to the MBR when using UEFI.  You also have an EFI partition with the files to boot both windows and Ubuntu in EFI.  You might take a look in the BIOS on your computer to see if you have optionss to boot using EFI.  I don't use it myself, so you might wait for someone else more familiar with UEFI to post or do a search here at the forums as there are many posts on similar problems.

---

