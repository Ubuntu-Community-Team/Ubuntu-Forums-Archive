---
title: "How to create a UEFI bootable usb (netinstall) stick?"
date: 2014-02-08
forum: Installation &amp; Upgrades
---

### Post by tom51 on 2014-02-08
So I got a new laptop (dell) and it shipped with Windows 8 (64 bit).  I re-installed Windows 8 to make space for a Ubuntu install, which worked great.  I now have half the disk unallocated and would like to install ubuntu for dual mode.  But how the heck do I make a bootable usb stick?  The laptop doesn't have an optical drive.  In the past, I've used this [guide]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows") with the tool from pendrivelinux to create a usb stick with a mini.iso.  But this tool doesn't appear to make the stick uefi bootable.  Neither [this]("https://help.ubuntu.com/community/UEFIBooting") nor this [page]("https://help.ubuntu.com/community/UEFI") was helpful.  So, I'm stuck right now, not sure how to even boot into ubuntu's setup.  Any ideas how to create a uefi-bootable usb stick?

---

### Post by oldfred on 2014-02-08
The standard 64 bit download is UEFI and BIOS bootable. You have to choose in UEFI menu which should show two boot options.

       Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

      
 Dell Inspiron 3521
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)
Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
Dell 17R Brightness
[http://ubuntuforums.org/showthread.php?t=2195650](http://ubuntuforums.org/showthread.php?t=2195650)

 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)

---

### Post by tom51 on 2014-02-08
> **oldfred said:**
> The standard 64 bit download is UEFI and BIOS bootable.
... if booted from a dvd maybe.  But my machine doesn't have any optical drives...

 > **oldfred said:**
> You have to choose in UEFI menu which should show two boot options.
This was easy with the win8 usb stick I created.  But my usb stick doesn't show up with any of the usb images created by the tools referenced in your links, most of which I have already found myself before posting this question.

Unfortunately, I'm still no step closer.  Neither the "Universal USB installer" nor the "UNetbootin" referred to in most of these articles create uefi bootable usb sticks for me.

---

### Post by oldfred on 2014-02-09
Are you sure you have not downloaded a 32 bit version, as it has no UEFI?

It should have both syslinux for BIOS boot and an EFI folder with grub for UEFI boot once extracted to flash drive.

---

### Post by tom51 on 2014-02-10
> **oldfred said:**
> Are you sure you have not downloaded a 32 bit version, as it has no UEFI?
This is the image I've been trying: [http://archive.ubuntu.com/ubuntu/dists/saucy/main/installer-amd64/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/saucy/main/installer-amd64/current/images/netboot/mini.iso)

It has some efi stuff in boot/grub it seems.  But I'm not sure entirely.

---

### Post by sudodus on 2014-02-11
I don't think the mini.iso and the alternate installers work with UEFI. Use the 64-bit ***desktop*** installer according to the advice of ***oldfred***.

---

### Post by oldfred on 2014-02-11
I have not looked at mini.iso.

One possibility might be to partition in advance with gpt, leaving an efi partition at the beginning of drive and having a 1 or 2MB unformatted bios_grub partition for BIOS boot with gpt partitioning.
Then install in BIOS mode and convert to UEFI. I think you can manually do it by uninstalling grub-pc and installing grub-efi, but not sure of details (May have to chroot from UEFI boot). Boot-Repair will automatically do that for you. Only 64 bit supports UEFI.

Only if you have gpt partitioning can you boot with either BIOS or UEFI with Ubuntu. 
Both Windows & Ubuntu only boot in BIOS mode from MBR(msdos).
And Windows only boots from gpt with UEFI.

---

