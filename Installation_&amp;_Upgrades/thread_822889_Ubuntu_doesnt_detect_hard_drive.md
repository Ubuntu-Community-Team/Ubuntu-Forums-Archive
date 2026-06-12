---
title: "Ubuntu doesnt detect hard drive"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by Forty-two on 2008-06-08
I've just recently built my first computer and decided to install ubuntu on it. I pop in the live cd, boot up the computer, it runs to the desktop, and I double click install. When I get to the partioner however it stalls at 46% then jumps to "prepare partitions" but there isnt anything to prepare, the box is empty. I loaded gparted and it managed to not detect my drive either. I attempted to use the gparted live cd but instead of a graphical interface I got a couple of prompts that I entered through and then a failure leading to a debian terminal thing. 

The drive is a SATA 160 GB and does appear in the bios. Does anyone have any idea what I could do?

Thanks

---

### Post by Pumalite on 2008-06-08
Try editing the boot line and adding at the end:
all_generic_ide

---

### Post by Forty-two on 2008-06-08
Sorry, Im very new to this. How do you edit the boot line?

---

### Post by Pumalite on 2008-06-08
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by Forty-two on 2008-06-08
I never experienced the "grub count down" that it talks about. Is this supposed to happen even on the live cd? Or should I make a permanent change with the second method?

Thanks

---

### Post by Pumalite on 2008-06-08
Do you see Grub? Explain the problem in a more detailed form.

---

### Post by Forty-two on 2008-06-09
Ok, heres the problem: I just built a brand new computer with an equally new hard drive. I boot the computer with the ubuntu live cd, however when I try to install it to the hard drive the installer does not detect said hard drive. 

If the grub looks anything like this:

[http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/IMG_0345.JPG](http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/IMG_0345.JPG)

then I dont see it during boot up.

Although I do see this screen:

[https://help.ubuntu.com/community/GraphicalInstall?action=AttachFile&do=get&target=boot.png](https://help.ubuntu.com/community/GraphicalInstall?action=AttachFile&do=get&target=boot.png)

but my keyboard is unresponsive when I try to click any of the options and I just wait for 30 seconds to pass and it automatically loads the first option, if thats at all relevant.

Thanks again

---

### Post by Pumalite on 2008-06-09
256 MB of RAM>Xubuntu ALternate CD. Other than that; you could use the Alternate CD to install and/or use some boot parameters:
noapic nolapic acpi=off pci=noacpi irqpoll pnpbios=off vga=0x317 vga=791 vga=788
To be used alone or in different combinations until you hit the right one.

---

### Post by Forty-two on 2008-06-09
I have 2 GBs of ram so I should be able to run ubuntu. Isn't the alternate desktop version of ubuntu only available in a text based installer and thus couldn't be run live? And if I cant see the grub screen how would I change the boot parameters?

Sorry for all of the rather basic questions.

---

### Post by dstew on 2008-06-09
I understand that the problem is that the Live CD (either Ubuntu or Gparted) is having trouble seeing your hard disk. To try the kernel parameter with a Live CD, you press F6 at the opening menu. That allows you to edit the kernel line. Put the kernel parameter(s) at the end of the line, and hit return. Try all_generic_ide first.

---

### Post by Forty-two on 2008-06-09
> **dstew said:**
> I understand that the problem is that the Live CD (either Ubuntu or Gparted) is having trouble seeing your hard disk. To try the kernel parameter with a Live CD, you press F6 at the opening menu. That allows you to edit the kernel line. Put the kernel parameter(s) at the end of the line, and hit return. Try all_generic_ide first.

Strangely my usb keyboard is completely frozen at that point, it works perfectly up until the opening menu. I even pushed the caps lock button to see the little light go on at start up and then at the menu the light was still on I just couldnt turn it off by pushing the caps lock button again. Could this just be a problem with my keyboard?

---

### Post by dstew on 2008-06-09
> it works perfectly up until the opening menuI am a bit lost here, I thought the opening menu was the first thing that comes up on the Live CD, so how can you be sure it was working until that point? I just want to understand which menu you are looking at...

---

### Post by Forty-two on 2008-06-09
It works in bios which is the first thing that pops up when I turn on the computer, then stops working during this screen: [https://help.ubuntu.com/community/GraphicalInstall?action=AttachFile&do=get&target=boot.png](https://help.ubuntu.com/community/GraphicalInstall?action=AttachFile&do=get&target=boot.png), and then works again after I assume the kernel is loaded and I have reached the desktop.

---

### Post by dstew on 2008-06-09
OK, that is a good explanation. I don't know how to solve it easily, since everything I can think of involves editing the kernel line.

When you have the Live CD running, you can see the hard disk partitions, correct? Have you tried to run GParted from the Live CD desktop instead of from its own live CD? I'm not at my Linux machine at present, so I can't be sure, but it might be in System --> Administration. If any of your hard disk partitions appear on the desk top, you have to unmount them before you can partition them (right click --> unmount). If the partitioner running on the desktop can see and partition the disks, maybe you will be able to install.

If none of this works, try the Alternate Install CD. It installs the same Ubuntu desktop system, using a text-based interface that might work more reliably. Get it from the [Download Ubuntu]("http://www.ubuntu.com/GetUbuntu/download") page, just check the box below the Start Download button.

---

### Post by Habbit on 2008-06-09
If you are unable to use your keyboard at boot time and it's a USB keyboard, you can try to activate a setting named something like "USB keyboard support in DOS" in the BIOS.

---

### Post by ErichZ on 2008-06-09
I am having exactly the same problem as forty-two (you're not using a Gigabyte mobo by chance, are you?). I also tried the all_generic_ide command recommended in the earlier post, but it didn't work. Any other suggestions? This is very strange to me, as my BIOS has no trouble finding the drive.

---

### Post by Pumalite on 2008-06-09
Burn a new CD. Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum, burn at 4x or less on good quality CD-R.

---

### Post by ErichZ on 2008-06-09
Not to be argumentative, but the disc I have burned was successfully verified. Furthermore, I'm experiencing this same problem when trying to install several different distributions of Linux (Fedora, openSUSE, etc. ALL fail to detect). The problem I'm referring to is the inability to detect my SATA HDD (not the keyboard problem that forty-two mentioned). Though, if you still think burning a new disc might work, I will try it.

---

### Post by Pumalite on 2008-06-09
Give it a try if you didn't do md5sum or you didn't burn at 4x or less on CD-R.

---

### Post by Forty-two on 2008-06-09
All of you rock.

I was able make the keyboard work everywhere through the bios and then all I had to do was add all_generic_ide to the boot parameters and it partitioned/installed perfectly through the graphic installer.

Victory!

---

