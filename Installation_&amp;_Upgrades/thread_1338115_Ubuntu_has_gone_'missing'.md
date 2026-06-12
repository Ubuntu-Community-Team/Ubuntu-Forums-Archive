---
title: "Ubuntu has gone 'missing'"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by mikeody on 2009-11-26
I have been running Vista for a while with two hard drives - one for Vista and the other as storage for archived files etc. I cleaned out the archive hard drive, formatted it all ready for installing and dual booting Karmic.
During install I selected the second hard drive and asked Karmic to use the whole of the drive.The installation appeared to go exactly as expected but on start up I dont see the GRUB menu and it boots straight into Vista. 
I of course cant see the second hard drive from Vista.
Can anyone tell me whats happened and how I can get the GRUB menu ?
Thanks.

---

### Post by darkod on 2009-11-26
Your vista drive is still the first choice hdd in BIOS for boot. So it is just going into vista as usual.

You need to set the other drive as first choice hdd. Be careful, there is two types of settings. The first type is general what devices should be searched for boot sector, for example, 1st cd-rom, 2nd hdd, etc. You don't need to make hdd 1st choice.
But there is additional setting, just for situations like this when you have multiple hdds, in what sequence the hdds to be searched for boot sector. You need this sequence to be 1st ubuntu drive, 2nd vista drive.

Try changing it in BIOS but I think the boot menu might be already wrong right now. You were supposed to change the order of drive BEFORE installing ubuntu.

What you can do is:
1. Change the drive order in BIOS and see if grub shows up and whether you can boot both ubuntu and vista from grub.
2. If that doesn't work, leave the drive setting in BIOS 1st ubuntu, 2nd vista, and try reinstalling grub. You can find info here, item number 12:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
3. If it still doesn't work, reinstall ubuntu again. Don't forget, your ubuntu drive HAS TO BE first choice in BIOS, and check whether ubuntu will be installed on that drive (should be by default).

---

### Post by mikeody on 2009-11-26
Thanks for that.
Have changed boot order and so far all looks good.

---

### Post by atomizer on 2009-11-26
What you should have done while installing:

on the last install page (6 or 7?) there is a summary with a "advanced" button. Press the button and choose hd(0,0) or sda (don't know how it is called by head) for installing grub.
It will overwrite the mbr on the first hd with grub.

---

