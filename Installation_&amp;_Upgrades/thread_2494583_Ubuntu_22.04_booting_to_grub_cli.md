---
title: "Ubuntu 22.04 booting to grub cli"
date: 2024-01-20
forum: Installation &amp; Upgrades
---

### Post by sprx-77 on 2024-01-20
I had Ubuntu 22.04 installed on the main HD of my laptop, operating normally.  I installed Ubuntu 22.04 to a USB hard drive, using my laptop to have a second portable version.  I was running the installation media from a slash drive with Ventoy installed and booting to the 22.04 iso.  The install to the USB HD ran fine no errors.  I can plug in the USB and boot to it, I can still boot to the ventoy USB and a third USB with Windows 11 installed.  All the boot options are listed in the BIOS config (including the original ubuntu on the laptop HD).  With no other UDB drives plugged in, when I boot to the laptop HD, it goes to the grub menu

I tried some of the suggestions [here]("https://unix.stackexchange.com/questions/329926/grub-starts-in-command-line-after-reboot") with no luck.  I have also tried adding some of the other .efi files in the /grub/boot directory,  and am a little nervous about trying much more as I do not want to make things worse.  

The output of the boot repair is [here]("https://paste.ubuntu.com/p/SF9g2Rg8Bf/").

Any help would be appreciated.

---

### Post by oldfred on 2024-01-20
Report itself has several issues.
Not able to mount your zfs.
And it does not then show any operating systems?
You mentioned 3?

Did you run into this issue using Ubquity installer? Newer version now use Subiquity installer which will let you choose to install to external drive's ESP. 
But I use Kubuntu and just installed 24.04 and it still used Ubiquity and still has bug.
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
You have to have an ESP on external drive. And with UEFI be sure to use gpt partitioning.

Rerun report with zfs manually mounted & decrypted if that is issue. And all drives connected.

---

### Post by tea for one on 2024-01-20
> **sprx-77 said:**
> The install to the USB HD ran fine no errors.  I can plug in the USB and boot to it.
When you boot to this external USB, do you see a grub menu?
Is there a grub menu entry for the Ubuntu OS located on your internal nvme disk?

---

### Post by sprx-77 on 2024-01-21
> Did you run into this issue using Ubquity installer? Newer version now use Subiquity installer which will let you choose to install to external drive's ESP.
I am not sure about this, I installed from the latest ubuntu 22.04.3 iso

> Rerun report with zfs manually mounted & decrypted if that is issue. And all drives connected.
how do I mount the zfs manually?

---

### Post by sprx-77 on 2024-01-21
> [COLOR=#000000]When you boot to this external USB, do you see a grub menu?[/COLOR]
When I plug in the external HD's I can boot to them with not issue
> [COLOR=#000000]Is there a grub menu entry for the Ubuntu OS located on your internal nvme disk?[/COLOR]
How do I determine this?

---

### Post by tea for one on 2024-01-21
> **sprx-77 said:**
> How do I determine this?
Attach your external Ubuntu USB
Boot and display the grub menu
Do you see something like  - [COLOR="#0000FF"]Ubuntu 22.04 on /dev/nvme0n1[/COLOR]?

---

