---
title: "Unable to boot Ubuntu 16.04 LTS live USB"
date: 2016-06-01
forum: Installation &amp; Upgrades
---

### Post by SnazzleLabsYT on 2016-06-01
I am having trouble booting the live environment of my Ubuntu 16.04 LTS live usb.
I can boot to the GRUB menu of the USB, and if I select 'Try Ubuntu', it gets to the Ubuntu screen for a couple of seconds and then goes to a console with a mount error.
I'm not sure why I'm having trouble as I have managed to boot the same version of Ubuntu on the same USB with the same BIOS configuration.

[ATTACH=CONFIG]269387[/ATTACH]

Laptop: Lenovo Z50-70
OS: Windows 8.1 (fast startup disabled)
BIOS options: Legacy mode on. Secure Boot off.

---

### Post by ajgreeny on 2016-06-01
Please do not add large images inline as you did.

In future please attach images by clicking on the paperclip icon in the toolbar, navigating to the image on your drive, then clicking the Upload button to add the image with thumbnail.

Are you sure the ISO file you used is not corrupt?  I am not sure from your comment if the USB is the same one you used before or if you recreated the USB, perhaps with a new ISO file.
See [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by ubfan1 on 2016-06-01
Which tool did you use to create the USB?  16.04 is a little touchy about which ones work successfully.  Nevertheless, on a UEFI system, just copying the IEFO files to a FAT filesystem will fail to boot with a similar error to yours (cannot find /cdrom... ) because the FAT fs does not have links, and apparently the "ubuntu" link is vital in the running
system setup, since "/cdrom" is not on the ISO.  You can actually edit the grub.cfg "try" boot paragraph to remove from the "linux..." line the "file=/cdrom/preseed..." and add 
live-media-path=/casper/      ignore_uuid  
just after the boot=casper.  This boots on my UEFI system, might allow you to test it out.

---

### Post by yoshii on 2016-06-01
I have had good luck with uNetBootIn for creating bootable USB drives.  
I usually format the USB drive as FAT32 (and set the boot flag) with gParted before starting though.  

I read somewhere that YUMI sometimes creates some problematic installs.  
I did have some trouble booting Ubuntu v14.04.4 via USB, but no problems booting gParted or AV Linux or Ubuntu v16.04 LTS.  

Good luck

---

### Post by SnazzleLabsYT on 2016-06-01
^^^ajgreeny,
                  yes, will make sure of this for the future. After checking the MD5 hashsums, the checker says they match.

^^ubfan1,
               I used Rufus to create my USB installer. I'll try uNetBootIn.
^yoshi2,
             Thanks for the information. ;)

---

### Post by SnazzleLabsYT on 2016-06-02
@ubfan1
Can you help me with those instructions? I'm just starting with Ubuntu [Linux in general at that ;)]
I tried uNetBootIn, and I can't even get to the Grub bootloader.

Also, does it matter that I disabled UEFI in my BIOS? I read somewhere that you need to have it on or then one or both wont boot.

---

### Post by ubfan1 on 2016-06-02
First, the procedure of just copying file to a USB will only work for a  UEFI boot, there would be no MBR at all on the device, so it wont boot in BIOS mode.  From Windows, I suppose you can directly open the ISO with file explorer and see the files on it.  Insert your USB which you will overwrite (have nothing else on it), and if it does not already have a FAT32 filesystem on it, format it.  You should see it in the file explorer too.  Then just copy the files from the ISO to the USB.  Then edit the /etc/grub/grub.cfg file.  That should be a working UEFI boot. for the "try".  Do a similar edit for the "install" set of grub instructions if you want to install it.

---

### Post by SnazzleLabsYT on 2016-06-02
Okay, thanks. For the grub.cfg, is it in *name of usb*/boot/grub? The contents of it (opened with Notepad++) are:

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true ---
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  boot=casper integrity-check quiet splash ---
    initrd    /casper/initrd.lz
}


Can you please show me where I'm ment to edit this? Maybe you could copy it, edit it and reply the text back, and then I could remove everything in the grub.cfg and paste the text you edited...?

Here are the properties for the USB drive.
Partition scheme: MBR
File system: FAT32
Size: 3.14GB (more than sufficient for Ubuntu)

---

### Post by ubfan1 on 2016-06-02
Change the first "Try" block as done below and see if it works for you on a UEFI booting machine (or just change the menuentry wording and add the commands somewhere:

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  boot=casper   live-media-path=/casper/   ignore_uuid  quiet splash ---
    initrd    /casper/initrd.lz
}

This worked on a Thinkpad for me.  Of course, the copy command complained about the inability to copy the "ubuntu" link, but that's why we do this change.

---

### Post by SnazzleLabsYT on 2016-06-03
@ubfan1
Thanks. I'll try this out and see if it works. As a side note, you've been really helpful! ;)

EDIT: I've tested it, and it works! I'm replying to you right from the live USB! You're a godsend! Thanks so much! :D 
Also, does this edit work for the Install Ubuntu section? I haven't tried booting that one but just in case! :)

---

### Post by ubfan1 on 2016-06-03
You're welcome.  I haven't tried the install part, so you can add your results here to this thread.  The "preseed" business is related to install questions, I think, so there may be some effect.  Hopefully, just a few more questions get asked.

---

### Post by galois2 on 2016-12-20
I tried this but is not working on my Macbook Pro :( help

---

### Post by ubfan1 on 2016-12-21
You would be better off starting your own thread with your machine details, what you tried, and what errors you got.  I don't know anything about Macs. so more attention would be desirable.

---

