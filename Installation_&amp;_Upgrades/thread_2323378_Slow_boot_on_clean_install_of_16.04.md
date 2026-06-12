---
title: "Slow boot on clean install of 16.04"
date: 2016-05-04
forum: Installation &amp; Upgrades
---

### Post by benn333 on 2016-05-04
Hello, I just installed a clean copy of Ubuntu 16.04 on a self-built system (specs below) and the system has a long pause while booting. Looking at dmesg, the delay occurs at the following point:

[    3.302920] clocksource: Switched to clocksource tsc
[   93.164531] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)

I'm not sure which item is causing the delay, but I haven't been able to pinpoint any issues with either. I've also tried utilities like "systemd-analyze blame" but nothing shows up taking more than a second or so to run. 

I previously had 14.04 installed, which booted in roughly 8-10 seconds. I reinstalled it early on just to check and it still booted quickly. Curiously, I tried 15.10 too and it also was slow to boot.

Any ideas what could be causing this?

-----------
Specs:
intel dq77kb board
intel ivy 3220T cpu
8gb ram
Samsung 830 128gb SSD

---

### Post by benn333 on 2016-05-05
*Bump*

Any suggestions on how to troubleshoot this further? Are there other logs that might give me more insight as to the cause?

---

### Post by oldfred on 2016-05-05
Why are you still getting dmesg?
With my 16.04, it is blank and it was only my older installs with upstart that recorded the data there.
I think I did see someone with 32 bit Ubuntu that still had dmesq?

Are you using UEFI or BIOS?
I doubt this will show anything.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by benn333 on 2016-05-05
I'm not sure why I'm still getting dmesg. I didn't tweak anything that I can think of to get it reporting there.
I am running the 64bit Ubuntu though.

I'm using a BIOS.
Here is my BootInfo summary report:
[http://paste2.org/ptDzLCvA](http://paste2.org/ptDzLCvA)

---

### Post by oldfred on 2016-05-05
It must be because of BIOS boot as I have UEFI boot.

Do you have AHCI on in UEFI/BIOS settings.
And I think most if not all the Intel advanced settings should be off.

If only booting Ubuntu, I also suggest you eventually plan to convert to gpt partitioning. You can boot Ubuntu in BIOS or UEFI from gpt if you have bios_grub or ESP - efi system partition. I converted to gpt years ago, as I knew eventually I would get to a newer UEFI system. The only issue with gpt is Windows only boots in BIOS mode from MBR, so those dual booting Windows in BIOS mode must use MBR(msdos) partitioning.

---

### Post by benn333 on 2016-05-05
I can try disabling any advanced settings in the BIOS, as it's always possible something in there is slowing things down. (AHCI is on.)
They didn't give me any trouble in 14.04 though, so perhaps it's related to the switch from upstart to systemd.

There was one change I made in the BIOS when installing 16.04, based on an error message when booting from USB:
tpm_tis 00:06: A TPM error (7) occurred attempting to read a pcr value
The Trusted Platform Module was disabled, so I enabled it and the error went away.

I'll report back over the weekend, as tweaking the BIOS isn't something I can easily do over VNC. 
This is a "headless" HTPC so I'll have to take it down to plug in a keyboard.

---

### Post by echotech2 on 2016-05-06
> **oldfred said:**
> It must be because of BIOS boot as I have UEFI boot. 

  FWIW - I BIOS boot, this older machine has no UEFI capabilities.  I have DMESG available.

---

### Post by benn333 on 2016-05-07
Sure enough, it turned out to be a setting in the BIOS. 
Apparently the "Secondary LAN" feature was the culprit (the board has two NICs) and once disabled it booted normally.
Boot time is down to 6 seconds now, according to dmesg.
Three of those seconds are waiting for Bluetooth, but I can't be bothered to address that; the TV takes longer to boot.

---

