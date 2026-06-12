---
title: "I installed Ubuntu 18.04, then my BIOS was restored and I can't find Ubuntu"
date: 2020-03-16
forum: Installation &amp; Upgrades
---

### Post by atmagh on 2020-03-16
Hi everyone,

I just recently installed Ubuntu 18.04 alongside Windows 10 on my Lenovo Legion laptop. It worked fine and I just finished installing some software for my school project. However, today Lenovo prompted me a BIOS update that went wrong as many others in the community pointed out, and I restarted my laptop successfully but now I don't see Ubuntu anymore. I can't choose the system at startup and I'm not sure how to check if it's still there or not. Do I need to install it again or is there a way to know if it's still there?

Thanks,
Ayman

---

### Post by slickymaster on 2020-03-16
Thread moved to **Installation & Upgrades** for a better fit

---

### Post by oldfred on 2020-03-16
UEFI update often resets many of the settings you have changed before. BIOS always reset everything, UEFI may save some settings.
I have several UEFI settings, some required & some optional that I have to redo on every UEFI update.

You may also have to totally reinstall grub or use efibootmgr to add back the ubuntu UEFI boot entry. Reinstall of grub is really only to add the UEFI boot entry as it uses efibootmgr to add it, but may be easier to do.

You typically have to use advanced options, not a default fix if using Boot-Repair.
May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
Advanced options:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by atmagh on 2020-03-16
Thanks, but to be honest I'm not sure I understood most of you what you said.

What I did understand is that you want me to use Boot-Repair to do a diagnosis and share the result here. But I can only open my Windows OS, and it seems that Boot-Repair is only through Ubuntu.

---

### Post by oldfred on 2020-03-16
Did you check UEFI settings?
And can you boot Ubuntu live installer that you used to install Ubuntu?

---

### Post by atmagh on 2020-03-17
I just checked the UEFI and found this

[ATTACH=CONFIG]285224[/ATTACH]

I rearranged the entries and put ubuntu to be first, and now I managed to login to Ubuntu straight away. This might have solved the issue.

---

### Post by oldfred on 2020-03-17
You UEFI update probably reset boot order.

You may occasionally need to directly boot Windows from UEFI boot menu, but can do that as a one time choice without changing boot order. Grub only boots working Windows. So if it needs chkdsk or turns fast start up back on with updates, you will need to boot Windows from UEFI.

---

