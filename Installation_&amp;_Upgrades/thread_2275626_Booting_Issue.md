---
title: "Booting Issue"
date: 2015-04-27
forum: Installation &amp; Upgrades
---

### Post by Mike_Hughes on 2015-04-27
My Ubuntu Server 14.04 was booting fine. When I turned it on it would go through and boot. Now for some reason it gets to a screen that says GNU GRUB and sets there at 3 choices. *Ubuntu, Advanced options for Ubuntu and System setup. Before it would bring this screen up wait and if nothing was done would continue to boot up. I would like to have it do that again. How can I get that back?

---

### Post by Bashing-om on 2015-04-27
Mike_Hughes; Hello;

You do not say, but, ubuntu does boot when you press enter with *ubuntu selected ?
That condition can happen IF ubuntu did not start properly on the former startup, OR maybe there has occurred a mishap in grub's config file ?
Show us the file that might be of question:
```

cat /etc/default/grub

```

a simple look at the 
[INDENT][INDENT][INDENT]simple things 1st
[/INDENT][/INDENT][/INDENT]

---

### Post by Mike_Hughes on 2015-04-27
Here is what the cat /etc/default/grub got me:

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=2
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""

---

### Post by Bashing-om on 2015-04-27
Mike_Hughes; Humm ..

I really do not see a problem :
this:
> 
GRUB_HIDDEN_TIMEOUT_QUIET=true

Says do not display the menu;
and this:
> 
GRUB_TIMEOUT=2

Says you have 2 seconds to change your mind from booting the default selection;

What results:
```

sudo update-grub

```
and rebooting twice ?
On the 2nd boot, is the performance as expected ?

[INDENT][INDENT]grub, it do be a complex system
[/INDENT][/INDENT]

---

