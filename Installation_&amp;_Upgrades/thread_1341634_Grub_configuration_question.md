---
title: "Grub configuration question"
date: 2009-11-29
forum: Installation &amp; Upgrades
---

### Post by Stolea on 2009-11-29
I currently run Ubuntu 9.10 and Win7 on the same computer. Grub gives me the choice which OS to boot.
I want to setup Fedora on a separate disk and be able to use Grub to let me choose between the 3 OSs. How do I do this without loosing access to one or all OSs?

---

### Post by jrrader on 2009-11-29
I have the same thing set up and I was about to come ask a question about it.  The way I had it before, with Fedora 11, grub2 gave me the option to boot into Ubuntu, Win7, Crunchbang, or Fedora.  I just (10 minutes ago) did a clean install of Fedora 12 - almost exactly the same way as before - came back into Ubuntu and ran update-grub.  No Fedora found.    The difference this time is that I decided to encrypt the drive.  I'm just going to reinstall Fedora 12 without the encryption and hopefully it will go back to how it was before.

**How to:**
The difference between a normal install and a second Linux install doesn't really come until right before the install takes place.  You'll want to "creat a custom layout"  to direct fedora to sdb, of course.  But right before install there will be a screen that tells you that the boot loader is going to be installed on sda.  Keep an eye out for it.  Redirect it to sdb- where ever you have your boot partition.  That way it won't overwrite your ubuntu boot loader.  That should be it.  

I'm about to retry this so it will hopefully work the way it did before.

---

### Post by jacobs444 on 2009-11-30
if you are using karmic, and keep that version of grub, them make sure to boot ubuntu and run update-grub, so it finds the fedora install, unless you are going to specifically use a bios hd boot loader to choose a different drive.

---

### Post by jrrader on 2009-11-30
The exact page I'm talking about is right after the partition set-up.  it will say > Install boot loader on /dev/sda/  Change Device

Click on change device and select "first sector of boot partition"  

I also changed bios drive order but I don't believe that matters.

---

### Post by oldfred on 2009-11-30
If you install Fedora's boot loader to the MBR of the second drive or the partition it is installed to, you can chainload into it with a simple chainload entry in 40_custom.

# Entry N - Chainload another bootloader
menuentry "Chainload my OS" {
    set root=(hdX,Y)
    chainloader +1
}

IF chainbooting to root use (hdX)     
 where X is drive number and Y is partition number in grub2 numbering.

---

### Post by Stolea on 2009-11-30
My setup is sda will be Fedora, sdb is Win7 and sdc is Ubuntu, grub is installed on sdc. My bios boot is set to boot the Ubuntu drive first. If I have to I can switch the bios setting to boot the Win drive and go straight into Windoze (which I loathe to use and only tolerate because of my accounts program)
So if I tell The fedora grub to setup house in sdc would be OK? (without totalling the other two boot options)?

---

### Post by oldfred on 2009-11-30
I always want an operating system on each hard drive and that operating system's boot loader in the MBR. Since I am familiar with Ubuntu and since grub makes it easy to add other systems I make it the first boot in BIOS to choose the other systems. If my current boot drive ever fails, I can switch drive order in BIOS and still boot. If you have a boot loader on one drive and the system on another, both drives have to work to boot. Any failure then requires liveCDs or other methods to just get into the system.

I can also use chainboot entries if I desire so I do not have to update grub all the time for every kernel update on the other systems.

---

### Post by Stolea on 2009-11-30
Thanks guys, it worked as promised.
Cheers

---

