---
title: "Please Help &quot;Missing Operating System&quot;"
date: 2008-01-31
forum: Installation &amp; Upgrades
---

### Post by Sunny Hundal on 2008-01-31
i was installing ubuntu 7.10 alongside my vista and i had to exit in the middle of ubuntu installing but when i restarted my computer it now says missing operating system please someone help id really appreciate it

---

### Post by zvacet on 2008-01-31
Reinstall looks like only resonable choise,because you didn´t install Ubuntu in first place.When you come to partition select manual and delete Ubuntu partition(it should be named ext3) and on that empty space install Ubuntu again.

---

### Post by Patsoe on 2008-01-31
Sounds like either your master boot record (MBR) is invalid, or else the partition table is broken (this is somewhat worse).

In the first case there are two options: 
* One is to do the Ubuntu installation completely, which should give you the GRUB bootloader (which will recognise Vista too)
* Or, if you don't care about Ubuntu right now, you could try to repair the MBR as explained here: [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

As for the second case: when did you break off the Ubuntu installation? What was the installer doing at the time?

---

### Post by Sunny Hundal on 2008-01-31
will my vista stil be there?

---

### Post by Sunny Hundal on 2008-01-31
> **Patsoe said:**
> Sounds like either your master boot record (MBR) is invalid, or else the partition table is broken (this is somewhat worse).

In the first case there are two options: 
* One is to do the Ubuntu installation completely, which should give you the GRUB bootloader (which will recognise Vista too)
* Or, if you don't care about Ubuntu right now, you could try to repair the MBR as explained here: [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

As for the second case: when did you break off the Ubuntu installation? What was the installer doing at the time?

ummm i think it was reading files or copying em i cant exactly remember

---

### Post by Patsoe on 2008-01-31
OK, that's good. I was worried it was partitioning...
So you should be able to go with one of the two options I mentioned.

---

### Post by Patsoe on 2008-01-31
> **Sunny Hundal said:**
> will my vista stil be there?

There's no guarantee, but if you didn't select to use the whole hard disk in the install procedure, it should still be there.

---

### Post by Sunny Hundal on 2008-01-31
i was following instructings from this site i had unlocated space and i used the option where it saysManual - use the largest continuous free space

---

### Post by Sunny Hundal on 2008-01-31
Also 1 last question is there a way to repair the master boot recordwithout the vista install disk cause its not at my house right now(nvm i found it)

---

### Post by Sunny Hundal on 2008-01-31
thanks for your help patsoe

---

### Post by Sunny Hundal on 2008-01-31
Can someone please help i fixed the MBR by doing bootrec.exe/FixMbr and it said operation complete but when i restarted it still came up with Missing Operating system.

---

### Post by Patsoe on 2008-01-31
> **Sunny Hundal said:**
> Can someone please help i fixed the MBR by doing bootrec.exe/FixMbr and it said operation complete but when i restarted it still came up with Missing Operating system.

That sounds bad, I'm sorry to say. I'll keep my fingers crossed that someone else has a good idea for you. Did you have data that wasn't backed up?

---

### Post by Sunny Hundal on 2008-01-31
i didnt really have data i needed on it

---

### Post by zvacet on 2008-02-01
if you have Ubuntu installed but have problems with MBR try [this](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub).

---

