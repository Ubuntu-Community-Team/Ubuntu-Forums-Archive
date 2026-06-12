---
title: "Can't boot on Windows 8.1 after installing ubuntu 14.04"
date: 2014-06-15
forum: Installation &amp; Upgrades
---

### Post by Cesar_Gomes on 2014-06-15
Hi,

I have installed the Ubuntu 14.04 in my Lenovo G400s with pre installed Windows 8 (upgraded to 8.1).

After installation I can't boot on Windows anymore unless I change the BIOS setting to load Windows Boot Manager.

Grub is always throwing a message "Can not load image file." when I choose Windows.

I have tried the Boot-repair, but also without sucess.

Below is the log of Boot Repair.

Any help will be welcome.

[http://paste.ubuntu.com/7648954/](http://paste.ubuntu.com/7648954/)
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Dec2013]

{deleted copy of script as too long and makes for very slow loading of post. oldfred}

---

### Post by oldfred on 2014-06-16
Please just post the link to paste bin as that is all that is needed. It was so long that it took forever for your post to load. And if posting longer text output please use code tags. You can easily add code tags with # icon in Advanced editor.

I do not see anything wrong. 

Do you have secure boot on? There is a bug in grub that with secure boot on it will not boot Windows 8.1.
       Unable to chainload Windows 8 with Secure Boot enabled  Also post #11 on using refind
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464)

---

### Post by johnwe1977 on 2014-06-16
To be trying the fix windows boot tool? NTBOOTautofix v2.5.7.exe

[https://www.google.com/?gws_rd=ssl#lr=lang_en&q=NTBOOTautofix+v2.5.7](https://www.google.com/?gws_rd=ssl#lr=lang_en&q=NTBOOTautofix+v2.5.7)

---

### Post by Cesar_Gomes on 2014-06-19
Oldfred, 

Thanks for replying and for the help.

I have disabled the secure boot before running the boot fix. I'll tke a look in the others tools as you described.

---

