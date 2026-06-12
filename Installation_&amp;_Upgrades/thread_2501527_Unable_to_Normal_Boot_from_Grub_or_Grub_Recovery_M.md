---
title: "Unable to Normal Boot from Grub or Grub Recovery Mode"
date: 2024-10-11
forum: Installation &amp; Upgrades
---

### Post by SpikeLS6 on 2024-10-11
I run a dual boot system with Ubuntu on one drive and WIN 10 on the 2nd drive. I do not mix them.
    24-10 Upgraded loaded but only comes up with a blank, black screen, either with a normal 6.11 boot or a 6.11 Recovery Boot. The Mouse arrow sometimes works in some parts of the display.

I have tried SUDO APT Grub Repair, SUDO Apt get dist-upgrade, and SUDO apt Clean. I still only get a blank, black screen.

What else can I try?

Michael

---

### Post by yancek on 2024-10-11
I don't know what you expected with Grub repair as a command.  I doubt it will do anything.  Are those typos or have you actually been using uppercase for sudo which won't work.  How about posting some information on your hardware, specifically graphics since that seems to be a problem.  24.10 was released yesterday so you can expect a variety of problems in the first months after a release.

You indicated you upgraded, which version did you have on earlier?

---

### Post by SpikeLS6 on 2024-10-12
Went back into Recovery and did the previous three commands in lower case with no change in results.
Using a AMD Ryzen 7 processor with GForce GTX-650 Video Card.
Windows 10 H2 will come up from second hard drive.
Tried going back to version 6-8-0-45, but still get the same black screen results.
I was on Ubuntu 24-04 with no problems.
What additional information can I provide?

---

### Post by yancek on 2024-10-12
Unless there is a problem using a long term release such as 24.04 or this is new software available on a newer release, there isn't any point in going to a short term release like 24.10.  As I pointed out above, upgrading on the first day of a short term release is generally pretty risky as there will often be bugs.

Is Ubuntu and EFI install?  Do you see these problems when trying to boot it from the BIOS UEFI boot  menu?  You could go to the boot repair site and download it from your Ubuntu installation USB and use the 2nd option explained and the Create BootInfo Summary option.  Do not try to make any repairs, just post the link here.

  [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by SpikeLS6 on 2024-10-12
Opened Recovery from a boot repair USB changing the BIOS to load it first. Then used the following commands:
   sudo add-apt-repository ppa:yannubuntu/boot-repair
   sudo apt-get update
   sudo apt-get install -y boot/repair && (boot-repair &)
The last command gives me an  error of: xhost:  unable to get display ""
Could not get the summary report to produce a result.

---

### Post by SpikeLS6 on 2024-10-12
By the way, is there a way to revert back to 20-04 LTS and just stay there until the next LTS? May be next alternative. I have files backed up on Deja Vu in Ubuntu.

---

### Post by oldfred on 2024-10-12
Do not use Boot-Repair ISO which often is not as current as ppa version, but Ubuntu ISO you used to install Ubuntu and add Boot-Repair to it using ppa.

---

### Post by SpikeLS6 on 2024-10-12
OK. Unfortunately I used the normal Software Upgrade when I installed 24-04 and 23-10. I do not have the Ubuntu ISO I used to install them.
   How are the commands to add the ppa file from the Recovery Terminal?

---

### Post by SpikeLS6 on 2024-10-12
Downloaded the 24-10 AMD Image and tried to bring it up from the USB. Looked at the same screens as before until the black blank screen. Are their further commands I could try once I get into the Recovery Terminal?

Or should I use the 24-04 LTS Image?

---

### Post by oldfred on 2024-10-12
With nVidia, you have to use the Safe boot option for vvideo to work.
And then when installing choose the optional restricted extras to get the correct nVidia driver installed.
You can install driver after Ubuntu install, but have to boot grub's recovery mode to terminal & install it ther as gui may not work or if it does, very low quality default mode.

---

### Post by SpikeLS6 on 2024-10-12
I am way over my head now. What is a Safe Boot and how do I do that? Not sure I am up to this.

---

### Post by oldfred on 2024-10-12
I install Kubuntu and do not have nVidia.
They used to have a grub menu with a second option for safe boot for those systems that have driver issues.
Looks like they have a work around to boot, anyway.

[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

---

### Post by SpikeLS6 on 2024-10-14
Thought about upgrading to WIN 11 on the other SSD, but the motherboard is over 10 years old and not capable. Need new tower and motherboard to which Ubuntu 24-04 can be installed and I'll recover the Deja Vu back up when it comes home.

Please consider this thread as SOLVED, albeit the hard way.

Thank you for all your help!

Can not find the Thread Tools to  mark it as SOLVED.

---

