---
title: "Installing Lucid with no drives..."
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by GoggleEyedSalmon on 2010-09-02
So, I have a 5 (ish) year old Sony Vaio (PCG-K315) that I want to install Ubuntu on. 

The first problem is it doesn't boot from USB and I cannot find any BIOS updates that allow it to do that. 

The second problem is that the CD drive is very temperamental, sometimes I can get to the menu of the Ubuntu CD but if I select install it reads for 15-30 minutes and then returns any of a number of errors. I get the same problem trying to load Kubuntu and Windows from CD. I know my CD is good because I have installed Ubuntu onto other machines with it.

I have a Macbook Pro and a 2.5" caddy that I was hoping I could use to install Ubuntu onto the Vaio's drive and then just pop it back, but no luck, it just sits there flashing an underscore at me. Are there any other steps I need to take to make it boot when I put the drive back in the Vaio?

Any help would be appreciated a LOT!

EDIT:
Oh yeah. I also tried partitioning the HD and putting the install files on one bit to install to the other. But then it just said operating system not found.

---

### Post by Master Cabbage on 2010-09-02
For the PCs with the unreliable CD drive, I would try to use an External CD drive (borrow one from a friend) and see what happens when you try installing Ubuntu on that computer from there.

---

### Post by GoggleEyedSalmon on 2010-09-03
Unfortunately the laptop won't boot from USB so an external CD drive isn't going to work either I don't think.

---

### Post by Master Cabbage on 2010-09-03
Perhaps the thing to do would be to install Ubuntu on your computer using the Wubi program. Wubi is an Ubuntu installer that runs through Windows and is very easy to use. It won't remove Windows from your computer, but it will give you the option to boot with Ubuntu at start-up and it will work nearly as well as a Ubuntu-only install on your computer. I would recommend giving Ubuntu 17 - 20 gigabytes to work from when it asks how many gigabytes you would like to dedicate to Ubuntu in the Wubi installer, hopefully you have the free space.

---

### Post by C.S.Cameron on 2010-09-03
You could also try the Unetbootin install to hard drive method.

---

### Post by GoggleEyedSalmon on 2010-09-03
Master Cabbage: I don't already have Windows installed. The Vaio drive is blank.

C.S.Cameron: Thanks I will give Unetbootin a try.

---

### Post by azertyh on 2010-09-03
yes, unetbootin can install ubuntu from an hard disk. just download the iso in your hard disk and let unetbootin install it.

---

### Post by GoggleEyedSalmon on 2010-09-05
Partial success! and failure,

I have used unetbootin to install ubuntu to the VAIO's HD, 4 or 5 times now....

Apparently installing with unetbootin just gives you a temporary install (squashfs) that you can then boot and do a full install from? So I tried this but it wouldn't install to the same drive that Ubuntu was running from. So I tried to pre-partition the drive ready for the swap and root but it still gave me the same problem (screenshots below).

So am I doing something wrong because this problem seems to defeat the point of unetbootin???

Are there any other ways to do what I'm trying to do? Which is basically install Ubuntu onto an HD in a USB caddy that I can then pop into the VAIO and boot from it?

Thanks

---

### Post by GoggleEyedSalmon on 2010-09-06
Bump

---

