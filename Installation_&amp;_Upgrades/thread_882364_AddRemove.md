---
title: "Add/Remove"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by Pen3356 on 2008-08-06
For some reason every time I try to add/remove/upgrade a program it says that an error occurred and that I should manually run the "dpkg--configure-a" to correct the problem.  I'm really frustrated, I'm new to Ubuntu and I just simply don't know what to do.

---

### Post by iaculallad on 2008-08-06
> **Pen3356 said:**
> For some reason every time I try to add/remove/upgrade a program it says that an error occurred and that I should manually run the "dpkg--configure-a" to correct the problem.  I'm really frustrated, I'm new to Ubuntu and I just simply don't know what to do.

Go to Applications->Accessories->Terminal, this should open your terminal and issue the command below to correct the error: Supply your password (password not being echoed back on screen is normal, just enter your password and hit enter key).

```
sudo dpkg--configure-a
```

---

### Post by Pen3356 on 2008-08-06
> **iaculallad said:**
> Go to Applications->Accessories->Terminal, this should open your terminal and issue the command below to correct the error: Supply your password (password not being echoed back on screen is normal, just enter your password and hit enter key).

```
sudo dpkg--configure-a
```

I just tried that, and it says "command not found"

---

### Post by iaculallad on 2008-08-06
> **Pen3356 said:**
> I just tried that, and it says "command not found"

That would be:

```
sudo dpkg --configure -a
```

There's a space between dpkg and --configure and -a

---

### Post by Pen3356 on 2008-08-06
> **iaculallad said:**
> That would be:

```
sudo dpkg --configure -a
```

There's a space between dpkg and --configure and -a


Thank you so much! I felt very illiterate. [I installed Ubuntu about 2 days ago; I left windows]

---

### Post by iaculallad on 2008-08-06
That's a good choice. Goodluck and Welcome to Ubuntu (Linux in General).

---

### Post by Pen3356 on 2008-08-06
> **iaculallad said:**
> That's a good choice. Goodluck and Welcome to Ubuntu (Linux in General).

Thank you, Which Messenger Program do you recommend in which the webcam can be used?

---

### Post by iaculallad on 2008-08-06
> **Pen3356 said:**
> Thank you, Which Messenger Program do you recommend in which the webcam can be used?

Try Ekiga. It supports webcam and VoIP (SIP) and offers SIP messages too.

---

### Post by Pen3356 on 2008-08-06
> **iaculallad said:**
> Try Ekiga. It supports webcam and VoIP (SIP) and offers SIP messages too.

will that work with somebody that has MSN?

---

### Post by iaculallad on 2008-08-06
> **Pen3356 said:**
> will that work with somebody that has MSN?

Try to read this [page]("http://wiki.ekiga.org/index.php/Which_programs_work_with_Ekiga_%3F") and find it out yourself.

---

### Post by Pen3356 on 2008-08-06
> **iaculallad said:**
> Try to read this [page]("http://wiki.ekiga.org/index.php/Which_programs_work_with_Ekiga_%3F") and find it out yourself.

Once Again, Thank You!

---

