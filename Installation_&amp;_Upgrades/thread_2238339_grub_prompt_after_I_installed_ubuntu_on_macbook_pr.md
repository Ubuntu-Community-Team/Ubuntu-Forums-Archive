---
title: "grub prompt after I installed ubuntu on macbook pro"
date: 2014-08-07
forum: Installation &amp; Upgrades
---

### Post by tim61 on 2014-08-07
Hi,
I have a late 2103 Macbook Pro and am wanting to experiment with ubuntu.  I have a usb-stick which boots and offers to try ubuntu or install it.  I tried installing it onto an external USB HD.  I followed some instructions that seemed close to my setup: //help.ubuntu.com/community/MacBookPro11-1/Saucy.
Included in these instructions were some edits of grub.  But when I came to the line: 
sudo update-grub
I got an error about not finding canonical cow or something.
Now when I reboot I get a grub command prompt and an error "failure reading sector 0x0 from hd0."
I then tried using instructions on //help.ubuntu.com/community/Boot-Repair and this generated a paste bin report 
paste.ubuntu.com/7979596
, said that it had solved the problem, but the problem still persists (i.e. grub command prompt).

Is this is the right place to post this question?  Can anyone help?

Tim

---

### Post by yancek on 2014-08-07
You can't update grub on an installed system from a DVD/flash drive without using chroot method.  Any reason why you did not post the contents of the Boot Repair report as that would be useful.

---

### Post by tim61 on 2014-08-11
Please ignore this thread now.  Solved by wiping and reinstalling mac. :(

---

