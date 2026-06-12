---
title: "some boot options"
date: 2008-08-31
forum: Installation &amp; Upgrades
---

### Post by herrbrand on 2008-08-31
hello

I run an ubuntu server since 2 day's and I have some questions.

- how can I let programs start direct after the boot of linux?
- if I power on the server do I have to login before it comes online or is it direct operationel wen linux booted?
- when I power on the server there comes an screen where i can chose an operating system whiche disapere in 10 sec. how can I romove this screen?

*I am sorry for my bad english*

Robbert

---

### Post by SkonesMickLoud on 2008-08-31
> **herrbrand said:**
> - when I power on the server there comes an screen where i can chose an operating system whiche disapere in 10 sec. how can I romove this screen?

In a terminal, enter:

```
sudo nano /boot/grub/menu.lst
```

Then, look for this section:

```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

```

And make sure that the last line isn't commented out.

Then, you can set your timeout for something a bit lower:

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         [COLOR="Red"]10[/COLOR]

```

Yours is set to 10 right not, you can set it to what you like.  I personally have mine set to 3.  Not long enough to notice during a normal boot, but long enough to have a chance to enter the menu when you want to.

---

### Post by herrbrand on 2008-09-01
oke thanks.
I go test it directly :-P

do you also know where I can add programs to the boot, that when I stast my pc some programs are directly loaded.

*I'm sorry for my bad english*

Robbert

---

