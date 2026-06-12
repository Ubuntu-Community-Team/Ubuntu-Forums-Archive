---
title: "PC Card service"
date: 2005-04-29
forum: Installation &amp; Upgrades
---

### Post by LinxNew on 2005-04-29
Hi,
I'm installing 5.04 on a laptop Toshiba.
After I choose language, Ubuntu try to auto detect hardware, but when arrive at 98%  it's block. 
THere is this issue :
'starting pc card services...'

What can I do ?  ](*,) 

should I forget to install Ubuntu on my laptop ?   [-X 

Thanks for your support.

---

### Post by LinxNew on 2005-04-29
Ok,

I'm tring to boot in expert mode. in this mode I  can choose to doesn't detect pc card.

But now i need your help.

I'm go to explorer this step :  Detect and mount CD-ROM
I don't know what modules are necessary, so I leave all modules enable.
When arrive at 98% for start PC Card Service I choose no, and so I can continue with insallation.
In the next screen I have some error :

Unable to load some modules :

ide-mod (Linux IDE driver)
ide-probe-mod (Linux IDE probe driver)
ide-detect (Linux IDE detection)
ide-floppy (Linux IDE floppy) - I don't have a floppy -

I choose to continue and installation ask if I want to use hdparm. I doesn't set any parameters.

After scanning CD-ROM I have this message: CD-ROM detected (I have a dvd-ram. is it correct ?)

I'm arrived at this point. 

Some question:

- I doesn't load PC Card, is this a problem ?
- Dome modules aren't loaded. is this a problem ?

I see at linux laptop that my TOshiba is ok for debian pack. So I think that there isn't any problem with Ubuntu.

---

### Post by az on 2005-04-29
"When arrive at 98% for start PC Card Service I choose no, and so I can continue with insallation."

When you are not in expert mode, doing this makes your computer crash, right?

It is not loading the proper module.  Try booting a live cd and see what module your pcmcia controller is.  Boot the Hoary installer and use the command to prevent pc card services from being scanned/loaded (see one of the F1 F2 F3... help pages after you boot the installer)

Once installed, put the module name in /etc/modules so that it loads and you can use your pcmcia card.  You may have to install pcmcia-cs if it is not installed (since it was not used in the installation)

---

