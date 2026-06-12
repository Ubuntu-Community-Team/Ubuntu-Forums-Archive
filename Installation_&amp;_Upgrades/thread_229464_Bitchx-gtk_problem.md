---
title: "Bitchx-gtk problem"
date: 2006-08-04
forum: Installation &amp; Upgrades
---

### Post by Amar_ze on 2006-08-04
I installed bitchx-gtk thru apt-get (apt-get install bitchx-gtk) but don't know how to start it.I read man pages of bitchx and I found xbitchx is X frontend so I guested that's it.When I run that command in console I got this error

```
amar@playboy:~$ xbitchx
bitchx:  unable to open font "default8x16", trying "fixed"....
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  18 (X_ChangeProperty)
  Resource id in failed request:  0x0
  Serial number of failed request:  101
  Current serial number in output stream:  102

```

Anyone can help me? :)

---

### Post by Necro-File on 2006-08-15
I am having the same problem. Launching "bitchx" from the terminal runs fine but the GUI version gives me the same error. I am not using the GTK version I just did apt-get install bitchx, though.

---

### Post by Nicolas Albani on 2008-01-25
Well ... in response to the original issue, the command you are looking for is gtkBitchX. You'll find it in ./usr/bin/gtkBitchX (if you had previously installed the bitchx-gtk application with your package manager).

Hope this will help.

---

