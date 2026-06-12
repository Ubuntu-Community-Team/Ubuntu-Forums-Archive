---
title: "Ubuntu dual boot with Windows 10 issues"
date: 2015-12-13
forum: Installation &amp; Upgrades
---

### Post by Zackary_Remillard on 2015-12-13
Hello, I was trying to dual boot ubuntu onto my pc earlier through the USB booter and I came across some issues. While going through some of the threads here I understand the the UEFI that is in Windows 8 and 10 will give users issues when trying to dual boot any version of linux onto their pc. I had read something of turning off legacy, and navigating to the EFI rather than UEFI might aid in solving some of those issues. While still in UEFI I had turned off the legacy adapter (The description had told me that it might disable some USB functions in another OS, but I figured I'd just fix it later if some issues arised) as well as switching the booter from UEFI to CSM. I really should have just kept searching more rather than getting so ahead of myself, as now my pc will not boot anything. When I turn it on it tells me that there is no bootable device, to insert boot disk and press any key to continue. How might I be able to bypass this , or have a temporary fix until I am able to somehow load windows again?
Thanks much!

---

### Post by oldfred on 2015-12-14
You posted as [Solved], so are you asking a question or is issue resolved and you do not need any help?

With UEFI, sometimes systems lock up and you have to cold boot or totally power down. If laptop also remove battery. And hold power switch for 10 sec or so to drain all power. Then on reboot immediately press correct key for your system to get into UEFI/BIOS.

You have to have UEFI/BIOS set for correct mode. 
Your UEFI has two entries to boot a flash drive normally if secure boot is off. One is UEFI and the other BIOS. If secure boot is on, you may only see UEFI (with secure boot). How you boot flash drive is then how it installs. But if you install in BIOS mode but have Secure boot on you have locked system as it only boots in UEFI with Secure boot. So make sure default UEFI boot matches the way you have installed.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

