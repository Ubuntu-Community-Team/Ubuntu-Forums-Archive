---
title: "Dual Booting Ubuntu Mate 16.04 &amp; Windows 10"
date: 2016-04-04
forum: Installation &amp; Upgrades
---

### Post by RobGoss on 2016-04-04
Hello everyone I have a question and I'm sure its been asked many times but here goes. I recently installed **Ubuntu 16.04** on a machine that also has Windows 10. 

When I install Ubuntu it did not give me the option to install alongside of Windows. I created a partition with about **150-GB** of space and installed Ubuntu on that partition, after everything was completed I restarted my machine and it booted straight into Ubuntu. 

Although I use Ubuntu on this machine 90% of the time I was thinking it might not be such a big deal fixing this as long as I don't have to uninstall Ubuntu and reinstall it again

Here's my problem, I have to go into my bios and chang the boot sequence in order to boot into Windows. 

For **Linux** my Bios is configured with **Legacy** so in oder for me to boot into Ubuntu it's has to be set to Legacy. 

For **Windows** my Bios is configured to **UEFI** so in order for me to boot into Windows my bios has to be set to UEFI.

From what I have been reading Ubuntu needs to be installed in the same boot order as Windows correct?

Question, how do I fix this to have the **GRUB** option to choose between **Windows or Ubuntu**,. I dont have the GRUB menu at all.

I was thinking maybe I can use **Grub boot loader repair disk** to fix this but I'm not sure because I never use it before. My system is running flawless and I hate to mess things up.

I been reading up on this and as far as I can see you are suppose to install Ubuntu on the same Bios setting as Windows is installed. I found this out after the fact but not sure how to fix it with out messing things up

Thank you for any help with this matter

---

### Post by oldfred on 2016-04-04
You probably should have installed Ubuntu in UEFI boot mode.
How you boot install media is then how it installs.

Do not run any fixes, and be sure to boot in UEFI mode.
 But may be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

After someone has reviewed that your install is otherwise normal, you may be able to use Boot-Repair's Advanced mode to uninstall grub-pc(BIOS) and install grub-efi-amd64(UEFI).

Of course good backups are always required before any major system changed.

---

### Post by RobGoss on 2016-04-04
Thanks Fred, So what you're saying there is a fix for this with out having to uninstalling Ubuntu again?

As far as backups I cloned my entire system so I'm not really worried about loosing data. I just did really want to reinstall Ubuntu 16.04 all over again being it's running so well

---

### Post by oldfred on 2016-04-04
Many have used Boot-Repair to convert if drive is gpt partitioned.
Best to see report to confirm current configuration.

---

### Post by RobGoss on 2016-04-04
Sounds good as always thank you for your help

---

