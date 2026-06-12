---
title: "ubuntu 13.04 install DVD"
date: 2013-11-11
forum: Installation &amp; Upgrades
---

### Post by harlie on 2013-11-11
I am trying to install ubuntu 13.04  64 bit in the place of the existing 32 bit I am bual booting with MS Windows. When I start to install form the 13.04 64 bit DVD I go to the menu selection  "something else' because I want to replace the existing ubuntu but not antyhing else leave Windows in place. When "something else" opens I get a box showing the partitions, I select the partition where ubuntu is installed. I click on "install now" then a box opens that says "no root file system is defined please correct this from the partition menu". I can't get beyond this point and cancle the operation. How do I get past this point? There is what appears to be a check box under the colum "format' but with this partition highlighted when I try to check it nothing happens. Help if you can.

Harlie

---

### Post by fantab on 2013-11-11
After selecting the Partition you want to install to you have select Use As = Ext4; Mountpoint = / and check Format box.

---

### Post by sammiev on 2013-11-11
I would have just used gparted and erased the 32 bit ubuntu partition. Booted off the DVD and it would of installed were the 32 bit ubuntu was, not unless you wanted something different.

---

### Post by harlie on 2013-11-13
Thanks I did as #2 post and it worked although the wording was somewhat different in the menus I was able to figure it out, so now I have the 64 bit installed and working. I didn't try the answer in #3 to use gparted, I am not familiar with that and can't find it in my manual.

Thanks   Harlie

---

