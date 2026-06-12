---
title: "Cant install Ubuntu"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by Ferr435 on 2008-05-15
Hi there

I cant install Ubuntu on my computer. I got a live cd from Canonical and I can boot up to the first part of installation, where I choose what to do. I choose to install it, and it goes to the loading bar. Eventually that goes away and it goes to a black screen, sometimes with a little gray bar flashing in the upper left hand corner and stays like that. I've left it alone there for hours before and nothing happened.

How do I fix this and install the operating system?

---

### Post by ugm6hr on 2008-05-15
What hardware are you using (i.e. specs of computer)?

What happens when you check the disc integrity from that first menu?

---

### Post by kippa on 2008-05-15
> **ugm6hr said:**
> What hardware are you using (i.e. specs of computer)?

What happens when you check the disc integrity from that first menu?

Hey i have had the same problem. Problem arose when it was in the partitioning part of instillation. Came up with an error. Tried the instillation again, still did not work. Decided to restart the system, but it doesn’t want to boot from the CD, and doesn’t load with vista. I am left with a black screen with a flashing grey bar. 

I’ve got a  Acer Aspire 5920. 

Any help would be appreciated

---

### Post by MaindotC on 2008-05-20
Bump - do either of you guys have any progress in the past few days?  One place I'd like you all to start is to make sure you have the latest BIOS on your motherboard.

---

### Post by wpshooter on 2008-05-20
Have you tried installing in Safe Graphics mode ?

---

### Post by ielemi on 2008-05-21
Im haveing the same issue I get the what I know refer to as the blinking cursor of death everytime I try booting the live cd I have tried about five different flavors and they all get to the cursor and do nothing. Im absolutely lost and have no idea where to begin. 
A little help please
*sys specs*
Amd 64 Dual core 4000+ 2.1 Ghz
1.88GB 
300 Hard drive
ATI Radeon X1200 Series
Realtek RTL8168/8111 Family PCI-E Gigabit Ethernet NIC (NDIS 6.0)
 What else do you need to know?

---

### Post by ugm6hr on 2008-05-21
> **kippa said:**
> Hey i have had the same problem. Problem arose when it was in the partitioning part of instillation. Came up with an error. Tried the instillation again, still did not work. Decided to restart the system, but it doesn’t want to boot from the CD, and doesn’t load with vista. I am left with a black screen with a flashing grey bar. 

I’ve got a  Acer Aspire 5920. 

Any help would be appreciated

Unfortunately, it sounds like you have corrupted your HD in the repartitioning process.

Did you shrink the Vista partition from the Ubuntu LiveCD?  If so - that may be the problem - GParted is not 100% reliable with Vista partitions yet.

Sorry.  I don't think the documentation makes that clear....

Fopr others - please ensure you shrink Vista from within Vista (it has its own Partition Manager) **before** attempting to install Ubuntu.

---

### Post by ugm6hr on 2008-05-21
> **ielemi said:**
> Im haveing the same issue I get the what I know refer to as the blinking cursor of death everytime I try booting the live cd I have tried about five different flavors and they all get to the cursor and do nothing. Im absolutely lost and have no idea where to begin. 
A little help please
*sys specs*
Amd 64 Dual core 4000+ 2.1 Ghz
1.88GB 
300 Hard drive
ATI Radeon X1200 Series
Realtek RTL8168/8111 Family PCI-E Gigabit Ethernet NIC (NDIS 6.0)
 What else do you need to know?

How far does the CD boot to?

Do you see the initial menu to choose install / check CD etc?

If not - I suspect you will not get very far with Ubuntu.

---

### Post by ielemi on 2008-05-21
I get to the intial screen and the even get the kernel load bar
I recently tried safe mode taking out quiet mode and turning off splash that at least gave me an error 
iomem ... cannot release
something to that effect
I think it might have something to do with my MBR but I don't know how to fix that issue.
I at one point had a 10GB partition and a really broken version of fedora I have done a complete system wipe and reinstall I also gparted my partiton back to windows. So I only have the one partition and a recovery partition. Windows works fine but any live cd I use just errors out.

---

### Post by ugm6hr on 2008-05-21
> **ielemi said:**
> I get to the intial screen and the even get the kernel load bar
I recently tried safe mode taking out quiet mode and turning off splash that at least gave me an error 
iomem ... cannot release
something to that effect
I think it might have something to do with my MBR but I don't know how to fix that issue.
I at one point had a 10GB partition and a really broken version of fedora I have done a complete system wipe and reinstall I also gparted my partiton back to windows. So I only have the one partition and a recovery partition. Windows works fine but any live cd I use just errors out.

Run a check of CD for integrity first on booting.

---

### Post by ielemi on 2008-05-21
Ok I don't know what happened I ran the Cd utl and found no problems then I let the mem test run for a little over an hour and then I tried the off chance that something might work and here I am surfing the forums on the live cd
I guess Im going to try an install now and see where that gets me. I know I will have questions about getting the visual effects working

---

### Post by MaindotC on 2008-05-21
Justy fyi - installing has nothing to do with the MBR.  Once it installs, THEN the MBR can cause problems - but hopefully that won't happen.

---

### Post by ielemi on 2008-05-21
Well everything is working now that I have the updates installed 
The Next project is going to be a pendrive version woo hoo

---

