---
title: "Win8 1 HDD Ubuntu 12.10 1 HDD - UEFI - Troubles"
date: 2013-03-10
forum: Installation &amp; Upgrades
---

### Post by Dwack on 2013-03-10
So I just got a new Gateway DX4870 ( [http://support.gateway.com/product/default.aspx?modelId=4263](http://support.gateway.com/product/default.aspx?modelId=4263) )and as far as I can tell it uses UEFI( I'm new to UEFI, never heard of it until trying to install Ubuntu )

My main goal is to have Win8 installed on the 1TB HDD that came with the system. I would like to install Ubuntu on an old 400GB HDD that I installed from a previous computer. 


I setup the second HDD as follows:
200mb EFI w/ boot flag
3gb swap
10 gb /
rest /home

I installed Ubuntu to the second HDD via a LiveUSB and chose sdb1 as the bootloader locaion. 

When I turn on the computer and press F12 to get my boot options I can successfully load Win8. However when I try to load the HDD with Ubuntu I get a message that says something like "Please choose the correct boot path and try again".

After installation I ran boot-repair and this was the log:
[http://paste.ubuntu.com/5602294/](http://paste.ubuntu.com/5602294/)

I then ran it again and got this:
[ http://paste.ubuntu.com/5602305/]("http://http://paste.ubuntu.com/5602305/")

Any help would be greatly appreciated

---

### Post by oldfred on 2013-03-10
It looks like Boot-Repair ran fixes on sda's efi partition but did not add the Ubuntu/grub files to sdb's efi partition.

It seems that Boot-Repair and Ubuntu find the efi partition on sda first. You want grub to install to sdb.

 Installing Ubuntu 12.10 alongside Windows 8 on Asus K95V laptop HD/SSD (EFI) Two drives. Details in post #6
[http://ubuntuforums.org/showthread.php?t=2116610](http://ubuntuforums.org/showthread.php?t=2116610)
UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

If you want to experiment (above links use disconnect Windows drive to force install in Ubuntu drive), you can edit fstab to mount the efi partition of sdb and reinstall grub-efi.

---

### Post by Dwack on 2013-03-10
Not sure how I missed that topic(post #14) but it was a tremendous help. I have managed to install Ubuntu on the 2nd HDD, doing so while the Win8 HDD was disconnected. It gave me the same error screen on reboot but a boot-repair has got it all sorted out and I am able to boot to GRUB.

Only one minor issue, when I click on the Win8 option in GRUB I get an error screen and then it boots into Win8. Not sure if the error screen is important or not but I will try to get a screenie so it can be worked out if it is.

Either way, thank you very much for helping to point me in the right direction!

---

### Post by oldfred on 2013-03-10
I do not have UEFI but do a lot of my own custom chain load grub entries. 

Some of them give me odd errors and then work. Not sure why? 

Seems to be only with the newer versions of grub2, but has not been enough of an issue that I have filed a bug.

---

### Post by Dwack on 2013-03-10
This is the error I get upon selection of my Windows 8 option in GRUB:

```
error: file not found.
/EndEntire
file path: /ACPI(a0341d0, 0)/PCI(2, 1f)/UnknownMessaging(12)/HD(2, c8800, 96000, fc9cd5a5ae67fe40, ad,c7)
/File(\efi\Microsoft\Boot)/File(bootmgfw.efi)/EndEntire


Press any key to continue...

```

It doesn't seem to effect anything cause if left alone it still goes to Windows Boot Manager and I can pick Windows 8. It's just a little annoying seeing it.

Thanks again for all the hep. It's been so long since I last tried using a dual boot linux/windows machine, I really like the new look of Ubuntu and want to start using it more then Windows.

---

### Post by darkod on 2013-03-11
I also don't use UEFI boot but I believe you shouldn't have two EFI system partitions. I assume the uefi boot manager looks for files only in one place, the EFI system partition. So, with UEFI, disconnecting one disk while installing a second OS might not be possible.

I believe it HAS TO find the original EFI partition on sda during installation.

---

### Post by oldfred on 2013-03-11
@Darko
You can only have one efi partition per drive, but there have been several threads where users booted from systems with efi files on different drives. Not sure myself how that works and with all things UEFI it may depend a lot on the vendors specific implementation of UEFI.

While my error is not a long efi path, it is a path or UUID not found and then it boots. I have seen different version of Windows boot. 
Grub typically has two ways to set where to boot from one is the set root and the other is the search. Either works if correct. The set root assumes the device will not change and the search uses UUID so if device has changed like hd0 has changed to hd1 then it can search drives and fine the correct UUID. So I think one or the other is not setting it correctly but it falls back to a correct one and works?

If you want to experiment to see if a different verson boot stanza eliminates the error, these are other boot stanzas. You will have to edit to correct drive or UUID as these as jsut examples. You can add to 40_custom or 25_custom but just make title unique enough to tell them apart. 
It may be the add in modules (insmod). Those that are needed are supposed to be loaded automatically, but perhaps it needs to be manually loaded like in first example.

       Chainload entry:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)
[http://ubuntuforums.org/showthread.php?t=1934773](http://ubuntuforums.org/showthread.php?t=1934773)

This first one uses both set root & search. You can edit one or the other out and if correct locations either should work. The others search the system for the windows boot file. May be slower as it has to do a lot of searching?
```
menuentry "Windows 7 UEFI" {
  insmod part_gpt
  insmod fat
  insmod search_fs_uuid
  insmod chain
  set root='[COLOR=#000000](hd0,gpt2[/COLOR])'
  search --fs-uuid --no-floppy --set=root AEB6-3D84    
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

   menuentry "Windows 7 UEFI" {
  search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

   [http://www.insanelymac.com/forum/lofiversion/index.php/t186440](http://www.insanelymac.com/forum/lofiversion/index.php/t186440)
menuentry "Windows 7 UEFI" {
  search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi

```

---

