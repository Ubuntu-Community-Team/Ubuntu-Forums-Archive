---
title: "Feedback on the installer"
date: 2010-03-10
forum: Installation &amp; Upgrades
---

### Post by Blutkoete on 2010-03-10
Hello!

I didn't find a good place to put this (you might show me the right place), so I'll just put it here, because many people might need support if the same happened to them. This is meant to be feedback on the quality of the Ubuntu Installer (from CD).

I had Windows 7 Professional on my Notebook and wanted to add Ubuntu 9.10 64bit as a second operating system. I split the harddisk into three partitions: The already-there Windows partition, one Data partition (hoping to use it for both systems) and one for Ubuntu. Then I booted from the Ubuntu CD.

WARNING: I used the German version, so the messages the installer gave me are just rough translations.

First, I chose the Partition-it-the-way-you-like mode for experienced users, but rejected it because the system told me there was no root system (without telling me how to get one). Ok, maybe I wasn't experienced enough (OS/2, Dos 6.22, Windows and Mac user before). So I chose the Not-use-my-whole-harddisk mode: Install it parallel to the other operating system. I clicked next. I was still waiting for the Installer to ask me which partition to install Ubuntu on, but there was a pop-up telling me that "The size of the partition will be reduced, there's no way back". O, I thought. It recognized that partition 1 is Windows 7, partition 2 contains data and partition 3 is free to be formatted and it will be resized for Ubuntu (Swap and things like that). So I clicked 'OK'.

Everything went fine. Ubuntu started without problems. But then I restarted Windows 7, and I got a bluescreen (unreadable, only for 0.01 seconds) and the computer booted again. I tried Ubuntu again, starting without problems. I opened the drive management. And there is the one thing I don't understand:

Instead of asking me which partition to use for the install, instead of using the No-OS Data partition or the empty partition, the Ubuntu installer reduced the size of my Windows 7 partition, leaving it unusable and installed Ubuntu on half of that partition.

I was able to recover my personal data from the Windows 7 partition and made a clean Whole-Harddisk-Ubuntu-9.10-64bit install to remove the partition garbage I was left with, but I would like the installer to

a) maybe ask which partition to use in the future;
b) state that it is reducing the partition of the former installed OS and that
c) this might leave your former OS unusable in the future.

"I'm reducing the size of the partition and this can't be undone" does neither state which partition is meant nor what that might mean to previous installed OS.

I still don't understand why the Installer made what he made, and I'm happy with my Ubuntu (and the whole 'Destroy the Windows 7 partition Carnage' up my migration), but I still think that the installer is very confusing and doing things it shouldn't.

If there's a better place to put this feedback, please tell me.

If this shouldn't happen and it might have to do with my computer's configuration, I'm glad to help by providing more information.

Thank you for all your work,

Tobias

P.S.: Some users might not know how to recover there personal files from the Windows 7 partition, so this problem should be solved.

---

### Post by ajgreeny on 2010-03-10
When you use the manual partitioner of the installation system, you choose the partitions and then must choose the mountpoints as well, and that is probably the bit you missed and why you got the error message.  You must then click  to select the "format" button, which you also may have missed.

Here's a great website explaining how to do the manual partitioning thing, here for a system with a separate /home partition, but the general info still holds good whatever partitions you choose to have.
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

