---
title: "User Name Password Live MATE"
date: 2016-06-29
forum: Installation &amp; Upgrades
---

### Post by borgward on 2016-06-29
What is the user name and password for ubuntu mate 16.04 live

---

### Post by howefield on 2016-06-29
Try ubuntu for the user name and no password.

---

### Post by borgward on 2016-06-29
that does not work

---

### Post by Liam_Murphy on 2016-06-29
Try

```
sudo -i
```

And it shouldn't ask you for a password.

---

### Post by RobGoss on 2016-06-29
I have never been ask for a User name and Password while running a live Ubuntu session so this is a first time I'm hearing about this issue

Is this when you log out and then try login back in to a Live session?

---

### Post by borgward on 2016-06-29
After issuing the su command.

---

### Post by Liam_Murphy on 2016-06-29
Yeah I second what the others are saying, that is very uncommon for Ubuntu live USB's.

At this point I'd say just post on the Ubuntu MATE forums, can probably hear from a MATE user quicker there.

---

### Post by &amp;KyT$0P# on 2016-06-29
> **borgward said:**
> After issuing the su command.
root doesn't have a password by default on Ubuntu-based systems.  Use instead [FONT=Courier New]sudo su[/FONT]

---

### Post by borgward on 2016-06-29
in live session sudo su does not ask for password. How to get back to the normal user prompt from the # prompt? I tried su and sudo su to no avail.

---

### Post by deadflowr on 2016-06-29
ubuntu mate's live session user is ubuntu-mate.
live sessions never have a password.
So if you are trying to run a ctrl+alt+F1-6 just type ubuntu-mate and hit enter twice.

> root doesn't have a password by default on Ubuntu-based systems.
Root has a password.
However it is locked and disabled.
But it does exist.

Edit: ^^ I mean on an installed system.
Live sessions are much different in terms of passwords and what nots.

---

### Post by deadflowr on 2016-06-29
> **borgward said:**
> in live session sudo su does not ask for password. How to get back to the normal user prompt from the # prompt? I tried su and sudo su to no avail.

exit

---

