---
title: "Update problems"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by kai333 on 2010-03-05
Hello I have been using 9.10 for some time now and last night when I ran update manager it threw a bunch of errors and asked me to reboot. I guess I should have written the errors down as after it rebooted I got "GRUB0: done" and it hung there with no prompt.

So I think that is okay I just backed up with DD to a external usb drive a few days ago and I can use that to boot from (as it will still point to the install on internal HD) and see if grub got hosed by the update. Everything booted fine I unplugged the usb drive and am posting this on my 9.10 install on the internal drive.

I think grub got hosed because I have grub installed on the 9.10 partition instead of MBR (I have a multiboot system with a few os's on it and if one os goes down I just move boot flag) so I think I have fixed grub with  "sudo grub-install --recheck --root-directory= /dev/sda1" and that went fine.

Here is my problem though when I start gparted it is telling me my sda (internal HD) is unallocated and has no partitions.
I know this is not correct as I am using the 9.10 install on it to post this and ubuntu can see and read data of the other partitions right now and yes my external usb drive is unplugged.

I am a little leary to reboot at this point anybody have a idea on what to do next?  Thanx Kai

---

