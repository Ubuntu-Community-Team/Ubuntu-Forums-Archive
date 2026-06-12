---
title: "How to Install Ubuntu with Vista onboard?"
date: 2008-02-16
forum: Installation &amp; Upgrades
---

### Post by Anish_M on 2008-02-16
Hi Guys!..

I want to know how to install Ubuntu 7.10 on a hard drive which already has Vista . Need guidance for a dual boot system. I am using the alternate CD (32Bit) to install Ubuntu, but i am afraid to proceed ahead when the partitioning part comes in. Infact i dont really know how to keep Vista and ubuntu on the same hard drive.. I have 2 hard drives connected ... 1 is a 250 GB and the other is a 160 GB. Both the hard drives have 4 partitions (NTFS). I want to install Ubuntu on the D drive of the 250 GB HDD.. Ive specially kept the 60 GB free space for Ubuntu.. 
I am an absolute noob in this, please help !.. is there any step by step method on this that i can refer to ?..  :confused:

Thanks !

---

### Post by Shippou on 2008-02-16
For me there are two options:
1. Install vmware. Since it is vista, it is an easy install (as compared to the Linux version). Then run the Linux ISO file (again, the ISO file) under vmware.

2. Use a Live CD.

3. Reformat and install a Linux distro.

Personally I will prefer the third option, since I've tried Vista myself under a 512MB RAM environment.

Enjoy your vista installation (though I personally prefer Linux over Windows...)

---

### Post by AnonCat on 2008-02-16
Following this guide worked well for me:

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by Pumalite on 2008-02-16
Here is another guide:
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by dstew on 2008-02-16
Use the Disk Management tools in VIsta to shrink the Vista partition. Then install Ubuntu. Make the Ubuntu root and swap partitions out of the unallocated space you freed up when you shrunk the VIsta partition. Let grub into the MBR. It should detect VIsta and Ubuntu, and let you dual boot.

Do not try to shrink the VIsta partition using the Ubuntu installation disk partitioner. It sometimes works, but often kills the Vista partition. I don't think the Alternate Install disk will let you shrink a partition anyway.

---

### Post by Pumalite on 2008-02-16
Good point.

---

### Post by Anish_M on 2008-02-17
Hey those links are really helpful .. thanks !.. I am now having issues with connecting to the network .. and the graphics .. m using 8800GT . how do i get all the eye candy ?

---

### Post by Anish_M on 2008-02-17
Hey those links are really helpful .. thanks !.. I am now having issues with connecting to the network .. and the graphics .. m using 8800GT . how do i get all the eye candy.. ?

---

### Post by Pumalite on 2008-02-17
Are you IN?

---

### Post by Anish_M on 2008-02-17
IN ? .. u mean Inside Ubuntu or Indian ?

---

### Post by Pumalite on 2008-02-17
He, He...inside Ubuntu.

---

### Post by Anish_M on 2008-02-17
OH yes! lol .. i am inside ubuntu .. working pretty well atm.. but m having issues with connecting to internet and not able to see the eye candy for what i am guessing a driver issue ?

---

### Post by Pumalite on 2008-02-17
Post:
lshw -C network

---

### Post by Anish_M on 2008-02-18
sorry but i am new to this.. do i type this in the terminal windows or press CTRL+ALT+F2 or F3 ?

---

### Post by Pumalite on 2008-02-18
Accessories>Terminal>Copy and paste the command>
Copy and paste the output.

---

