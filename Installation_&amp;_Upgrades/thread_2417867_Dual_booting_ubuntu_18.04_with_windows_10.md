---
title: "Dual booting ubuntu 18.04 with windows 10"
date: 2019-04-28
forum: Installation &amp; Upgrades
---

### Post by wvp2 on 2019-04-28
Hi all,

I want to dual boot ubuntu 18.04 with windows 10. 
My installation of ubuntu is on my main m.2 ssd, and windows is installed on a seperate ssd.
I have tried setting up grub via ubuntu to be able to choose the os on boot, however this menu never shows up.

I am using this grub config:
> 
GRUB_DEFAULT="0"
GRUB_TIMEOUT_STYLE="hidden"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


I have done a complete boot repair ( [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) ) and both ubuntu and windows boot properly.
Am i supposed to press a button on boot? In that case I might as well get rid of grub and use the bios option.

Thanks

[URL="https://help.ubuntu.com/community/Boot-Repair"]
[/URL]

---

### Post by oldfred on 2019-04-28
You have to have grub, it is both the boot manager (menu) and boot loader (required).
You can boot from UEFI if desired.
And grub only boots working Windows, or Windows that is not hibernated.

If issue, do not post link to Boot-Repair, we know that. But what we want to see is the link to the summary report it creates, if you have issues.

---

### Post by wvp2 on 2019-04-29
Thanks for pointing me to that thread, however this doesn't help me very much. I already have both windows and ubuntu installed and am using ubuntu as main OS.
Should I completely remove ubuntu and start from windows and follow that guide, or is there still a way i can dual boot having ubuntu as primary OS?

---

### Post by Rubi1200 on 2019-04-29
What oldfred meant was that you should boot using a liveCD/USB and not repair anything. Instead create a summary report to post here so we can advise further.

The link is in my signature.

Thanks.

---

### Post by DAVID_LECKIE on 2019-04-29
I have a very similar setup working OK.
Make sure you have Fast Boot off in your BIOS settings
Before I switched fast Boot off I had similar GRUB issues

By the way the app "Grub Customizer" makes life much easier when selecting which OS is the default.
Dave

---

