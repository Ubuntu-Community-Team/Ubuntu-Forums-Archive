---
title: "Intrepid install to USB drive for 2 different laptops"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by sdrubble on 2008-11-02
Hi all,

As a Linux almost-noob I may be trying to accomplish too much at the same time but I'm willing to try - at the very least I suppose I'll learn a lot in the process.

However as I've been several years away from my previous Linux experience I'm afraid I might be taking incompatible approaches together. So if somebody would care to comment on what I'm planning to do I'd be most grateful.

I've got the following HW / SW -


[LIST]
[*]1st laptop Dell Latitude 120L - Pentium-M 1.73 GHz, 2 Gb RAM, Windows XP, 80 Gb HD w/ multiple partitions (including some LVM ones made w/ System Rescue live CD)
[/LIST]

[LIST]
[*]2nd laptop Asus EEE PC 901 - Atom N270 1.6 Ghz, 2 Gb RAM, 4 + 16 Gb SSDs, currently w/ soon-to-be-removed Xandros OS
[/LIST]

[LIST]
[*]USB 160 Gb portable HD which I intend to format w/ multiple partitions including a bootable one
[/LIST]

After firstly considering a dual-boot setup on the EEE PC (Win XP + Xubuntu) I thought it might be too troublesome to accomplish & manage within just 20 Gb of storage. Then I'm now considering making an Intrepid install to the USB HD that [should] work on BOTH laptops above.

So I'd like to know if this is doable with all the following in mind:


[LIST]
[*]putting GRUB on USB HD only (and NOT on either of the laptops' MBRs) , so that I could boot Ubuntu from either laptop and ONLY when USB HD attached at power-on - possibly using UNetbootin from [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
[/LIST]

[LIST]
[*]2 alternative kernels on USB HD GRUB - normal one when booting on the Dell Latitude and the one from [http://www.array.org/ubuntu/setup-intrepid.html](http://www.array.org/ubuntu/setup-intrepid.html) when booting on the EEE PC (to get full support for HW components on the EEE)
[/LIST]

[LIST]
[*]performing the Ubuntu install from the alternate CD (not sure if UNetbootin is compatible with this), in order to use some LVM partitions (what I believe can't be done with the standard CD)
[/LIST]

Thnx a LOT in advance to anyone who might give me some guidance on this.

Cheers

sdrubble

---

### Post by caljohnsmith on 2008-11-02
Do you want to install the Ubuntu Live CD to your USB drive, or do a full installation? UNetBootin is for installing the Live CD to your USB drive. Also, I've not used the alternate installer, but make sure you tell it to install Grub to /dev/sdb or whichever is your USB drive, not (hd0) or /dev/sda which will be your internal drive. Good luck and let me know how it goes. :)

---

### Post by sdrubble on 2008-11-02
> **caljohnsmith said:**
> Do you want to install the Ubuntu Live CD to your USB drive, or do a full installation? UNetBootin is for installing the Live CD to your USB drive. Also, I've not used the alternate installer, but make sure you tell it to install Grub to /dev/sdb or whichever is your USB drive, not (hd0) or /dev/sda which will be your internal drive. Good luck and let me know how it goes. :)
Hi john,

My wish is to make a full install. I believe I'd lose much flexibility by installing the Live CD instead.

I've read [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) (main page) and found the following:

>  . . . it's no different from a standard install, only it doesn't need a CD > . . . run the file, select a distribution, floppy/hard disk image, or [COLOR=Red]**kernel/initrd to load,**[/COLOR] select a target drive (HDD/USB), then . . .From this quotes, plus the screenshot at [http://sourceforge.net/dbimage.php?id=173795](http://sourceforge.net/dbimage.php?id=173795) , I assumed that the Live CD is one option but not the only one - I might be able to do a net install starting from the actual Ubuntu installer script. In this case I'd choose the alternate installer to have more install options.

I'll try this myself later on add see if it can indeed be done as I'm thinking - can't do it right now for I need to do some backups before attempting this. 

In the meantime I'd like to know what you think of my assumptions.

Many thx

sdrubble

---

### Post by caljohnsmith on 2008-11-02
Instead of using UNetBootin, I would simply do a full install using the Alternate CD, but it's up to you of course. As I mentioned in my previous post, I think the only thing to be concerned about is making sure Grub gets installed to the MBR (Master Boot Record) of the USB drive, instead of your internal drive. And since I've never used the Alternate Installer, I'm not sure what you need to do to specify that Grub gets installed to /dev/sdb (or whichever is the USB drive). Sorry I can't be of more help, but let me know how it goes. :)

---

### Post by C.S.Cameron on 2008-11-02
You should be able to plug your USB drive into the Dell and install Ubuntu to it from the Live CD.
The install should give you a grub option to boot to windows if you want to leave it plugged in.
(You need to select your USB as first hard drive in BIOS)
The USB drive should also work on the EEE if it is selected as first HDD in bios.

---

### Post by sdrubble on 2008-11-02
John,

> **caljohnsmith said:**
> Instead of using UNetBootin, I would simply do a full install using the Alternate CD, but it's up to you of course.

This makes a lot more sense, of course - I just wasn't aware that the official installer could do a full install to an USB drive (including the GRUB & boot parts). This is great !  :-)

So it doesn't look like I'll need Unetbootin this time.

> **caljohnsmith said:**
> As I mentioned in my previous post, I think the only thing to be concerned about is making sure Grub gets installed to the MBR (Master Boot Record) of the USB drive, instead of your internal drive.

Yes, I'll pay CLOSE attention to this . . .   8-[

> **caljohnsmith said:**
> And since I've never used the Alternate Installer, I'm not sure what you need to do to specify that Grub gets installed to /dev/sdb (or whichever is the USB drive). Sorry I can't be of more help, but let me know how it goes. :)

Well, I suppose this won't be too hard to figure out when actually performing the install. Many thx again !  :biggrin:

---

