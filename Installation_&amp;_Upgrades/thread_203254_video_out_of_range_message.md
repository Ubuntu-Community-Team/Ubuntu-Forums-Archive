---
title: "video out of range message"
date: 2006-06-24
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2006-06-24
Every time I reboot I get an Out of range message just prior to getting to the login screen.  How do I get rid of this ?

Thanks.

---

### Post by hippy4life on 2006-06-24
perhaps posting the error itself would be helpful.

---

### Post by wpshooter on 2006-06-24
[QUOTE=hippy4life]perhaps posting the error itself would be helpful.[/QUOTE]

That is the error "Out of Range"

Thanks.

---

### Post by hippy4life on 2006-06-24
[QUOTE=wpshooter]That is the error "Out of Range"

Thanks.[/QUOTE]

and there are no other errors in your boot logs?

---

### Post by wpshooter on 2006-06-24
[QUOTE=hippy4life]and there are no other errors in your boot logs?[/QUOTE]

I don't know any thing about boot logs !!!

---

### Post by rcarring on 2006-06-24
Xorg needs to be reconfigured.

Issue from commandline (boot, hit esc on grub, choose recovery mode)

```

dpkg-reconfigure xserver-xorg

```

And choose a conservative range such as 800 x 600 at 60 hz.

---

### Post by hippy4life on 2006-06-24
[QUOTE=wpshooter]I don't know any thing about boot logs !!![/QUOTE]

or manners either

none the less

less /var/log/messages  would be a good place to start, as would a 'please' and a 'thankyou'.

---

### Post by wpshooter on 2006-06-24
[QUOTE=rcarring]Xorg needs to be reconfigured.

Issue from commandline (boot, hit esc on grub, choose recovery mode)

```

dpkg-reconfigure xserver-xorg

```

And choose a conservative range such as 800 x 600 at 60 hz.[/QUOTE]

I tried changing the resolution at the desktop, down to 1024 x 748 - 60 hz, but when I say apply and then reboot the change to the refresh rate does not seem to take place.  Stays at either 85 or 75 hz.   Why is that ?

I believe this computer has an ATI 9200 video card.  Does Ubuntu Dapper Drake include a proper driver for this card ?

Thanks.

---

### Post by wpshooter on 2006-06-24
When I issued dpkg-reconfigure xserver-org it says:

Package xserver not installed, no other info found.

What does that mean ?

Thanks.

---

### Post by hippy4life on 2006-06-25
[QUOTE=wpshooter]When I issued dpkg-reconfigure xserver-org it says:

Package xserver not installed, no other info found.

What does that mean ?

Thanks.[/QUOTE]

it means you may have mis typed

try

dpkg-reconfigure xserver-xorg

---

### Post by wpshooter on 2006-06-25
Thanks.

---

