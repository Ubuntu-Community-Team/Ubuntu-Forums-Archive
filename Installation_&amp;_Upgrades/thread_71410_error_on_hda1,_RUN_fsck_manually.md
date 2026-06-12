---
title: "error on hda1, RUN fsck manually"
date: 2005-10-03
forum: Installation &amp; Upgrades
---

### Post by Kristo on 2005-10-03
Hi,
Recently loaded HedgeHog 5.04 on a Dell.  Worked great for a month or so.  I enjoy it more than YDL (though they had great howto pages that were easy to find and use).  I beleive the problem happened during an upgrade that halted and caused me to do a restart.  My knowledge of linux is limited, so please direct me to specific help pages whenever possible.  Perfer to learn to fix it than reload.
Need basic comands to have read/write permissions and howto RUN fsck.
"UNEXPECTED INCONSISTENCES RUN fsck manually 
I/O error on hda1 logic blocks '3004425 through 3004430'."

---

### Post by myha on 2005-10-03
Try writing this in console to force fsck:
```
sudo shutdown -F -r now

```

edit:Try also this for help:
Ubuntu wiki:
[https://wiki.ubuntu.com/UserDocumentation#head-19e51e4331625e264a28ed6c484b946c86882d15]("https://wiki.ubuntu.com/UserDocumentation#head-19e51e4331625e264a28ed6c484b946c86882d15")
Unoficial ubuntu guide:
[http://ubuntuguide.org/]("http://ubuntuguide.org/")

---

### Post by Kristo on 2005-10-03
Thanks for the option. . .
Nope, "command not found"
;) Kristo




[QUOTE=myha]Try writing this in console to force fsck:
```
sudo shutdown -F -r now

```

edit:Try also this for help:
Ubuntu wiki:
[https://wiki.ubuntu.com/UserDocumentation#head-19e51e4331625e264a28ed6c484b946c86882d15]("https://wiki.ubuntu.com/UserDocumentation#head-19e51e4331625e264a28ed6c484b946c86882d15")
Unoficial ubuntu guide:
[http://ubuntuguide.org/]("http://ubuntuguide.org/")[/QUOTE]

---

### Post by Kristo on 2005-10-07
Still having a challenge learning how to "RUN fsck manually".  The guide links are great and non specific to help me fix the logic block errors.

Thanks,
Kristo

---

