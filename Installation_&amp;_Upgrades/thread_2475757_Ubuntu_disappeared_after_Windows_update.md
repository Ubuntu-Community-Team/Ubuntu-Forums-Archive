---
title: "Ubuntu disappeared after Windows update"
date: 2022-06-07
forum: Installation &amp; Upgrades
---

### Post by 07danielx on 2022-06-07
Hello. Ubuntu has disappeared along with GRUB after a Windows update. I didn't find it in BIOS either, so I assumed I lost it. Searching for information, I found that GRUB could be repaired. Hoping for that, I installed Boot-Repair on a Ubuntu Live, but when using it, I ran into this error. 

[IMG]https://i.pinimg.com/originals/13/35/cd/1335cd97bce35043039942310d667033.jpg[/IMG]

Accepting everything, I decided to install Ubuntu again. However, when installing I ran into this. 

[IMG]https://i.pinimg.com/originals/46/a0/1d/46a01d94b8589358b48be828b4cf4e5e.jpg[/IMG]

Taking a risk, I decided to follow the first option, instead of the last one where I choose partitions. I followed the first option, because it gave me a little hope that maybe all was not lost. However, I found this error.

[IMG]https://i.pinimg.com/originals/87/46/6f/87466f2ab5838df2d6feaf32187275f4.jpg[/IMG]

What should I do?

---

### Post by tea for one on 2022-06-07
> **07danielx said:**
> What should I do?

Boot into a live session, download and install the boot-repair utility.
This time, run the software and upload the report to pastebin.
Put the pastebin link in your next reply so that forum members can peruse the report and provide advice.

---

### Post by yancek on 2022-06-07
Before reinstalling, did you try to disable Secure Boot in the BIOS firmware as suggested by boot repair?  If so, what was the result?

The message you got from boot repair about no EFI partition makes me wonder what windows version you are running.  Was your windows install an EFI install?

---

### Post by grahammechanical on 2022-06-07
NVRAM = Non-Volatile Random-Access Memory. I found this description of what it is for:

> Computer manufacturers mainly use NVRAM **to hold information about the state of the computer for faster boot times**.  This allows information about the components and devices in the  computer to be stored from one use to the next while the system power is  turned off.

I guess that it is the integrated circuit that holds the UEFI settings information. Boot Repair likes to access that information but it cannot access that information because secure boot is on. This is my guess.

I do not run Windows but I have seen in many forum posts that a Windows update will re-activate Windows fast startup. This needs to be disabled for Ubuntu to load. Windows fast startup is a form of hibernation and I think that Linux cannot read a drive that holds Windows that is in hibernation. This could be the reason that the Ubuntu installer is saying that it could not find a EFI system partition. You are choosing to re-install Ubuntu therefore the installer will expect to find an existing EFI system partition which in fact it cannot see because of Windows being hibernated.

Regards

---

### Post by debian-is-powerful-gcc on 2022-06-12
Do you install Ubuntu with the partition manager and you create differents partitions? If is a yes, you are going to install again Ubuntu, then, format the others partitions except home, and that's all, all it's going to work

If doesn't work,  try creating a EFI partition, I remember that I could be easy because the installer via partitions has it

---

