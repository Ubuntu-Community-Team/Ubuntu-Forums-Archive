---
title: "Dual-boot system stopped booting to both SO"
date: 2013-08-16
forum: Installation &amp; Upgrades
---

### Post by pauloborges on 2013-08-16
I have a dual-boot system with Ubuntu 12.10 (or 04, can't  remember right now) and Windows 8 working perfectly for almost 6 months.

  But yesterday the laptop was in Windows 8 and I put it to  sleep/hibernate (by closing the lid) and hours later I've opened it.  Strangely, a couple error messages showed up but honestly I ignored them  because at that time I thought they were not important.

  Anyway, Windows was asking to be restarted in order to complete the installing updates. So I did.

  Then the computer booted in grub rescue:

> error: file `/boot/grub/x86-64-efi/normal.mod’ not found
grub rescue> ls
(hd0) (hd0, gpt9) (hd0, gpt8) (hd0, gpt7) (hd0, gpt6) (hd0, gpt5)  (hd0, gpt4) (hd0, gpt3) (hd0, gpt2) (hd0, gpt1) (hd1) (hd1,gpt1) (cd0)
 
Then I used a livecd to try to recover the grub. First of all, I've generated a boot-info summary: [http://paste.ubuntu.com/5992517/](http://paste.ubuntu.com/5992517/).
  
Then I've tried to do the recommended boot-repair:

GPT detected. Please create a BIOS-Boot partition (>1MB,  unformatted filesystem, bios_grub flag). This can be performed via tools  such as Gparted. Then try again.   Alternatively, you can retry after activating the [Separate /boot/efi  partition:] option.
 
I don't know how to make such partition, then I've tried first to  activate the reffered option (in sda1). The boot-repair has been  completed with the following boot-info summary: [http://paste.ubuntu.com/5992562/](http://paste.ubuntu.com/5992562/).
  
But now when I restart the machine:

> [...]
PXE-E61: Media test failure, check cable
PXE-E61: Exiting PXE ROM.
No boot device found. Press any key to reboot the machine

 How can I fix this?

---

### Post by slw210 on 2013-08-16
Usually > PXE-E61: Media test failure, check cable means a bad/loose cable or failed hard drive. Might be something in the BIOS, you might check all the settings.

---

### Post by pauloborges on 2013-08-16
[SIZE=2]I did th[SIZE=2]e D[SIZE=2]ELL ePSA Pre-boot System Assessment and apparently there is no problem with any pi[SIZE=2]ece of hardware[SIZE=2], including [SIZE=2]hard drive.[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]

---

