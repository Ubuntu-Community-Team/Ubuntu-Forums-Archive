---
title: "After Linux Install, Windows BSOD"
date: 2008-06-10
forum: Installation &amp; Upgrades
---

### Post by ArchCorsair on 2008-06-10
The other day i successfully migrated Hardy Haron 64bit from my 150gb to my new 500gb (where Vista 64bit used to reside) and tonight i attempted to install Vista 64bit again to my 150gb, installation goes by smoothly, but when the setup auto-reboots after the installation process the pc goes into a constant BSOD cycle. any ideas? I mostly need to access windows because i am overclocking my CPU and there are not any tools really available for linux to aid to that, but if you do know of some please let me know

thnx

---

### Post by hal8000 on 2008-06-10
> **ArchCorsair said:**
> The other day i successfully migrated Hardy Haron 64bit from my 150gb to my new 500gb (where Vista 64bit used to reside) and tonight i attempted to install Vista 64bit again to my 150gb, installation goes by smoothly, but when the setup auto-reboots after the installation process the pc goes into a constant BSOD cycle. any ideas? I mostly need to access windows because i am overclocking my CPU and there are not any tools really available for linux to aid to that, but if you do know of some please let me know

thnx


If youre overclocking your CPU then this will be done in your BIOS and so applies to Ubuntu (or any other OS) you are running.

Vista will overwrite the MBR so perhaps this is your problem, you don't say if grub is loading or whether ubuntu still loads. Either way this link may help:

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by ArchCorsair on 2008-06-10
Nevermind, I found the issue:

**Resolution:**
Since BSOD indicated error "0x0000007E" i automatically recognized this as a RAM related error, so i googled "0x0000007E ram" and what do you know, for certain chipsets vista has an issue with **storport.sys** and refuses to boot with 4GB of ram.

**_[SIZE="4"]Workaround:[/SIZE]_**
•	Remove 2 GB of RAM, and then restart the installation process. After Windows Vista is installed, reinstall the RAM.

If this fails resort to **Workaround #2**
Patch for this issue: [download here]("http://www.microsoft.com/downloads/details.aspx?displaylang=en&FamilyID=91672c7c-614b-404c-850c-377541e93c18")

---

