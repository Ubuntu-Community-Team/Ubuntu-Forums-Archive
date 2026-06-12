---
title: "Need help making a fedora Live USB from within ubuntu..."
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by OmegaAI on 2010-06-15
Does anyone know how to do this? I have tried using the startup disk creater but it doesn't want to use the Fedora ISO...


How would I go about this in terminal?


Any help would be much appreciated.

---

### Post by lechien73 on 2010-06-15
The startup disc creator will only recognise Ubuntu ISO images. You could try UNetbootin, which can be installed through Synaptic, or the command line:

```
sudo apt-get install unetbootin
```

You can then run it from the Applications > System Tools menu.

---

### Post by OmegaAI on 2010-06-15
Hm... I completely forgot about that little bugger. Thanks for bringing it to my attention.

Where is the thanks button?

---

### Post by lechien73 on 2010-06-15
> **OmegaAI said:**
> Hm... I completely forgot about that little bugger. Thanks for bringing it to my attention.

Where is the thanks button?

No problem - you're welcome...it caught me out too!

If you wouldn't mind, please mark the thread as "Solved" using "Thread Tools" at the top of the page.

Thanks :)

---

### Post by jsiret on 2010-12-28
Hello, 

I am only running Ubuntu and I'd like to try out fedora, however Unetbootin creates a dodgey copy which gives the error...

no root device found boot has failed. sleeping forever
I've read this a lot, is there a way through ubuntu to create a live usb without unetbootin.

Regards,

Josh

Edit: tried running fedora's liveusb-creator.exe through wine, no luck at finding usb drive

---

