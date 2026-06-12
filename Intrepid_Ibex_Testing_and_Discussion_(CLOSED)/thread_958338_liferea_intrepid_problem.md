---
title: "liferea intrepid problem"
date: 2008-10-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by sfusion on 2008-10-25
Hi Everyone,

Having trouble running Liferea. As soon as the window loads it crashes.

I ran in terminal and this was the output:
```
:~$ liferea

(liferea-bin:9524): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
Segmentation fault
```

Can anyone help me out?

Thanks:)

---

### Post by spupy on 2008-10-25
Could you paste what version of liferea you are running?

Also, one thing you could try:
- **backup** the folder ".liferea_1.4" from your home folder.
- delete it. **But make sure you have the backup!**
- try to start liferea.
- if nothing has changed restore the backup to ".liferea_1.4".

---

### Post by sfusion on 2008-10-25
Thank you

```
:~$ liferea -v
liferea 1.4.18
```

I tried removing the .liferea1_1.4 folder, unfortunately my problem persists. :confused:

I have also ran 
```
sudo apt-get remove --purge liferea
```

and
```
sudo apt-get install liferea

```
Still no solution

---

### Post by spupy on 2008-10-25
Can you try to install a different version of liferea, using the Synaptic package manager?

---

### Post by sfusion on 2008-10-28
there are no other versions currently available in the synaptic package manager.

I have tried installing a version from getdeb which also fails with the same error

---

