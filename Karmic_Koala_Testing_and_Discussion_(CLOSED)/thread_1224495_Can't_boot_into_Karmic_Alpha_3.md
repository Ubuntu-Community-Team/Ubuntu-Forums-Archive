---
title: "Can't boot into Karmic Alpha 3"
date: 2009-07-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by krausest on 2009-07-27
My Notebook (a HP hdx 9300) runs really nicely with Fedora 11, fine with 8.10 and works with 9.04, but with Karmic Alpha 3 it doesn't even boot anymore unless setting acpi=off or acpi=noirq (for both the installation cd and after installation on hd). 
Any idea what to do about it or what information except the screenshot to attach to a bug report?
The screenshot taken without the quiet but with the nosplash option is all karmic prints after booting without disabling acpi.

---

### Post by ranch hand on 2009-07-27
What happens when you try booting to 9.10 (recovery)?

You get a boot option there to boot to terminal with networking.  I would try the filesystem check first and then, in terminal with networking:
```

sudo apt-get update 

and 

sudo apt-get upgrade

```
and then try booting.

If this doesn't work, I would keep booting as you are and updating.  This should get straight in short order.

---

### Post by rtalcott on 2009-07-27
For me on one machine will boot from the cd...dumps me into the command line and asks for a login  and password...

This is a machine that runs 9.04...
rt

---

