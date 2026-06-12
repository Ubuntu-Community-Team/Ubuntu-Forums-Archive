---
title: "Grub Error 17"
date: 2006-11-14
forum: Installation &amp; Upgrades
---

### Post by Sarin42 on 2006-11-14
First off, to make things easier to understand, here's my HD setup:

2x 80G internal IDE drives (First drive has XP Pro SP2 installed, and each one has a single partition)
1x 80G external USB drive (just extra Windows storage)
1x 200G external USB drive (first partition is for Windows backup, then the second is my new Ubuntu boot parition, all other partitions are for Ubuntu (swapspace and whatnot))

This past weekend I installed Ubuntu on an external USB drive. I had received Grub Error 22 when I first booted it, learning that the Grub had not properly been installed on the MBR, and was not pointing to the right. I fixed this using the method described on [this]("http://ubuntuforums.org/showpost.php?p=121355&postcount=5") forum post. Everything worked fine, except that for some reason, I had to keep my other USB drive unplugged when I booted. I don't know why.

Then, since I had messed up with changing the size of the original partition on the 200G USB drive, I decided that I should redo everything that I did the last time, but make sure that I resized the Windows Backup partition to the proper size. So I re-formatted the drive (after running fixmbr on my Windows install CD and then booting into Windows) and then re-installed Linux using the Ubuntu Live CD.

Now, when I boot, I receive the Grub Error 17. I followed everything that I had done the last time, making sure to include the Grub setup (as detailed in the above link) beforehand so as not to receive Error 22. So I don't know how to get to the bootloader, or what's causing Error 17 (letalone what it really means), and I was wondering if anyone had any suggestions.

Thank you.

Also, I apologize if the post is a bit fragmented, but I tried to explain everything that I did as best as I could.

Edit: I installed Ubuntu 6.10 (fyi)

---

### Post by ciscosurfer on 2006-11-14
GRUB Error 17 = [cannot mount selected partition]("http://gnu.rtin.bz/software/grub/manual/grub.html#Troubleshooting").

Searching GRUB error on the forums here will avail many more answers.

---

### Post by Sarin42 on 2006-11-14
Yes, I did read that. But I don't know what to do about it. Perhaps Grub is pointing to the wrong partition, but I followed all the instructions on that link that I provided in my first post. As far as I know, that should work since it did the first time...

---

