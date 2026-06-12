---
title: "Remove only one windows on a triple boot"
date: 2015-09-26
forum: Installation &amp; Upgrades
---

### Post by kevin182 on 2015-09-26
Hello,

I had to install a second windows seven ultimate on my dual boot laptop for my internship.
Now that my internship is done I want to remove my windows ultimate partition and replace it to an empty NTFS partion.

I am not sure what is the safest way to do it since I have two boot "choice screen", one to chose between linux or the windows bootloader and then a second that ask me what windows OS I want to boot.

I wish that Grub would not be damaged by doing this operation.

Here is a capture of my hard drive partitions schematic
[https://drive.google.com/file/d/0B_OU8PFA9cJLWW1YWXl6WXpUTWc/view?usp=sharing](https://drive.google.com/file/d/0B_OU8PFA9cJLWW1YWXl6WXpUTWc/view?usp=sharing)

---

### Post by oldfred on 2015-09-26
Are you using grub or something in Windows like EasyBCD.

Best to see details:

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Mark Phelps on 2015-09-26
A problem you're going to face is that, unless you have a separate windows BOOT partition, then the boot loader for Win7 is present in ONE of the two Win7 installations.  And, if you remove the one containing that, after a reboot, you won't be able to boot again because the boot loader will be gone.

Running the utility that OldFred pointed you to will provide information to aid folks in giving you detailed advice.

---

### Post by kevin182 on 2015-09-28
I exposed your ideas to a Linux help group off my city. We came out to the conclusion that it wax easier and saffer to not touch at the partition but simply delete most of the files in the "Windows for work" partition using the rm command in Linux. It turned out well. Only 2GB of files are left. My friend has been cautious to not remove any file that was pointed by some links between a partition to an other

---

### Post by kevin182 on 2015-09-28
Do you want me to reply to your questions still? for curiosity?

---

### Post by oldfred on 2015-09-28
Not really necessary.

I do run Boot-Repair or bootinfoscript which is a script that really is the first part of Summary report for my own information and documentation of what is installed where and system configuration. You may want to do the same just for your own info.

---

