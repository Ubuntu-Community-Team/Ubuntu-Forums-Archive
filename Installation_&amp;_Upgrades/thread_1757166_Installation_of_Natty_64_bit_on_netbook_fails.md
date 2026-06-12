---
title: "Installation of Natty 64 bit on netbook fails"
date: 2011-05-13
forum: Installation &amp; Upgrades
---

### Post by db6edr on 2011-05-13
Hi folks,

I have an awkward problem with installing Natty on my netbook (Samsung NC10 Plus). As the CPU is 64 bit , downloaded the 64bit alternate installation cd and dumped it on a USB stick using unetbootin.

The installation fails with defective packages - several xorg-dependencies are marked as "can't be installed". Running the installer from the same ISO file in a virtual machine works fine.

Running the installer from the 64bit Natty live CD on the netbook also works fine. Using this is not an option for me as I want to have the entire harddisk encrypted.

Any ideas? Need more info?

Regards,

Dirk - DB6EDR

---

### Post by wyliecoyoteuk on 2011-05-13
Actually, the Atom N270 CPU in  the Samsung only supports the 32 bit instruction set according to Intel, not all Atom processors are 64 bit.

[http://ark.intel.com/Product.aspx?id=36331](http://ark.intel.com/Product.aspx?id=36331)

---

### Post by db6edr on 2011-05-13
Hmm, the NC10 Plus is equipped with the Atom N450: [http://ark.intel.com/Product.aspx?id=42503&processor=N450&spec-codes=SLBMG](http://ark.intel.com/Product.aspx?id=42503&processor=N450&spec-codes=SLBMG) - which has 64bit instruction set.

I found this description [https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto](https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto) and have installed Natty following it. Well, the installation worked fine. On boot, I'm asked for the LUKS passphrase. cryptsetup tells me pvcrypt has been set up successfully.

After that, booting fails with
/scripts/local-top/cryptroot: can't open /dev/mapper/vg: no such file

Sure, there's none. It's /dev/mapper/vg-root ... but the vg entry is added to cryptroot upon update-initramfs
How to fix that?

---

### Post by db6edr on 2011-05-13
Sorry for the quick reply to myself.

I found the solution. The wiki entry currently has an error - at least regarding Natty.
After removing lvm=vg from /etc/crypttab and updating initramfs, Natty boots fine from a fully encrypted LVM.

Great!

---

### Post by wyliecoyoteuk on 2011-05-14
Sorry, must be a newer version of the NC10 plus, or I looked at an incorrect spec sheet.The specs I looked at on the first site I found  said it had an N270.

---

### Post by db6edr on 2011-05-14
Seems so ... thanks anyway and have a happy weekend!

---

