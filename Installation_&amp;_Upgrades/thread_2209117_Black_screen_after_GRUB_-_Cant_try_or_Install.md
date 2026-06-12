---
title: "Black screen after GRUB - Cant try or Install"
date: 2014-03-04
forum: Installation &amp; Upgrades
---

### Post by AlwaysRemind on 2014-03-04
Hey guys! I have Windows 8 and I'm trying to dual boot with Ubuntu.  However, I can't even seem to boot into Ubuntu. Earlier I was able to  make an installation on a thumb drive with no problem. Now all of the  sudden I just get a black screen after I select Try or Install. I made a  different USB image and I'm still getting the same problems. Secure  boot is disabled, fast boot is disabled, and UEFI is still enabled.

I would really appreciate some help. I've tried a few different things  and nothing seems to be working for me. When I hit 'e' here's what it  says


setparams 'Try Ubuntu without installing'

```
set gfxpayload=keep
linux /casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed  cdrom-detect/try-usb=true no prompt floppy.allowed_drive_mask=0  ignore_uuid boot=casper quiet splash --
initrd /casper/initrd.lz
```

I tried to add nomodeset before quiet splash and that didn't work  either. I would really appreciate any advice you guys can give me. Thank  you so much!

Note: I'm just wondering if the whole /cdrom part is normal, even if  this is on a thumb drive? Sorry I'm brand new to Ubuntu/Linux!


[SIZE=4]**SOLUTION**[/SIZE]- found [here]("http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html")

I was able to dual boot Ubuntu with Windows 8 (UEFI) with Fast Boot disabled and **Secure Boot Enabled**.  When Secure Boot was disabled I could see the GRUB menu but my screen  would just go black after selecting 'Try' or 'Install'. So I renabled it  and was able to move right past it.

[SIZE=2]So what ended  up working for me was first using UNetbootin and enabling Secure Boot.  By doing this I was not only prompted by GRUB I was able to Install  Ubuntu. It didn't recognize my Windows 8 OS so I had to select  'Something Else'. I anticipated this so I shrunk my C drive (I only have  one hard drive with no extra partitions other then the recovery ones)  and gave myself about 200 gigs for Ubuntu[/SIZE]. Once I got to the partition selection, I found the empty space and made the following partitions:

**Logical **50gig (EXT4) - mounted to "/"
**Logical **~134gig (EXT4) - mounted to "/home"
**Logical **16gig (SWAP)
** Also to make sure that both / and /home are selected to format

I left the destination for the bootloader to be "/dev/sda"

Once  it was complete I tried it out to see which OS would boot, if any, and  if GRUB would display. It didn't show GRUB. In fact it went straight to  Windows 8 like nothing happened. Apparently this was a good thing though  so I followed the guide again and put the thumb drive back in and  restarted.

This time choose the Live version and run the boot repair:
1) Open up a terminal
2) sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
2) sudo-apt-get install -y boot-repair && (boot-repair &)
3) I selected Recommended repair (I also had a pop-up about EFI and just clicked past it)
4) I left everything default regardless of the warnings and let the repair complete.

Once  it was finished I restarted and was happy to see GRUB. I do have a lot  of different entires in it instead of just Windows 8 and GRUB, but I'm  able to boot into both of them perfectly fine.

---

### Post by AlwaysRemind on 2014-03-04
UPDATE: So I had a strange idea to not only make a new bootable USB using UNetbootin but to also enable Secure Boot. For whatever reason it finally decided to cooperate with GRUB and the installation screen seemed to work. It didn't detect my Windows 8, but from what I'm reading that seems normal. I'm following [this]("http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html") tutorial and it seems to be cooperating so far. I guess we'll see once it's all said and done. I'll update the post when it's complete!

---

