---
title: "Problems with installing from flash drive"
date: 2012-11-13
forum: Installation &amp; Upgrades
---

### Post by SchmichaelM on 2012-11-13
I was trying to upgrade from 12.04 to 12.10 as a clean install, and I had a couple of problems.

When I try to boot to a live session from flash drive, the computer boots to the hard disk. There's no error message. The light on the flash drive blinks a few times (like it's supposed to), and then the computer boots to the hard disk. With the exception of the blinking light on the drive, it's as though it weren't even plugged in.

Things I've done:

* Checked the BIOS. It's set to boot from removable media first.

* Checked the USB drives. They all work fine.

* Used a different flash drive. Same results.

* Used a different ISO. Same results.

* Tried to boot another computer from the same flash drive. It worked fine with the other computer.

I eventually gave up and just installed 12.10 using update-manager -d. It's running fine without any problems, so there wasn't some sort of incompatibility issue.

None the less, I'd really like to be able to do a clean install. Just in case there's some catastrophic failure in the future, or if I decided to change operating systems, or even if I just want to muck around with DSL or a similar distro, the option of booting from a USB flash drive would be nice to have. Especially since I'm using an Eee PC and don't have an optical drive.

I've searched the forum and a bunch of things on the intertubes, and I can't seem to find another iteration of my same problem. If anyone has any ideas, I'd love to hear them.

---

### Post by dannyboy79 on 2012-11-13
very strange. i would say that the usb stick wasn't created correctly BUT you mentioned that you were able to boot that same stick but on another computer. Are you sure the Eee PC is able to boot to a usb stick? Maybe there is another option in the BIOS you're missing.

---

### Post by Hakunka-Matata on 2012-11-13
Maybe the USB is showing up in BIOS as a hard drive, in which case you would have to switch which hard drive boots?

---

### Post by SchmichaelM on 2012-11-13
> **dannyboy79 said:**
> very strange. i would say that the usb stick wasn't created correctly BUT you mentioned that you were able to boot that same stick but on another computer. Are you sure the Eee PC is able to boot to a usb stick? Maybe there is another option in the BIOS you're missing.

I've used that exact stick to boot this machine in the past. It's how I got Ubuntu on here in the first place.

I poked around in the BIOS and couldn't find any other options. Every other time I've booted this machine from a USB flash drive, it's been set exactly the way it is now. I don't generally play with my BIOS unless I absolutely have to.

> **Hakunka-Matata said:**
> Maybe the USB is showing up in BIOS as a hard drive, in which case you would have to switch which hard drive boots?

I only saw one hard drive on the list of options. I set it to be the last thing the computer checks for.

---

### Post by Hakunka-Matata on 2012-11-13
If BIOS offers the BBS Popup boot menu in BIOS first thing when booting, you might try that.  The selection is F9 on my American Megatrends Bios screen, I don't know what your machine's first screens look like.

---

### Post by SchmichaelM on 2012-11-13
I guess I missed it before, but indeed, it was reading the flash drives as hard drives and prioritizing them after the normal HD. So I set the actual HD as the last disk, saved, exited, and booted onto the flash drive. A live session started without further issue.

Thank you all very much. This issue is now resolved. Y'all rock.

(:

---

### Post by Hakunka-Matata on 2012-11-13
goodie, glad you got it, and you're welcome

---

