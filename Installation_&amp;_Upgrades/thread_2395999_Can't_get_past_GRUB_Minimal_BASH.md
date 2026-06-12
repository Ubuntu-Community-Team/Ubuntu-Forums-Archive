---
title: "Can't get past GRUB Minimal BASH"
date: 2018-07-09
forum: Installation &amp; Upgrades
---

### Post by longitude on 2018-07-09
Hello! I'm new to Linux and decided to try installing Ubuntu from a live USB. Yesterday, I installed Ubuntu in the BIOS version by accident, so I tried deleting my Linux partitions and GRUB. I really want to get through the installation, so I tried to do it in UEFI this time so that both Windows and Linux could be in UEFI mode. It went fine, but when I restarted my laptop, I got a black screen that says:
 **"Minimal BASH like line editing is supported. For the first word,  TAB lists possible command completions. anywhere else TAB lists  possible device or file completions.**"

I've looked around some forums and I've tried the boot repair solution, but boot repair tells me it's fixed and I get the same screen when I try to reboot. 

I can get back to Windows using the fourth comment’s suggestion here: [https://unix.stackexchange.com/questions/259069/how-to-start-a-windows-partition-from-the-grub-command-line](https://unix.stackexchange.com/questions/259069/how-to-start-a-windows-partition-from-the-grub-command-line)

I'm thinking that I didn't properly delete/update GRUB, so it can't find my files. My idea is that uninstalling and reinstalling GRUB might work, but I have no idea how to go about doing that... Is there any way to repair this? Help would be greatly appreciated! I don't know what information might be useful, but I'll gladly provide it if asked :)

---

### Post by paranoidcoder on 2018-07-09
It's very odd you mention this. I have been using Linux for years, and I just stumbled onto this issue today and have been severely stumped. I have reset all of my UEFI/BIOS settings to optimized defaults and formatted all my drives and I still run into this issue. I have also tried several USB's, at least one of which I have used successfully for an install previously.

EDIT
There's another thread with the same issue: [https://ubuntuforums.org/showthread.php?t=2395995](https://ubuntuforums.org/showthread.php?t=2395995)

What I have tried:
- Tested 2 different flash drives, one of which I have used to install on my system previously
- Restore UEFI/BIOS defaults
- Disable secure boot/fast boot
- Unplug all drives other than destination drive
- Ensure the UEFI Ubuntu install option is booted
- Perform a "Normal install" without downloading updates or extra packages

---

### Post by powerjas on 2018-07-09
I'm having the same issue.

Got a new to me Lenovo T470 and thought it was something with the uefi settings in the bios. 

I have tried both ubuntu and kubuntu same result install go fine no errors, when it reboots it only boots to the grub> prompt and I can't go any farther.

I can get the following distros installed on it with no issue
elementary OS
fedora
manjaro

---

### Post by powerjas on 2018-07-09
I just tried 16.04 and it installed with out any issues, there is something going on with the current installer for 18.04 versions.

---

### Post by oldfred on 2018-07-10
@paranoidcoder & powerjas     
Please do not hijack someone else's thread. Boot issues almost always are unique. If solution works here & also for you that is great, but probably best to run Boot-Repair and start your own thread with the Summary report.

@longitude
       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

While Boot-Repair or its advanced options usually can repair system if just a Linux boot issue, often best to have someone review report. There may be other issues or fixes needed first.
You can reinstall grub from live  installer, or using Boot-Repair.

---

### Post by paranoidcoder on 2018-07-10
Try and install without any internet access, so no WiFi or ethernet. That seems to be causing my issues. I was able to install without internet access successfully, followed by a failed installation with internet access, and then yet again a successful installation without internet access.

---

### Post by longitude on 2018-07-10
Hey, thanks so much for the replies! I decided to try @paranoidcoder's suggestion and then @oldfred's if it didn't work as soon as I woke up today. Luckily, re-installing without wifi worked like a charm!

---

### Post by paranoidcoder on 2018-07-10
No problem @longitude, glad I could help. Hopefully this issue is resolved soon as I can see this affecting a ton of people.

---

### Post by oldfred on 2018-07-10
@paranoidcoder
Please post link to your bug report and try to get others with same issue to add to it. I will also when I see that issue.
With only one user, issue is often ignored. With 2 at least someone looks at it. And often need 5 or more before it becomes a priority.

---

