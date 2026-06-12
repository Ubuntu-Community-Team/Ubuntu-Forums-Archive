---
title: "Ubuntu won't boot after installing..."
date: 2022-10-15
forum: Installation &amp; Upgrades
---

### Post by odlarhg on 2022-10-15
Hi, I'm new to linux and ubuntu.


I am trying to install from a live usb Ubuntu 22.04.1 LTS on a Core 2 Quad computer, but even though I follow all the steps of the installation, in the end when I restart the computer I am not able to complete the system boot. I always get a message "No bootable device -- Insert boot disk and press any key". I have already tried disabling USB booting in the bios but I did not achieve any positive result.


I assumed that installing from a live usb Ubuntu would configure the boot, but apparently this is not the case. What should I do to make the computer boot with ubuntu without problem? I will appreciate your help.

---

### Post by yancek on 2022-10-15
Did you download the iso from the Ubuntu site?  Did you do a checksum on the iso to verify the download?
Is Ubuntu the only OS on the computer?
Which installation option did you choose, erase disk and install ubuntu, install alongside, something else?
Is the computer UEFI capable?  If so, did you install UEFI?

---

### Post by ajgreeny on 2022-10-15
See **Boot Repair** in my signature below and follow the instruction there to run the **Boot- info** script.
**Do not run any default repair** but simply run the script and show us the pastebin link that will be given in the script.

---

### Post by odlarhg on 2022-10-15
Hi

Yes, I downloaded from the official ubuntu site and did the verification.
If ubuntu is the only operating system
I chose the delete and install option.
I installed from a live usb, I don't know if that's what you mean.


Thanks for the help.

Pd. Sorry if my English is not very good.

---

### Post by yancek on 2022-10-15
> No bootable device -- Insert boot disk and press any key" 

There are quite a number of reasons you might get that error.  I had it on a one month old laptop and it turned out to be a hardware problem, a connection on the motherboard.  Other possibilities would be not properly installing the Grub bootloader, a hardware failure, not setting the drive to first boot priority in the BIOS.  You did not answer whether you are using UEFI or Legacy?  Did you boot and install in UEFI or Legacy mode?  Did you set the drive on which you installed Ubuntu to first boot priority in the BIOS?  Did you accept the defaults for installing the bootloader (Grub)?

I would suggest you get boot repair from the link in post 3, use the 2nd option explained on the page to install it on the booted USB live Ubuntu and run it by selecting to Create BootInfo Summary.  Do NOT try to make any repairs.  Post the link you get when it finishes here to get help.

---

