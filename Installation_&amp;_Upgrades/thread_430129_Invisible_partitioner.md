---
title: "Invisible partitioner"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by Donald F. Robertson on 2007-05-01
I'm trying to install Ubuntu 7.4.  Everything goes fine until I get to the disk partioner.  I'm given one option, to manually partition.  When I say okay, I go to the next screen, which is blank.  I can see the title, and the outline, but what I presume to be a graphical partitioning display is invisible.

I get this behavior in both the full and minimal graphic install.  There does not appear to be a text based install.

Suggestions?

Thanks!

-- Donald

---

### Post by cypherzero on 2007-05-02
Same problem here with kubuntu feisty, the error is in that the partition manager crashes. If you run the partition manager alone the window will close without warning, in the installer this means you get an empty window. Running the manager from a terminal will allow you to see that an error did occur, not that this is in any way helpful!

You can use the command line partitioner 'parted' but this still wont allow you to get past the installer.
I think a major oversight has been made with regards to feisty in general here, we'll all probably have to wait for the next upgrade.

---

### Post by psusi on 2007-05-02
What does sudo fdisk -l show?

If you want the text based installer, you need to get the alternate cd.

---

### Post by Donald F. Robertson on 2007-05-04
It returned nothing accept the prompt ">" (without the usual system name).  However, I'm running this from the CD, as it is not installed on the hard drive.

What's the "alternate CD"?  Is that the one you can order from the Ubuntu home page, instead of doing a download?

Thanks!

-- Donald

---

### Post by Sef on 2007-05-04
> What's the "alternate CD"? Is that the one you can order from the Ubuntu home page, instead of doing a download?

No, you get the desktop cd from ship-it.   The alternate cd is a text-based cd.  It is very easy to install.  To download it, at the bottom of the download page, it says "Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer."

---

### Post by psusi on 2007-05-06
If you got a > prompt then you typed something wrong, like an open quote with no end quote.

---

### Post by Donald F. Robertson on 2007-05-08
Thanks!  However, I downloaded and burned the "alternate" CD, but it won't boot.  It goes into a recursive boot and re-boot, booting the machine over and over without giving me any options to install.

Thanks!

-- Donald

---

