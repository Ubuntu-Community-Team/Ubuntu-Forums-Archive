---
title: "Grub rescue after install"
date: 2015-03-29
forum: Installation &amp; Upgrades
---

### Post by dan-bower88 on 2015-03-29
Hi,

I've recently installed 14.02 over my 12.02 install using the LiveCD. The install itself went fine but when I rebooted, I got a "grub rescue" prompt. When I look at devices in BIOS, I've got a "ubuntu" device with a UEFI label over it. It seems to be booting up this. If I override the boot order and pick my hard drive, which doesn't have the UEFI label, I'm able to correctly boot up grub. Now I had 12.02 running alongside Windows 7 before this install and I notice this grub boot menu is slightly different to the old one. I can see both Ubuntu and Windows 7 in this menu. However I can only successfully boot up Ubuntu. Windows starts to load then immediately resets the machine. I remember having this problem when I originally installed 12.02 but boot-repair resolved it. However when I run boot-repair now, it complains about being in legacy mode. To be frank I'm totally at a loss as to what I should do to resolve this. Surely if I repair in UEFI mode then I won't be able to access my Windows partition and storage disc? I'm currently in Ubuntu and I can see my Windows 7 partition mounted so I haven't deleted it, I just can't boot it up :(

Ideally I'd like to remove this UEFI device from the boot order and get Windows booting up. I'd really appreciate some help!

Here's my boot-repair summary: [http://paste.ubuntu.com/10700570/](http://paste.ubuntu.com/10700570/)

Thanks.

---

### Post by dan-bower88 on 2015-03-29
OK guys, I backed up my important data and decided to create a bootable USB boot repair and ran the recommended option. Worked absolutely flawlessly. Much love to the developers of that.

---

### Post by oldfred on 2015-03-29
You have a newer UEFI based system that also has the CSM  or BIOS.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

And how you boot installer is how it installs for both Windows & Ubutu. So you need to be consistent with both current Windows install and Ubuntu.
Windows only boots from  a gpt partitioned drive with UEFI and your drive is gpt with Windows booting in UEFI mode.
But you can install Ubuntu in CSM mode on a gpt partitioned drive, but then cannot dual boot from grub menu only from UEFI. And you may have to turn on/off UEFI or CSM mode to boot system installed in that mode. UEFI and BIOS are not compatible and once you start booting in one mode cannot switch to the other mode without rebooting. Or grub only boots systems installed in same boot mode as Ubuntu.

Your Ubuntu installer should have two options in UEFI boot menu. One usually is clearly UEFI and the other often is just name/label of USB flash drive. Just always boot in UEFI mode.

You still show grub in the gpt protective MBR for BIOS boot. But if you try to boot using that you now will get grub errors, if Boot-Repair has updated install from grub-pc(BIOS) to grub-efi-amd64(UEFI).

---

