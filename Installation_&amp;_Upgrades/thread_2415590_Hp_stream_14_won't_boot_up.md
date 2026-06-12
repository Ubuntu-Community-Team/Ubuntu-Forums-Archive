---
title: "Hp stream 14 won't boot up"
date: 2019-03-28
forum: Installation &amp; Upgrades
---

### Post by mac-2check on 2019-03-28
Solved: I set legacy support to Enabled and secure boot to disabled and then installed xubuntu as "delete the whole disc and install xubuntu". After this it works normally. I didn't need to even use boot-repair disc.
Hello,
  

I reinstalled xubuntu on my HP stream 14 after a year and I completely messed it up. It won't boot the installed system nor can I boot a system from the USB drive. I tried to google a solution but nothing helped. I attached some screenshots. I hope it'll help you.

I tried changing legacy support and secure boot settings but it leads to the same outcome  

Thank you in advance.

Martin

---

### Post by kc1di on 2019-03-28
[This page]("https://help.ubuntu.com/community/UEFI") may be of help to you.

---

### Post by mac-2check on 2019-03-29
Hello, thank you for the link. I got a bit further.

I used the boot-repair disk and it said the problem was resolved, but not completely. Here is the report: [http://paste.ubuntu.com/p/SwHCFKK4TB/](http://paste.ubuntu.com/p/SwHCFKK4TB/).

When I rebooted the laptop, it said: Boot device not found. Please install an operating system. I googled a solution and found that I  should set legacy support to Enabled and secure boot to disabled. After this, it still does not work but I can enter the boot menu right after start and manually boot from an EFI file and then I can finally use the xubuntu I installed. I guess I need set that this grubx64.efi file is loaded right after starting the laptop. Would you know how? Otherwise, I would need to always choose it manually...

---

