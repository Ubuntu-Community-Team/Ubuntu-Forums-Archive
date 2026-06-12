---
title: "Boot Straight To WINDOWS 10 (No GRUB)"
date: 2016-11-28
forum: Installation &amp; Upgrades
---

### Post by zakwanzen on 2016-11-28
Hi. First of all, thanks for taking your time to read this thread! 

I had formatted my laptop and install Windows 10 followed by Elementary OS.

But whenever i open my laptop, it straight boot to Windows 10. No GRUB screen appear. 

I had try these following solutions:
1. Run live USB Boot Repair ISO and click "Recommended Repair"
2. Run the following command in Windows 10:
bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi
bcdedit /set {bootmgr} path \EFI\ubuntu\grub64.efi

But those solution does not working.
Here is the link of pastebin (i got it from doing solution 1):
[http://paste.ubuntu.com/23550676/](http://paste.ubuntu.com/23550676/)

---

### Post by QIII on 2016-11-28
Duplicate of [https://ubuntuforums.org/showthread.php?t=2344864](https://ubuntuforums.org/showthread.php?t=2344864)

Closed.

---

