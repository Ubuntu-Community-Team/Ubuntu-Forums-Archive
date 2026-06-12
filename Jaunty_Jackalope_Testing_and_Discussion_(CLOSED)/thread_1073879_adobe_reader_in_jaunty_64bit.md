---
title: "adobe reader in jaunty 64bit"
date: 2009-02-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by lonniehenry on 2009-02-18
I have enabled Medibuntu repos and installed acroread, plugins, etc.  The reader opens and freezes.  If I try opening a multipage pdf, it will load first page and grey out.  I think that I am up to date.  I have used acroread in intrepid 64bit in the past but am puzzled about getting it to work in jaunty.
I would appreciate any help.

Running acroread from terminal gives the following: Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
Killed

I don't know what to do about it.

---

### Post by praxis22 on 2009-02-18
use evince :)

---

### Post by BwackNinja on 2009-02-18
Note how its loading it (or trying to) from /usr/lib/gtk-2.0/modules/ this would be getting the 64-bit version, while you'd want the 32-bit version because adobe reader is only 32-bit. I'd say that this is probably missing a dependency on a  32-bit libcanberra if it needs it, or something needs to be changed in how the program is trying to load itself to prevent trying to load 32-bit modules. Move the file temporarily (just rename to libcanberra-gtk-module.so.bak, I'd say not a good idea to keep it away, its for notification sounds, etc and it missing would make some other things complain) and then try opening adobe reader. If that works, then libcanberra is the only problem there, and file a bug report if there isn't one already.

---

### Post by lonniehenry on 2009-02-18
I do use evince, however there are some forms that allow filling in the blanks and saving, printing the form such as tax forms and business forms and adobe reader allows this. Acroread simplifies this for me as I can then email back the filled in forms.

---

### Post by rebegin on 2009-03-08
> **praxis22 said:**
> use evince :)

i do usually. but is there any way to set the background to something darker? as i would like to read a book but with white background my eyes are not happy...
i have the same problem as the topic opener :(

---

### Post by lonniehenry on 2009-03-08
I have gone through numerous updates to Jaunty and the original problem continues.  I have no idea on how to change background of document in evince.

---

### Post by michael37 on 2009-03-14
Acroread doesn't work for me on jaunty 64-bit.  

The Acrobat Reader window appears, the document renders, and then the whole window locks up.

Force quit aka Kill -9 is the only way to proceed.

Any ideas?

---

### Post by lamborghiniwang on 2009-03-14
same problem here.

---

### Post by Sockerdrickan on 2009-03-14
Adobe®+x86_64=:lol:

---

### Post by michael37 on 2009-03-14
> **Tux0r said:**
> Adobe®+x86_64=:lol:

Actually, seems to be Jaunty issue.  Used to work for me in Hardy.

---

### Post by lcohen999 on 2009-03-14
Add me to the Adobe Reader doesn't work list

it just hangs...

---

### Post by zenarcher on 2009-03-14
Add me, as well...

Cheers,
zenarcher

---

### Post by jp_coll2003 on 2009-03-14
> **michael37 said:**
> Actually, seems to be Jaunty issue.  Used to work for me in Hardy.

Same here. Only loaded the first page up and then froze. Had to go to Evince.

---

### Post by lonniehenry on 2009-03-15
Still not working.  I did the suggestion for temporarely removing libcanberra and it did not work. Worked under Intrepid.

---

### Post by BwackNinja on 2009-03-15
any new terminal output with temporarily removing libcanberra?

---

### Post by lonniehenry on 2009-03-16
Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory

so it must need a canberra-gtk-module - just a 32 bit one.

---

### Post by rebegin on 2009-03-16
> **lonniehenry said:**
> Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory

so it must need a canberra-gtk-module - just a 32 bit one.

i tried to install the 32 bit version of libcanberra-gtk-module but acroread still hangs after starting it.
i installed it with this command:

```
sudo dpkg -i --force-architecture libcanberra-gtk-module_0.11-1ubuntu2_i386.deb
```

any suggestion?

---

### Post by Timon&amp;Pumba on 2009-03-16
I have had the same problem as well. I need Acrobat, because Evince cannot handle transparency very well (gradients and stuff).

But a workaround that works for me is:
```
acroread --sync your.pdf
```

Good luck!

---

### Post by rebegin on 2009-03-16
> **Timon&Pumba said:**
> I have had the same problem as well. I need Acrobat, because Evince cannot handle transparency very well (gradients and stuff).

But a workaround that works for me is:
```
acroread --sync your.pdf
```

Good luck!

Thanks! works great.

---

### Post by lonniehenry on 2009-03-19
Acroread now works.  I am not sure which of the many updates did it.  I suspect that it may have happened with the ia32-libs updates yesterday and today.  Whatever did it, i am happy to be able to use it.

---

### Post by lcohen999 on 2009-03-20
> **lonniehenry said:**
> Acroread now works.  I am not sure which of the many updates did it.  I suspect that it may have happened with the ia32-libs updates yesterday and today.  Whatever did it, i am happy to be able to use it.

speak for yourself :)

---

