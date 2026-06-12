---
title: "Install Kubuntu FROM a USB Drive"
date: 2007-11-18
forum: Installation &amp; Upgrades
---

### Post by Brando569 on 2007-11-18
First off this isnt another thread about installing kubuntu onto a flash drive, its about installing kubuntu FROM a flash drive. the reason is my dvd drive broke and i dont have an OS on my computer.

I was wondering if this was possible and if it would be relatively easy. my problem as stated before is that i dont have an optical drive and i dont have an OS on my computer. i just ordered a new drive and it should be here in a few days but why wait? :)

i would think that it should be relatively easy, and that all i would have to do is break open a live cd iso, copy it to my usb drive, setup grub on it and go from there. If this is going to be a major PITA its not worth it, ill just use BartPE or DSL for the time being.

---

### Post by MajinCline on 2007-11-18
This thread gives a pretty good description of how to install normal Ubuntu edgy from a very small flash drive over a network: [http://ubuntuforums.org/showthread.php?p=1588127]("http://ubuntuforums.org/showthread.php?p=1694569")

This will also work for gutsy if you substitute it in the paths. I don't know if a kubuntu boot.img.gz even exists but you can always install kde afterward with> sudo aptitude install kubuntu-desktopSome more information on this can be found here: [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

After that is done you will have both gnome and kde but the same site also tells how you can just have kde: [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

Hope this was helpful :)

---

### Post by Rizado on 2007-11-19
It's more or less a piece of cake if you already have a linux system running you can work from:

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

Just make sure you read the kubuntu differences. I think you can skip the persistant partition if you only want a live system.

Also check out [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by Brando569 on 2007-11-19
im going to try the pendrive linux install (well i already have it extracted) but the pc im on here at work wont let me run syslinux, so ill just do it on my roommates pc when i get back to my room. thanks for the help.

---

### Post by Brando569 on 2007-11-19
pendrive linux works like a charm, im using it now. but i have to download kde since i hate gnome lol. thanks for the help.

---

### Post by Rizado on 2007-11-20
> **Brando569 said:**
> pendrive linux works like a charm, im using it now. but i have to download kde since i hate gnome lol. thanks for the help.But you could have used kubuntu on the pendrive instead :) It's just a few things that you need to think about:

```
Kubuntu difference: replace 'preseed/ltsp.seed' by 'preseed/kubuntu.seed'.
``` in syslinux.cfg

---

### Post by Brando569 on 2007-11-21
the thing is i wasnt using ubuntu i was using debian etch. im debating on getting a 4gb thumb drive in place of my 2gb so i can have UBCD4Win and Kubuntu 7.10 on there plus room for anything else i wanna put on there.

---

