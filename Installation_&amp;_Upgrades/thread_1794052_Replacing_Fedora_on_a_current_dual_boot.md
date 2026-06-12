---
title: "Replacing Fedora on a current dual boot"
date: 2011-06-30
forum: Installation &amp; Upgrades
---

### Post by kikenovic on 2011-06-30
Hi everyone,

Currently I have a dual boot Win 7 / Fedora 14 on my Dell Inspiron 1546.

After being unable to upgrade to F15 I think it's time to try something different like Ubuntu 11.04

I'd like to format all the Linux partitions, install Ubuntu there and being able to boot to Win 7 from Grub (just like I currently do with Fedora).

Can I just go ahead and install like usual, or is there anything else I should consider?

Do you think Ubuntu will have a problem finding Win7?

Thanks.

---

### Post by ajgreeny on 2011-06-30
Should be very easy.

1.  Pop in the live CD/USB and boot to it, just to check that everything works OK.

2.  Double click on the "Install ubuntu" icon.

3.  When you get to the "Prepare disk" page choose the final option, "Something else".  This will let you see all your current partitions, delete the ones you want to get rid of and then install to the space.

4.  Consider making a new separate /home partition if you don't already use one as it is very helpful when you re-install your OS.  [Separate home at install.]("http://www.psychocats.net/ubuntu/installseparatehome")

5.  Grub2 will be placed on the MBR of your first disk sda by default and will find your windows install, and should offer you the choice when you boot.

---

### Post by coffeecat on 2011-06-30
+1 to what ajgreeny said. The only thing that I'd add, as an alternative to what he said under #3, instead of deleting all the partitions, you can simply re-use them. Mark them to be re-formatted, of course, and define the mountpoints as appropriate. You don't have to worry about the swap partition. It will be automatically picked up and reformatted and, because of the magic of the Ubuntu installer, will be re-assigned the previous UUID. That's so as not to upset other Linux installations for those who happen to have a Linux multi-boot setup - not a thing that Fedora takes into consideration at all. :rolleyes: :wink:

And, yes, Ubuntu will pick up the presence of Windows and give you a dual-boot menu.

Good luck!

---

### Post by YesWeCan on 2011-06-30
I would just add that for flexibility it is best to use just one primary partition for Ubuntu. Make it an extended partition, then make logical partitions within it for / and swap and /home and anything else.
This leaves you with 3 primaries for Windows or something else. :)

The Ubuntu Grub2 boot-loader will detect your Windows installation.

---

### Post by kikenovic on 2011-06-30
Thanks to all for your help. I'm about to give it a shot in a few mins.

Bye bye Fedora, hello Ubuntu.

---

### Post by kikenovic on 2011-06-30
Everything went fine. I'm posting this from my brand new Ubuntu installation :D

I deleted the Fedora partitions and created a / partiton and a /home partition.

Fedora's Grub was replaced by Ubuntu's and I'm able to boot into Windows 7 as usual.

Thanks.

---

### Post by nothingspecial on 2011-07-01
> **coffeecat said:**
> +1 to what ajgreeny said. The only thing that I'd add, as an alternative to what he said under #3, instead of deleting all the partitions, you can simply re-use them. Mark them to be re-formatted, of course, and define the mountpoints as appropriate. You don't have to worry about the swap partition. It will be automatically picked up and reformatted and, because of the magic of the Ubuntu installer, will be re-assigned the previous UUID. That's so as not to upset other Linux installations for those who happen to have a Linux multi-boot setup - not a thing that Fedora takes into consideration at all. :rolleyes: :wink:

And, yes, Ubuntu will pick up the presence of Windows and give you a dual-boot menu.

Good luck!

Fedora's installer does have the option to assign UUID manually.

---

