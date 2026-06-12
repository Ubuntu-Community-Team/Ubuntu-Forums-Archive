---
title: "GRUB2 hangs if external drive is connected"
date: 2012-05-13
forum: Installation &amp; Upgrades
---

### Post by cosmicgr on 2012-05-13
Hello
I have GRUB2 on my laptop's internal SATA, with Win7 and Ubuntu 10.10. I also have an external USB HDD (WD 320GB) with Ubuntu 10.10 and its own GRUB2 on the external drive. This external Ubuntu with its own GRUB2, works well on other computers, which do not have GRUB2 on their internal HDDs. But if I plug in my external HDD in my laptop, which already has its own copy of GRUB2, it hangs. I mean when i power on, i all i get is a blinking cursor on the top left with black screen, no GRUB2 boot screen or anything. I have tested my external USB with other computers which have GRUB2 installed on their internal drives. I get the same problem. What could be the reason for this strange behavior?

---

### Post by wilee-nilee on 2012-05-13
I have a 2 terrabyte external that does as well I just don't boot with it plugged in. 

Why it does not, no idea.

---

### Post by cosmicgr on 2012-05-13
I tried another external, same problem. I guess since both (internal and external) drives have GRUB2, they may get confused somehow and none of them starts GRUB2! But this is  a bug indeed.. I cannot boot my external HDD in my laptop due to this. As a temporary fix, I have installed GRUB legacy in my external HDD which chainloads GRUB2 for Ubuntu 10.10. But this is a just a stupid workaround.

---

### Post by wilee-nilee on 2012-05-13
> **cosmicgr said:**
> I tried another external, same problem. I guess since both (internal and external) drives have GRUB2, they may get confused somehow and none of them starts GRUB2! But this is  a bug indeed.. I cannot boot my external HDD in my laptop due to this. As a temporary fix, I have installed GRUB legacy in my external HDD which chainloads GRUB2 for Ubuntu 10.10. But this is a just a stupid workaround.

I suspect the bios to be honest this only happens with my Toshiba laptop, but not with my acer netbook, same OS's

---

### Post by cosmicgr on 2012-05-13
I tried my friend's Toshiba laptop too..Same thing happens! Would try in some other laptop. Are you sure its with BIOS? I guess its with GRUB..as my HP and my friend's Toshiba have different BIOS, yet the same behavior with GRUB2..

---

### Post by dino99 on 2012-05-13
i beleive you should consider to not using uuid with grub, as they are dynamically set when you plug it, better to set a label to this external drive, then using it inside grub

---

### Post by cosmicgr on 2012-05-13
Thanks for suggestion, but the problem is that GRUB2 doesnt show any message at all on power up. If it was due to UUID, it wud have thrown some error like so and so device does not exist or something like that.. I use my external on various laptops and desktops,  it always boots up.. Only if the host system also has the same GRUB2 on its internal disk, then this situation arises.

---

### Post by oldfred on 2012-05-13
Just to see if there is something in the configuration that looks wrong, run this report. If it is the BIOS then we will not know. We have seen were some systems will not boot from one computer but will from another due to BIOS settings.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by YannBuntu on 2012-05-14
> **oldfred said:**
> Just to see if there is something in the configuration that looks wrong, run this report. If it is the BIOS then we will not know. We have seen were some systems will not boot from one computer but will from another due to BIOS settings.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

or easier: indicate your [BootInfo URL]("http://ubuntuforums.org/showpost.php?p=11136267&postcount=1") ;)

---

### Post by choppyfireballs on 2012-05-14
I probably missed this somewhere who is your laptop manufacturer because i know that some manufacturere's bios hangs when you have any kind of usb storage plugged in that's not bootable in the case of grub it might just be making it to the grub2 before it hangs.

---

