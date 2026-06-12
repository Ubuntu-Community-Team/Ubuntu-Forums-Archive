---
title: "Removing an old Ubuntu installation"
date: 2010-10-19
forum: Installation &amp; Upgrades
---

### Post by Kaheil on 2010-10-19
Hello,

My computer has 5HDD, two Raid0 and a single one. My first installation of Ubuntu on it, Lucid, was made on the single HDD. Howevre I installed the new Maverick on one of the Raid. The problem is that I didn't find anyway to remove the old, single, HDD and it's Ubuntu entry in grub. I've tried many things on a virtual machine and, of course, asked my dear friend google, but failed to succeed. 

I would simply like to remove that old Ubuntu install from the system, I have no need to keep any of the data stored on that disk or related to it. 

Help please! :)

---

### Post by ronparent on 2010-10-19
Do I understand that you simply want to remove the entire drive from that box? How you go about it would depend on whether the two raid sets were software raid or fakeraid. Which are they? If fakeraid, the boot loader would merely have to be reinstalled to one of the raid sets remaining as boot. I am too uninformed of software raid protocols to help you. But my understanding is that you can't boot directly into a software raid. Let us know what you are working with and someone can pitch you an answer.

---

### Post by Kaheil on 2010-10-19
Maybe I was a bit unclear toward what my problem is. What I want to do is to physically remove the fifth (no-raid) hard drive, which contains the old Ubuntu install, from the box without loosing the possibility to access the other OS (therefore without damaging grub).

The newer version of Ubuntu is installed on one of the two hardware based Raid0. Both Raid0 are completely functional and do not requier any particular attention. 

Thanks, in advance, for your help :)

PS: I've tried going to the boot.lst and searching for the linux headers in the software centre (on the newer install), but without success.

---

### Post by ronparent on 2010-10-19
It appears from what you said that your raids are actually what the Ubuntu community refers to as fake raids. All you require is a grub 2 reinstall. See here for the steps: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

Just be aware that you have to substitute the raid /dev/mapper designations for the target partition and the raid boot loader. In a list of /dev/mapper the first item after control designates the raid location to install the boot loader to and the items following are all your raid partitions. The raid partition your 10.10 is installed to is the one you have to mount. Post if after looking your system over you still have questions.

---

### Post by Kaheil on 2010-10-19
I fail to understand one thing: on my computer, the raid0 are treated as a single 1To drive by both windows (I have a dual boot, for gaming) and Ubuntu; the single HDD are only visible throw the bios. I don't see how this configuration is of any relevance to the probleme, since what I want to do is to remove the other, single, non-raid, harddrive (and the associated grub entry), rather than changing the install on the Raid0.

PS: I'm probably missing what you are trying to say by kilometers, but I genuinely don't understand how the raid0 come into this :)

---

### Post by ronparent on 2010-10-19
I was under the assumption that you were booting on the single disk. If that were so, then when the bootable disk was removed you would have to install a new boot loader onto one of the raid drives to be able to boot. 

Even if you are booting on the raid disk, the grub program itself is installed on the single disk and that disk's removal would no longer leave anything for the boot loader to find.

In either case grub would have to be reinstalled to permit the system to boot without the single disk. Your objective, therefore is to reinstall so that the grub located with 10.10 is found by the boot loader installed on the boot raid. Then the system would boot without the single disk. Otherwise you would have no problem and a simple update-grub would suffice to remove 10.04 from the boot menu after the single disk was removed!

---

