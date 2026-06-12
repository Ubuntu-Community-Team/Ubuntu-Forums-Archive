---
title: "Installing Linux on eeePC"
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by tomi3 on 2014-04-18
[COLOR=#333333][FONT=UbuntuRegular]I have a computer, with no CD drive, with no operating system on it. Something went wrong while I was resetting XP and the computer now has no operating system. I am currently trying to install Linux on it via a USB drive. I only have access to a mac and this computer.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I used unetbootin to load Ubunto 12.04 [Live] onto a USB drive.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I then try to boot from the USB and it stops at this message: "- BusyBox v1.18.5 (Ubuntu 1:1.18.5-1ubuntu4.1) built-in shell (ash) Enter 'help for a list of built-in commands. (initramfs)"[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Details on the computer:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Asus 1005Ha ACPI BIOS Revision 1601[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Processor Intel Atom, 1.6Ghz,[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]System Memory: 1024MB[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]IDE Configuartion ATA/IDE Config. = [Compatible] (Options Compatible & Enhanced) Boot Device Priority = (USB: Lexar USB Flash] Quiet Boot = Enabled OnBoard LAN Boot Rom - Enabled[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]A 'screenshot' of the screen at cessation[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][http://postimg.org/image/556qag42h/](http://postimg.org/image/556qag42h/)

Do you have any ideas where I could go next?...I'm rather out of options[/FONT][/COLOR]

---

### Post by varunendra on 2014-04-20
Welcome to the forums tomi3!

The combination of a **particular BIOS + Suitable USB flash drive + Suitable method to make it bootable** can be tricky sometimes. Unetbootin is one of the most trusted methods but it does fail sometimes with some BIOS/flash drives.

Sometimes, a particular BIOS may not like a particular flash drive, no matter which method you use to make it bootable. So try different brands/models of flash drives as well if you have some available.

For a different method, have you tried the official method for creating bootable USB on Mac OS yet? Here's the link : [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx)

I personally prefer the native "Startup Disk Creator" program available on the Ubuntu ISO itself. So far I have found it most trustworthy, but you need to boot a computer with the Live CD/DVD to be able to use it. Alternatively, you can boot a virtual machine (on VMware or Virtualbox) directly with the ISO, and use it to make the USB Live bootable.

---

### Post by mörgæs on 2014-04-20
Ubuntu 12.04 is not a good choice for an eee. You will be better off with Lubuntu 14.04.

---

### Post by SeijiSensei on 2014-04-20
> **varunendra said:**
> I personally prefer the native "Startup Disk Creator" program available on the Ubuntu ISO itself.

+1

I always use Startup Disk Creator and have never had problems.  I used it to create the boot device for an Xubuntu installation on an ASUS 1201n.

However you should also make sure you have the right architecture.  For an Atom you should probably be using the 32-bit version of Ubuntu.  

[Lubuntu 32-bit ISO]("http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/lubuntu-14.04-desktop-i386.iso")
[Xubuntu 32-bit ISO]("http://cdimage.ubuntu.com/xubuntu/releases/14.04/release/xubuntu-14.04-desktop-i386.iso")

You'll also be a lot happier with performance if you [add another GB]("http://www.crucial.com/upgrade/ASUS-memory/ASUS+Netbooks/Eee+PC+1005HA-upgrades.html") of memory.

---

