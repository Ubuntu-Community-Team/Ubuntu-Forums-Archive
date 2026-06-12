---
title: "64 bit Woes"
date: 2013-04-07
forum: Installation &amp; Upgrades
---

### Post by vandalheart on 2013-04-07
I have a simple question, hopefully with a simple answer.

I have a laptop with a intel b960 sandy bridge, running windows 7 64 bit pre installed.

I read somewhere that I could install amd64 on a 64 bit system regardless of the manufacturer. I cant understand why the live USB fails to boot, and WUBI also throws an error right at the end of installation. I downloaded ubuntu 64 confindent that I would be able to run it alongside my other 64 bit system.

Linux Mint 32 bit installs fine, but I feel the extra processing power is wasted. Plus I simply do not like Mint. (if someone can convince me that I should be using 32 bit instead, I will likely download it.

Simply put, why can I run windows 7 64 bit, and not ubuntu 12.10 64bit? thank you, in advance.

---

### Post by oldfred on 2013-04-07
Is system perhaps UEFI?

Or did you download, verify and correctly write Ubuntu to flash drive.

What video do you have as that can often be an issue.

Do you have Mint installed. If so post this:
       sudo parted /dev/sda unit s print

---

### Post by MAFoElffen on 2013-04-07
Quicker, if you install the 64bit version ISO to USB... If you first "Try Ubuntu Without Installing"... If it can't run it, it will immediately tell you that your PC is not capable of running the 64bit OS and lock up at that message. But if you can run Win7 64bit, that's a good sign.

---

### Post by ahallubuntu on 2013-04-07
~

---

