---
title: "Enabling dual boot of windows after rewriting MBR"
date: 2014-05-11
forum: Installation &amp; Upgrades
---

### Post by qutab on 2014-05-11
Hi. Some time ago I had two OSs on my hard disk and I could double boot Windows vista and Windows 8. Windows vista was the active partition (C:\ drive). Then I formatted the C drive and installed Ubuntu 12.04 on it. Now I have GRUB2 on my MBR but I want to boot Windows 8 also from it besides Ubuntu. How can I do it? I don't have very good Linux skills so please guide me here. I am attaching information about my hard disk that I got from running some script I found on these forums. Thank you very much. Any help is appreciated.

EDIT: I tried running the boot-repair utility and it gives me the following information:
[http://paste.ubuntu.com/7445554/](http://paste.ubuntu.com/7445554/)

---

### Post by oldfred on 2014-05-11
You cannot boot your Windows as currently configured.

Windows boots from a primary NTFS partition with the boot flag. Second installs put all boot files in that active partition. So when you deleted the primary partition with the boot flag you deleted all boot files.

You still have a primary NTFS partition sda3 with just bootmgr. You need to move boot flag or active partition to sda3. Grub does not use nor need boot flag.  And create a BCD with a Windows repair CD or flash drive or third party Windows tools in sda3. Then you can boot the Windows in a logical partition from the primary partition. Once Windows is repaired then you can run this to add it to grub menu.
sudo update-grub

       Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by qutab on 2014-05-11
Hi thanks for the reply. The thing is I don't want to boot Windows Vista which has a /bootmgr record as you said. I want to boot Windows 8 which is on sda5 which still has a bootmgr and also winload.exe (don't know what this means). Now, will the method you described above be still valid for that partition? I can set the boot flag of sda5 and rebuild bcd on sda5. But then I won't be able to see grub, or will I be?

---

### Post by oldfred on 2014-05-11
Re-Review link on 1000+ words, it also applies to Windows 8 in BIOS mode.
You cannot boot from a logical partition. You have to boot from a primary partition.
If you run Windows 8 repairs on the Vista partition it will update the bootmgr & BCD to also boot Windows 8.

---

