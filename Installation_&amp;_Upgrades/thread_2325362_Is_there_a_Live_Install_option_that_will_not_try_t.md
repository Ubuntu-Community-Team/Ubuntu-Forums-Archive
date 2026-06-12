---
title: "Is there a Live Install option that will not try to install grub?"
date: 2016-05-21
forum: Installation &amp; Upgrades
---

### Post by miatawnt2b on 2016-05-21
I'm having issues with the live installer erroring out of the install when trying to install grub. Is there a way to tell the installer to skip that step?
-J

---

### Post by yancek on 2016-05-21
As far as I know, you have the option to install to the partition on which you install Ubuntu, to the MBR (if you are using MBR) or an EFI partition so, no I don't believe you can although that option was available in some distros years ago, certainly with Grub Legacy.

Maybe some specifics on what happens, what error you get would help as someone may have a suggestion.

---

### Post by dpaulat on 2016-05-21
I believe that is the last step of the install anyway.  You may be able to try boot-repair after the failure (note it will install GRUB): [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by grahammechanical on 2016-05-21
We need a boot loader. Best to identify the error message and ask for help in solving the problem than trying to force the install to finish without a boot loader installed. We could end up with an unusable OS.

---

### Post by malspa on 2016-05-21
With some distros you can do the installation without installing grub. Used to be able to do it in Ubuntu with the alternate CD, but there's no alternate CD now. See [http://askubuntu.com/questions/132116/installing-ubuntu-12-04-without-installing-grub](http://askubuntu.com/questions/132116/installing-ubuntu-12-04-without-installing-grub) and [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/690926](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/690926).

Edit: Not sure if the **ubiquity -b** option works these days...

---

### Post by yancek on 2016-05-21
You haven't indicated whether you have another operating system installed with a bootloader.  If you don't, you need to install Grub.  What error do you get or what exactly happens on the grub install?

---

