---
title: "Windows 7 dual boot"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by rplantz on 2010-05-01
I'm currently using the Windows 7 boot loader. I used EasyBCD to add my Ubuntu 9.10 installation so I can dual boot. The two systems are on separate disks.


I only started using Windows with Vista, but it's my understanding that grub was recommended over the Windows boot loader previous to Vista. I've heard that the newer Windows boot loader is much better.

I'm getting ready to do a new install of Ubuntu 10.04 on the same disk with Windows 7. Is it better to install grub 2 as my primary boot loader? Will the installer recognize my Windows 7 and set things up okay? And I assume that it would find my current Ubuntu 9.10 on the second disk and incorporate that okay.

--Bob

---

### Post by Water_Spirit on 2010-05-01
[This]("http://ubuntuguide.org/wiki/Ubuntu:Lucid") may help you

---

### Post by wilee-nilee on 2010-05-01
I have W7 and Lucid on the same hard drive, I use grub. I don't see a reason for myself to use a third party booting tool to make the stock MS one work. Grub will read the ntfs boot and run with very little; if any problems, by and large. The MS bootloader needs the third party to work, for me that is the answer, but use what you feel most comfortable with.

---

### Post by rplantz on 2010-05-01
> **wilee-nilee said:**
> I have W7 and Lucid on the same hard drive, I use grub.

Thank you. The main thing I wanted to know is that grub 2 will work okay. I was pretty sure it would, but it's good to hear someone say it does.

The history behind my using EasyBCD is that I had to do that on my laptop (running Vista and Ubuntu 9.04) so that I could get to the hidden Vista partition in case I ever needed to restore Vista. I don't use the laptop very much, so I don't feel like spending much time tweaking it.

--Bob

---

### Post by wilee-nilee on 2010-05-02
> **rplantz said:**
> Thank you. The main thing I wanted to know is that grub 2 will work okay. I was pretty sure it would, but it's good to hear someone say it does.

The history behind my using EasyBCD is that I had to do that on my laptop (running Vista and Ubuntu 9.04) so that I could get to the hidden Vista partition in case I ever needed to restore Vista. I don't use the laptop very much, so I don't feel like spending much time tweaking it.

--Bob

Well having access to the recovery partition does seem like a valid reason for sure. I just have the Install DVD I don't like the recovery partition idea myself. With XP you can do a repair of the installed system without losing the original setup it is hidden in the machine and disc you just have to know where to look. W7 probably will do the same, beside being able to return to the last working system, maybe not though.  

If you have any trepidations about the dual boot on the same HD post on the forum, this is the best place to get the real truth. On another MS forum I go to often, gotta help the other you know; when somebody has a grub issue it is deep clean time for them as they don't understand how easy it actually is to reload the MBR with MS or Grub. If you want links to that info just post back and I or somebody else will hook you up.

---

### Post by wilee-nilee on 2010-05-02
Argh a double post sorry.

---

### Post by rplantz on 2010-05-02
> **wilee-nilee said:**
> Well having access to the recovery partition does seem like a valid reason for sure. I just have the Install DVD I don't like the recovery partition idea myself. With XP you can do a repair of the installed system without losing the original setup it is hidden in the machine and disc you just have to know where to look. W7 probably will do the same, beside being able to return to the last working system, maybe not though.  


I have an install disk for W7, which is on my desktop machine, so I'm comfortable with doing more on that machine.

I think there's a way to create a restore CD for Vista on my laptop, but since I use the machine so seldom, I just haven't taken the time to figure it out.

Since I have your attention here, do you know what the installer does in the "along side Windows" option? I've done manual partitioning many times, so I'm okay with that. But I'm curious to learn what this "along side" partitioning does. I asked this question in another thread, but nobody has responded.

---

### Post by oldfred on 2010-05-02
The along side trys to simplify the install process and makes space 'along side' of windows. You will get whatever sizes some process thinks makes sense. If familar with partitions it is always better to create you own partitions, you also can add a /home partition for your data and then root (/) only has to be 10-20GB. Swap can be 2GB or your RAM size. 

During manual install you select the partitions and tell it which is / and how to format it, and the same for others. Swap it seems to find on its own.

If you have converted to win7 the restore Vista disk is not worth much. It would restore to as factory delivered. All you data is erased including the update to win7.

---

### Post by rplantz on 2010-05-02
> **oldfred said:**
> The along side trys to simplify the install process and makes space 'along side' of windows. You will get whatever sizes some process thinks makes sense. If familar with partitions it is always better to create you own partitions, you also can add a /home partition for your data and then root (/) only has to be 10-20GB. Swap can be 2GB or your RAM size. 

During manual install you select the partitions and tell it which is / and how to format it, and the same for others. Swap it seems to find on its own.

Thank you, oldfred. That's pretty much what I guessed. Yes, I do set up a separate /home partition. I've done manual partition installs dozens of times, so that's what I will do again. "If you want it done right,...."
> 
If you have converted to win7 the restore Vista disk is not worth much. It would restore to as factory delivered. All you data is erased including the update to win7.
Just for clarification, I have not converted to Win7. I'm still running Vista on my laptop, but Win7 on my desktop. My laptop is only for occasional use, so I just leave it at Vista.

---

### Post by wilee-nilee on 2010-05-02
I would agree with the manual partitioning.

---

### Post by rplantz on 2010-05-08
I went with the manual partitioning and grub2. It all works very well. Thanks to all who contributed to my knowledge here.

--Bob

---

### Post by haafmaad on 2010-05-09
i have windows 7 in c drive and ubuntu in the d drive . i installed windows first .
now windows is the boot loader. 
then if my windows is deleted then how can i  get access to ubuntu?

---

### Post by oldfred on 2010-05-09
haafmaad welcome to the forum.

You should start your own thread as this one is solved on only those looking for a solution for an identical problem will be looking at it. Also put a good title on your thread and post the results.txt from boot info script.
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags ([COLOR=Red]# in edit panel[/COLOR]) to make it easier to read when you post the results.txt.

---

