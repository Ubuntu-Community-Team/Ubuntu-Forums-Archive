---
title: "Trying to install Ubuntu on my new Sony Vaio laptop"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by nickbourcier on 2010-02-24
I successfully before install Ubuntu on my last laptop along with windows vista and it was rather easy because ubuntu allowed me to partition the disk so simply.

However, on my vaio, my whole hard disk is partition and there is no unallocated space. It will not allow me to partition the disk and when I boot up the ubuntu live cd to install, the partitioner doesn't look the same and I'm hesitant to make any changes because I'm afraid I'm going to damage my data. I have a 500GB HDD in which I want to use just 60GB for Ubuntu and the rest for Windows 7.

I'm very confused on how to go about this. Any advise?

Also, I'm runing 64-bit Windows if that matters at all.

---

### Post by QIII on 2010-02-24
Defrag your Windows drive at least twice.  That will get your files as contiguous as Windows can make them.  Use the disk partitioning utility in Windows to shrink your Windows partition and create a new one the size you want.  Using the Windows utilities will (more or less!) ensure that the partition created will not overwrite anything.  

Install Ubuntu on the newly created partition.

---

### Post by grubdude on 2010-02-24
Other than trying the above idea.

If your windows install allocated the entire hard drive for the OS partition, the only way that you could possibly get around that is to use something like Partition Magic to resize the original partition. If you try to install Ubuntu now, you will have to format over at least part of your Windows partition and it will corrupt your OS.

Another possibility, is to install Virtualbox and run Ubuntu in a virtual machine. I do that on several of my machines and it works great...It will just take some of the unwritten portion of your hard drive and allocate that for the virtual machine without messing up your windows install.

I hope that helps....

---

### Post by Mark Phelps on 2010-02-26
Strongly support the previous suggestion to use the Win7 disk management utility to do partition shrinkage.  Don't let the Ubuntu installer do this.

Also, since every laptop is different, you should boot from a LiveCD first and confirm that all your hardware works.  Anything that does not work in LiveCD mode can range from trivial to impossible to fix after installation.

---

