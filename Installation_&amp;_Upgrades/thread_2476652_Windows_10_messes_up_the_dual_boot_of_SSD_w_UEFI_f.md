---
title: "Windows 10 messes up the dual boot of SSD w/ UEFI firmware failing to detect it"
date: 2022-07-01
forum: Installation &amp; Upgrades
---

### Post by garyshee on 2022-07-01
[COLOR=#232629][FONT=inherit]My SSD drive on an HP desktop with UEFI firmware [Nov 2016] is loaded with dual boot of Xubuntu and Windows 10, but when Windows 10 shuts down and is booted again, it boots directly to Windows 10 without showing the dual boot options. After I disable the Fast Startup option in Control Panel, the issue keeps occurring, then I use boot-repair and the dual boot option shows up again; however, after using Windows 10, the same issue begins again.[/FONT][/COLOR][COLOR=#232629][FONT=-apple-system][FONT=inherit]I use a USB stick with Xubuntu to boot the PC, then install boot-repair from the internet, however, since I meet this issue so often, I decided to make a live-USB disk of Boot-Repair-Disk, and the bad problem happens after I use the Boot-Repair-Disk to boot the PC to fix the missing dual-boot issue:[/FONT]

[LIST]
[*]it first reports some errors of the UEFI firmware, then reports no SSD found
[*]if I try to reboot the PC with the USB stick of Xubuntu to run boot-repair, it reports the same errors
[/LIST]
[FONT=inherit]How can I access the SSD again to see what happens and/or what else should I try *(I hope to find some kind of low-level USB scanning tools for detecting the SSD first)*?[/FONT]


[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system][FONT=inherit][FONT=inherit][/FONT]
[/FONT]
[/FONT][/COLOR]

---

### Post by Skaperen on 2022-07-01
i'm not surprised that Windows of any version would do this.  i don't use Windows, so i was unsure if it would, until now.  my workaround would be to get a 2nd PC, even an old 386 (for Linux), and let each OS use all the disk space on the PC it runs on.  networking them together can be fun.  or you might prefer a server (an old used one, perhaps) and run Ubuntu Linux on that.

---

### Post by kurt18947 on 2022-07-01
I'm not much help, my dual boot installations work as expected. I have used boot repair in the past with satisfactory results, you are not having the same result. I bookmarked an app from years ago, here's the wikipedia entry

[https://en.wikipedia.org/wiki/REFInd](https://en.wikipedia.org/wiki/REFInd). 

I have no personal experience with it, I just kept the bookmark in case I had a need. I think one thing that helps when doing  a fresh install of everything is to install Windows first then install linux OS s after. GRUB boot loader plays well with others, Windows boot loader doesn't seem to. I've wondered if Bill Gates was an only child* because Microsoft software tends to not play well with others.;)

* He isn't.

---

### Post by oldfred on 2022-07-01
When grub boot loader is installed, it uses efibootmgr to create UEFI boot entries and change boot order to have Ubuntu first.
But with HP, it seems a Windows boot always resets back to Windows as first.
Many with HP have said they had to go into UEFI settings (not UEFI boot menu) to change boot order.
Some just have decided to always boot with UEFI boot menu.

And many have had to update UEFI from HP.
but if Windows did do an UEFI update, it may have reset UEFI to defaults.
Double check settings in UEFI particularly AHCI & Secure Boot. My Asus motherboard has 7  or 8 settings I have to redo with UEFI update. Its now older, so no recent updates, but I still keep list handy.

Many also have had to update SSD firmware.

You can see UEFI boot entries & boot order if booted in UEFI boot mode.
sudo efibootmgr -v

---

### Post by yancek on 2022-07-02
If you have not resolved this issue, could you indicate whether your dual boot ever worked after the initial installation?
Are both windows 10 and Xubuntu installed in UEFI mode?  Can you access the BIOS firmware (use F10) and select the xubuntu entry there to boot Xubuntu? 
You would probably get more help if you knew and posted the UEFI errors you refer to.

Is your windows 10 installed on the SSD or do you have multiple hard drives?

>  But with HP, it seems a Windows boot always resets back to Windows as first.

I've been using HP UEFI machines exclusively for about 5 years and have never seen this.  I believe it has happened with some updates but not with a simple boot into windows.  I will agree that efibootmgr doesn't really work with the HP computers I have, other than during the install.  efibootmgr should show any EFI entries.

---

