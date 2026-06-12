---
title: "Newbie questions about bootable CD"
date: 2007-02-28
forum: Installation &amp; Upgrades
---

### Post by Doughy on 2007-02-28
I have a few questions about running ubuntu from a CD, but have virtually no experience with Ubuntu or linux in general.

1) To try Ubuntu, I just need to write the 700MB file to a CD, then boot from that CD, correct?

2) If I try ubuntu from the CD, can I install 3rd party stuff?

3) Will my file directories be available in ubuntu?  For example, can I try out the photo organizing stuff with the files that are already on my hard drive?

Thanks.

---

### Post by mac.ryan on 2007-02-28
> **Doughy said:**
> 1) To try Ubuntu, I just need to write the 700MB file to a CD, then boot from that CD, correct?

More or less... the file is a "CD image" so you have to tell your software to burn a "CD image" and not a file. If you don't have a burning suite that can do the job, there is the link to a free windows one from ubuntu's download page.

The reason for which copying the file is not enough is that you want your CD to be bootable (hence the CD image, that contains info for booting the CD).

> 2) If I try ubuntu from the CD, can I install 3rd party stuff?I don't know for sure, but I think you can't do that because even if you would write the files on your HD you couldn't change the config files on the CD... I suppose the best option if you want to "play around" would be to install ubuntu on a usbdrive or external HD, provided that your bios allows you to boot from USB.

> 3) Will my file directories be available in ubuntu?  For example, can I try out the photo organizing stuff with the files that are already on my hard drive?Yes, you can in read mode only (assuming you have your windows partition formatted in NTFS). With an installed version of ubuntu, though, you could install a beta utility that grants writing permissions too.

If you have your data on a FAT32 partition, no problem: both read and write are possible.

Hope this helps.

---

### Post by celticbhoy on 2007-02-28
1. burn the ISO image to cd and then just boot from it (assuming that you have enabled cr-rom as first boot device in bios)

2. Not sure

3. You should be able to access your drives to use your files, but you would be better not try writing to them if they are formatted in NTFS

---

