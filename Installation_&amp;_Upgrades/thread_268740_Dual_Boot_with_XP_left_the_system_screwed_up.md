---
title: "Dual Boot with XP left the system screwed up"
date: 2006-09-30
forum: Installation &amp; Upgrades
---

### Post by kkumar on 2006-09-30
My system (MSI MB and AMD Sempron processor) had Win 98 in C and Win XP in D. I decided to delete Win 98 and install Ubuntu there. I  put the Ubuntu CD in the CD ROM and format the C drive using Ubuntu and install it on CD. The other partitions are left untouched. Ubuntu installed successfully on C. However I no longer have boot option. The system boots into Ubntu without offering any option. Other partitions can't be accessed either. Besides, Ubuntu has no sound nor video support. Ubuntu doesn't recognise the drivers that came with the MSI Mother Board. Can I save the XP installation on my D drive? If I want XP and Ubuntu dual boot, how should I go about it? Please advise me.
Thanks in advance.
Kumar

---

### Post by fred22 on 2006-09-30
Firstly I am no expert, but I dont think you need panic.

When you installed was C set to be master and D slave? I have exactly the same setup (only working) on my desktop.

How is your bios set up, what are the boot devices listed?

---

### Post by kkumar on 2006-10-01
Hello,
Thanks for your reply.
C & D were partitions on the same HDD. So, master or slave setting doesn't apply here, does it? The Phoenix Bios system says nothing about the OS options. 
Something like GRUB (I don't know what it is) can help?
kkumar

---

### Post by jys_sachin on 2006-10-01
Hi Kumar, Just to understand yor in 98 & XP setup... I beilieve you had Win XP & 98 setup on the same computer with XP giving you an option to choose between xp/98. Now that you have installed ubuntu, grub has taken over the MBR and does not give an option to boot XP at all. This is suprising because if XP's boot manager was a part of the MBR earlier it should automatically configure GRUB to give you options to boot between XP/Ubuntu. Are you sure that the Ubuntu was installed on C: if yes is the D: drive stil intact, you can try mounting this partition in Ubuntu to confrim. It seems that you will have to reconfigure GRUB but since you cannot boot your XP system at all you might need the XP installation disk for rescue. refer to the microsoft website for more information.

---

### Post by jys_sachin on 2006-10-01
boot your computer with a WINXP installation disk. choose "recovery" and at the DOS prompt type "FIXMBR".. you should be able to boot your computer in WinXP... hope this helps

---

### Post by kkumar on 2006-10-02
Hi Jys_sachin,
Thank you for your reply. I think I am on the way to understand the problem thanks to your reply. 
Your name suggests that you are from India. Am I right? I am from Kerala. 
Now, about my problem. I was having Win98 on C partitiond and WinXP on D partition of the same HDD. However, the first OS installed was Win 98 and not WinXP. Whenerver I power on I would get an option to choose XP or 98. By default it will boot into XP after the stipulated seconds. I am sure I installed Ubuntu on C and not D and also that D was untouched during Ubuntu installation. I don't know a thing about Linux. So I will have to ask at #ubuntu how I can mount the partition as you suggested.  Further I am going to try the recovery process of Win XP as you suggested. If that would help it would be much easier. 
Thanks again for your help. I will post the result of my experiment later.
Kkumar

---

### Post by jys_sachin on 2006-10-02
Hi Kumar,

I am from Mumbai, born in kerala though :). I just recovered by Ubuntu installation. I had lost my GRUB loader and had to reconfigure GRUB all over again. Now I have a 40 Gig harddrive, with WinXP, Fedora Linux & Ubuntu Linux. I thankful to Ubuntu for having created this forum, I would have never been able to configure grub otherwise. I'll keep checking this thread if I can help you in any way. I would strongly suggest that you read through the beginners guide to installtion before you try reinstalling Ubuntu. And also the documentation section on ubutu support. It really helps ;)

---

