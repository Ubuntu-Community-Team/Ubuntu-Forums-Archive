---
title: "Grub 18 Fix (sort of)"
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by tesseract420 on 2007-06-02
Parameters: Feisty, Intel 800 Mhz, 200 g hard drive


I had a power outage and when I came into work (where I have been happily using Ubuntu for nine months) I couldn't boot because I was getting the fsck error, i.e., asking to run fsck in maintenance mode and asking for the root password. The root password is supposed to be provided with the following syntax:

$sudo "your normal user password"

This did not work, despite the fact that there are lots of threads suggesting this, and suggesting that it does. For me, at least, it didn't.

If you resize a partition using Gparted, it will first fix errors on the drive. My partitions were OK--as far as I knew--so I resized the boot partition and fixed all the errors. Or so I thought.

I was able to boot back into my installation, but after about a half hour, the system became sluggish and finally froze, causing a need to reboot. I tried the update but the update manager would hang (another problem frequently commented on in the installation threads). Finally, just by trying over and over, I got the upgrade manager to work. I left it chugging away, getting ready to apply changes.

Sometime during the night, there was another power failure. The fsck error was back.

Since my data was already backed up (more or less) I figured that I would solve the problem by re-installing. I put in the new live cd (my original install was back in April) and installed the program. Upon boot:

GRUB ERROR 18.

I researched the threads which suggested that the problem is that you have to set LBA in the BIOS and some older BIOS's won't boot a drive bigger than 100 g. There's no place in my BIOS for LBA, I looked. I resized the first partition to 80 g. Rebooted:

GRUB ERROR 18.

I used the alternate install CD. After a while, same problem. I couldn't fix it. Nothing worked. I have noted that there is a thread on problems with the 2.6.20.16 kernel; a conflict between drives being listed as hda vs. sda. 

In any event, I could never get past the GRUB 18 error.

The solution (and it's not much of one) is that I downloaded Austrumi 1.50 live CD. I ran the live CD, no problems. I ran the installation. No problems. It's very fast.

If you run Austrumi, you may have trouble mounting your USB drive. The solution is to insert the drive, reboot, and you will find it under sda1 in the /mnt directory.

Now I could rescue the data that I hadn't 'sort of' backed up. While the Ubuntu live cd mounted the usb stick, I couldn't get any data onto it because the permissions weren't correct. CHMOD is a problem (because of my own admitted lack of familiarity with the command syntax), and there wasn't internet access for this operation.

After boot-up, the USB drive was there.

I'm not writing this thread to suggest Austrumi as an alternative over Ubuntu. But after despairing and going through about six installs, Austrumi saved the day. 

When they fix the kernel/GRUB error (if that's what it is) I'll go back to Feisty. Probably. 

If anyone has a REAL Grub 18 solution, please let me know.

---

