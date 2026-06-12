---
title: "Install 7.10 on USB drive"
date: 2008-03-17
forum: Installation &amp; Upgrades
---

### Post by radio1 on 2008-03-17
I apologize for opening another topic on USB installs, but the most recent: 'snafu, usb and ...' was marked solved.

Here's what I would like:
I would like to install 7.10 AMD x64 on my Seagate 200GB PATA 133 HD in a USB 2.0 enclosure.
I want to set it so, when I switch my BIOS to 'boot USB-HDD' this will boot up.
My motherboard is a Gigabyte AMD 690G chipset with 2GB memory and a Athlon x2 5200+.

Here what I have done:
1) I've downloaded the x64 710 .iso and burned to a CD-R
2) I've run the LiveCD and I've installed on the USB drive using all the partition, but the grub loader was put on my SATAII 500GB on my computer. So, when I disabled the sata drive and rebooted I got a grub error 21. I disabled the usb drive, reset everything and fixed my mbr on the sata drive with my XP disc.
3) It dawned on me that the grub loader should be on my USB drive. So I disabled my sata, and reinstalled the same way and the grub loader went to hda/0. When I reboot I get a:

'kernal panic error, nothing at (0,0)' typer error with '000000000000: xxxx' error at the bottom.

Uh, help!

---

### Post by Pumalite on 2008-03-17
Restore first your Windows MBR with your installation disk>Recovery>FIXMBR>FIXBOOT.
Or Super grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Then reinstall following this guide: [http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/](http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/)
On step 8, go to 'Advanced Tab' and change (hd0) for /dev/???
??? is your USB.
You can find out running:
sudo fdisk -lu

---

### Post by |{urse on 2008-03-17
i did this with a similar hdd in an enclosure, i thinks it's always /dev/sdb1

---

### Post by radio1 on 2008-03-18
Great!
 I hope it works, I will try this out tonight.

I'd really like to just dual-boot, but every time I do that, my wife always ends up in Linux and does not get it. She only surfs the web, so I say, "Just click the Firefox icon". But to no avail.

---

### Post by radio1 on 2008-03-18
It worked!

---

### Post by |{urse on 2008-03-20
awesome ^^ :guitar:

---

### Post by SneakyWho_am_i on 2008-03-20
> **radio1 said:**
> She only surfs the web, so I say, "Just click the Firefox icon". But to no avail.

That's terrible :P

What if you renamed the icon to "internet explorer"? I've seen that trick employed successfully (although only to switch browsers, not operating systems)

At work all the heroin addicts' blue "e"s are labelled Virus Explorer, and all the internet capable computers have Firefox installed (not that most of the otherstaff should be on the internet)

WARNING DO NOT READ THE REST OF THIS POST, IT WILL POTENTIALLY HIJACK THE THREAD


In addition it's fun to create a file on your disk with extension xhtml (or serve a "application/xhtml+xml" content type from php or something) and set that as the homepage in Virus Explorer.
When anybody tries to open Virus Explorer directly, it offers the file for download so that you can look at it in a proper browser which supports ten year old standards.

Of course, the XHTML web page simply tells them off for using such a bad browser and driving so many webmasters to suicide.

In XP (which we don't use) the preferred applications settings come to the rescue disallowing IE for most things, and then we just have to patch NAUGHTY programs which  send the system stupid isntructions like "iexplore page.html" instead of letting the system secide.
One such stupid horrible program is Yahoo's instant messenger (which we also dont' use at work) which gives multiple insults simultaneously:
- is ugly
- harrasses you with obnoxious animated emoticons every three seconds
- is plastered with ads
- won't respect the default browser
- is not noticably fast
- is feature poor (well, maybe not, but the features are all just toys. prerecorded voice messages? What about the basics!?)


I know its all off topic. I couldn't help myself. I did tell you to nt read it ;)

---

