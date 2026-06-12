---
title: "hello, ubuntu cannot load, I see wants call administrator, what can I  do to resolve."
date: 2024-09-21
forum: Installation &amp; Upgrades
---

### Post by spi_ on 2024-09-21
hello,


ubuntu cannot load, I see wants I call administrator, what can I  do to resolve. I use Windows 10.


thanks.
Gr.

---

### Post by oldfred on 2024-09-21
What brand/model system?
What video card/chip?

When do you get message?

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version with your USB installer or any working install over somewhat older ISO. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)
    Note that grub only boots working Windows. Or if Window need chkdsk or is hibernated then grub will not boot it, but if UEFI install, you should still be able to boot from UEFI boot menu.

Windows updates can turn Windows fast startup or even UEFI Secure boot, which then can cause issues.

---

