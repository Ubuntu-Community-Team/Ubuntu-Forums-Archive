---
title: "monodevelop 6:10"
date: 2007-02-28
forum: Installation &amp; Upgrades
---

### Post by thick0 on 2007-02-28
I am running ubuntu 6:10 and maybe I am missing something obvious here...I install mono as per the ubuntu guide
[COLOR="Red"]
[INDENT]tim@sapphire:~$ sudo aptitude install mono mono-gmcs mono-gac mono-utils monodevelop
[/INDENT][/COLOR]
I list /usr/bin and I can see mono

[INDENT][COLOR="Red"]tim@sapphire:~$ ls /usr/bin/mono*
/usr/bin/mono      /usr/bin/mono-find-provides  /usr/bin/monop2
/usr/bin/monodiet  /usr/bin/mono-find-requires  /usr/bin/mono-service2
/usr/bin/monodis   /usr/bin/monograph
[/COLOR][/INDENT]

Errrrm, where is monodevelop? The install seems to have gone okay.

I really want monodevelop so I can play around with .NET basics under linux.

---

### Post by jethro10 on 2007-02-28
Not infront of my home PC rightnow but mine is in my home directory.

Dont think its a hidden directory

something like :-
cd ~/monodevelop-1.2
monodevelop

both commands from the terminal should get you there.
I cant get mine to work from a GUI

J

---

### Post by Dekster on 2007-02-28
Why not install it from the "add remove applications" installer? you can then find it in the Applications->Programming->MonoDevelop.

---

### Post by jethro10 on 2007-03-01
> **Dekster said:**
> Why not install it from the "add remove applications" installer? you can then find it in the Applications->Programming->MonoDevelop.

The downloaded version is a lot newer. However I suppose it more than enough to get you started.

J

---

