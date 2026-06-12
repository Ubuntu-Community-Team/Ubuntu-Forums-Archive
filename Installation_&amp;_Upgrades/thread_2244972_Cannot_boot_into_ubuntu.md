---
title: "Cannot boot into ubuntu"
date: 2014-09-20
forum: Installation &amp; Upgrades
---

### Post by gamingpioneerr on 2014-09-20
Using universal usb installer, I put ubuntu on my usb, I also checked the format option. However, when I try to boot into the usb, nothing happens, it just gets stuck, no errors nothing. I also tried with Mint, the same story. What could be the problem?

---

### Post by fantab on 2014-09-20
More info about your machine. 
Is there a pre-installed Windows8 in the picture?
Is you machine allowed to boot from USB device?

---

### Post by gamingpioneerr on 2014-09-20
I have windows 8.1 already, and yes I can boot from USB.

---

### Post by oldfred on 2014-09-20
What brand, model computer and particularly what video card/chip?
Some require nomodeset or other boot parameters to work.

---

### Post by gamingpioneerr on 2014-09-20
A GTX 760, 8 gb RAM and a Phenom X4 965

---

### Post by fantab on 2014-09-20
In Windows8 have you disabled 'Fast Startup'? If not, then [disable fast startup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html").. Its nothing but hibernation, and when the pc is 'hibernating' it is not 'shutdown' even when you think you've shutdown the computer.
Also if there is an pre-installed SSD, then there is a chance that you have *Intel SRT*... this is a kind of RAID and can cause boot issues.
Check your UEFI menu and disable 'fastboot' if you see it.

I am assuming you know about UEFI and GPT.

If Windows is installed in UEFI then you must also install ubuntu in UeFI mode... 
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You will also have to make space for Ubuntu on your HDD... you can [**shrink**]("http://www.tweakhound.com/2013/01/02/how-to-resize-your-windows-8-partition/") one of the NTFS windows partition and make space... but don't create a new partition.
After you shrink the partition reboot Windows8 atleast a couple of times... if there are any filesystem errors Windows will fix it.

(Optional: This will be a good time to make a backup of your HDD, you can use any third-party Windows tools to do so, for instance you can use [Macrium Reflect]("http://www.macrium.com/reflectfree.aspx"))

Make sure you boot your Ubuntu dvd/usb in UEFI mode only, you should see the black menu screen: [see here]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_EFI_mode").

Install Ubuntu. When you are at the 'Installation Type' dialog confirm that grub is being installed to the ESP [Efi System Partition].

If you have any doubts regarding setting up your HDD then post the output of the following:
```
sudo parted -l
```
You can run this command in the Terminal [ctrl+alt+T] after you've boot your Ubuntu in 'Try Ubuntu' mode.

---

### Post by oldfred on 2014-09-20
With nVidia you also need nomodeset to boot live installer and first boot after install.

Since UEFI in both cases you need to manually edit grub menu.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

