---
title: "Kubuntu on ThinkPad E595 sometimes doesn't boot, stuck in BIOS BOOT menu"
date: 2020-11-22
forum: Installation &amp; Upgrades
---

### Post by uxr2 on 2020-11-22
Hello,
Sorry if this issue is already solved but I couldn't find what I am looking for. 
 
The  issue is, SOMETIMES, after choosing to restart and while rebooting, my  system just waits in Boot Menu. Choosing any of those 3 options (shown in picture) only  refreshes this screen.
[ATTACH=CONFIG]287414[/ATTACH]
[ATTACH=CONFIG]287415[/ATTACH] 


When this happens, I turn my  computer off and turn it on back and it works. Then it boots and asks  for password, loads desktop etc.

 
Kubuntu is installed on my SSD, and I have an HDD which doesn't contain any bootable stuff.

 
Operating System: Kubuntu 20.04
KDE Plasma Version: 5.18.5
KDE Frameworks Version: 5.68.0
Qt Version: 5.12.8
Kernel Version: 5.4.0-54-generic
OS Type: 64-bit
Processors: 8 × AMD Ryzen 5 3500U with Radeon Vega Mobile Gfx

Memory: 13,6 GiB

---

### Post by oldfred on 2020-11-22
That is warm reboot and cold boot.
UEFI has a setting for fast boot which assumes no system changes. Then it is booting old configuration.
But once you cold booted it should have updated configuration, so next warm boot should work.
But check UEFI settings.

Have you updated UEFI?
And if SSD, SSD firmware.
Not update to UEFI may reset some settings, so you have to redo them. I keep a list.
With UEFI some settings are remembered, back with BIOS, everything was reset to defaults.

---

### Post by uxr2 on 2020-11-22
> **oldfred said:**
> That is warm reboot and cold boot.
UEFI has a setting for fast boot which assumes no system changes. Then it is booting old configuration.
But once you cold booted it should have updated configuration, so next warm boot should work.
But check UEFI settings.

Have you updated UEFI?
And if SSD, SSD firmware.
Not update to UEFI may reset some settings, so you have to redo them. I keep a list.
With UEFI some settings are remembered, back with BIOS, everything was reset to defaults.

Hello @oldfred thank you for your reply.

I have never updated by SSD firmware but I updated BIOS a couple months ago. It is the latest version 

As soon as I saw your reply about warm reboot and cold boot, i immediately restarted my ThinkPad.
The first try it was flawless. This video shows how it works without any errors: [https://youtu.be/Betz2IVEF9s](https://youtu.be/Betz2IVEF9s)
But I kept restarting it, and computer "failed to find SSD" again.
I am uploading some pictures I was able to capture, some of them show my BIOS/UEFI settings

This is cold (re)boot:
[ATTACH=CONFIG]287417[/ATTACH][ATTACH=CONFIG]287418[/ATTACH]

This is warm reboot:
[ATTACH=CONFIG]287419[/ATTACH]

---

### Post by uxr2 on 2020-11-22
I have my UEFI settings as follows

[ATTACH=CONFIG]287422[/ATTACH][ATTACH=CONFIG]287423[/ATTACH][ATTACH=CONFIG]287424[/ATTACH][ATTACH=CONFIG]287425[/ATTACH][ATTACH=CONFIG]287426[/ATTACH]

---

### Post by oldfred on 2020-11-22
I do not know AMD and if that has any unique issues.

But try with UEFI Secure Boot off and still in UEFI boot mode. Do not turn legacy/BIOS/CSM mode on.

---

### Post by uxr2 on 2020-11-22
> **oldfred said:**
> I do not know AMD and if that has any unique issues.

But try with UEFI Secure Boot off and still in UEFI boot mode. Do not turn legacy/BIOS/CSM mode on.

Thank you for your reply. oldfred You have been great help, thanks a lot.

I have turned UEFI Secure Boot off now, and I will use it like this from now on. Let me see if the issue will repeat. I will update this thread in couple of weeks.


I think you are kind of sure about this issue is not related to Ubuntu, is it probably SSD firmware? What do you think is wrong? Should I contact Lenovo or SSD devolopers?

---

### Post by CelticWarrior on 2020-11-22
The "boot mode" setting is unusual but probably means the following:

Quick = Fast Boot
Diagnostics = Normal Boot

---

### Post by uxr2 on 2020-11-26
> **oldfred said:**
> I do not know AMD and if that has any unique issues.

But try with UEFI Secure Boot off and still in UEFI boot mode. Do not turn legacy/BIOS/CSM mode on.

I have been using these settings and I can say that problem is still there.

---

### Post by uxr2 on 2020-11-29
I installed Windows 10 on my SSD, checked for firmware and Bios/Uefi updates but it was all up-to-date. Restarted for several times to see if warm-boot fails. Nope
Then I installed Ubuntu on my HDD. Working with dual boot. Now I can restart it as much as I want. &#128517;

---

### Post by uxr2 on 2021-04-08
Replaced ATA HDD with ATA SSD (Samsung EVO), and it still behaves the same, can't do warm-boot

---

