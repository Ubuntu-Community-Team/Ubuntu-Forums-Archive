---
title: "Installing Ubuntu with a separate /home, marked for encryption, crashes Ubiquity"
date: 2009-01-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-01-20
Anyone else experiencing this?

Ubiquity will not crash if the /home partition is not set to be encrypted.

---

### Post by FuturePilot on 2009-01-20
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/317068]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/317068")

Known issue.

---

### Post by bash on 2009-01-20
For me the partioner on the LiveCD doesn't work at all atm. But have you reported this as a bug yet?

**Edit:** Someone was quicker and this seems to already be reported

---

### Post by Archmage on 2009-01-20
Somebody have clue when this will be fixed? It makes the testing pretty hard, if you can't test ext4+encrypted folder+64-Bit.

---

### Post by LordVeovis on 2009-01-20
Currently the only way to do encrypted install is alternate CD.  If you are worried about having multiple users and didn't want 1 key to mount the whole drive, partition the drive for different users.  This would cause problems with space if you do not know how much you want to give each user.  If space is a concern, perhaps you can do what the alternative CD does for an encrypted private directory.  That is to make a /home/.username/ folder and mount it to the /home/username/ folder.  I am not sure how they make the folder encrypted, but I think it is just using the cryptsetup.

EDIT: Yes, this is done with cryptsetup. 'man cryptsetup' and 'cryptsetup --help' has some helpful info.

---

### Post by Gourgi on 2009-01-20
> **Starks said:**
> Anyone else experiencing this?

Ubiquity will not crash if the /home partition is not set to be encrypted.

also noted in the alpha3 known issues
[http://ubuntuforums.org/showthread.php?t=1041736](http://ubuntuforums.org/showthread.php?t=1041736)

---

