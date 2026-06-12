---
title: "boot hangs at running /scripts/local-top"
date: 2007-04-02
forum: Installation &amp; Upgrades
---

### Post by winter42mute on 2007-04-02
hi.  i recently did a fresh install of edgy and everything went great.  my only problem is that every third boot or so my system hangs at "running /scripts/local-top" for up to several minutes, and then eventually proceeds.  other times things are super-fast and boot goes without a hitch.  what gives?  via google searching i've seen references to a boot-time race issue (?) with feisty but am not really sure how to proceed.  i figured i'd ask the experts before i tried something and got into trouble...

any suggestions as to how i can remedy this are greatly appreciated.

thanks!

---

### Post by amohanty on 2007-04-03
in /boot/grub/menu.lst
(please back it up first)

sudo cp /boot/grub/menu/lst /boot/grub/menu.lst.org

edit the file
sudo gedit /boot/grub/menu.lst

look for  
kernel.... ro quiet splash

Take out the **quiet splash** part.

Reboot. see where it actually hangs and then post that.
Also when you do that, you will no longer see the nice splash screen, just a bunch of text scrolling past quickly. Add the words back to get it.

HTH
AM

---

### Post by winter42mute on 2007-04-03
first of all, thanks for replying.  so here's where it gets interesting ;)  i had previously removed 'quiet', which is why i knew the hang was happening when /scripts/local-top was running.  however, when i removed the boot splash screen, things got much better (!).  i rebooted 5 times in this configuration and 3 times it went very fast, no delay at all.  two times there was a slight delay (<30 sec) after ide hd discovery but nothing like the minutes delay i had earlier. is this surprising?  it is to me.  anyhow, i'll definitely keep an eye on it.  i may not be the biggest fan of eye candy but i did like the edgy boot splash screen, so i'm sad to see it go.  if you have any further thoughts i'd love to hear them.  again, thanks!

---

### Post by amohanty on 2007-04-04
AFAIK it should not affect usplash. Try reinstalling usplash and see if it works.

AM

---

