---
title: "Which Win7 partitions do I shrink for dual boot?"
date: 2012-08-07
forum: Installation &amp; Upgrades
---

### Post by Buntu Bunny on 2012-08-07
Two years ago I installed Ubuntu 10.04 as a dual boot with Windows 7. I created the partitions from Windows and it didn't seem to be a big deal. This time around I am puzzled. 

Windows 7 is also on my new computer (an Asus CM 1740-02) and the hard drive is divided into 3 partitions:

14.18 GB primary partition with 100% free space (greyed out)

WIN 7 (C) 186.3 GB NTFS for system, boot, etc. 157.07 GB free space

DATA (D) 265.27 GB NTFS primary partitions, 100% free space.

In trying to figure out what to do I've been reading through forum threads, official documentation, and how-to websites, but cannot apply the examples to my situation. 

Am I correct that I leave the first one alone?

Is it C: with Windows, that I shrink and partition for Ubuntu 12.04?

What do I do with the DATA partition or can it be shrunk to accomodate space for Ubuntu as well? As an aside, I am planning to install the 64 bit version, unless this complicates it even more.

I apologize if this is an often asked and therefor redundant question, but the more I read others' questions and particulars, the more confused I become. :confused:

---

### Post by black veils on 2012-08-07
that should be your partition order, and your data partition is free, if you dont plan on using the data partition, just delete it from within the windows disk manager. then you will have free/unallocated space left to use for ubuntu. this is when you put the install disc/usb flash drive in etc

you might want to check in your file explorer also, within windows, to see if there is anything on the 'data'

you will want to check things like uefi, gpt, or if those partitions are dynamic or basic.

of course, make backups of all your files before doing anything to the harddrive!

---

### Post by Buntu Bunny on 2012-08-07
Black Veils, thank you for a quick reply. The data partition is all free space. I've done basically nothing with this computer yet except make the back-up and research how to install Ubuntu. Would the data partition serve any purpose for Ubuntu? Or is it just for Windows' use. I do not use Windows unless I need tech support on a hardware issue with a rep who is unfamiliar with Ubuntu.

---

### Post by irv on 2012-08-07
If you boot with the live DVD and run without installing. They run the gparted from the live DVD and post a screen shot of your drive. It will come up with something like sda1 and sda2 with space used and space free. I am guessing that sda2 will be the bigger and the one with the most free space. And most likely be the one to install it on. But sda1 will be where your grub will mostly go. This way you will be able to dual boot to either Windows or Ubuntu.

---

### Post by Buntu Bunny on 2012-08-07
Irv, thanks. Your information is helpful. Everything I'm reading though says Windows 7 partitions best with it's own tools rather than gparted.

---

### Post by irv on 2012-08-07
> **Buntu Bunny said:**
> Irv, thanks. Your information is helpful. Everything I'm reading though says Windows 7 partitions best with it's own tools rather than gparted.

The reason I said to do it this way, is because Linux read the drive a little differently. In windows it shows Drive letter; C and D. In Linux you will see sda1 and sda2 or something like this. I am thinking that if you leave drive C; which most likely partition sda1 as is and install on D; partition sda2 this will work best. After verifying this with gparted, you could just install on the right partition.

---

### Post by Buntu Bunny on 2012-08-07
Irv, I appreciate the clarification. My D drive on windows is 100% free and big enough with 265 GB. You are saying I can just install Ubuntu on that, correct?. Considering what I do on my computer, I may not need to resize anything actually, just use the partitions already there.

---

### Post by irv on 2012-08-07
> **Buntu Bunny said:**
> Irv, I appreciate the clarification. My D drive on windows is 100% free and big enough with 265 GB. You are saying I can just install Ubuntu on that, correct?. Considering what I do on my computer, I may not need to resize anything actually, just use the partitions already there.

Correct. But the grub will have to be on the boot partition for it to work so Windows and Ubuntu can be booted from the grub. Also you will need to set a swap partition and that can be setup from the install process.

---

### Post by Buntu Bunny on 2012-08-07
> **irv said:**
> ...grub will have to be on the boot partition for it to work so Windows and Ubuntu can be booted from the grub.
 
Currently the boot partition for Windows is on the C drive along with system and all other files. Will this need to be created for grub as well?

> **irv said:**
> Also you will need to set a swap partition and that can be setup from the install process.

Right.

---

### Post by irv on 2012-08-07
> **Buntu Bunny said:**
> Currently the boot partition for Windows is on the C drive along with system and all other files. Will this need to be created for grub as well?

During the install when it ask you where the grub will go make sure you pick the boot partition.
Your mount point "/" for Ubuntu will be where you are installing Ubuntu.

---

### Post by Buntu Bunny on 2012-08-07
Irv, I appreciate your being so patient with me and answering all my questions. Looks like it's time to dive in. :)

---

### Post by black veils on 2012-08-07
scroll to **Step 7-C**

[http://www.techspot.com/community/topics/step-by-step-beginners-guide-to-installing-ubuntu-11-10.172128/](http://www.techspot.com/community/topics/step-by-step-beginners-guide-to-installing-ubuntu-11-10.172128/)

---

### Post by irv on 2012-08-07
> **black veils said:**
> scroll to **Step 7-C**

[http://www.techspot.com/community/topics/step-by-step-beginners-guide-to-installing-ubuntu-11-10.172128/](http://www.techspot.com/community/topics/step-by-step-beginners-guide-to-installing-ubuntu-11-10.172128/)

Nice link. It spells it out nice and clear.

---

### Post by Buntu Bunny on 2012-08-07
> **black veils said:**
> scroll to **Step 7-C**

[http://www.techspot.com/community/topics/step-by-step-beginners-guide-to-installing-ubuntu-11-10.172128/](http://www.techspot.com/community/topics/step-by-step-beginners-guide-to-installing-ubuntu-11-10.172128/)

Excellent link! Being a visual person, this is the kind of thing I've been looking for. Many thanks.

---

### Post by pgmer6809 on 2012-08-07
> **Buntu Bunny said:**
> Irv, I appreciate the clarification. My D drive on windows is 100% free and big enough with 265 GB. You are saying I can just install Ubuntu on that, correct?. Considering what I do on my computer, I may not need to resize anything actually, just use the partitions already there.


Not quite I think. 
The partition that is already there (D:) is now formatted as NTFS. ( I am guessing).
You need it formatted as ext3 or ext4.
To do that you will have to 'delete' (or shrink) D: the partition, select the free space that gets created as a result, and create  new partition(s) (ext4 and swap) formated for Linux.

IMHO having a D: drive is a good thing. If you delete D: you could shrink your C: some, and create a new D: (NTFS formatted). This will give Ubuntu a place to write files to, that Windows can see, but will still allow you to boot C: (/dev/sda3 or whatever) as ReadOnly in Ubuntu. Probably a good idea.

Echoing what you have read elsewhere, personally I would do as much partition fiddling as possible in Win7, and only use Ubuntu/Linux to create the LInux ext4 (and swap) partitions out of what free space is left.

---

### Post by Buntu Bunny on 2012-08-07
> **pgmer6809 said:**
> Not quite I think. 
The partition that is already there (D:) is now formatted as NTFS. ( I am guessing).

That is correct.

> **pgmer6809 said:**
> You need it formatted as ext3 or ext4.
To do that you will have to 'delete' (or shrink) D: the partition, select the free space that gets created as a result, and create  new partition(s) (ext4 and swap) formated for Linux.IMHO having a D: drive is a good thing. 

Okay. So that means I cannot reformat it, correct? I read about keeping a NTFS data partition for both Windows and Ubuntu, but don't understand in experientially. 

> **pgmer6809 said:**
> If you delete D: you could shrink your C: some, and create a new D: (NTFS formatted). This will give Ubuntu a place to write files to, that Windows can see, but will still allow you to boot C: (/dev/sda3 or whatever) as ReadOnly in Ubuntu. Probably a good idea. 

Could I shrink both the C: and exsisting D: ? Or do I need to delete D: and recreate it? I really don't do anything with Windows unless it's address hardware issues.

> **pgmer6809 said:**
> Echoing what you have read elsewhere, personally I would do as much partition fiddling as possible in Win7, and only use Ubuntu/Linux to create the LInux ext4 (and swap) partitions out of what free space is left.

Since there's already 3 partitions (don't know what the first one is for, it's 14.18GB and appears unformatted), I would need to make the 4th partition logical, correct(?) for ext4 and a swap(?)

---

### Post by xachu4u on 2012-08-07
haven't you tried the option of

"install along side windows"....the one that comes up when you boot Ubuntu from a CD/pendrive

your partition has disk space to handle both OS.

---

### Post by Buntu Bunny on 2012-08-07
> **xachu4u said:**
> haven't you tried the option of
"install along side windows"....the one that comes up when you boot Ubuntu from a CD/pendrive
your partition has disk space to handle both OS.

Xachu4u, that's the plan. I just wasn't sure how to deal with the 3 exsisting partitions in preparation for installing Ubuntu alongside Windows. Hence the questions in this thread.

---

### Post by Shadius on 2012-08-07
You might want to check if your data partition contains some type of recovery console for your Windows 7 also. I believe Windows usually keeps it there.

---

### Post by Buntu Bunny on 2012-08-07
> **Shadius said:**
> You might want to check if your data partition contains some type of recovery console for your Windows 7 also. I believe Windows usually keeps it there.

Thanks for that Shadius. Will do.

---

### Post by Buntu Bunny on 2012-08-08
Update: Using Windows, I ended up leaving the first partition alone (14.18 GB), Shrank C: as much as was allowable (to 102.64 GB), and deleted D: which contained no files. As much as I like the idea of a shared data partition, I know I'll never use it. That leaves me 348.94 GB for Ubuntu. I don't know why this is always so stressful everytime I do it. Seems simple in the end. Maybe by the time I'm 90 it will seem a piece of cake, LOL

---

### Post by irv on 2012-08-08
> **Buntu Bunny said:**
> Update: Using Windows, I ended up leaving the first partition alone (14.18 GB), Shrank C: as much as was allowable (to 102.64 GB), and deleted D: which contained no files. As much as I like the idea of a shared data partition, I know I'll never use it. That leaves me 348.94 GB for Ubuntu. I don't know why this is always so stressful everytime I do it. Seems simple in the end. Maybe by the time I'm 90 it will seem a piece of cake, LOL

I'll be 74 in a few weeks and it is a piece of cake. I install an OS about 2 or 3 times a year, and sometimes more. I like doing testing. I keep three hard drive for doing this.

---

