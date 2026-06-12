---
title: "Grub shell when trying to install from a USB sticker"
date: 2017-02-17
forum: Installation &amp; Upgrades
---

### Post by guarriman on 2017-02-17
Hi.

I'm trying to install Lubuntu on a HP 255 G3 laptop, from a USB sticker (I created it by using 'Startup Disk Creator' in another Lubuntu PC), and each time I reboot the laptop, I get the grub shell ("GNU GRUB version 2.02") without any chance to keep on with the usual installation.

I configured the BIOS to modify the boot order:
1) USB Diskette on Key/USB Disk
2) Internal CD/DVD ROM Drive
3) USB CD/DVD ROM Drive
4) Network Adapter
5) OS Boot Manager

However, each time I reboot the laptop, I get the same grub shell.

If I type on the grub shell
> set pager=1
> ls
I get this info:
(hd0) (hd0,gpt3) (hd0,gpt2) (hd0,gpt1) (hd1) (hd1,msdos1) (cd0) error:failure reading sector 0x0 from 'cd0'.

If I type "exit" on the grub shell, I get two options:
- ubuntu (HGST xxxx)
- Boot From EFI File

If I select the first option, I go back to the grub shell. If I select the second one, I enter in a "File Explorer" with a first message "NO VOLUME LABEL. Acpi (PNP0A03,0)/..." with no options to start the Ubuntu usual installation.

Any tip is welcome to start the usual installation of Ubuntu/Lubuntu. Thank you very much.

---

### Post by vidtek on 2017-02-17
Save yourself a heap of time, burn a dvd of the install and run from there.
There can be a zillion reasons for this, installs from sticks are still problematic.
I find I can stuff about for hours unproductively and in the end I just end up burnig a dvd.

Cheers, Tony.

Edit-

Don't know what gives with the site tonight- second time it's double-posted sorry guys.

---

### Post by guarriman on 2017-02-17
* I just end up burning a cd/dvd.*

I've just burned a DVD with a new fresh Ubuntu ISO, I modified the BIOS to set the DVD boot as the first option, and the grub shell appears again :-(

Thank you for your answer, by the way :-)

---

### Post by vidtek on 2017-02-17
> **guarriman said:**
> * I just end up burning a cd/dvd.*

I've just burned a DVD with a new fresh Ubuntu ISO, I modified the BIOS to set the DVD boot as the first option, and the grub shell appears again :-(

Thank you for your answer, by the way :-)

I'd try downloading the image again, possible corruption.  Try with a different distro.  I've had problems like this with several Ubuntu flavours.

Gotta love Linux, can try all these flavours for nothing-try that with ios or windaz costa plenty.

Cheers Tony

---

### Post by ubfan1 on 2017-02-17
1) Did you md5sum check the downloaded iso?
  See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
  Check the number against the listing in the link for your release listed at
  [http://releases.ubuntu.com](http://releases.ubuntu.com) under the MD5SUMS link.
  For other releases' hashes, like lubuntu, see:
  [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
2) If using a CD/DVD, did you burn the disc as slowly as possible?
  See [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
3) Did you select the media check before trying to install?
 [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
4) Did you ever do a "memory check" (perhaps another live-media menu choice) on your PC?

Doing the above can save you a lot of time struggling with a bad install media or
hardware problems.

Was the version of lubuntu which you used to burn the USB/CD the same as the ISO you were using?  If not, you might have better luck with mkusb.

---

