---
title: "Windows 7 always wants to run a disk check after dualbooting Ubuntu 12.04?"
date: 2012-06-17
forum: Installation &amp; Upgrades
---

### Post by BenAdamson on 2012-06-17
Hi, I recently installed Ubuntu 12.04 using all of the default options for dualbooting. Strangely, now Windows 7 wants to run a disk check every time I boot up with 7. This has me a tiny bit worried.

By the way, for some reason in the bootloader's OS selection menu, windows 7 is listed twice, both seem to work - what's up with that?

My hard drive partitions as seen by Win7:

[IMG]http://img1.uploadscreenshot.com/images/orig/6/16723105878-orig.jpg[/IMG]

Any idea on why the dualbooting has made Win7 angry, and why it is listed twice?

Thanks,
Ben

---

### Post by kc1di on 2012-06-17
Hi Ben,

My first guess is their was something wrong with windows 7 MBR to begin with. the reason you have two listing for window is most likely there are two partitions with window installed on them.

But with that being said here are somethings to try.
1. download and run boot repair from here:
[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

2. if that does not work then I would reinstall the windows boot in mbr. follow these instructions:

[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html]("http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html")

Then follow the instructions here to re-install Grub2 :

[http://www.noobslab.com/2011/10/install-grub2-from-live-cdusb-after.html]("http://www.noobslab.com/2011/10/install-grub2-from-live-cdusb-after.html")
one of those two methods should fix it for you.
Good luck

---

### Post by BenAdamson on 2012-06-17
Thanks for the great reply kc1di, before I do anything I thought I'd let people know that my GRUB looks like this: [https://www.dropbox.com/s/tops5w9adew8x3p/GRUB.jpg ]("https://www.dropbox.com/s/tops5w9adew8x3p/GRUB.jpg")

(I don't think Dropbox likes hotlinking)[IMG]https://www.dropbox.com/s/tops5w9adew8x3p/GRUB.jpg[/IMG]

---

### Post by BenAdamson on 2012-06-17
Ok, option number 1 did not work for me, it said that it was a success but when I shut down, this weird error popped up: [https://www.dropbox.com/s/w1rlqdm49f70ssv/DSC_0097.jpg](https://www.dropbox.com/s/w1rlqdm49f70ssv/DSC_0097.jpg) - not really sure what happened there.

Boot-repair's log - [http://paste.ubuntu.com/1045569/](http://paste.ubuntu.com/1045569/)

Nothing changed, there are still 2 Win7 options and the Win7 chkdsk still happens every Win7 boot. On to option 2!
[]("https://www.dropbox.com/s/w1rlqdm49f70ssv/DSC_0097.jpg")

---

### Post by wilee-nilee on 2012-06-17
Not unusual to see both windows partitions showing in grub. Sda1 is the boot, and sda2 has all of the full boot files.

From a quick look at google the general consensus I see is a dirty disc, which includes stopping that chkdsk so you can run a chkdsk of a  different type to clean it up.
[https://www.google.com/search?hl=en&output=search&sclient=psy-ab&q=wimdows+7+runs+dskchk+every+reboot&btnG=&gbv=1&sei=tePdT6ScB8Kf6AGe_JSlCw](https://www.google.com/search?hl=en&output=search&sclient=psy-ab&q=wimdows+7+runs+dskchk+every+reboot&btnG=&gbv=1&sei=tePdT6ScB8Kf6AGe_JSlCw)

---

