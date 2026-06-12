---
title: "Windows Migration Tool for 9.10"
date: 2010-06-21
forum: Installation &amp; Upgrades
---

### Post by GaryB} on 2010-06-21
I think a little background will help people understand what I'm trying to do. I've been supporting Microsoft OS and Apps since 1992. I hold a BSEET and am one test shy of MCSE. I have my own Computer Support business helping Individuals and Small Business keep their M$ PCs running. 

I'm also sick of Microsoft. I'm tired of their manipulations, deceptions, and failure to produce Software that serves the needs me and my customers. I've been watching Open Source for 3 years hoping for an Alternative I could recommend to my customers. I'm very excited about Ubuntu 9.10. 

There is just one thing missing. I think it can be done, but I need the help of the experienced Users here. What I'd like to do is copy the existing "C:\Documents and Settings" folder to a USB Drive, Install Ubuntu using the entire disk (blow Windows away), and finally point the (excellent) Windows Migration Tool in Ubuntu to those Profiles and have it Import them just like it does in a Parallel Install. 

I found this:

```

1.) Fire up live CD 

2.) Open up a terminal

3.) sudo gedit /etc/apt/sources.list and remove all comments (#) in front of the 
repositories, and save the file.

4.) sudo apt-get ntfs-3g

5.) mkdir /mnt/win

6.) ntfsmount /dev/<disk and partition number here> /mnt/win

7.) mkdir /mnt/win/users

8.) mv /mnt/win/Documents and Settings/<userprofile here> /mnt/win/users/

9.) umount /mnt/win

10.) start ubiquity from the commandline wih the new-partitioner switch like this:  ubiquity --new-partitioner

11.) after the setup is done do NOT reboot

12.) mount the disk in step 6 again and move the profiles from step 8 back to the 
Documents and Settings folder. Else Windows might throw a tantrum not finding the
profiles.

```

But it fails at the sudo apt-get ntfs-3g command. I guess that's because this was written for a version that's several years old. Could someone help me update the Process for v9.10? 

My customers and I would be so grateful, 
Gary Barr

---

### Post by GaryB} on 2010-06-22
bump

---

### Post by GaryB} on 2010-06-24
I'm trying to get people OFF Windows and onto Ubuntu. I thought that was a good thing. Could someone please answer my question? Is it really that hard to do? I was thinking it's a sudo command, but I don't know what the name of the Migration Tool is or the Arguments it responds to. 

Maybe I'm making a mistake with this. If I can't get help from you guys then I guess I'll keep my customers on Windows.

---

### Post by Affirmative on 2010-06-24
I might be wrong, but I do believe that 9.10 and 10.04 come with the ntfs-3g driver already, and you may not need to apt-get it.

Otherwise, you can search in the Synaptic Package Manager for 'ntfs' and see what pops up.

---

### Post by GaryB} on 2010-06-24
Thanks for the reply, Affirmative. 

> I might be wrong, but I do believe that 9.10 and 10.04 come with the ntfs-3g driver already, and you may not need to apt-get it.

Otherwise, you can search in the Synaptic Package Manager for 'ntfs' and see what pops up.
Where are the Experienced Hands? 

I guess I'm being misunderstood. I thought I was pretty clear, but maybe I put too much information out there. 

What I want to do is run the Migration Wizard Manually and point it to a Windows Profile String that resides on a USB Hard Drive. I need suggestions for the whole Process. Should the USB Drive be Mounted or not? What Terminal Command would be used to run the Migration Wizard? Is there a Risk I don't know about? 

I Posted that old Code to show that I HAVE done my Research. I did try to do this on my own. Now, I need your help. 

Thanks

---

