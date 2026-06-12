---
title: "Have 32bit Ubuntu, want to install 64bit instead"
date: 2010-04-06
forum: Installation &amp; Upgrades
---

### Post by Voluntaryist on 2010-04-06
I have a couple questions about changing my Ubuntu install from 32bit to 64bit. 

I have separate partitions for "/" and "/home" that I configured when I first installed the 32bit Ubuntu. Now that I am going to run a clean install of 64bit, can I just install it on the "/" partition and leave "/home" untouched? 

And if that is so, will my 64bit Ubuntu installation be able to recognize and use the "/home" partition without any issues? I'm concenred about this because I made the "/home" partition using the 32bit Ubuntu install. 

Thanx!

---

### Post by Tylerjd on 2010-04-06
Having the /home partition being created with 32-bit is fine, there is no difference, as long as you don't have a binary's in the /home. As for the /home partition getting recognized, that's not my area of expertise, so I don't know.

---

### Post by Voluntaryist on 2010-04-06
> **Tylerjd said:**
> Having the /home partition being created with 32-bit is fine, there is no difference, as long as you don't have a binary's in the /home. As for the /home partition getting recognized, that's not my area of expertise, so I don't know.

Thank you for the quick reply :)

Your info is good news for me, and I'm getting anxious to install the 64 bit now since it sounds like the "/home" partition won't need any changes in order to work. 

Does anyone know if 64 bit will recognize and be able to access the files on a "/home" partition that was created with the 32 bit Ubuntu? I just need to make sure because I dont have enough space on my external HD to backup my entire "/home" folder (ghetto I know).

---

### Post by oldfred on 2010-04-06
With Karmic I converted to 64bit from 32bit. I had for 3 years just root and swap with a small shared FAT partition for data to share with XP. I bought a new drive so I had lots of room so I kept my 32 bit install, created a new root for 64 bit Karmic, added a root for Karmic beta to test it before I converted to make sure it seemed to work.

I also moved home to a new partition and have had no issues with 64 bit reading the old home data. But I moved all my data folders to another ext3 /data partition and now /home is only about 1GB of hidden files & folders with a few default saved files that I need to move to my data partition. Some of the stuff in my /home is 3 years old so I did do some housecleaning.

I did have to go back only twice to my 32 bit partition to find settings and those I could have recreated, it was just easier to copy from the old partition.

---

### Post by Voluntaryist on 2010-04-06
Thank you, once again that info is very helpful.

OK now I've got one more question and it's a serious n00b question:

I have an Intel Quad Core processor. But on the 9.10 download page at Ubuntu.com, it has radio buttons for selecting either 32 bit or 64 bit. If I select the 64bit, it begins downloading an .ISO file that is called "ubuntu-9.10-desktop-amd64.iso"!!!  I don't want the AMD 64 bit version, I want the INTEL 64 bit version. Or is this .ISO that says "AMD" actually meant for both INTEL and AMD 64bit processors? I would hate to accidentally install the wrong version for my chipset, but I dont want to be stuck with 32bit Ubuntu either! :confused:

---

### Post by wojox on 2010-04-06
It's the same thing. AMD bought the name or something. You're safe to download it and install it on your Intel.

---

### Post by Voluntaryist on 2010-04-06
Perfect. Thanks for the clarification. I'm now going to download the AMD64 .ISO and install it on my "/" partition. :KS

---

### Post by rustutzman on 2010-04-06
I just did this very thing. Just remember after you select the manual partitioning you need to hit the little drop down menu. There you select root with / , you need to select /home on your existing home partition. Of course don't format it.

Russ

---

