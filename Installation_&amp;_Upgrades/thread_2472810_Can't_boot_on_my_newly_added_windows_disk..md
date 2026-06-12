---
title: "Can't boot on my newly added windows disk."
date: 2022-03-13
forum: Installation &amp; Upgrades
---

### Post by davsim on 2022-03-13
[SOLVED]

Hi, 
Feeling a bit sorry to ask for help but it s been a week of tries so i m out of options.

Here is my boot sum: [https://pastebin.ubuntu.com/p/w9m2X7s87h/](https://pastebin.ubuntu.com/p/w9m2X7s87h/)

I just want to be able to choose to boot on windows or Ubuntu.

Please help...

Thank you in advance if you invest even a little of your time looking at my problem.

---

### Post by grahammechanical on 2022-03-13
What messages did you see and do you see when you run this command from Ubuntu?

```
sudo update-grub
```

Regards

---

### Post by davsim on 2022-03-13
Here it is. (thanks for caring ^^)

sudo update-grub
[sudo] password for simdav: 
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.13.0-35-generic
Found initrd image: /boot/initrd.img-5.13.0-35-generic
Found linux image: /boot/vmlinuz-5.13.0-30-generic
Found initrd image: /boot/initrd.img-5.13.0-30-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done

---

### Post by tea for one on 2022-03-14
You have both Ubuntu and Windows 8 or 10 installed in older BIOS mode?

The modern (easier to manage) way is to have both systems installed in UEFI mode with GPT.
Would you consider re-installing both systems to be more future-proof?

As you have two disks, each OS in UEFI mode with GPT can be managed independently.

---

### Post by oldfred on 2022-03-14
I also suggest reinstall in UEFI boot mode to gpt partitioned drives.

But can you install a Windows boot loader to sda? And then boot Windows? And make sure Windows fast start up is off?
Grub only boots working Windows & that includes Windows cannot be hibernated. Fast Start up sets hibernation flag on all NTFS partitions.
Then try the update to grub again.

---

### Post by davsim on 2022-03-14
Ok thanks a lot. 
I m on my way to a complete re-install of my system in  UEFI boot mode with gpt partitioned drives...
I come back to you after that.

---

### Post by tea for one on 2022-03-15
When installing each OS on a separate disk, it is a good practice to only have the [COLOR="#0000FF"]target[/COLOR] disk accessible.
After you have installed your first OS and are happy that everything is OK, power off the PC and de-activate, isolate or physically remove the drive.
Therefore, the second OS will automatically be configured with an [COLOR="#0000FF"]E[/COLOR]FI [COLOR="#0000FF"]S[/COLOR]ystem [COLOR="#0000FF"]P[/COLOR]artition.

Each drive with an ESP allows independence if one or the other systems misbehave in the future.

---

### Post by davsim on 2022-03-16
I just refaced that problem again... My windows was running perfectly on the nvme. I plus the other disks and then.... Bam brug want to do the booting, doesn t find linux and My Windows doesn t boot anymore too...
I m gonna re/re instal once more and comme back to you after the dust settles.

---

### Post by oldfred on 2022-03-16
Make sure both are in UEFI boot mode. How you boot install media, is then how it installs.

Thisb report will show if boot issue.
Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by davsim on 2022-03-16
I m gonna go through all that on the weekend. 

Thank a lots for your  concerns, I almost got myself thinking about not installing ubuntu and do a thumb drive of it.
Coming back for new on the weekend.

---

### Post by oldfred on 2022-03-17
Full install in UEFI mode has a minor issue, that can be major if you want to use an external drive on any other system.
Ubuntu's Ubiquity installer only installs grub bootloader to first drive's ESP.
Be sure to partition in advance to have an ESP on external drive.

Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26)
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall of grub to correct drive.

---

### Post by tea for one on 2022-03-17
> **oldfred said:**
> Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.

This is my preference every time.
If only one drive is accessible, then the Ubuntu installer will add the EFI partition automatically.

You can add other systems to Grub later if you wish.

---

### Post by davsim on 2022-03-19
:KS Thanks a lot. I redone everything following what you said and I worked.

I m now searching how to tag Solve on this thead

---

### Post by tea for one on 2022-03-19
Good news that everything is now OK.
Here is the info to mark a thread as solved.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

