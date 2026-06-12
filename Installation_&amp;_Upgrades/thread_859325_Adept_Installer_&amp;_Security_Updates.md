---
title: "Adept Installer &amp; Security Updates"
date: 2008-07-14
forum: Installation &amp; Upgrades
---

### Post by fifth on 2008-07-14
Just noticed in my software sources that 'Important Security Updates' is not selected. However, when I try to tick the check box it returns to an unchecked state? So I'm not sure if I am getting security updates or not, anyone else noticed this?

In case its relevant, I have all sources checked, ie Recommended, Proposed, Unsupported, etc. I just cant select Security updates.

[Edit]
Just checked my sources.list and looks like I am getting security updates;

> deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security restricted main multiverse universe

Could be a bug with the Software Sources app?

---

### Post by solitaire on 2008-07-14
I've just noticed the same with my Install.

I have the Security deb lines in my list as well...

---

### Post by fifth on 2008-07-14
> **solitaire said:**
> I've just noticed the same with my Install.

I have the Security deb lines in my list as well...

Thanks for confirming solitaire.

Looking again at my source.list, not sure if this line should be there;

```
deb http://security.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe 
```

Seems to me that this duplicates the preceding lines?

---

### Post by solitaire on 2008-07-14
I've the same lines but it has: 

The ```

deb http://security.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe
```
is doubled in my list with 
```

#Added by software-properties

```
at the end of the second set of lines. (There is a few lines with that at the end.)
I hope it's just a Bug rather than an issue.

---

### Post by UKHacker on 2008-07-15
Just thought I'd post to say that I too have this problem but in Ubuntu Hardy. Don't actually know how to get the list of sources up to check that I am getting the updates.

---

### Post by Partyboi2 on 2008-07-15
> **UKHacker said:**
> Just thought I'd post to say that I too have this problem but in Ubuntu Hardy. Don't actually know how to get the list of sources up to check that I am getting the updates.
Alt+F2 then enter
```
kate /etc/apt/sources.list
``` Or open a terminal (Applications>Accessories>Terminal)
```
cat /etc/apt/sources.list 
```

---

### Post by UKHacker on 2008-07-15
> **Partyboi2 said:**
> Alt+F2 then enter
```
kate /etc/apt/sources.list
``` Or open a terminal (Applications>Accessories>Terminal)
```
cat /etc/apt/sources.list 
```

Thank You. Looks like I am receiving the security updates so it must just be some sort of bug with the software sources app.

---

### Post by fifth on 2008-07-15
After a bit of experimenting, the correct changes are being made to the sources.list file by Adept Installer. However, the current state is not reflected in the application - it always shows Security Updates as off.

Each attempt to check the updates box will enable/disable the security updates.

I've also found line in the sources which is effected is the multi item line;

```
deb http://security.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe
```

The individual lines I have in my sources file are not effected, ie in my case security updates will always be enabled due to the duplicates.

Was thinking of filing a bug on this, but for completeness would be good to have more feedback on whether everyone else has the individual lines for the security repo's as well as the 'all-in-one'line?

[Edit]
As an aside, Synaptic is unaffected and correctly comments/uncomments the security multi line - although the other individual lines remain.

---

### Post by solitaire on 2008-07-22
I'm using Ubuntu and i've got 3 extra set's of the "all in one" line  (dep http & dep-src http).

I'm gonna clean up the file and see what difffrence that makes.

---

### Post by solitaire on 2008-07-22
Cleaned out the Sources.list file. It's not made any diffrence. the "Important Security Updates" tick box.

Looks like it's a code problem with the "Software Sources" program.

---

