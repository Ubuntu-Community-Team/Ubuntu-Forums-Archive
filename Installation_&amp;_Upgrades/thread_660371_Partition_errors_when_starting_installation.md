---
title: "Partition errors when starting installation"
date: 2008-01-06
forum: Installation &amp; Upgrades
---

### Post by lamarcheb on 2008-01-06
I am unable to install the OS. Xubuntu 7.10. When I begin the installation, the partitioning software returns an error. I selected to use the entire disk. What can I do? 

This machine had Fedora 7 installed. I installed xubuntu/ubuntu/kubuntu on several machines, and this is the first time I get this error. :confused:

---

### Post by Bllasae on 2008-01-06
> **lamarcheb said:**
> I am unable to install the OS. Xubuntu 7.04. When I begin the installation, the partitioning software returns an error. I selected to use the entire disk. What can I do? 

This machine had Fedora 7 installed. I installed xubuntu/ubuntu/kubuntu on several machines, and this is the first time I get this error. :confused:
Yeah, I got a similar error, if I know what kind of error you're getting. What exactly is the error?

---

### Post by idiotonuni on 2008-01-06
I used o get that error.  My problem is that when i was going through install I had a flash drive plugged in, I unplugged it and it went smoothly.  Try that and see if it works.

---

### Post by lamarcheb on 2008-01-08
It stated that "the creation of the ext3 partition had failed" then would open the manual partitioner - which was setup with an ext3 and swap partition. I tried all three options (Guided, Guided using largest contiguous free space, manual) and got the same error message.

I then experimented with Gparted but got errors when trying to erase the existing partition. It stated it was mounted, even though it was not mounted when I made the selections. I understand that perhaps the Live version was swapping virtual memory to that disk I was trying to format.

Finally, after completely destroying the partitions I tried Ubuntu 7.10. While its the same software that walks the user through the install, it gave me some warning messages but worked. Later I  installed xFce4 from apt-get.

But now openoffice.org does not work in xFce and I need to make another post!

---

