---
title: "Grub2 cannot detect Windows 8"
date: 2013-10-31
forum: Installation &amp; Upgrades
---

### Post by helloworld1215 on 2013-10-31
At installation it did not detect Windows. I mounted the Windows partition and have run os-prober with no results returning.
  I am able to boot Windows or Ubuntu by specifying the partition in  UEFI boot order. The bios does not appear to allow booting with legacy.  SecureBoot is on. 
  This is with Ubuntu 12.04 LTS on a Inspiron 15. 
  Here is the gdisk:
  ```
   1            2048         1026047   500.0 MiB   EF00  EFI system partition
   2         1026048         1107967   40.0 MiB    FFFF  Basic data partition
   3         1107968         1370111   128.0 MiB   0C01  Microsoft reserved part
   4         1370112         2394111   500.0 MiB   2700  Basic data partition
   5         2394112       544743423   258.6 GiB   0700  Basic data partition
   6       606183424       625140399   9.0 GiB     2700  Microsoft recovery part
   7       544743424       545230847   238.0 MiB   0700  (/boot)
   8       545230848       556949503   5.6 GiB     8200  (swap)
   9       556949504       606181375   23.5 GiB    0700  (/)
```  
When installing ubuntu, I believe I specified that the bootloader be installed on /dev/sda. 
  I added the following to /etc/grub.d/40_custom but booting ubuntu did not offer a grub menu:
  ```
menuentry "Windows 8" {
set root = "(hd0,4)"

  chainloader +1

  }
```  When booting I think I see "EFI Disk error" flash very quickly before Ubuntu starts booting.

---

### Post by oldfred on 2013-10-31
Grub2's os-prober and your entry are the old style BIOS boot entries that try to boot a Windows partition. With UEFI you chainload to the efi partition to boot Windows. 

Boot-Repair will add correct entries to 25_custom.
       Unable to chainload Windows 8 with Secure Boot enabled  Also post #11 on using refind
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464)

Several examples exist, either using search or specifing the UUID of the efi partition. Bug report above shows those also.


```
 menuentry "Windows 7 UEFI" {
  search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}


```

After any grub change to get menu updated.
```
sudo update-grub
```

If installer did not see Windows at all, did you still have fast boot or the always on hibernation still on. Or is it an Ultrabook with Intel SRT? See links in my signature for more info.

---

