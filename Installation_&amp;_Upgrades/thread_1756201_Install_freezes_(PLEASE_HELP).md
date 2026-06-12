---
title: "Install freezes (PLEASE HELP)"
date: 2011-05-12
forum: Installation &amp; Upgrades
---

### Post by Jason2302 on 2011-05-12
I'm sorry if I shouldn't put "PLEASE HELP" in the thread title, but I kinda wanna do this fast haha.

When I install Ubuntu 11.04 with Wubi, I get this freeze screen after I reboot and get past the Ubuntu splash screen: [https://dl-web.dropbox.com/get/2011-05-12_00-49-35_974.jpg?w=24b3001d](https://dl-web.dropbox.com/get/2011-05-12_00-49-35_974.jpg?w=24b3001d)

As you can see, it's a scrambled picture of my Windows desktop. This happens with every other version of Ubuntu also.

I'm running a 64-bit PC and I don't wanna waste another CD or use a USB to install, because I actually progress further in my efforts whenever I use Wubi.

Please help ASAP. I also have a question about updates but I'll save it for a more appropriate section.

EDIT: I guess this IS the appropriate section about my second question. I'll wait until my main problem is solved though.

---

### Post by Jason2302 on 2011-05-12
Ugh. Nobody can help??

---

### Post by bcbc on 2011-05-12
Try nomodeset: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
If that fails, try acpi workarounds.

that dropbox picture link doesn't work. Also post your hardware specs (brand/model/graphics card etc.) if nomodeset doesn't help.

---

### Post by Jason2302 on 2011-05-12
Noticed that :P
[http://img23.imageshack.us/img23/6692/20110512004935974.jpg](http://img23.imageshack.us/img23/6692/20110512004935974.jpg)

Also, I'm a complete noob with stuff like GRUB/terminal...

---

### Post by bcbc on 2011-05-12
> **Jason2302 said:**
> Noticed that :P
[http://img23.imageshack.us/img23/6692/20110512004935974.jpg](http://img23.imageshack.us/img23/6692/20110512004935974.jpg)

Also, I'm a complete noob with stuff like GRUB/terminal...

It's easier to troubleshoot from an Ubuntu CD as described in that link I showed. With wubi you probably have to uninstall reinstall each time. So that's what I'd suggest. It's not totally straightforward but I think it is clearly described there with images - so I don't think there's anything to add. 

Also don't forget to post your specs - that might help identify the boot workarounds required.

---

### Post by Jason2302 on 2011-05-12
> **bcbc said:**
> It's easier to troubleshoot from an Ubuntu CD as described in that link I showed. With wubi you probably have to uninstall reinstall each time. So that's what I'd suggest. It's not totally straightforward but I think it is clearly described there with images - so I don't think there's anything to add. 

Also don't forget to post your specs - that might help identify the boot workarounds required.

NVIDIA VEGA GT 240 graphics card
6 Gigs of RAM
[IMG]http://gyazo.com/20434aae408fe9e15803fe57f98ec0eb.png[/IMG]

---

### Post by bcbc on 2011-05-12
I'd normally suggest nomodeset for nvidia - but is that an optimus card? If it is I don't believe ubuntu supports that so it's probably booting an onboard intel graphics card.

---

