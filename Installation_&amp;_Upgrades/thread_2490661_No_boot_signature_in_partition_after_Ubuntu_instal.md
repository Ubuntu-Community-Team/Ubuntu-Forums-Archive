---
title: "No boot signature in partition after Ubuntu install"
date: 2023-09-11
forum: Installation &amp; Upgrades
---

### Post by ilcamorista on 2023-09-11
Hello guys,
Im in trouble with an installation of Ubuntu to my Pc.

I have windows 10 and i tried to install Ubuntu 23.04 . I tried to create partitions etc,
The Ubuntu installed and worked, but after that , windows installation cant start.
I tried with rescatux but now i see only
"No boot signature in partition"..

Please give me some advice how to identify what's the problem snd how to fix it..

Thanks

---

### Post by MAFoElffen on 2023-09-11
Please run the boot-info report from [boot-repair]("https://help.ubuntu.com/community/Boot-Repair") and post the URL of where it uploads to. That will give Members here the information they need to assist you.

---

### Post by ilcamorista on 2023-09-11
<snip>

I think here it's the report

Keep in mind that the only software that i have to a usb is rescatux. For sure if it's needed  i can find something different

---

### Post by coffeecat on 2023-09-12
@ilcamorista, I've removed your WeTransfer link. Asking forum members to go through the various WETransfer hoops to get to a download link is not the way to do it. The boot-info report would have given you an Ubuntu paste link where members can view the report without having to download anything.  Please post that link, not a link to a commercial website.

---

### Post by yancek on 2023-09-12
The two most likely scenarios are that you accidentally have overwritten the windows partitions OR (more likely) have installed Ubuntu in a different mode.  If your windows 10 was preinstalled, it is almost certainly in UEFI mode and Ubuntu would need to be booted and installed UEFI if it is on the same drive or it would not boot windows.  After booting Ubuntu, go to the /boot/efi/EFI directory and see if there are both Microsoft and ubuntu directories.  If there are, both are installed UEFI and it is another problem.  Post what you see.

---

