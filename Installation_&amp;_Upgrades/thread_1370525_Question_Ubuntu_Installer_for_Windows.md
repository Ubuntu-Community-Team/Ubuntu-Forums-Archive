---
title: "Question: Ubuntu Installer for Windows?"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by LadySapphira on 2010-01-02
What is the difference between the Ubuntu Installer for windows and the Ubuntu CD image?

If I use the ubuntu installer for windows, does it have the capability to partition my drive, will it enable to share files with windows etc or is it just a way not to have to burn a CD.  Just curious, the exact details of the installation files were not made clear on the website.


Note: Windows Version: XP, 32bit, SP3.  I have not partitioned anything yet.

Thanks everyone.

---

### Post by Mark Phelps on 2010-01-02
> **LadySapphira said:**
> What is the difference between the Ubuntu Installer for windows and the Ubuntu CD image?

If I use the ubuntu installer for windows, does it have the capability to partition my drive, will it enable to share files with windows etc or is it just a way not to have to burn a CD...

The Ubuntu Installer for Windows (known as Wubi) allows you to install Ubuntu "inside" and MS Windows-formatted partition, which are nowadays NTFS partitions, instead of having to shrink the MS Windows partition to make space for Ubuntu, and then having to format Linux-compatible partitions.

The end result is functionally nearly identical to a separate partition installation, with the exception that if the MS Windows filesystem gets corrupted, since you use the MS Windows loader to boot into Ubuntu, you won't be able to boot Ubuntu.

Also, if the NTFS filesystem gets corrupted, you then will not be able to boot into Ubuntu.

And, no, it does not install any MS Windows-special stuff.

But, since it does install packages that can read and write NTFS partitions, you will be able to easily share your MS Windows partitions.

---

### Post by LadySapphira on 2010-01-02
Thank you very much, this explains it perfectly :KS

---

