---
title: "Installing 64-bit Ubuntu over 32-bit 16.04"
date: 2016-12-25
forum: Installation &amp; Upgrades
---

### Post by aoniumo on 2016-12-25
I currently have 32-bit version of 16.04 LTS and would like to have a 64-bit OS instead because I would like to upgrade my chrome browser.

I don't have any data on the installation drive that will be lost, but I have no idea on how to start with this. I've upgraded from one 32-bit version to another and have not really done a clean install since 2013.

And just to clarify, my goal is NOT to upgrade from 32-bit to 64-bit per se. I would just like to do a clean installation of the 64-bit UBUNTU OS (16.04 or later) but initiate it inside my current 32-bit OS and just overwrite everything (similar to how one would do command line upgrade from one version to another).

Can anyone help with this? I've done some googling, but haven't found a way yet.

---

### Post by howefield on 2016-12-25
Not sure what you mean by "*initiate it inside my current 32-bit OS *". There was a blog detailing how to convert a 32 bit install to 64 bit but I am struggling to find the link to it for the minute.

The easiest method would be to boot from the new version live media and select "*Something Else*" at the partitioning stage of the install. Then mount your existing partitions which the 32 bit is installed on and mark for formatting. (Not marking / for formatting would leave your existing /home folder intact)

Are there any other operating systems on the machine ?

---

### Post by vasa1 on 2016-12-25
Something related here: [https://ubuntuforums.org/showthread.php?t=2341497](https://ubuntuforums.org/showthread.php?t=2341497) ?

---

### Post by RobGoss on 2016-12-25
Hello and welcome, depending on how old your machine is some machines will have the capability to run a 64-bit operating system, you will have to check the specs for your machine to see if it can handle the 64-bit OS, example I have a **Dell inspiron 531,** it had a 32-bit version of Windows 7,  I believe but had a 64-bit-capable processor which allow me to install a 64-bit ISo for Ubuntu mate which runs very well

I recommend if you are able to use the 64-bit version of Ubuntu just do a clean installation. I also know if your machine is in fact only able to handle the **32-bit ISO **of Ubuntu it will not allow you to boot into the Live session this is a simple way to know if 64-bit will install  

You can read about this using the link I provided below

[https://support.microsoft.com/en-us/help/15056/windows-7-32-64-bit-](https://support.microsoft.com/en-us/help/15056/windows-7-32-64-bit-)

---

### Post by aoniumo on 2016-12-25
I'm looking if there's a way to do a clean install of a 64-bit version of Ubuntu using a command line or other means (except CD, DVD, USB stick because I don't have those). My system supports 64-bit OS. I remember when I was just starting to use ubuntu, there was a way to do a fresh install of the same OS, reformatting the drive, overwriting the existing OS. It would be similar to overwriting a 32-bit Windows XP on a machine that supports 64-bit OS by installing 64-bit Windows 7 using a CD, which would reformat the drive and erase the 32-bit XP. Except what I'm looking for would not require a DVD, CD, USB stic, etc. because I don't have any of those.

---

### Post by Impavidus on 2016-12-26
I never tried this myself, but read this: [https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
So it appears you can boot the live disk directly from the hard drive using grub2.

But I have to say that a live usb is a very good tool to have in an emergency. It can rescue your system. It saved me once and it saved many people on this forum. As the cost of a small usb stick is only 1% of the cost of a computer, I don't see why anyone would not invest in one of those.

---

### Post by DuckHook on 2016-12-26
> **aoniumo said:**
> I'm looking if there's a way to do a clean install of a 64-bit version of Ubuntu using a command line or other means (except CD, DVD, USB stick because I don't have those)…My observation is not technical. Instead, it is practical. For technical help, vasa1 and Impavidus have already responded with good advice.

The first rule of upgrading is stated in bold in my signature. If you have any data that is of any value to you, then you must backup. But if you have no means of booting from USB or DVD, then this also means that you have no means of backing up. Ergo: you are already juggling a live hand grenade, never mind the utterly convoluted and arcane steps required in any of the solutions below. Are you prepared to lose all of your data and be left with a broken system? If so, then feel free to proceed with the steps that my compatriots have linked to.
> **vasa1 said:**
> Something related here: [https://ubuntuforums.org/showthread.php?t=2341497](https://ubuntuforums.org/showthread.php?t=2341497) ?The key link within this thread is: [http://www.ewan.cc/?q=node/132](http://www.ewan.cc/?q=node/132) which provides the instructions for finessing this death-defying upgrade magic trick. To be absolutely candid, I would not even attempt such a bleeding-edge and convoluted upgrade on my production machine without my data backed up ten ways to Sunday.
> **Impavidus said:**
> I never tried this myself, but read this: [https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
So it appears you can boot the live disk directly from the hard drive using grub2.Another ingenious solution. But the same warnings apply. In particular, unless your /home is in a separate partition, the linked method has the potential to wipe all your data. You can copy your /home to a separate partition now, but since everything is on the same HDD/SSD, a momentary lapse in concentration during install could destroy it all anyway.> But I have to say that a live usb is a very good tool to have in an emergency. It can rescue your system. It saved me once and it saved many people on this forum. As the cost of a small usb stick is only 1% of the cost of a computer, I don't see why anyone would not invest in one of those.+1

Only you can decide whether the cost of a USB stick is worth the potential heartache that will ensue from a failed upgrade. 16 GB USB sticks are on sale this week at my local computer store for USD$4. 64 GB are less than $20.

---

