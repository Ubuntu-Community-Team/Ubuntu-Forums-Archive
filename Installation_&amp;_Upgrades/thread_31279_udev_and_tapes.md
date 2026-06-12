---
title: "udev and tapes"
date: 2005-05-02
forum: Installation &amp; Upgrades
---

### Post by freelsjd on 2005-05-02
I am new to udev.  How do I set up a link to allow my tape programs that look for 
/dev/tape ?  I used to do a ln -s /dev/st0 /dev/tape, but that will get erased on a reboot since udev defines the /dev directory.  How do I configure udev to create this link on boot ?

---

### Post by ssam on 2005-05-02
if you are in the uk, pick up a linux format, may issue , firefox on the front.

it has a tutorial on customising udev

---

### Post by freelsjd on 2005-05-02
I'm not in the UK, but I did see several UK-published linux magazines the other day here in the US at "Books-a-Million".  Is the jouirnal called "Linux format" ?

Anyone else familiar with this problem ?

---

### Post by freelsjd on 2005-05-03
Well, I did not get any help here.  Look like this forum is not that helpful.  I dug into it myself and realized that the following entries in the /etc/udev/udev.rules file and a /etc/init.d/udev restart will do it:

# for SCSI tape devices
BUS="scsi", KERNEL="st0*", NAME="tape", GROUP="tape"
BUS="scsi", KERNEL="nst0*", NAME="tape_norewind", GROUP="tape"

This may not be a general fix, but it is sufficient for my needs.

---

