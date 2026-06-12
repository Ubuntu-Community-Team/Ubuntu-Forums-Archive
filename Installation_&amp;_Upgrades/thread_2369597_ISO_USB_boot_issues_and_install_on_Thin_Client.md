---
title: "ISO USB boot issues and install on Thin Client"
date: 2017-08-24
forum: Installation &amp; Upgrades
---

### Post by ssxt on 2017-08-24
EDIT: Burned ISO to DVD (used Win10's built-in burner) and it boots w/out issue from a USB DVD drive. Loaded Lubuntu 32-bit w/out any other issue. Why is tech STILL such a pain?:confused:


- Goal: Repurpose HP T610 Thin client w/Linux 'SMALL/Thin' distro that runs only RDP to Windows server. Thin client is x86 based and originally had Windows 7 embedded (Win7e) on the internal 16GB SATA Flash Module.

 - Downloaded lubuntu-17.04-desktop-amd64.iso, used ISO to USB and it boots but will not install - [COLOR=#000000]when trying to install @ the boot menu AND after loading to Lubuntu on the USB drive to install from the OS[/COLOR]. I get the somewhat common error: "[COLOR=#000000] " the 'grub-efi-amd64-signed' package failed to install into /target/. Without the GRUB boot loader, the installed system will not boot. "[/COLOR]

[COLOR=#000000]-  I've read multiple ways to fix this online, but most involve accessing the folder structure or modifying the partitions (add a 200MB partition @ the start??), which doesn't match what I'm seeing in the Lubuntu partition install section, and I get another error that the partition won't work....and I'm admittedly very ignorant about all Linux commands/processes and don't know HOW to access the folder structure.[/COLOR]

 - So, I gave up and tried the 32-bit version......more issues.

[COLOR=#000000]2nd Issue but related:[/COLOR]
[COLOR=#000000]- I've ALSO downloaded the 32-bit version: [/COLOR]lubuntu-17.04-desktop-i386.iso.  This won't boot from the USB @ all. I get an error that it can't load from the USB drive. I've used ISO to USB, Tuxboot, and just copying the extracted files (used 7-Zip) directly to the USB  - as recommended on here. But just to reiterate - I DID THIS THE SAME WAY AS WITH THE 64-bit ISO.

[COLOR=#000000] - I've also tried two other 32-bit Linux distros and neither of those will boot either.

- I've tried two other USB sticks w/different brands - 8gb and 16gb - and neither of those will boot.

 - I've tried two other PCS; one is another T610 TC and also an HP PC....they'll also boot the 64-bit but not 32-bit.

 - I've tried other USB ports.

 - Just to verify it's not a HW issue, I reloaded the Win7E on the USB and it loads normally.

- I Downloaded all the files again, from a different network, and get the same issue - won't boot.

There's something going on w/the 32-bit versions?? 

Is there a way to just copy the 'OS' portion from the 32-bit to the 64-bit install since it boots  from the 64-bit, and then it'll load the 32-bit?
[/COLOR]

---

### Post by BenginM on 2017-08-24
Hiya , So the problem is with the usb not bootable! , since you have a MS Windows you may wish to try [https://rufus.akeo.ie/](https://rufus.akeo.ie/)

---

