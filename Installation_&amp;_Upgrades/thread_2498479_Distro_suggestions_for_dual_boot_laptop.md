---
title: "Distro suggestions for dual boot laptop"
date: 2024-06-15
forum: Installation &amp; Upgrades
---

### Post by 13242rer on 2024-06-15
This is the 3rd time and the 3rd new laptop I have tried to install Ubuntu into as a dual boot system. 
Every time Ubuntu updates it maliciously corrupts or deletes a nonbitlocker'ed non-hybernating Windows 11 install on a separate SSD. Unbelievable for 2024 that Ubuntu would do this. 


Combined with Windows recall and co-pilot spying on everything and ubuntu not playing nice with any other SSD in a laptop- I have had it with computers.


What distro plays nice and doesn't require all sorts of grub editing/ command line black arts? 

I want plug and play no fighting while I need windows for some business applications. Any suggestions?

---

### Post by TheFu on 2024-06-15
Don't bother with dual booting. That's the TL;DR version.

Don't dual boot. Doing so, requires OSes to cooperate on boot choices.  MSFT isn't know for their great cooperation with anyone.  They use proprietary encryption that is actually pretty good, so how should any linux be able to work with it?  MSFT could provide the code to be a better neighbor on the hardware, but they haven't.  Any tools that might claim to work with BitLocker on non-MSFT OSes are reverse engineered as a best effort. Sometimes those things fail.

So, the only real options is to not use BitLocker at all or live with the occasional issues or manually do all updates or do like much of the world has done and use a hypervisor to run other OSes.  Boot issues with MS-Windows and Linux isn't new. They've existed since the early 1990s.  Usually it takes about a decade for non-MSFT OSes to figure out what they've changed ... just in time for MSFT to make a slight change and break everything.

I've been running MS-Windows inside a VM under different hypervisors since the late 1990s. Around 2008, I completely switched except for 1 laptop that was dedicated to MS-Windows only for work reasons.  Around 2012, my personal requirement ended to have MS-Windows boot on hardware. Since then, I've only had MS-Windows running inside a VM. It works very well for everything I do. I even ran a media center with Win7 inside a VM hosted on a Linux hypervisor.  

The only time I had issues running Windows under a VM was when either direct hardware connections were needed (specialized video recording adapters or for gaming when a direct GPU connection from MS-Windows was needed.  There are ways to make this possible (GPU passthru), but they aren't trivial to setup and require 2 GPUs in the system, since hardware passthru requires exclusive access to the hardware being passed through by the guest virtual machine.

But for normal productivity applications, none of this passthru is needed. The virtual GPU presented to each Guest OS (Linux or Windows) is absolutely fine for 99% of the uses. [https://mathiashueber.com/windows-virtual-machine-gpu-passthrough-ubuntu/](https://mathiashueber.com/windows-virtual-machine-gpu-passthrough-ubuntu/) is from 18.04, but I bet you can find a 22.04 version somewhere that isn't much harder.  Yep - [https://mathiashueber.com/passthrough-windows-11-vm-ubuntu-22-04/](https://mathiashueber.com/passthrough-windows-11-vm-ubuntu-22-04/)

Ah ... one more idea ... lots of people run their complete Linux system over a USB3 connection with an NVMe external enclosure.  I know 2 people doing this today and they've been doing it at least 4 yrs. Their Linux install doesn't touch the internal storage on the computer.  However, all the people that I know doing this use MXLinux.  That's a Debian-based, non-systemd version that uses APT still, so it wouldn't be too unfamiliar to most Ubuntu users.

---

### Post by oldfred on 2024-06-15
Only if you choose the install to full drive, should any Linux install erase Windows.
But if multiple drives, best just to disconnect Windows drive during install if not confident with SomeElse or manual install where you create & choose partitions for ESP & / (root), and optionally /home.

I prefer to create partitions in advance.
Use Windows tools to shrink Windows if installing on same drive and then create partition for / with gparted. You use same ESP - efi system partition.
If separate drive you can partition however you desire.

I installed Kubuntu to my Dell laptop with 11th Gen Intel chip. Worked great until I had to return to Dell as it would not charge or power up. First return both systems worked. Second return Kubuntu worked, but Windows would not. I think Dell forgot to update Windows Product code in UEFI to old motherboard's ID. Only Windows fix that worked was a total restore with Dell Image that erased Kubuntu.
Or I have had more trouble with Windows and Kubuntu.

I now have external SSD with Kubuntu that I use with that Dell and have used with 2006 system & desktop.

---

### Post by currentshaft on 2024-06-15
> **13242rer said:**
> This is the 3rd time and the 3rd new laptop I have tried to install Ubuntu into as a dual boot system. 
Every time Ubuntu updates it maliciously corrupts or deletes a nonbitlocker'ed non-hybernating Windows 11 install on a separate SSD. Unbelievable for 2024 that Ubuntu would do this. 


Ubuntu didn't "do" this. You did this by being careless during installation. To call it a "malicious corruption" is bordering on the absurd.

---

