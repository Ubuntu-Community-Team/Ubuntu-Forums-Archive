---
title: "Can't install Feisty or Gutsy on ia64 - problem reading data from the CD-ROM"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by cmoore4 on 2007-11-06
I'm trying to install onto an HP zx2000 ia64 workstation.  I've tried Gutsy and Feisty.
I've also tried burning both CDs and DVDs, tried different download sources for the ISO,
and tried different burners.  In every case I get the same thing.

It makes it past booting, does the language and keyboard selection, then I get
the "There was a problem reading data from the CD-ROM" error at the
"Load installer components from CD" step.

I broke out to a shell and checked /var/log/syslog and I see lines like:
cdrom-retriever: warning: File /cdrom/dists/feisty/main/debian-installer/binary-ia64/Packages does not exist.

There are four of these, as it searches for Packages and Packages.gz in main and restricted.

Then I get "anna: WARNING **: bad d-i Packages file"

The CDROM is mounted on /cdrom, and I'm able to poke around on it and examine files.  There is a /cdrom/dists/feisty/main, but no debian-installer under that.

If anyone has any suggestions on how to proceed I'd appreciate them.

Thanks,

Chris

---

### Post by LaRoza on 2007-11-06
Which ISO is it? I usually use a text installer, or the alternative disk, that may eliminate the problems.

---

### Post by Pumalite on 2007-11-06
Did you do md5sum on the iso?
Did you burn at 4x?
Clean the lens in you burner
Try the CD's in different computers

---

### Post by mwalston on 2008-02-07
> **Pumalite said:**
> Did you do md5sum on the iso?
Did you burn at 4x?
Clean the lens in you burner
Try the CD's in different computers

I am having the exact same problem. As the OP.  I have checked MD5SUM on the ISO and it checks out.  I have run md5sum on each file in the disc after burning and they all check out.  I burned the disc at 4x on two different burners.  I've tried both gutsy and feisty.  Unfortunately I don't have another system to try it on.  Traversing the filesystem after mounting the CD doesn't give me any indication that debian-installer is on there.  I also noticed on my most recent attempt that it said that this distrubution was not meant for install off CDROM.

---

### Post by Pumalite on 2008-02-07
Download from here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
And make sure you burn the iso as image.
Follow this:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

---

### Post by mwalston on 2008-02-07
> **Pumalite said:**
> Download from here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
And make sure you burn the iso as image.
Follow this:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

A) I downloaded mine from [http://cdimage.ubuntu.com/ports/releases/gutsy/release/](http://cdimage.ubuntu.com/ports/releases/gutsy/release/), the link you gave does not have a download for IA64.
B) I know how to burn an iso.
C) I've installed ubuntu many times on many different hardware configurations and platforms.

You aren't actually helping because you are assuming that anyone who has a problem is technically inept.

---

### Post by Pumalite on 2008-02-07
Touché

---

