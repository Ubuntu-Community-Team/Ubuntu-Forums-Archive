---
title: "Newbie with flaky Lubuntu"
date: 2023-05-03
forum: Installation &amp; Upgrades
---

### Post by woogie2 on 2023-05-03
I think I want to give up on my Lubuntu. I think it's simply buggy. It's like it's gaslighting me trying to convince me I'm crazy.

I also have an ISO for Ubuntu MATE which I want to try.

I did not know I needed a download so I could do a dual boot. Is my WIN10 trashed now? I'm hoping it's on my HD somewhere. I moved the slider so (I thought) Lubuntu would get 75% of the HD and Win10 the other 25%, but I don't know where Win10 is now. I didn't format the drive or anything.

I put Ubuntu on my wife's machine with Win10 4-5 years ago and it is automatically set up to dual boot. I didn't realize anything had changed.

I'd like to start over with MATE but I'm looking for someone to hold my hand so I can get this machine going so I can get back to work. It's a Dell Optiplex 9020 with a brand new HD. I got it on Walmart site, refurbed with Win10. 

I'll also need my HP Officejet 4630 connected to I can scan. Very important.

Can anyone help me?

---

### Post by oldfred on 2023-05-03
Typically it just works. But we need more information on what is where.

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version over somewhat older ISO with your USB installer  or any working install.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by woogie2 on 2023-05-05
> **oldfred said:**
> Typically it just works. But we need more information on what is where.

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version over somewhat older ISO with your USB installer  or any working install.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Hi oldfred.

I went to [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) and tried the first way out of two ways it suggests and got the message: "yannubuntu/boot-repair not found"

Right now I'm miraculously in Windows. I'll have to do a restart in Setup to tell you how I found it.

Also I have to try the second way on that gave you gave me to see about fetching and sending the BootInfo summary report. I'll be back. Thanks for your help so far.

---

### Post by yancek on 2023-05-05
Did you shrink the largest windows partition from within windows using Disk Management?  Generally better to use windows tools to modify windows partitions.  You should also run chkdsk after making partition changes in windows.

The second option described on the boot repair page needs an Ubuntu derivative so use the Lubuntu install USB.  This USB is read only so data is not saved on reboot so do not reboot after running boot repair before posting the link here.

---

### Post by woogie2 on 2023-05-06
> **yancek said:**
> Did you shrink the largest windows partition from within windows using Disk Management?  Generally better to use windows tools to modify windows partitions.  You should also run chkdsk after making partition changes in windows.

The second option described on the boot repair page needs an Ubuntu derivative so use the Lubuntu install USB.  This USB is read only so data is not saved on reboot so do not reboot after running boot repair before posting the link here.

I shrank the partition according to what came up on my install screen. 

I'll do a chkdsk now.

I'll need a few minutes to figure out what is meant by your next instruction.

How I just started my machine: Did F12 during startup. Screen says "Boot mode is set to LEGACY
Secure boot: OFF

I scrolled down to UEFI BOOT: Windows boot manager, hit ENTER.

Yesterday this is how I accidentally got it to boot into Windows. Today I did this and it booted into Lubuntu. I tried it again, the exact same thing, and it booted into Windows, so I'm in Windows right now.

It did some kind of checkup process starting up in Lubuntu that looked like a Windows thing; it showed a MSWindows logo thing on the screen while doing this iirc, but then booted into Lubuntu. It's haunted.

Will do chkdsk now.

---

### Post by woogie2 on 2023-05-06
How about if I just take it to a repair shop and have the disk wiped and a fresh Win10 install done? CHKDSK isn't working for me the two different ways I tried it. Something about a syntax error.

With a fresh install then I could come back here and get help to put Lubuntu on it properly. Yes?

---

### Post by tea for one on 2023-05-06
> **woogie2 said:**
> How about if I just take it to a repair shop and have the disk wiped and a fresh Win10 install done? 
If you wish to spend your money, then your choice.
However, there are many forum members here, who would only be too pleased to help you.
A fresh install of windows 10/11 would wipe the disk anyway.

> **woogie2 said:**
> With a fresh install then I could come back here and get help to put Lubuntu on it properly. Yes?
Of course, plenty of help available.

Have you backed up your Windows and Lubuntu personal data?
Do you have or know how to make a bootable Windows 11 install disk?

---

