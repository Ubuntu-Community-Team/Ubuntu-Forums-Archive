---
title: "Installing Ubuntu 7.10 with linux RAID"
date: 2007-11-11
forum: Installation &amp; Upgrades
---

### Post by Micke Witt on 2007-11-11
Hi!
I'm trying to set up a new installation on a machine that will act as file server/NAS. The machine is kitted with 4 x 250 GB drives that I would like to set up in Ubuntus own RAID 5 config.
I tried the normal live CD, but get no options to set up RAID during the installation. I then went for the alternative installation CD which according to the description should have options for LVM and RAID set-up, but there are no RAID option given during the installation, only LVM?

Can anyone help me out with a comprehensive description on how to set up Ubuntu 7.10 with built-in RAID 5?

Best regards
/Micke

---

### Post by ViRMiN on 2007-11-11
I've got it set-up and running on two SATA2 disks in RAID-0 config... have a read of this; helped me get it going!

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by Micke Witt on 2007-11-11
Thanks, but I dont use fakeRAID as the link describes, what I want to do is set up Ubuntu softRAID. There is a comment on this in the beginning of the article, but no explanation od refference to how this is done.

/Micke

---

