---
title: "Replace Ubuntu 10.10 with Xubuntu 14.04"
date: 2014-06-12
forum: Installation &amp; Upgrades
---

### Post by AZinOH on 2014-06-12
I currently have a functioning dual-boot of WIn XP and Ubuntu 10.10. What I want to accomplish is a seamless replacement of 10.10 with Xubuntu 14.04 and preserve the dual-boot. Question...do I need to delete the existing Ubuntu partition before attempting the install, or can I get the install to overwrite that partition? Note: there is nothing on the existing Ubuntu partition that I want to save. I want to delete or overwrite everything that is there.

Thanks for any assistance.

---

### Post by sudodus on 2014-06-12
I think that you should try Xubuntu and Lubuntu 14.04 LTS as well as Xubuntu 12.04 LTS ***live without installing before deciding*** what to install. It depends a lot on the hardware, so if you tell us about it, we can give better advice.

- Computer brand name and model
- CPU
- RAM size
- graphics chip/card
- wifi chip/card

---

### Post by AZinOH on 2014-06-12
Processor a		 		Main Circuit Board b
2.80 gigahertz Intel Pentium D
16 kilobyte primary memory cache
1024 kilobyte secondary memory cache		 		Board: Dell Inc. 0FJ030
Serial Number: ..CN7082166JG0FH.
Bus Clock: 800 megahertz
BIOS: Dell Inc. A05 05/30/2006

The hardware is a 2007 Dell XPS400 w 2GB memory. I've already booted the Xubuntu 14.04 live DVD and am satisfied with the appearance/function of Xubuntu. There is no wifi and it has a nVidia GeForce  7300 LE video card. 

Thanks for the reply.

---

### Post by sudodus on 2014-06-12
> **AZinOH said:**
> I currently have a functioning dual-boot of WIn XP and Ubuntu 10.10. What I want to accomplish is a seamless replacement of 10.10 with Xubuntu 14.04 and preserve the dual-boot. Question...do I need to delete the existing Ubuntu partition before attempting the install, or can I get the install to overwrite that partition? Note: there is nothing on the existing Ubuntu partition that I want to save. I want to delete or overwrite everything that is there.

Thanks for any assistance.

I suggest that you format the existing Ubuntu partition before attempting the install. It can be done with ***gparted*** when booted from the Xubuntu install DVD/drive. It can also be done by the installer. In any case, I strongly suggest that you select '***Something else***' at the partitioning window of the installer, and select carefully the correct partition and leave Windows alone. Make sure to install the bootloader into the head of the internal drive (not to a partition, so **/dev/sda**, not for example /dev/sda5 for the first drive 'sda').

> **AZinOH said:**
> Processor a                 Main Circuit Board b
2.80 gigahertz Intel Pentium D
16 kilobyte primary memory cache
1024 kilobyte secondary memory cache                 Board: Dell Inc. 0FJ030
Serial Number: ..CN7082166JG0FH.
Bus Clock: 800 megahertz
BIOS: Dell Inc. A05 05/30/2006

The hardware is a 2007 Dell XPS400 w 2GB memory. I've already booted the Xubuntu 14.04 live DVD and am satisfied with the appearance/function of Xubuntu. There is no wifi and it has a nVidia GeForce  7300 LE video card. 

Thanks for the reply.

This computer seems good for running Xubuntu. If it runs well with the built in free (nouveau) driver, fine! Otherwise you can try a proprietary nvidia driver.

-o-

Finally, Win XP has passed end of life, and there will be no more security updates. I suggest that you never run it when connected to the internet, and I suggest that you plan for replacing it (look for alternatives for the application programs that you 'have to run in XP').

---

### Post by Bucky Ball on 2014-06-12
If Xubuntu 14.04 LTS is running fine from the DVD go ahead and install it! When you get to the partitioning section of the install, you will see the option 'Something Else'. Choose that to manual partition. You should see your / partition in the list of partition there. It will probably be EXT3. Delete that and leave free space. 

Now, create a partition using that free space, choose the default mountpoint '/' (you'll find it in the drop down list) and the filesystem EXT4 (also in a list). I generally then check all the other partitions to make sure they are set to 'Do not use', or whatever it is, and that's pretty much it. The install will know to install to the partition '/' and leave the rest alone. 

As always, backup valuable data before proceeding with this.

* Oops, ninja-ed by sudodus! Well, you have two ways of going about it now. If you format the partition from a LiveDVD prior to the install, just choose 'Something Else' at the partitioning section of the install and then what I've outlined above still applies; choose the EXT4 partition you created before the install for the '/' partition. ;)

Thing is, if you create an EXT4 partition prior to the install, you still need to choose 'Something Else' where you could do it all. I generally find leaving free space makes it clear (at least to my usually muddled head) where to put the OS and I don't get the pre-formatted partition confused with any of the previously existing EXT* partitions! Whatever suits, but I'd have a good look at the setup using Gparted and take notes prior to install (write down sd** particularly) so you are totally sure of what's what when you get to 'Something Else'. Good luck ...

---

