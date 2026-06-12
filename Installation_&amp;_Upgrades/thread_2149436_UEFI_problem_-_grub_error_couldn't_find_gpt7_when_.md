---
title: "UEFI problem - grub error couldn't find gpt7 when I try to boot to windows 8 USB"
date: 2013-05-28
forum: Installation &amp; Upgrades
---

### Post by YummyBrains on 2013-05-28
[SOLVED]
I have trid to fix this for the past two days but I haven't found a solution to my singular problem. The problem of my computer giving a grub/uefi error when I insert a windows 8 installer USB. (tested already)

I had a dual boot system workin well.  Something happened to my windows 8 side and I decided to set back to factory preset.   It started giving the grub error "Can't find gpt 7".  I found that my windows 8 USB was causing problems but my ubuntu usb worked fine. I tried a number of online "fixes" for grub errors, but none worked.  I then used a live USB and gparted to reformat the drive.  I put in a new install of ubuntu 12.10 and hoped it would rewrite my hda1 to fix my problem.(standard install)  It didn't.  I then used boot-repair in various configurations but the same problem persisted. 

Here is the info from the last boot-repair.  [http://paste.ubuntu.com/5711642/](http://paste.ubuntu.com/5711642/)

Any and all help would be appreciated.  I need both os's on my system for work. (I would rather not do a windows vm)

Thanks.

---

### Post by YummyBrains on 2013-06-04
I finally got it!

 

After much poking around the  internet, I was finally able to identify my problem.  My bootx64.efi in  the EFI/Boot folder wasn't working.  I found this out by putting UEFI  shell on another usb and using that to test my *.uefi files.   Thankfully, I had a backup of my EFI folder from my initial Ubuntu  install.  This had a backup made my ubuntu. (bkpbootx64.uefi) I ran the  backup and the USB worked!  

 

On another forum someone  (Agent268) said this, which may help.  I'm guessing you need to have a  windows pe DVD/USB to make this work though. 

"You should be able to use DISM to manually reimage this bad boy using the WIM or SWMs on that USB recovery flash drive."

 

Hope my research helps someone out there.  Cheers to everyone who looked.

---

