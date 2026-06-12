---
title: "Installing in Parallels Virtual Machine - Unable to find a medium ..."
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by rjcarlson49 on 2011-05-03
I have a 4 core Sandy Bridge Win7-64 system running Parallels Desktop 4. I created a new VM with a CDROM connected to the 11.04 ISO. It perks for a little while showing some Ubuntu stuff then I get the console message "(initramfs) Unable to find a medium containing a live file system".

I don't get this. It is obviously booting from the CDROM. I'm guessing it does not like the unformatted disk. Why doesn't it offer to format the disk of start the installation prcess? Is it something else?

-Bob

---

### Post by rjcarlson49 on 2011-05-04
Not a big surprise. It turned out to be my fault. The software certainly could have produced a better error message though. 

When I download the ISO, I got the 64-bit version since I have a 64 bit capable machine. However, when I looked more closely at the ISO file name, 64-bit means 64-bit AMD! This should be made more obvious. Wouldn't it be kind of obvious for AMD code to the processor it is running on and tell the user if it's wrong?

-Bob

---

### Post by dikallison on 2012-01-11
AMD-64 is the name for all 64 bit installs - Intel and AMD. Confusing or what!

---

