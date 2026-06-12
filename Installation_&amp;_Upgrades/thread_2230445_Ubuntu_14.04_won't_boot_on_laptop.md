---
title: "Ubuntu 14.04 won't boot on laptop"
date: 2014-06-19
forum: Installation &amp; Upgrades
---

### Post by Andrew_Brenner on 2014-06-19
Hi. I'm having a problem getting Ubuntu (14.04) to boot. So, I got a new laptop (Toshiba Satellite c55-B5202), and I'm trying to install Ubuntu as the sole OS. I installed Ubuntu from USB, but now when I start up the computer, after it displays the Toshiba logo for a few seconds it says "Reboot and select proper Boot device or Insert Boot Media in selected Boot device and press a key"


I can't get past this screen. I ran Boot-Repair, but it didn't help. Here's the URL it gave me: paste.ubuntu.com/7668726


I'm pretty ignorant about this sort of stuff, although I've used Ubuntu for years on my previous laptop. So, I appreciate any help I can get here, but please present any instructions as you'd present them to a total n00b. Oh, and I'm sorry if a solution to my problem has already been presented. I've tried to follow the discussions in this ([http://ubuntuforums.org/showthread.php?t=1769482&page=216](http://ubuntuforums.org/showthread.php?t=1769482&page=216)) thread of people who have had similar problems, but it's all either gibberish (to me), or involves copying and/or renaming files that, as far as I can tell, I don't have.

---

### Post by sudodus on 2014-06-19
Welcome to the Ubuntu Forums :-)

It seems you have installed an encrypted disk (crypto-LUKS). This makes things a bit more complicated. Is it important for you to have this kind of encryption? Even if it is, maybe it is a good idea to install Ubuntu without encryption to learn about it, and later on install it with encryption.

You have a GUID partition table and probably the computer in UEFI mode. Can you get into the BIOS/UEFI menu system and check that? In my similar but one year old Toshiba, I click F12 to get a boot selector (boot menu), where I can also select to enter the BIOS/UEFI menu system. It is also possible to enter it directly via F2.

See this link [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If you intend to use only Ubuntu (and not Windows) you might also run in BIOS mode, where you need a 1 MiB partition without file system (unformatted) with the flag **bios_grub** with your GUID partition table.

Anyway, I think you should use the 64-bit Ubuntu desktop iso file, and install from that. See also the following links (and links from the link) for more tips
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

and [https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

---

### Post by Andrew_Brenner on 2014-06-19
Hi, thanks, I really appreciate your taking the time to help.

Unfortunately I get to the same dead end whether or not I include the encryption in the installation, whether or not I have secure boot enabled, and whether or not I have UEFI boot mode enabled (or, for that matter, CSM boot mode). Just to be clear, I have no problem installing Ubuntu (I'm installing the 64-bit desktop version, fyi) or running Ubuntu live from a USB drive. The problem comes in when I startup the computer after installing Ubuntu.

---

### Post by Andrew_Brenner on 2014-06-19
fyi, I ran boot-repair after installing Ubuntu without encryption. It seemed to do much more to my computer, so I guess removing the encryption made a big difference. Nevertheless, the computer still won't boot into Ubuntu. Here's the URL boot-repair gave me: paste.ubuntu.com/7671965

---

### Post by sudodus on 2014-06-20
You can run Ubuntu live and you can install it, but it does not work when installed. There was an error during boot repair.

1. Try with some boot options. Start with **nomodeset**, then try with one or more options at the same time. See this link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

2. Since you have nothing else installed, I suggest that you try installing according to

[https://help.ubuntu.com/community/In.../UEFI-and-BIOS]("https://help.ubuntu.com/community/Installation/UEFI-and-BIOS")

but into your internal drive instead of to a USB drive.

Also here you might try some boot options.

---

### Post by Andrew_Brenner on 2014-06-26
I'm sorry for my late response. I appreciate your help, but after following the instructions on the second link ([https://help.ubuntu.com/community/In.../UEFI-and-BIOS]("https://help.ubuntu.com/community/Installation/UEFI-and-BIOS")) I've just given up. I don't have the temperament (or time) for this sort of thing. I installed Fedora on the laptop, and while it installed and booted without issue, it ran very slowly. I think I'll just return this laptop and hope for better luck with something else. Again, I appreciate the help!

---

