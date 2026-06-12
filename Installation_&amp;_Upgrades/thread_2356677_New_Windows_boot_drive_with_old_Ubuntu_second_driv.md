---
title: "New Windows boot drive with old Ubuntu second drive"
date: 2017-03-25
forum: Installation &amp; Upgrades
---

### Post by mslinklater on 2017-03-25
HI - I had 16.04 installed in my primary drive for a few months then had to take the drive out and install Windows10 onto a fresh drive. Now I want to put my old Ubuntu drive back into my machine as a second drive and be able to dual-boot into either WIn10 or Ubuntu.

So sda has my Windows install - which auto boots etc.
sdb is my old Ubuntu install, which still has all my old data and OS on.

Can someone tell me how I install grub and set it up so that my machine will boot into Win10 off sda or Ubuntu off sdb ?

Thanks.

---

### Post by yancek on 2017-03-25
Is windows 10 installed using UEFI/GPT?
Was Ubuntu installed using UEFI/GPT?

Both system should be either UEFI or both the older MBR.  If not, you may have problems although it may be possible with separate drives.
Normally, if they were both MBR installs, you would simply set the drive with Ubuntu on to first boot priority in the BIOS, boot it and open a terminal and run:

```
sudo update-grub
```

---

### Post by mslinklater on 2017-03-26
Thanks for the suggestion. I decided to swap the drives around so Ubuntu was sda, then ran 'sudo update-grub' as you suggested, and grub automatically found the Win10 install on sdb and set up a boot option for me.

All is working perfectly. Thank you !

---

### Post by RobGoss on 2017-03-26
Glad you got it all sorted out, Is you have resolved your issue you can mark thread as solved. You can do this by using the **Thread tool** tab at the top of this post

Thanks so much

---

