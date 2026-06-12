---
title: "Install with windows on h.d."
date: 2010-03-21
forum: Installation &amp; Upgrades
---

### Post by puzzledboy on 2010-03-21
Hello everybody,
 
I have a P.C. with Windows XP Pro installed and now I want to put Ubuntu on the H.D.
Will the partitioning of the H.D. damage the Windows OS meaning a reinstall of Windows.If it does then I may be a bit stuck as I do not have the Windows install disc.
Windows XP was put on the machine by the vendor.
 
Looking forward to any help,
 
Puzzledboy

---

### Post by underquark on 2010-03-21
Download ubuntu and burn a Live CD.

Delete as much rubbish as possible from your hard drive. Turn off Windows pagefile/swapfile/restore points to prevent fixed portions of the disk being used. Defrag the hard disk.

Boot from the Live CD.  Use Gparted to resize the Windows partition.  Choose to install ubuntu alongside your existing Windows installation using the remiaing space on the disk.  Leave a bit for a swap file (about twice RAM size is often suggested).

Remove the CD and re-boot.  You should be presented with a choice of booting into Windows or ubuntu.

If you're really worried, get another hard disk and clone your old one to it first.

---

### Post by Mark Phelps on 2010-03-21
BEFORE you do anything else, boot from the LiveCD and see how well the Ubuntu version detects your hardware and installs the right drivers.  IF all your hardware works, then an install should go OK.

Anything does not work, post the details back here.

It's better you find out what will need to be fixed, and how hard that will be, before you start messing around with resizing your partitions.

---

### Post by puzzledboy on 2010-03-21
Helo Underquark
Thank you for your quick reply.First of all I must tellyou that I know very little about the Windows OS.  and so I have to ask what is pagefile/swapfile /restore points and where can I find these things and how do I turn them off.I must say that I find Windows to be like  a cross between a maze and a rabbit warren with ambiguous names and messages everywhere none of which can be easily understood. 
I have aN Ubuntu CD which  I purchased however I do not know if it is a Live CD. I do know how to defragment the HD.
What is Gparted.Where can I get it from? 
How do I find the Windows partition and when found how do I resize it?What size should it be?
You say put Ubuntu alongside Windows,but how is this done?
What is a swap file and where is it?
I would not know where to get another hard drive.What does clone to it mean and how is this done?
Sorry about so many questions but I know nothing about computers and Iexpect it would take a small book to explain all I need to know.Ihave previously just bought a computer with everything done ready for me,even then I have had problems putting in programmes which I have purchased.
It took me about 15 minutes to find the quick reply symbol as it is not clear where to find it and I could only find it by trial and error This is typical of lots of things in programmes and web pages.
 
 
Puzzledboy

---

### Post by puzzledboy on 2010-03-21
Hello Mark Phelps,
I have an Ubuntu disc which I puchased whether this constitutes a live CD I do not know.If I install Ubuntu what will this do to the Windows already installed because if I muck that up I will  be in trouble as I do not have a Windows XP disc to put it back and this is my main worry.If I mess up Windows then I would need to buy the new Windows 7 system as Windows XP can no longer be purchased.This would set me back about £140 which to me is a lot of money also I understand that programmes which were written fof Windows XP and Windows 98 might not work on Windows7.To have to buy programmes that work on Windows 7 would be a further burden and my idea of using Ubuntu is to use free progammes and cut out endless expense that makes Microsoft rich.The main problem is that I dont't know what I am doing.
 
Puzzledboy

---

