---
title: "How do I restore grub after windows 10 creators update"
date: 2017-09-20
forum: Installation &amp; Upgrades
---

### Post by daan-vanrest on 2017-09-20
Hi all,

I used to have a dual boot windows 10 + Ubuntu.

After updating windows 10 I lost grub when starting. It looks like ubuntu is still on sda7.

Boot-repair gave me this report [http://paste.ubuntu.com/25581834/](http://paste.ubuntu.com/25581834/)

When I try recommended repair with boot-repair I get this: GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.

Does anyone know how to fix grub?

Thanks in advance,

---

### Post by oldfred on 2017-09-20
It looks like you left Windows fast start up or always on hibernation. You need to turn that off first. Windows updates will turn this back on, so you need to turn it off anytime grub does not boot Windows. With UEFI you can always directly boot Windows from UEFI boot menu.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Both Windows & Ubuntu are installed in UEFI boot mode.
If you are booting live installer, you must boot it in UEFI mode also.

If Boot-Repair is wanting to install the BIOS version of grub, it needs the bios_grub partition. You do not want nor need that as you are booting in UEFI mode.

Did you choose a BIOS boot version of grub. Or has latest version of Boot-Repair mixing your UEFI boot of live installer & wanting to install a BIOS boot version of grub??

---

