---
title: "installation Question"
date: 2012-07-07
forum: Installation &amp; Upgrades
---

### Post by MikeyPooh on 2012-07-07
here is what i am trying to do, I have a 750GB HDD, I Have a unused 80GB Partition, the rest of the drive has an ntfs partition with all my media files on it, How do i partition the 80 GB partition to install ubuntu on that partition while leaving the ntfs partition intact?

what mount points do i need and what file system


Thanks

Mike

---

### Post by darkod on 2012-07-07
Ubuntu can't install on ntfs so you need to delete that 80GB partition and leave the space as unallocated.

Ubuntu usually installs with only two partitions:
-root (mount point /), the main system partitions, filesystem ext4
-swap (no mount point), filesystem swap area

Except those, it's good practice to have separate /home partition, also ext4. This can allow you in future to make a clean install formatting root while keeping /home unformatted with all your data there.

To install with separate /home you need to use the manual method (Something Else), and create the partitions yourself. Make all of them logical partitions.

If using the auto method it will install the standard root+swap using the 80GB unallocated space.

In case you want to do it manually with /home, the sizes should be more or less:
swap - 2GB or 1.5 x RAM if you plan to hibernate
root - 15-20GB, depending how much software you use
/home - the rest left over from the 80GB

---

### Post by MikeyPooh on 2012-07-07
ok will try that....Thanks Bro

---

