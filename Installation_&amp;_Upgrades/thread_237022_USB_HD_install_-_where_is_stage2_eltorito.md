---
title: "USB HD install - where is stage2_eltorito?"
date: 2006-08-15
forum: Installation &amp; Upgrades
---

### Post by pebo on 2006-08-15
I'm installing 6.06 on a USB external hard drive. It was all going fine, following instructions on [https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

Now I get to the instruction - 

Now that you have a kernel which can boot your USB drive it is time to put it on a bootable CD. You will need to download [WWW] this archive of the GRUB source code and extract it to obtain the "stage2_eltorito" file inside. Now that you have the needed files we can make your CD.

So I've downloaded grub 0.97 but where is the stage2_eltorito file? What am I missing?

---

### Post by John.Michael.Kane on 2006-08-15
In the grub97 folder open stage2 then look for this file **start_eltorito.S** . then open the doc folder and look for this file **menu.lst**

---

### Post by pebo on 2006-08-16
OK, I copied the start_eltorito.S file to the boot folder, then try to build the iso image, but this is what I get: 

I've got a feeling I'm being particularly dumb on this, but that USB install is sooo close!

---

### Post by pebo on 2006-08-16
Ok, I found a ready made stage2_eltorito in my suse install and was able to make the iso. Still can't get past the ubuntu menu though...more work to do
Tx for reply SD...

---

