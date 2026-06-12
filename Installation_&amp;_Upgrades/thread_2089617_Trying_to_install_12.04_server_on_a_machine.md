---
title: "Trying to install 12.04 server on a machine"
date: 2012-11-29
forum: Installation &amp; Upgrades
---

### Post by Dubslow on 2012-11-29
Hey everybody. I've recently gotten my hands on a standard consumer desktop ($100 ASUS micro ATX mobo, i5-2500K) which I will be using as a server (i.e. headless, no screen/keyboard etc.).

As my graphics card is currently being RMAd, my usual desktop's Ubuntu 11.04 won't run graphics properly, so I'm stuck in Winbloze (7) for a week or two.

I followed the instructions [here]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows") to make a USB stick with 12.04 server on it. The file is named "ubuntu-12.04.1-server-amd64.iso", and in the drop down menu of the [PDL program]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/#button") I selected "Ubuntu 12.04 Server Installer", being the only selection with "12.04" and "server" in the same line. I thought it was curious that the desktop versions didn't have the "Installer" qualifier while the server versions did, but I continued on anyways.

I plugged the new server into my monitor and keyboard temporarily to run the install. I plugged in my now live-disc'd flash drive and booted it. The mobo screen came up fine, then the live-disc's language selection screen, and then keyboard layout. After the keyboard layout selection, it said "Your installation CD-ROM couldn't be mounted", and if I skipped that, the install failed.

In my previous attempts to install various forms of Ubuntu/Mint desktops I've never gotten such an error. I thought the live-disc would be able to do everything itself.

What exactly am I doing wrong? I'm only barely-proficient in this sort of thing, so there could potentially be a variety of things wrong.

---

### Post by Dubslow on 2012-11-29
Great. I tried making the live disc in an Ubuntu VM, and that seemed to work, but when I booted the server, it said "bootable medium not found".

And now Windows can't format the flash drive. :/

Edit: Fortunately for me,
1) I can still access my usual box in Linux via my phone/command line
2) I found formatting instructions for Linux/cmd line.

Now back to the original problem...

---

### Post by Dubslow on 2012-12-01
Well, I borrowed a proper Ubuntu install from a friend, and that Startup Disk Creator's finished product installed without problem. Moral: Don't use PenDriveLinux or Ubuntu in a virtual box to create a server live disk.

---

