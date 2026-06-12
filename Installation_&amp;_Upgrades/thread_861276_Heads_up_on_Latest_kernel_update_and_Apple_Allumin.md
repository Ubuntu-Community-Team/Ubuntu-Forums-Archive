---
title: "Heads up on Latest kernel update and Apple Alluminium Keyboards"
date: 2008-07-16
forum: Installation &amp; Upgrades
---

### Post by dantum on 2008-07-16
Hi

Just did an upgrade from 2.6.24.19.34 to latest 2.6.24.19.36 and apple alluminium keyboard no longer works once logged into gnome.

It works fine in console and on GDM login screen but once logged in, most keys are dead, and some type different characters.

I tried reverting to previous kernel but that just messed up my nvidia graphics card which was also a pain to get working last time.


Funmy enough I was just reading yesterday how Mr Shuttleworth thinks they made the right choice to make this a LTS release and I sort of agreed with him on that point but bugs just keep coming.

---

### Post by coffeecat on 2008-07-16
> **dantum said:**
> Just did an upgrade from 2.6.24.19.34 to latest 2.6.24.19.36 and apple alluminium keyboard no longer works once logged into gnome.

I've just done the same update and I cannot confirm this. Both the aluminium Apple keyboard and the earlier white plastic one are working fine with this latest kernel in Gnome here.

There is only one thing I can suggest. I usually use the white plastic keyboard with my Linux box - I use the aluminium one with my Mac Mini. I moved the aluminium one over to test after I read your post. A couple of weeks ago or more I was applying some Apple system updates to my Mini and included was a keyboard firmware update. At least that's what I remember. I thought it odd at the time. I'd never heard of firmware in a keyboard before. Anyway, if your keyboard hasn't been connected to a Mac for sometime perhaps it needs its firmware updating. Of course, I could be misremembering, but it might be worth checking this out.

No, I wasn't dreaming. I've just done a quick google. [Keyboard firmware update]("http://www.apple.com/support/downloads/aluminumkeyboardfirmwareupdate10.html"). :?

---

### Post by dantum on 2008-07-16
Hey,

I just reinstalled the kernel and the keyboard is working. I have previous version of apple keyboard too and it was working. 

I managed to sort out my graphics card issue too but now my sound card is not working. Audigy is listed in lspci but card is not working.

It was quite strange only 4 packages were updated. Libpcre3, linux-headers linux-image and linux-libc-dev.

Update.  Discovered the modules package was not installed and that caused sound to be broken. All fixed now.

---

### Post by coffeecat on 2008-07-18
Just thought I'd add for information, in case anyone stumbles across this thread...

I'm posting from Ubuntu 8.04 running in a VirtualBox VM with MacOS Leopard as host OS. I'm using the aluminium keyboard. I've just fully updated and now running with the 2.6.24-19.36 kernel. I didn't have any concerns that there would be problems with a Virtual Ubuntu and the Apple keyboard, but as you can see, there aren't.

---

