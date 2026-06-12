---
title: "grub update after install failed"
date: 2012-07-30
forum: Installation &amp; Upgrades
---

### Post by mortsemious on 2012-07-30
I just installed Ubuntu 12.04 32 bit on a laptop and set it up as a dual boot with windows vista. After the installation finished, I installed all available updates. When the grub update was being installed a window came up and asked where should grub install to. I did as recommended and installed to all available options. The window changes and i clicked the only available option and kept going. the updates finished and i rebooted. To my surprise, the computer booted directly into windows without grub showing up.

What should i do?

---

### Post by levlaz on 2012-07-30
> **mortsemious said:**
> I just installed Ubuntu 12.04 32 bit on a laptop and set it up as a dual boot with windows vista. After the installation finished, I installed all available updates. When the grub update was being installed a window came up and asked where should grub install to. I did as recommended and installed to all available options. The window changes and i clicked the only available option and kept going. the updates finished and i rebooted. To my surprise, the computer booted directly into windows without grub showing up.

What should i do?

This is the "[official guide]("https://help.ubuntu.com/community/WindowsDualBoot")" on dual booting. 

You may need to [reinstall grub]("http://www.av8n.com/computer/htm/grub-reinstall.htm"). 

Good Luck, 

Lev

---

### Post by mortsemious on 2012-07-30
i put my usb drive with the ubuntu installer in when attempting to reinstall grub, i boot my laptop and i get the grub screen. i can now boot into ubuntu, instead of the computer booting directly into windows. I'm guessing the grub on my usb is causing grub to show up after turning on the computer. Does this change anything?

---

### Post by levlaz on 2012-07-30
> **mortsemious said:**
> i put my usb drive with the ubuntu installer in when attempting to reinstall grub, i boot my laptop and i get the grub screen. i can now boot into ubuntu, instead of the computer booting directly into windows. I'm guessing the grub on my usb is causing grub to show up after turning on the computer. Does this change anything?

You are on the right track. 

I think you just need to reinstall grub, you want to see grub without having the live USB present. Just make sure you install it to the Master Boot Record and not just to the Linux Partition.. 

Just to make sure the grub screen shows both Windows and Ubuntu correct?

---

### Post by mortsemious on 2012-07-30
Yes and i can boot into windows without difficulty. i used ```
dpkg --get-selections
```
 to make a list of installed packages and couldn't find any references to the words grub or boot in said list. What's my next step?

---

### Post by levlaz on 2012-07-30
Follow[URL="http://www.av8n.com/computer/htm/grub-reinstall.htm"] this guide to reinstall grub. 
[/URL]

---

### Post by oldfred on 2012-07-30
There is now a gui tool to repair grub.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

If you installed grub to the Windows partitions, you will break Windows. Windows has to have its boot code in the NTFS partition boot sector. If Windows does not work post the link to BootInfo that Bootrepair creates.

---

### Post by levlaz on 2012-07-30
Oldfred.. thanks for the link. (and also the same link in the "absolute beginners" section.) I was not aware of this tool, this is great!

---

