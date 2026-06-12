---
title: "My ubuntu boot option disappear after I'm shutdown in Windows 11"
date: 2024-07-30
forum: Installation &amp; Upgrades
---

### Post by imbios-dev on 2024-07-30
My ubuntu boot option disappear after I'm shutdown in Windows 11, I found this [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) and it suggest me to share my pastebin here:
[https://paste.ubuntu.com/p/WjDhcwC9cC/](https://paste.ubuntu.com/p/WjDhcwC9cC/)

---

### Post by imbios-dev on 2024-07-30
[https://paste.ubuntu.com/p/xTzgpPjdT6/](https://paste.ubuntu.com/p/xTzgpPjdT6/)

here's the report when I apply recommended repair

---

### Post by yancek on 2024-07-31
You're a little bit vague about your situation.  Did you actually have a functioning installation of both Ubuntu and windows 11 and were you able to boot successfully from either and did you do this from the Grub menu?

Your first boot repair shows that you have windows boot code in the MBR of the device (Line 5) and it also shows you have an EFI partition (Lines 15-26) which has the required EFI files to boot windows.   If you look through that section of the report, you will see there is NO reference to any Ubuntu files so Ubuntu will not boot UEFI.  

Line 131 shows that you r hard drive is a GPT drive which would mean that windows MUST be installed in UEFI mode which it is.  Ubuntu can be installer either Legacy or UEFI but since both systems are on the same drive, you need Ubuntu installed in UEFI mode which it is not.  Look  at boot repair starting at Line 95 which shows UEFI options.  There is not reference at all to Ubuntu.  Out of curiosity, what's with the Linspire entry on Line 103?

The big problem showing in the second boot repair on line 64, nvram is locked also referred to on Line 82.  There are solutions available for this problem but the solution varies depending upon hardware so you might search the forums here for 'nvram locked' and include your specific hardware in the search parameters.

You haven't indicated if this is a new install or if you had been using Ubuntu for some time before this problem.  Does not seem probably to me based on boot repair but you might try reinstalling Ubuntu in UEFI mode after backing up any personal data.  Not sure that would overcome the nvram locked problem though.

---

