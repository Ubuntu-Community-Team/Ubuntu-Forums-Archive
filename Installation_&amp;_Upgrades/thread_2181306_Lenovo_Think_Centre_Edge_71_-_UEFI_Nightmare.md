---
title: "Lenovo Think Centre Edge 71 - UEFI Nightmare"
date: 2013-10-17
forum: Installation &amp; Upgrades
---

### Post by kc3WXWJ on 2013-10-17
Hi,

I've been using Ubuntu for around a year now and have used less and less Windows during that period. I've been running a dual-boot system (Win7 and Ubuntu 12.04) for a while and decided to upgrade to 13.04 and remove Windows in full. However, this just has not worked out for me as the machine refuses to boot Linux and Windows is now gone.

I've spent the past two days trying to correct this issue following ever recommended solution in these forums and external forums. I've also opted to reach out to the community on Google Plus and whilst your all helpful it has not sorted my problem.

Any help will be much appreciated.

I've pasted the URL as requested below: [http://paste.ubuntu.com/6251098/](http://paste.ubuntu.com/6251098/)

---

### Post by |{urse on 2013-10-17
I've ran into this, have you set the boot mode from UEFI to Legacy in the bios?

---

### Post by kc3WXWJ on 2013-10-17
There are no options to change this in the bios - I'm considering updating my bios to see if these options appear but I'm reluctant to go down that route unless entirely neccessary. I can easily kill a machine playing with a bios.

---

### Post by oldfred on 2013-10-17
You have a UEFI install. And it looks normal.
Do you see a ubuntu entry in the boot choices in UEFI/BIOS?

Since you have only one install now, you will not normally get grub menu. If a black screen issue then you may need boot parameters like nomodeset.
Normally you can hold shift key from BIOS until grub menu appears to add boot parameters, but some with UEFI have had to use escape key??

---

