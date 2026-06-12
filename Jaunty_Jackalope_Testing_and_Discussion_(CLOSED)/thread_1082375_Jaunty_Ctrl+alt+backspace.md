---
title: "Jaunty Ctrl+alt+backspace"
date: 2009-02-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Sashin on 2009-02-27
In Jaunty they got rid of the Ctrl+alt+backspace hotkey to restart x. How would I go about adding it again?

---

### Post by terry_gardener on 2009-02-27
try the following link 

[http://albertomilone.com/wordpress/?p=335](http://albertomilone.com/wordpress/?p=335)

---

### Post by Sashin on 2009-02-27
It doesn't seem to work.

---

### Post by BGFG on 2009-02-27
think the terminal command is
```

dontzap --disable

```

I think! :)

---

### Post by Guidoo on 2009-02-27
> **Sashin said:**
> It doesn't seem to work.

You're sure you used the right parameter?
It says 
> Where “disable” means that Ctrl+Alt+Backspace restarts the xserver while “enable” means that it won’t.

To me, this is counterintuitive, as I'd expect it to be the other way around.

---

### Post by terry_gardener on 2009-02-27
after doing the steps on the site try rebooting. 
i forgot to mention to reboot after following the instructions
these are the steps i followed

---

### Post by Sashin on 2009-02-27
I tried both. It doesn't work, I think the point in that program is to disable it. Not to be able to enable it.

---

### Post by terry_gardener on 2009-02-27
it is parameter --disable 

but you have to reboot before the settings takes effect

---

### Post by BGFG on 2009-02-27
[QUOTE=]
To me, this is counterintuitive, as I'd expect it to be the other way around.[/QUOTE]

Ctrl+alt+Bkpsce 'zaps'
package 'Dontzap' disables aforementioned, ergo: 'dontzap --disable' thus enabling Ctrl+alt+Bkpsce.

---

