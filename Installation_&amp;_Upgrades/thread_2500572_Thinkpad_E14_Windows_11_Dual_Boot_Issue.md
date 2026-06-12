---
title: "Thinkpad E14 Windows 11 Dual Boot Issue"
date: 2024-09-05
forum: Installation &amp; Upgrades
---

### Post by rmbscotland on 2024-09-05
I am hoping for some help resolving this issue on a new Windows 11 Thinkpad E14.
I was aware of the issues with setting up a dual boot system and so followed the instructions in [Windows 11, version 23H2 known issues and notifications | Microsoft Learn]("https://learn.microsoft.com/en-us/windows/release-health/status-windows-11-23h2#issue-details")

System is Windows 11
Ubuntu 24.04.1 LTS

In summary, this is what I did:


[LIST=1]
[*]Disabled Secure Boot in BIOS
[*]Logged into  Ubuntu and opened a terminal
[*]Deleted the SBAT policy with: sudo mokutil --set-sbat-policy delete 
[*]Verified SBAT Revocations: with  mokutil --list-sbat-revocations   
Output: sbat,1,2021030218
[*]Rebooted the PC and logged back into Ubuntu to update the SBAT policy
[*]Rebooted and then re-enable secure boot in the BIOS.
[/LIST]
[FONT=inherit]
But When rebooted I got the error: Secure Boot Violation 
- On Selecting Continue the machine boots into Windows with no option for Ubuntu.


Any help or diagnostics to identify the problem would be really appreciated.


[/FONT]

---

### Post by tea for one on 2024-09-05
Disable Secure Boot again.
Does Ubuntu 24.04.1 boot successfully?

---

### Post by rmbscotland on 2024-09-06
> **tea for one said:**
> Disable Secure Boot again.
Does Ubuntu 24.04.1 boot successfully?

Yes, If i disable Secure Boot Ubuntu boots successfully.

---

### Post by rmbscotland on 2024-09-06
I just found something i found strange. The Microsoft instructions tell you to edit this reg key but it does not exist on my system [COLOR=#161616][FONT=SFMono-Regular]HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecureBoot\SBAT
I searched the Registry and SBAT is not there at all.

[/FONT][/COLOR]

---

