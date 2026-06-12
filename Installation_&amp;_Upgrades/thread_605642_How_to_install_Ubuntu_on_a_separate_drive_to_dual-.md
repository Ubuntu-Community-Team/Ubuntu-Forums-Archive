---
title: "How to install Ubuntu on a separate drive to dual-boot with XP?"
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by alicson on 2007-11-07
Hi, I'm having trouble finding the basic answer to this question, so I'm hoping someone here can answer or point me in the right direction:

This will be my first experience with Linux (finally)... I'm on a desktop with two harddrives, running 32-bit XP Pro.  **I would like to install Ubuntu on the second drive, and then set up my system to dual-boot**.

The instructions that come with the installation, and others that I've found, seem strictly tailored to install into a partition on the same drive as Windows; I really don't want to do that.
I've seen several different things about Grub, and I'm sure I'll have to read that more closely and tackle that, but first I'm wondering how to go about installing Ubuntu on the second drive. **Do I run the installation while in Windows?  Or run it from the CD on boot-up?**

If there's an existing tutorial/guide for this, I would be grateful for the link.

Thank you!

---

### Post by taurus on 2007-11-07
You boot your machine with the LiveCD.  Then, tell the installer to install Ubuntu on your second harddrive, leaving your first harddrive with windows alone.  Don't forget to install GRUB to MBR so you can boot either Ubuntu or windows when you turn on your machine.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Baldeagle63 on 2007-11-07
H E L P.
I tried to something very similar and have have a propblem.
I have 2 HD's one 20Gig and has windoze on it (XP) My second drive is 160G partitioned into 4 seperate drives. I cleaned one partion off as I wanted to install UBUNTU to it. alas it wanted the whole drive and reparttioned it.

I have thousands of family photos I would really like to recapture if I can.

PLEASE PLEASE let there be an answer nto recover them.    :(

---

### Post by oilchangeguy on 2007-11-07
> **Baldeagle63 said:**
> H E L P.
I tried to something very similar and have have a propblem.
I have 2 HD's one 20Gig and has windoze on it (XP) My second drive is 160G partitioned into 4 seperate drives. I cleaned one partion off as I wanted to install UBUNTU to it. alas it wanted the whole drive and reparttioned it.

I have thousands of family photos I would really like to recapture if I can.

PLEASE PLEASE let there be an answer nto recover them.    :(

this is exactly why you MUST backup your data BEFORE attempting to do something like this. and the only way it used the entire drive, is if you clicked ok. there are companies that do data recovery. it's not cheap. look in your phone book under computers, or data. i really hope you can get your pics back. but hopefully this is also a lesson learned.

---

### Post by Baldeagle63 on 2007-11-07
Thank you very much.
I know that and wanted to install on a spare partition. Being spare there was nothing there and nothing to back up.
I did not expect it to reformat the entire drive.
I'm a newbie who came here looking for help.

Is there someone who can actually help?

---

### Post by oilchangeguy on 2007-11-07
> **Baldeagle63 said:**
> Thank you very much.
I know that and wanted to install on a spare partition. Being spare there was nothing there and nothing to back up.
I did not expect it to reformat the entire drive.
I'm a newbie who came here looking for help.

Is there someone who can actually help?

there's not much the forum can do for you if the drive's been formated. unless they own a data recovery company.

---

### Post by oilchangeguy on 2007-11-07
i found this company listed in the book upgrading and repairing pc's
[http://www.ontrack.com](http://www.ontrack.com)

---

### Post by bulldog on 2007-11-07
> **Baldeagle63 said:**
> Thank you very much.
I know that and wanted to install on a spare partition. Being spare there was nothing there and nothing to back up.
I did not expect it to reformat the entire drive.
I'm a newbie who came here looking for help.

Is there someone who can actually help?

I'm sorry for your data,but I'm perfectly sure you choosed the option to use the whole disk and applied it.
You should have chosen MANUAL partitioning instead.
And Oilchangeguy is right  I'm afraid,the data is lost for normal people,only special recovery tools and company's can bring some of it back.

---

### Post by alicson on 2007-11-07
First of all, thank you for the answers.  I guess that because all the installation screenshots I saw did not show options for other existing partitions or drives, I was afraid the option wasn't there.  Now it seems elementary and obvious that when my turn comes up, the installation screen should show all my (2) harddrives and should show the existing partitions.

Now, to be sure that I do this right (and do NOT reformat my entire drive!..)
I'll be selecting "Manual partitioning" and then I'll be able to select the ALREADY partitioned space (set to O:\ for me.. does Linux care about drive letters?) on my second drive, and tell it to move in there, and it *shouldn't* affect any of my other partitions/drives?  (I understand that things can go wrong..but of course I'd like the highest-possible probability for success!)

Thank you much :)

---

### Post by bulldog on 2007-11-07
Some understanding in the way your hdd's are partitioned comes in handy.
Make a note for yourself so you know what is what.
The partitioner uses no C:/ or D:/ but uses numbers instead.
Your first hdd is hd0 the second is hd1 and so on or sda or sdb for that matter if they are sata.
Your partitions are listed as hd0,0 hd0,1 and so on or sda1 sda2 sdb1 sdb2
So first the drive and after the , the partiton starting with zero 

So what you have to do is choose manual partitioning,choose the correct hdd and then the correct partition.

Looks a little difficult,but when you see it you'll understand.

---

### Post by alicson on 2007-11-07
Thank you, that really helps too.
:)
'Very appreciated.

---

