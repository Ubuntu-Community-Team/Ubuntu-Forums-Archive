---
title: "Upgrading Windows how to get GRUB back"
date: 2010-07-06
forum: Installation &amp; Upgrades
---

### Post by sadssandiford on 2010-07-06
[SIZE=2]Hi All,

I had Vista loaded on my computer, then loaded the BRILLIANT ubuntu onto a second partition!  This gave me the GRUB boot loader which is fine.

My 2 points are;

1.   Can I change the position of the items in the GRUB loader so if no keys are pressed it loads Windows automatically??  (Its for my sons computer!!)  Also can I edit the GRUB so its less complicated for him??

2.   I want to update his Windows to Win 7, free upgrade!  This over rights the Win partition and will therefore get rid of my GRUB loader.  When I have updated how can I get back the ability to chose between booting Win 7 and Ubuntu??  How do I get the GRUB back??


This is probably easy peasy but Im a brand new convert to Ubuntu so need help!!

Please as I dont want to loose my Ubuntu!!

Sads[/SIZE]

---

### Post by lechien73 on 2010-07-06
Hi,

I'm glad you're enjoying using Ubuntu. In answer to your questions:

1. This link may help you: [http://uri.tl/7](http://uri.tl/7) look particularly under section 5 about editing /etc/default/grub, you will want to change the **GRUB_DEFAULT=** option. Since the positions of items in the Grub menu shift around quite a bit - due to kernel updates etc, you may be best changing it to **GRUB_DEFAULT="xxxx"**, where "xxxx" is the exact name of Windows in the Grub menu.

2. Another link :) [http://uri.tl/8](http://uri.tl/8) this time look under "How to restore the Ubuntu grub bootloader (9.10 and beyond)"

Hope this helps. Both of the links are to other posts in the Ubuntu forms.

---

### Post by sadssandiford on 2010-07-06
[SIZE=2]Thanks for info, but the re-installing the GRUB loader info is from within Ubuntu!!  If I update Windows and loose the GRUB loader, it will boot me into Win 7.  How do I get into Ubuntu??[/SIZE]

---

### Post by imondanet174 on 2010-07-06
Hello Sadssandiford
 
You can try this link too
 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
 
Cheers

---

