---
title: "Trouble Upgrading to Jellyfish - Continuous Restarts"
date: 2022-06-18
forum: Installation &amp; Upgrades
---

### Post by Qbert on 2022-06-18
Hello Gals and Guys - 

I have a HP laptop I was running 20.04 on it, but decided to upgrade to 22.04.  I do a clean install because it doesn't take long, but after finishing the install, which seems to go well, I get the HP splash screen, then it restarts.  Rinse and repeat until I turn it off.  I'm not particularly talented with Linux, but is there something I can look at this to fix it?  Thanks for any help.

---

### Post by web-user on 2022-06-18
Seems like hardware incompatibility issue. I think you should try to figure out what driver is missing and install it from chroot. (you should use LiveCD to do it).

---

### Post by Qbert on 2022-06-19
Thank you for the reply.  Is there a guide on how to find missing drivers?  I looked in the BIOS and it's set to Intel GPU only.  I checked on the software page and it said there were no additional drivers, but that was while I was installing it.  It seems difficult to find any missing drivers when you can't log in even once, but that's why I'm here.  Thanks again.

---

### Post by tea for one on 2022-06-19
> **Qbert said:**
> but is there something I can look at this to fix it? 
Can you boot into an Ubuntu live session and download the boot-repair utility.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
2nd option – Create boot-repair summary and post the pastebin link to the report in this thread before attempting any repair.

---

### Post by Qbert on 2022-06-22
Thank you for the reply.  Is this the link that's needed?


[https://paste.ubuntu.com/p/TtW9jYdz4F/](https://paste.ubuntu.com/p/TtW9jYdz4F/)


Thanks again.

---

### Post by tea for one on 2022-06-22
You have 3 disks although one OS Ubuntu on nvme0n1p2.

[COLOR="#0000FF"]Line 34 - 36[/COLOR] - sda1 with Bitlocker
[COLOR="#0000FF"]Line 40 - 47[/COLOR] - sdb1 with another set of boot files
[COLOR="#0000FF"]Line 64[/COLOR] - Secure boot enabled
[COLOR="#0000FF"]Line 67 -85[/COLOR] - Multiple boot files

I would first try:-
Isolate, de-activate or remove two drives sda & sdb (sdb is your live system)
Disable Secure Boot via UEFI
Try and boot into Ubuntu

---

### Post by Qbert on 2022-06-23
Thank you for the reply.  I should have two disks, not three.  Ironically, I installed 22.04 to get the pastebin report, when I rebooted, it worked.  Of course I now have a new problem.  As stated I have two drives in the notebook, but when I click on the other drive in 22.04, it tells me it's encrypted and prompts me for a password.  I tried my log in password, but it does not work.  I installed Windows and the drive works normally, but when I put 22.04 back on, I got the password request again, though I had deleted the partition with the Windows disc before putting 22.04 back.  If I disable the the encryption will that get rid of the need for a password?  Thanks again.

---

### Post by tea for one on 2022-06-23
I'm not sure what the position is now?
You removed the drive with Windows/Bitlocker and Ubuntu 22.04 boots and functions OK (without continuous restarts)?

---

### Post by Qbert on 2022-06-24
Thank you for the reply.  Yes, my notebook functions normally, without restarts, but when I installed 22.04 to get the pastebin link, I had my second drive in the notebook.  I somehow managed to encrypt the second drive when installing Ubuntu, so that it now asks for a password I do not know when attempting to use it, which means I have no access to it.  

I'm pretty sure I've installed Ubuntu before without encrypting the drive, but those probably were NTFS partitions, not FAT, which is what I have on there now.  After I noticed the drive was encrypted and I could not gain access to it, I installed Windows on the notebook to see if I could get onto the drive, which I could.  I also attached the drive to my Windows via USB and it functioned normally.  I then deleted the drive using my Windows disc so I could ensure it was a completely fresh install.  When I put 22.04 back, it still asked for a password when trying to access the second drive, so it's still encrypted.  What I need to figure out is how to get rid of the encryption on the second drive?  If I just delete the drive and put it back, will that fix it?  I have backups of the files.  Thanks again.

---

### Post by ajgreeny on 2022-06-24
It sounds as if you might have inadvertently chosen the encryption option when installing 22.04.

I have never used encryption when installing but I think that unless you know the encryption password you will never get that OS to boot.
Assuming you can overwrite the new installation with a reinstallation I think this may be your best option.

Do you chose the full live desktop to install from when you install or do you ignore the "Try Ubuntu " option and go immediately to "Install"?
If you use the immediate Install option try the full live desktop first as it may give some better clues of problems.
However it does appear that the encryption is the problem which you will have to remove to be able to proceed further.

---

### Post by tea for one on 2022-06-24
> **Qbert said:**
> Thank you for the reply.  Yes, my notebook functions normally, without restarts
That's good news - Thank you for the clarification.
> **Qbert said:**
> I somehow managed to encrypt the second drive when installing Ubuntu, so that it now asks for a password I do not know when attempting to use it, which means I have no access to it.
That is somewhat unusual but, nevertheless, let's explore a bit.

Boot into Ubuntu
Attach the problem disk (if not already attached)
Open Disks (gnome-disk-utility)

Is the problem disk recognised?
If so, top right (3 vertical dots) will open the menu to format the disk.

Alternatively, you can boot into a live session and use gparted to create a new partition table/re-format the troublesome disk.

---

### Post by Qbert on 2022-06-25
Thank you both for the replies.  I'm not sure what I did, but I just deleted, and then remade the partition.  I put my files back and it seems to be working normally, so I'm now where I wanted to be when I started, upgraded to 22.04.  I probably won't have many questions until the next LTS version comes out in a few years.  Thanks again.

---

### Post by tea for one on 2022-06-25
If you are now satisfied with the outcome, it is helpful to other forum members/searchers to mark the thread as solved.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

