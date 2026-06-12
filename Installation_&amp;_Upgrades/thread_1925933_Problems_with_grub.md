---
title: "Problems with grub"
date: 2012-02-15
forum: Installation &amp; Upgrades
---

### Post by Morrigan69 on 2012-02-15
I had installed Windows 7 on my computer and wanted to set up dual boot with Ubuntu 11. Now I can only load ubuntu.. At first bootloader wasn't prompting at all but I solved that problem with grub customizer.
Now the problem is that on windows is not listed on menu load. I tried to add it manually in etc/grub.d/40_custom but nothing changed.
I am new to linux and I really don't know what else to do since I tried all tutorials there.. Here are current results of running that boot_info_script if helps:
[http://pastebin.com/GnwFQ9fq](http://pastebin.com/GnwFQ9fq)

---

### Post by darkod on 2012-02-15
Did you install with the manual method? Did you delete any partition that said System Reserved?

With win7 microsoft started putting two boot files on a small separate partition. If you delete this partition you can't boot win7 any more because the boot files are gone. It seems that is what happened.

You can try repairing the win7 install if you have the dvd. But first boot ubuntu and open Gparted (you might need to install it). Then right-click /dev/sda2 and select Manage Flags. Set the boot flag on /dev/sda2, not it's on /dev/sda3. It needs to be on the win7 partition.

Then boot with the win7 dvd and do the repair process 3-4 times, sometimes it needs to be done more than once. See if win7 starts booting directly. The repair will delete grub2 from the MBR but don't worry about this. You can reinstall it easily with the ubuntu cd.

First try to repair the win7 boot, when it starts booting fine post here and we'll help you reinstall grub2. DO NOT reinstall ubuntu again just because grub2 is not showing up, that will mess it up further.

---

### Post by Morrigan69 on 2012-02-19
Thank you for your fast answer. I finally got back my Windows CD and saw error that it's not compatible with the version I have (even though there are all versions on my CD) and then remembered that I got that Windows installed (cracked) when I bought my laptop -.- Is there a way to find and download the exact one I need (I'm trying to avoid asking them first)?

---

### Post by darkod on 2012-02-19
I'm not sure about that.

Earlier there was a free download of win7 rescue cd (you can't install with it, just repair) but now I think they charge $10 for it. If you are interested this was the page:
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

I am not aware how would you find a download that can match your win7.

---

### Post by Morrigan69 on 2012-02-22
I couldn't get CD to repair it so I installed new Windows. I got grub loader back but again there's no Windows on the list (I did update). I can't open grub customizer cuz it crashes since I was manually adding windows to the list before and now I can't find or remember which files I edit... New script outcome, if needed: [http://pastebin.com/23CTD460](http://pastebin.com/23CTD460)

---

### Post by dino99 on 2012-02-22
[http://www.google.com/search?q=grub2%2Bw7%2Bubuntu](http://www.google.com/search?q=grub2%2Bw7%2Bubuntu)

---

### Post by darkod on 2012-02-22
Try to reinstall grub2 booting with the cd in live mode and executing:

```
sudo mount /dev/sda3 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

That should sort it out.

---

### Post by Morrigan69 on 2012-02-22
When I said "I got grub loader back" I meant that I did that... :D Just to make sure I've done it once again and still same problem.. =/

---

### Post by darkod on 2012-02-22
Yes, but your results said "grub2 is installed on /dev/sda and looks for cd".

It should say something like "looks for core.img at sector XXXX....etc"

Doesn't look installed OK, looking at the right partition. That's why I suggested to reinstall it on the MBR which should have sorted it out, depending how you installed.

---

### Post by Morrigan69 on 2012-02-22
Yay, I finally fixed it somehow and not even sure how exactly :D However, my grub customizer still crashes but don't care, I don't need it anymore. Really BIG thanks for your assistance!

---

