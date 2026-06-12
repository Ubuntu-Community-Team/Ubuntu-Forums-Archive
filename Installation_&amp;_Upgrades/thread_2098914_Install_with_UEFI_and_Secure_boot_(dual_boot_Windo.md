---
title: "Install with UEFI and Secure boot (dual boot Windows 8 and Ubuntu)"
date: 2012-12-28
forum: Installation &amp; Upgrades
---

### Post by alexthunder on 2012-12-28
I did manage to install ubuntu onto my Vizio laptop with Windows 8 after changing the following settings in the Setup:
[LIST=1]
[*]Security -> Boot -> Secure boot -> Disabled
[*]Advanced -> OS support -> Other OS
[*]Boot -> UEFI -> USB key first
[/LIST]

Ubuntu was installed successfully, I was able to boot without any problem. However to boot Windows I needed to enter Setup again and select Security -> Boot -> Secure boot -> Enabled.

Since I wanted to have entries for both Windows and Ubuntu I decided to run [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair"). I ran it with "Secure boot" checked (from Ubuntu which was running with the "Secure boot" disabled option). Other options were left by default. I wasn't able to boot Windows and Ubuntu after restarting.

I booted using my bootable flash drive and run Boot Repair again. But now with the "Secure boot" unchecked. After rebooting I get grub with both Ubuntu and Windows. They both boot successfully. The only problem is that now if I choose Security -> Boot -> Secure boot -> Enabled in the Setup, I get the following error:
[INDENT]Secure boot violation
Invalid signature detected. Check secure boot policy in setup.[/INDENT]

I must admit that I'm new to UEFI. I don't understand how to make Secure boot working. By the way is it really needed?

---

### Post by N3OX on 2013-01-02
I am having a similar problem.  I installed Ubuntu 12.10 secure remix 64 bit from USB stick this afternoon on my new ASUS N56VJ-DH71 that came with Windows 8 preinstalled.  In order to get the installation to proceed, I had to turn Secure Boot off in the BIOS.  If I had Secure Boot enabled, I could still boot from the USB stick and get to the menu where I could "Try Ubuntu..." "Install Ubuntu..." etc, but if I selected either, the machine would hang with a dark screen.

With Secure Boot disabled in BIOS, the install went smoothly (and impressively fast, IMO) and both Ubuntu and Win 8 will boot from GRUB2.  Then I go to turn Secure Boot back on, and I get a Secure Boot error on startup and GRUB2 did not appear. The system proceeded to boot into Win 8.

I shut Secure Boot back off in BIOS and booted into Ubuntu from the hard disk.  I ran Boot Repair with the recommended repair and it popped up a dialog like "EFI present, check settings..." I noticed "Secure Boot" option but did not select it at the time.   Boot Repair (sensibly I guess) didn't really change anything.  Still got an error with Secure Boot enabled in BIOS, and GRUB didn't come up, system booted to Win 8.


---

Finally, I shut Secure Boot back off, booted into Ubuntu on the hard drive, and ran Boot Repair again, but this time I checked the box labeled "Secure Boot" that was highlighted in red.  Boot repair then presented me with several dialogs of commands to cut and paste into a terminal to update/uninstall/reinstall a lot of packages which I did, and that seemed fine.

Boot Repair finished and provided the following URL

[http://paste.ubuntu.com/1490180](http://paste.ubuntu.com/1490180)

I restarted the computer and enabled Secure Boot in the BIOS settings.  Now, the GRUB2 purple bootloader DOES come up, which is encouraging. But the problem isn't solved. Win 8 boots okay.  If I select Ubuntu, it hangs at a purple screen with no hard disk activity.

----

The current status is this, as far as I can tell:

With Secure Boot disabled, I can still use Windows 8 and Ubuntu just fine.  This is a nicer scenario than your situation, because I can choose to just ignore Secure Boot for now.  With Secure Boot enabled, there is no Secure Boot error anymore and I get the GRUB 2 bootloader screen to select an OS but then the boot process for Ubuntu hangs at a blank purple screen, Windows 8 works fine (what I'm typing from now).

It seems to be very close but not quite working. If I have any new information in the future, I will post here.  Good luck.

-Dan

---

