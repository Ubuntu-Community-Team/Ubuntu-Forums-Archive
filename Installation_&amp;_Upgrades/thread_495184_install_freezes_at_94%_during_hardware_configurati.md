---
title: "install freezes at 94% during hardware configuration"
date: 2007-07-07
forum: Installation &amp; Upgrades
---

### Post by chuckado on 2007-07-07
When installing fiesty fawn i go through the installation and when it get to 94% it freezes on the hardware configuration.  the mouse stop working and the keyboard will not respond thank you to anyone who can help me.

---

### Post by Pumalite on 2007-07-07
Check iso. Do Md5sum. Check CD for corruption. Hardware is important. 256 Ram or less>'Alternate Xubuntu CD' Post your specs. Give more info and people will be able to help you better. Check your hardware for compatibility. Especially Graphics card.

---

### Post by chuckado on 2007-07-08
The monitor port is on the mother board it has a pentium 4 processor and 512 mb of ram.

---

### Post by Pumalite on 2007-07-08
With that amount of memory, with a good iso and a good burn, you should be able to use the Ubuntu Live CD without any problems. If you end up without a graphical interface; post back.

---

### Post by njparton on 2007-12-19
Did you resolve this issue? I'm having this problem with Gutsy AMD64 on my desktop PC :(

---

### Post by Pumalite on 2007-12-19
Give details of your problem. Post your specs. What iso are you using?

---

### Post by njparton on 2007-12-19
My specs are here:

[http://ubuntuforums.org/showthread.php?t=644919](http://ubuntuforums.org/showthread.php?t=644919)

I'm using the AMD64 desktop gutsy iso.  I installed it on my NAS from the same CD so I don't think the media is to blame.

Any help gratefully received :)

---

### Post by njparton on 2007-12-20
Can anyone else help me?

---

### Post by Pumalite on 2007-12-20
Do you also freeze at 94% of booting Live CD or stuck during installation after booting Live CD?

---

### Post by njparton on 2007-12-20
The live CD loads fine.  It's the installation that freezes during "hardware configuration".

I've not got anything outlandish so I'm wondering what it can be?

---

### Post by Pumalite on 2007-12-20
I imagine you already hit 'Esc' to see the output. So, what's the exact message. Could you post a screenshot?

---

### Post by njparton on 2007-12-20
It's frozen at the install stage still showing the desktop so the keyboard an mouse are dead.

I think grub must be installed last as I can't reboot it even into a terminal.

---

### Post by Pumalite on 2007-12-20
Try the Alternate CD. If it doesn't work, I'll give you some boot parameters to try.

---

### Post by njparton on 2007-12-21
The alternate CD freezes installing at 6% "verifying passwd".

Some helpful boot parameters would be great :)

---

### Post by Pumalite on 2007-12-21
Here is a guide and some to try:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317

---

### Post by njparton on 2007-12-21
Cheers, I'll give them a whirl now.

I guess I add them via F6 at the install screen?

---

### Post by Pumalite on 2007-12-21
Read the guide.

---

### Post by njparton on 2007-12-21
No luck so far with either of the CD's.  Whatever I do it hangs at different points.

Then next step is to start removing hardware. I'm thinking either my X-Fi card or some RAM to start with.  Everything else is kind of essential so I have no other option.

I'll also try "mem=1024m" to see if that helps too. Not sure if it likes 4GB?

I could also try the 32bit version...

Thanks for trying to help me out.

---

### Post by Pumalite on 2007-12-21
Try with 2 GB of memory.

---

### Post by njparton on 2007-12-21
This one's got me well and truely defeated... Tried about 30 times now and no joy. Tried 2GB ram, "mem=2048m", different hard drives, alternate CD, no joy.

My last resort is the 32 bit distro, but I can't face another try until tommorrow :(

---

### Post by Pumalite on 2007-12-21
You could try different distros to see if you are incompatible with Linux in general or Ubuntu in particular.

---

### Post by mad_max0204 on 2007-12-22
> **Pumalite said:**
> Here is a guide and some to try:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317


Okay. I see you posting in a lot of threads about people not being able to install Ubuntu on their computer. Most of them have a problem as I did. I solved mine with nolapci and acpi=off boot parameters. Works good but I still dont understand what they do. Now since you mentioned those parameters and you didnt want to explain your answer to my post, would it be so much trouble for you to do it here ? I think it would help a lot of people in resolving much problems with installation. Of course if you can explain. I'm not pushing any buttons but I'm just curious now come my hardware (as many other peoples hardware) dont even boot live install kernel out of the box.
This problem seems to be widely spread so any way to solve it would be much appreciated.
Another thing, when I do manage to load and install Ubuntu, after install it also hangs so I have to set those parameters to be permanent in boot loader.

Thanks

---

### Post by Pumalite on 2007-12-22
All you have to do is read the article I gave in your post. Linux has a learning curve. You have to read, to experiment and to learn. Just like any OS.

---

### Post by njparton on 2007-12-22
I have opensuse 10.3 and gentoo 2007 burnt to CD's so I'll try them.  The gentoo live CD has issues though so I'll start with opensuse and report back, probably tommorrow.

I was thinking about Mint too, but I guess that's too similar to ubuntu?

---

### Post by njparton on 2007-12-24
Well I cured my installation problem (kind of).  It was a faulty hard drive as neither Feisty or opensuse would install either.

After the first reboot following install, everything is fine.  I then make a few tweaks to menu.lst to ensure splash is disabled and remove "quiet", I then get X server problems on restart.

I haven't even got around to installing restricted drivers for my 8800GTS or anything!

This is just too much hassle and I've wasted about 10 hours trying to get this working.

Linux makes a great server OS, but is miles off as a desktop OS in my book :(

---

### Post by Pumalite on 2007-12-24
'It was a faulty hard drive as neither Feisty or opensuse would install either.'
After this, you can hardly blame Ubuntu. It's obvious is a matter of hardware.

---

