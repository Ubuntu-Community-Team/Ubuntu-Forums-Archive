---
title: "Natty installation freezes on boot"
date: 2011-05-14
forum: Installation &amp; Upgrades
---

### Post by keayz on 2011-05-14
I was running Maverick on my Toshiba Tecra A4 and clicked the button in the update manager to do a distribution upgrade to Natty. Since then it boots into the Ubuntu splash screen and goes no further. I've managed to get a terminal up and this is the message:

"Err upgrade tool signature
Could not resolve 'archive.ubuntu.com'
Err upgrade tool
Could not resolve 'archive.ubuntu.com'
WARNING: root:file 'natty.tar.gz.gpg' missing
Failed to fetch
Fetching the upgrade failed. There may be a network problem."

I've tried booting from an iso on CD (posted in General under 'Grub won't let me access BIOS') but the CD drive seems not to be working.

I have little knowledge of Linux, help please.

---

### Post by Hedgehog1 on 2011-05-14
keayz,

Do you have access to another computer (or the Windows side of your dual-boot) to create an 11.04 LiveCD/LiveUSB?

If so, please create one and boot your system from it.

When you boot from the 11.04 LiveCD/LiveUSB, you may have an upgrade patch offered in the 'install 11.04'.

[IMG]http://img848.imageshack.us/img848/874/upgradetonatty.png[/IMG]

If this is not offered, if you have your data in a separate '/home' partition you can reinstall 11.04 over your 10.10 '/' partition and be sure to not format the '/home' partition:

First, define your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

Then define your '/home' partition:

**[SIZE="4"]IF YOU ARE DOING AN UPGRADE, DO NOT FORMAT THIS PARTITION![/SIZE]**

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

***The Hedge***

:KS

p.s. To learn how to move your '/home' into it's own partition: **_[SeparateHomePartition]("http://www.psychocats.net/ubuntu/separatehome")_**

---

### Post by keayz on 2011-05-15
Thank you Hedgehog for all your advice. I can't try this as I am having problems with my CD drive - posted under 'General help' as 'Grub won't let me access BIOS' - and can't get my CD drive to work. I had hoped I could do something from the terminal but have no expertise in this.

---

### Post by MAFoElffen on 2011-05-15
> **keayz said:**
> Thank you Hedgehog for all your advice. I can't try this as I am having problems with my CD drive - posted under 'General help' as 'Grub won't let me access BIOS' - and can't get my CD drive to work. I had hoped I could do something from the terminal but have no expertise in this.
Welcome to Ubuntu.

Please go to this sticky and follow the troubleshooting Flowchart (Post 1):
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Veriy that you can display a Grub Menu (that grub 1.99 is booting) and that you can boot the kernel into text console (that the kernel can boot susccessfully)...

Successfully getting that far would narrow it down to a graphics  or desktop issue.  Since you are getting to Ubuntu's splash screen when it stops, I suspect it is graphics or desktop.

If it was a distribution upgrade  that brought you from 10.10 to 11.04, one major diffrence is that the norma/default graphics mode before xorg was started was 640x480x16bit, where some needed a nomodeset... Natty changed this a little, so now, more may be needed (see sticky) or taken away, based on what your PC is asking for.

---

### Post by keayz on 2011-05-16
Many thanks MAFoElffen, I have tried and can get a Grub menu with various kernels. I have tried to boot from each kernel but with the sahe freezing at the purple Ubuntu screen. If I press 'e' at the Brub boot menu I get the following (apologies for typing it but I can't print a screenshot for obvious reasons):

uuid  d9be0ea4-38ed-42b2-9be6-e8bbff311262
kernel  /boot/vmlinuz-2.6.35-28-generic root=UUID=d9be0ea4-38ed-42b2- (here there's a arrow to the right)
initrd  /boot/initrd.img-2.6.35-28-generic
quiet

If I now press 'c' I get a command prompt but it does not recognise the 'sudo service gdm start' from your sticky (error 27).

Can you advise further?

---

### Post by keayz on 2011-05-22
Help please anyone?

---

### Post by keayz on 2011-05-27
Thanks guys, but I guess it's the scrapheap for my old Toshie as there seems to be no solution to my problem.

---

