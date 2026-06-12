---
title: "Grub menu now missing"
date: 2015-09-26
forum: Installation &amp; Upgrades
---

### Post by Dáire Fagan on 2015-09-26
Hi


My laptop was not working for some  time as there was an issue with the DC IN port. A local repair shop  repaired this but now when I boot, instead of being presented with the  Grub menu and options for Ubuntu and Windows 8.1, instead it tries to  boot straight into Windows, which attempts automatic repair but fails.


I can worry about Windows later, what I really need is to access Ubuntu! :)

Please see the startup repair log I created using Ubuntu Live on a flash drive:

[http://paste.ubuntu.com/12581328/](http://paste.ubuntu.com/12581328/)

FTR I tried booting after running startup repair but nothing appears to have changed.


Can you please advise?

[IMG]https://ssl.gstatic.com/ui/v1/icons/mail/images/cleardot.gif[/IMG]

---

### Post by Dáire Fagan on 2015-09-26
By the way, Ubuntu LUKS encrypted inside a LVM.

---

### Post by oldfred on 2015-09-26
I do not know LVM nor encryption.

But you have standard UEFI boot. Can you go into UEFI or one time boot key often f10 or f12 and choose ubuntu entry?
Can you boot Windows directly and use f8 to get into its own repair console?

Did you unencrypt your install when running Boot-Repair? That is needed for it to work.

If you are primarily an Ubuntu user, I have seen users eliminate the Intel SRT and just use the 24GB SSD as / (root) with rest of data on rotating drive. Not sure if with LVM that would work.

       fsck on encrypted LUKS 
[http://serverfault.com/questions/375090/using-fsck-to-check-and-repair-luks-encrypted-disk](http://serverfault.com/questions/375090/using-fsck-to-check-and-repair-luks-encrypted-disk)

---

