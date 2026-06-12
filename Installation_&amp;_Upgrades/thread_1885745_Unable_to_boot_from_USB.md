---
title: "Unable to boot from USB"
date: 2011-11-23
forum: Installation &amp; Upgrades
---

### Post by ChromeFusion44 on 2011-11-23
I have correctly (form all that I know) Ubuntu 11.0 onto my USB drive to see what its like, but after installation and everything, when I go to restart my laptop, it just begins booting up windows.

Ive gone to the BIOS settings menu, but I don't know how to make my laptop boott form my USB drive, or how to configure the BIOS settings to boot form the USB drive.

Any help out there? :???:

---

### Post by darkod on 2011-11-23
Depending on the BIOS, you usually need to go into Advanced BIOS Settings and look for Boot Devices, or Boot Order, or similar.

Do you mean you installed ubuntu with the ext hdd as destination, or you just want to use ubuntu bootable usb stick to try it?

---

### Post by ChromeFusion44 on 2011-11-23
I was going to install Ubuntu permanently, but I was following the directions form the website, and one of them was to create a bootable USB stick, so I did.
I just wasn't quite sure where I go to edit the options to boot form the USB stick.

Also, I don't know what you mean with the "ext hdd" thing.xD
I wasn't just going to try it, I was going to fully install it afterwards.The website says that after you boot from the USB, you will be able to fully install it.

I WILL try to find the bot devices thing and such when I go to my BIOS settings.

---

### Post by Oxyris on 2011-11-23
what BIOS do you have? I have Aptio and it doesn't act like most of the examples I've found through googling. In my case I had to change the something called legacy hard drive (I forget what it was actually called but it was something along those lines) so that it booted straight from USB and completely ignored the internal hd (my boot order was listed as cd first then the usb drive and then something called aeros, it did not list the hd at all).

---

### Post by ChromeFusion44 on 2011-11-23
Ok, when I go to change my BIOS settings the header/thing on top says "PhoenixBIOS Setup Utility."Now, Im going to assume my BIOS is Phoenix.
But, when I go to try to go setup BIOS settings form my friend's computer, (awkward, right?) I can get Ubuntu started up perfectly fine from the USB, so now I think its my BIOS that is being weird.

On my friend's computer, there is a section that is kind of like "boot devices" as someone else had said before.I can change the primary device to the USB stick.When I go to boot the computer up, I get Ubuntu.

On the other hand, with my computer, under the "Advanced" tab, there is something that says Primary IDE adapter, and Secondary IDE adapter.I can't change the first or second, and I apparently do not have a secondary IDE adapter.
Under the "Boot" tab, there are little sub section like things that say:

Removable Devices

CD-ROM Drive

*Hard Drive

Network Boot


If i select Hard Drive, it brings up another item that says this:

IC25030ATCS04-0-(PM)


I'm assuming that's my hard drive, but before I go any further, what the heck?!
Under "Removable Devices" shouldn't the USB stick be listed?
That's honestly pretty weird...

---

### Post by scradock on 2011-11-23
> **ChromeFusion44 said:**
> 

On the other hand, with my computer, under the "Advanced" tab, there is something that says Primary IDE adapter, and Secondary IDE adapter.I can't change the first or second, and I apparently do not have a secondary IDE adapter.
Under the "Boot" tab, there are little sub section like things that say:

Removable Devices

CD-ROM Drive

*Hard Drive

Network Boot


If i select Hard Drive, it brings up another item that says this:

IC25030ATCS04-0-(PM)


I'm assuming that's my hard drive, but before I go any further, what the heck?!
Under "Removable Devices" shouldn't the USB stick be listed?
That's honestly pretty weird...

Try going there (BIOS Setup) again with the USB Stick inserted. It may show up as an option in the same list as the IC250...... Hard Drive.

If it does, you can select it by using the up/down keys and tell the machine to re-boot. Don't turn off the power - just re-boot. 

HTH

---

### Post by ChromeFusion44 on 2011-11-23
Tried that, but it doesn't work...
I found some website that is BIOS update plus or something, and since my BIOS seems pretty different than everyone else's, I'm going to try to "update" or whatever my BIOS.

I'll edit this and post results when I'm finished.

---

### Post by Worlds Tallest Engineer on 2011-11-23
I had the same thing happen to me.  For some reason my BIOS was reading my flash drive as a hard drive.  So I went in to the option where I changed the boot order of the hard drives.  That fixed it, and it booted from the flash drive.  :D

I'm using an ASUS, not sure if that makes any difference.

---

### Post by tersogar on 2011-11-23
I try that on an old pc but there was no option for the usb so all I did is burn a cd. If the option I want give me trouble I just try another.

---

### Post by ChromeFusion44 on 2011-11-24
The USB drive I'm using doesn't come up as a hard drive...

I guess I'll just burn a CD.
I think the CD I have has enough space.

[EDIT] I just tried a bunch of different CD burners, but they won't let me burn the CD. :/
I don't think Best Buy cells burnable CD's so...
Im probably just going to get the CD from the Ubuntu store. [EDIT]

---

### Post by tersogar on 2011-11-24
The download is less than 700mb so you should be fine.

---

### Post by lsemmens on 2011-12-10
It may well be that you Laptop is forgetting that there is a device plugged into your USB port on a warm restart. I've found that, for whatever reason, that I can only boot from the USB device once and, should a reboot be required I must perform a cold boot. When I find a solution, and I'm sure there is one, I shall report back!

(I am currently running 11.10 from a USB stick on a Toshiba Laptop from which I've stolen the HDD for another project.)

---

### Post by kurt18947 on 2011-12-10
> **ChromeFusion44 said:**
> 
<snip>

On the other hand, with my computer, under the "Advanced" tab, there is something that says Primary IDE adapter, and Secondary IDE adapter.I can't change the first or second, and I apparently do not have a secondary IDE adapter.
Under the "Boot" tab, there are little sub section like things that say:

Removable Devices

CD-ROM Drive

*Hard Drive

Network Boot


If i select Hard Drive, it brings up another item that says this:

IC25030ATCS04-0-(PM)


I'm assuming that's my hard drive, but before I go any further, what the heck?!
Under "Removable Devices" shouldn't the USB stick be listed?
That's honestly pretty weird...

Of those choices, I'd go with removable devices as the first boot device then CD-ROM.  If your machine is a bit older, it may not support booting from a USB device.  I have an older Thinkpad with a similar boot menu and does not support booting from a USB stick, the removable device supported is a USB floppy drive.  My experience is that booting from a CD/DVD is slower but is reliable.

---

### Post by steffstar on 2012-10-18
I was having the same problem with my asus computer with "Aptio setup utility". Came across this thread while I was trying different options in setup when I suddenly found the USB device.
I don't remember what I did, but I think it was that I disabled SVM Mode under advanced and then restarted and entered setup again. Then I found the USB drive.

---

### Post by alexcohn on 2012-10-19
On my ancient Dell Latitude D600, the magic trick was to set emulation to **enabled** in BIOS setup. Thanks to [Cubis]("http://en.community.dell.com/support-forums/software-os/f/3524/p/19321441/19654220.aspx#19736509") for this tip in a Dell forum!

---

