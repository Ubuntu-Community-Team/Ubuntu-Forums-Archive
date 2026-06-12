---
title: "Partitioning, dual boot with Vista"
date: 2014-10-05
forum: Installation &amp; Upgrades
---

### Post by grumpy_old_man on 2014-10-05
I have just down loaded latest version of Unbuntu.  I have installed unbuntu previously alongside Vista and at that time I got an option to install alongside Vista.  On the current software I don't get this option.  The options are to install and remove vista, or something else. I have found the installation guide which suggests that I should be presented with an option to install along side vista. I am trying to install the 32 bit version.

Thank you

gom

---

### Post by nerdtron on 2014-10-05
Can you provide a screenshot of the installer screen on how you reached and the error you have encountered?

---

### Post by yancek on 2014-10-05
Which installation type option did you select?  If you select the 'Something Else' option, you will get an 'Allocate drive space' window and you can either select a partition which is available or free/unallocated space.  If you select a partition, click the Change tab below the main window, if you select free space, select the Add tab below the main window.  In either case you will get a new 'Edit a partition' window where you will have several options to select.  The no root filesystem defined can be eliminated by going down to Mount point in that window, clicking the down arrow to the extreme right of the entry box and selecting the option:  /  just the forward slash which is the symbol for root.  Click Ok and that should resolve that problem.  If you are using one of the auto-install methods, good luck.

---

### Post by grumpy_old_man on 2014-10-05
Thanks for the reply.  I have been looking at Unbuntu installation guide and it would seem I should be given the option to install alongside vista but this option is missing, see edited post above.

gom

---

### Post by nerdtron on 2014-10-05
> I have installed unbuntu previously alongside Vista and at that time I got an option to install alongside Vista.

Alright.. so you mean there is an ubuntu version currently installed alongside vista and you want to replace Ubuntu to a newer version?

If this is correct, then you should definitely choose "Something Else" option. Are you familiar with your partition sizes? Because it would be hard to identify each drive as they are not labelled C: or D: once you go to the partitioning screen.

---

### Post by grumpy_old_man on 2014-10-05
Sorry my post was not clear.  I had reformatted hard drive and the previous version of Unbuntu has been removed, so new installation.  As I am not getting option to install alongside Vista, could download be corrupted?

gom

---

### Post by nerdtron on 2014-10-05
Since this is just a fresh install, are you comfortable editing your partitions. You can do manual install. Follow the tutorial with screenshots. Although your partition sizes, you should be the one to decide.
[http://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/](http://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/)

Not sure if you can shrink your partition in Vista (as you can on windows 7). So it would be easier to create a partition for Ubuntu while you are in Vista and then boot into Ubuntu to start the installation.

---

### Post by grumpy_old_man on 2014-10-05
Thanks for your reply.  I have read the through the link provided, this refers to W8, does it apply equally to Vista, in that I need to create the three partitions referred to?

gom

---

### Post by nerdtron on 2014-10-05
It does apply to windows vista. The only required partitions are / and the swap partitions on the tutorial. This two partitions are created on background when you choose "Install Alongside Windows". You are now going to create/assign them manually. The / partition will be the size of your Ubuntu partition just like how you would resize on the "Install Alongside Window" option. Good luck and post the screenshot here of your partitions before continuing on the installation.

---

### Post by Vladlenin5000 on 2014-10-05
> **grumpy_old_man said:**
> Thanks for your reply.  I have read the through the link provided, this refers to W8, does it apply equally to Vista, in that I need to create the three partitions referred to?

gom


No, you don't. And you probably don't need to worry about UEFI.
What still isn't clear to me is precisely that Windows you mentioned. Not clear because in post #6 you said
> I had reformatted hard drive and the previous version of Unbuntu has been removed, so new installation.
So, how exactly have reformatted it? You may have deleted Windows as well...

---

### Post by grumpy_old_man on 2014-10-10
I have now succesfully installed Unbuntu.  When I reloaded software from dvd the option to intall alongside Vista appeared on menu and so didn't have to form partitons etc.  Thank you for responding to my intial plea for help.

gom

---

