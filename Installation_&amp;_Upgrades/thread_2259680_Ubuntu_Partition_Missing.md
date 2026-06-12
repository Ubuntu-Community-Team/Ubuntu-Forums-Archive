---
title: "Ubuntu Partition Missing"
date: 2015-01-06
forum: Installation &amp; Upgrades
---

### Post by jvestrand on 2015-01-06
Hi all,

I have a Dell L702x laptop which has two hard drive bays. Up until last week I had a 500 GB HDD and 240GB SSD. On the 500GB, was factory windows 7 with Dell Recovery Partition. On the 240GB I had Ubuntu 14 installed. I used Grub for the boot and all worked fine.

Last week I decided to upgrade my 500GB to 1TB and fresh install Windows 7 from disk. I wanted to install Windows to the 240SSD and get rid of Ubuntu for the moment and virtualize it later. When I went to install Windows, I was only able to see a small portion of my SSD. I am assuming this is because Ubuntu was not NTFS format. I carried on with my install to address the space issue later. 

Since I could not boot with Grub any longer to Ubuntu,  I did further research and came across GParted Live. So I created a Live USB and was into GParted. To my dismay the partition and install of Ubuntu still does not show up even on Live boot. 

I've found similar issues with people wanting to create dual boots. I am trying to do the opposite and start with a clean slate. Likely will run Ubuntu in VMware as I need it for work but not a true install. 

Any help would be appreciated.

---

### Post by yancek on 2015-01-06
If you installed windows 7 to the 240GB SSD, I expect it wrote over your Ubuntu install.  Did you see anything in the installation process asking you which partitions you wanted to use on the SSD and giving you an option.  I'ts been years since I installed windows so I don't really know what options your get, if any.

---

