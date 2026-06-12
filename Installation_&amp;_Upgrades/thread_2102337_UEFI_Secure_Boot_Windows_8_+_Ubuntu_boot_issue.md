---
title: "UEFI Secure Boot Windows 8 + Ubuntu boot issue"
date: 2013-01-07
forum: Installation &amp; Upgrades
---

### Post by bitp on 2013-01-07
I have a Lenovo X230 that came with Windows 8 installed (UEFI with Secure Boot enabled). I tried to install Ubuntu using Wubi, but it wouldn't boot and searches turned up posts claiming Wubi does not work with UEFI and Secure Boot. Still wanting to be able to use Ubuntu, I used the Windows 8 disk management tool to shrink the main partition by 20 GB for Ubuntu. Booted off the  12.10 x64 DVD I selected the option to install alongside Windows 8. I believe the system was only booting into Ubuntu after the install, but I was working on this very early morning and I'm not sure. I ended up running boot-repair to attempt to fix it. When booting I'm now greeted by a GRUB version 2.0 loader, with options for Ubuntu, Advanced options for Ubuntu and the following:
&#8220;Windows UEFI bootmgfw.efi&#8221;
&#8220;Windows Boot UEFI loader&#8221;
&#8220;EFI/Lenovo/Boot/bootmhfw.efi&#8221;
&#8220;Windows 8 (loader) (on /dev/sda4)&#8221;.

However, Ubuntu is the only option the works. I would prefer my system boots to a Windows loader that allows me to select the operating system I would like to use (Windows 8 or Ubuntu). I really appreciate all help that might help me get my system operating correctly. Thank you!

boot-repair log: [http://paste.ubuntu.com/1505843](http://paste.ubuntu.com/1505843)


Selecting &#8220;Windows UEFI bootmgfw.efi&#8221; results in the following message:
/EndEntire
file path: /ACPI(a0341d0,0)/PCI(2,1f)/UnknownMessaging(12)/HD(2,1f4800,82000,e30a542b47257544,a5,46)/File(\EFI\Microsoft\Boot)/File(bootmgfw.efi)/EndEntire
error: cannot load image.

Selecting &#8220;Windows Boot UEFI loader&#8221; results in the following message:
/EndEntire
file path: /ACPI(a0341d0,0)/PCI(2,1f)/UnknownMessaging(12)/HD(2,1f4800,82000,e30a542b47257544,a5,46)/File(\EFI\Boot)/File(bootx64.efi)/EndEntire
error: cannot load image.

Selecting &#8220;EFI/Lenovo/Boot/bootmhfw.efi&#8221; results in the following message:
/EndEntire
file path: /ACPI(a0341d0,0)/PCI(2,1f)/UnknownMessaging(12)/HD(2,1f4800,82000,e30a542b47257544,a5,46)/File(\EFI\Lenovo\Boot)/File(bootmgfw.efi)/EndEntire
error: cannot load image.

Selecting &#8220;Windows 8 (loader) (on /dev/sda4)&#8221; results in the following message:
error: Secure Boot forbids loading module from (hd0, gpt6)/boot/grub/x86_64-efi/ntfs.mod
error: no such device: 522EFA022E9DEC3.
Error: can't find command 'drivemap'.
Error: invalid EFI file path.

---

### Post by Oubountourette on 2013-01-07
Have a look here: [http://ubuntuforums.org/showthread.php?t=2098914](http://ubuntuforums.org/showthread.php?t=2098914) This two guys may be found a way.

---

### Post by benzejaa on 2013-01-07
Hey Bitp,

EDIT:  I'm actually not sure if the below will help you.  I'm looking at your boot-repair log and it seems to be sane, so I'm not sure why you are getting those errors.  I'll leave my explanation below in case your curious.

I had a very similar issue this weekend trying to install Ubuntu alongside Windows 8.  

It looks for you that grub is not finding the right windows .efi files.  I'm not sure why.  Here's how I would suggest you try and fix it.

1)  Determine which partition contains your .efi files.  I'm going to refer this as your "EFI" partition.  Fromg your boot-repair log this appears to be sda2

2)  Now that we know the partition, we need to know which file boots windows.  If you can boot into ubuntu, go to /boot/efi/EFI/Microsoft/Boot/.  If you can't, open up a live cd (any will do), and mount the partition discovered in the last step (sudo mount /dev/sda2 /mnt), and go to EFI/Microsoft/Boot/.

Basically, Grub lives on the file EFI/ubuntu/grubx64.efi.  However some terrible motherboard firmwares won't let you change the boot file, so, boot-repair will rename the standard bootfiles, such as bootmgfw.efi, to bootmgfw.efi.bkp, and replace the original one with grubx64.efi.

Look for files bootmgfw.efi.bkp  If it exists, this is what we probably want to boot.  Otherwise you'll want bootmgfw.bkp.

3)  Now that we know what we want to boot, we need to add a grub entry for it.  This is a bit more difficult if you can't boot into the system, as far as I know (someone can correct me if I'm wrong) you'll need to mount everything, and chroot into it.  If you can boot into ubuntu, you'll be fine.

Go to /etc/grub.d.  Find a file that has the word "custom" in it (such as 25_custom or 40_custom).  We're going to add the menu entries here.  

Add this entry

```
menuentry "windows UEFI bootmgfw.efi.bkp" {
set root='(hd0,gpt2)'
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi.bkp
}
```

Note that if you don't have a bootmgfw.efi.bkp, you probably want bootmgfw.efi instead.

4) Run "update-grub" to rebuild your grub menu

5) Restart the computer to test out your handiwork.

If Microsoft/Boot/bootmgfw.efi(.bkp) doesn't work for you, you can also try Microsoft/Boot/bootx64.efi(.bkp) or Boot/bootx64.efi(.bkp).  If these don't work, go ahead and try the rest of the .efi files as well.

Note that you can press "E" from grub to edt the command (just for this session, it will revert once your done) so you don't have to keep booting and rebooting to test this.

If grub IMMEDIATELY cycles back to itself, then the file you are bootloading is the grub file, look for one that begins with .bkp

If you get error messages like you were getting before, then you are trying to load a .efi file that doesn't exist.  Check you path and drive/parition designation, and make sure you're on the right one.

If you boot into the Windows Recovery Environment by accident, then you found the wrong file.

Here's my adventure into dual-booting windows 8 and Ubuntu
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)

Also this thread on how boot-repair works I found to be super helpful.
[http://ubuntuforums.org/showpost.php?p=12379441&postcount=637](http://ubuntuforums.org/showpost.php?p=12379441&postcount=637)

Good luck!

---

### Post by ubershmekel on 2013-04-03
I have a lenovo thinkpad x230, pre-installed windows 8 and installed ubuntu 12.10x64 and this didn't work for me. Ubuntu works fine but GRUB can't load windows. Windows works if I set the bios to default to its device.

Here's my boot repair report: [http://paste.ubuntu.com/5673252/](http://paste.ubuntu.com/5673252/)

I tried modifying the GRUB menu, and manually entering the commands with the 'c' console option as well.

The efi filese exist but they all give me the same error, manually typed here with probable typos:

```


grub> chainloader /efi/Microsoft/Boot/bootmgfw.efi
/EndEntire
file path: /ACPI(a0341d0,0)/PCI(2,1f)/UnknownMessaging(12)/HD(2,1f4800,82000,a4141d5849d[...]/File(\efi\Microsoft\Boot)/File(bootmgfw.efi)/EndEntire
error: cannot load image.


```

I'm seriously confused here. Any help would be appreciated.

---

### Post by oldfred on 2013-04-03
It looks like Boot-Repair commented out an fstab entry which you need. I normally see it comment out an entry that uses device like /dev/sda2 and add a new entry with UUID. But it did not re add entry?

Please check fstab and make sure you have an entry for efi partition. If missing remove # from the UUID entry to uncomment it.

> 
# /boot/efi was on /dev/sda2 during installation 
#UUID=5851-2533  /boot/efi       vfat    defaults        0       1

Are you using this menuentry to boot Windows? And some boot with secure boot on or off, others require it to be on.

 menuentry "Windows UEFI bootmgfw.efi" {
search --fs-uuid --no-floppy --set=root 5851-2533
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}

---

