---
title: "Install linux 7.04 with Partition Magic v8 partitions"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by DonE on 2007-05-25
I am planning to install Ubuntu Linux Ver 7.04 from a purchased CD. I have Partition Magic 8 plus Boot Magic. I am planning to keep my Windows partition and use Boot Magic to select operating the system at startup. Partition Magic provides a feature to set up the Linux partitions in advance of the installation of Linux; it then recommends inserting the Linux CD and booting with it afterward to start the linux install. 

If I create the linux partitions in this way, how to I handle the partitioning step included in the Linux 7.04 installation? Is there a provision in the linux software that would recognize the partitions already set up for the Installation? Does the "Manual" selection in the partition set up window allow me to select the linux partitions set up in advance? Would I just skip the partioning and proceed to the next step in the install? Would the install software permit that and still install the linux program in the correct partitions? 

I just wanted to mention that I have used various versions of Partition Magic over the years and always had a successful result. Creating linux partions would be a new use of PM but I expect it to function in the same way as before. 

Any anwers will greatly appreciated. 

DonE

---

### Post by merlinus on 2007-05-25
When you get to the Ubuntu live cd partitioning screen, you should see those you have already created.  If you click on them one at a time and select edit, there should be a dropdown menu where you choose the mountpoint.

At minimum you need / and /swap.

Good luck!

-merlin

---

### Post by DonE on 2007-05-25
Thanks very much. I will see how it goes.

Don E

---

