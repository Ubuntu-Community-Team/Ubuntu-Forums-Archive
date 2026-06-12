---
title: "Need IDE help/hda1 and hdb1"
date: 2006-10-15
forum: Installation &amp; Upgrades
---

### Post by randell6564 on 2006-10-15
Hi!
I'm having some trouble getting my HD's to work properly!
I have two HD's, one master (hda1), that houses Ubuntu and one slave (hdb1) that is formatted as ext3 that I use just for storage purposes.

I initially had hdb1 plugged in when I installed Ubuntu to hda1, but it was not formatted yet.  After I installed Ubuntu and retrieved all the updates, I then installed 'qtparted' and commenced to formatting hdb1 and adding it to my /etc/fstab. All of this went flawlessly. I even copied some music over to hdb1!
But THEN I shutdown, and upon rebooting, I was not able to boot, getting a message like.,> Boot from CD
                     Boot from CD...nothing happened after this!
So, I shutdown again, unplugged hdb1, rebooted and was confronted with the command-line. I then reinstalled GRUB from there and was then successful in booting into Ubuntu.

Any ideas on how I can plug my slave drive (hdb1) back into my box and still be able to get to my desktop?
Thanks!

---

### Post by Dr. Nick on 2006-10-15
Thats odd, how is the boot order in your BIOS setup? When you formatted hdb1 did you mess with any boot flags? I have never had this problem before; but I would start by checking to make sure the jumpers on both drives are correct, and that they are both seen in the bios correctly. Then I would put IDE 1 as the first boot device in the bios

---

### Post by randell6564 on 2006-10-15
> **Dr. Nick said:**
> Thats odd, how is the boot order in your BIOS setup? When you formatted hdb1 did you mess with any boot flags? I have never had this problem before; but I would start by checking to make sure the jumpers on both drives are correct, and that they are both seen in the bios correctly. Then I would put IDE 1 as the first boot device in the bios
Well, I never touched the jumpers since my first installation of Ubuntu. (everything worked fine then).  As far as the Bios, I will have to go and double-check but I'm almost certain it is set to CDROM first, then Floppy, and then IDE 1.
I did not do anything regarding "boot flags" when formatting hdb1 with qtparted.
Ill check the Bios and post the output.
Thanks!

---

