---
title: "More problems, can not install Ubuntu and can not reboot Vista"
date: 2008-04-16
forum: Installation &amp; Upgrades
---

### Post by agrab0ekim on 2008-04-16
I have recently started attempting to install Ubuntu via a cd. my computer automatically goes to the Ubuntu instalation and i attempt to start. It gets to the install section then says it can not find a certain file (corrupt), i hit okay, and it says that it can not download the file. Eventually, after about twenty of these, it says it can not install the file

so, two things
1) how can i fix this
2) I attempted to get my computer to boot from the HD and it can no longer find it, which means i can not boot Vista, how can i fix that

---

### Post by kutjara on 2008-04-16
> **agrab0ekim said:**
> I have recently started attempting to install Ubuntu via a cd. my computer automatically goes to the Ubuntu instalation and i attempt to start. It gets to the install section then says it can not find a certain file (corrupt), i hit okay, and it says that it can not download the file. Eventually, after about twenty of these, it says it can not install the file

so, two things
1) how can i fix this
2) I attempted to get my computer to boot from the HD and it can no longer find it, which means i can not boot Vista, how can i fix that

You should be able to get your machine to boot Vista by using the Vista CD (or the recovery disks that came with your machine). Boot off the CD and choose the "Repair" option. That'll restore your MBR (master boot record) and should enable you to boot Vista normally.

When you do that, however, Ubuntu will no longer be bootable, so only take this course of action if you're prepared to reinstall Ubuntu. If you want to keep trying to fix your Ubuntu problem, then you'll need to edit your /boot/grub/menu.lst file so that it will recognize the Vista partition. I don't know the specific entries you need to make, but there are no doubt several threads around here on editing menu.lst.

---

### Post by agrab0ekim on 2008-04-16
> **kutjara said:**
> You should be able to get your machine to boot Vista by using the Vista CD (or the recovery disks that came with your machine). Boot off the CD and choose the "Repair" option. That'll restore your MBR (master boot record) and should enable you to boot Vista normally.

When you do that, however, Ubuntu will no longer be bootable, so only take this course of action if you're prepared to reinstall Ubuntu. If you want to keep trying to fix your Ubuntu problem, then you'll need to edit your /boot/grub/menu.lst file so that it will recognize the Vista partition. I don't know the specific entries you need to make, but there are no doubt several threads around here on editing menu.lst.

I never got a disk that came with the machine so dont know how to fix it off of that
well, i can not install the grub without the rest installed, and cant do that

---

### Post by kutjara on 2008-04-16
> **agrab0ekim said:**
> I never got a disk that came with the machine so dont know how to fix it off of that
well, i can not install the grub without the rest installed, and cant do that

You can create a Vista repair disk by downloading and burning the image here:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Once you've burned the CD, boot from it and use the repair option to fix your MBR.

---

