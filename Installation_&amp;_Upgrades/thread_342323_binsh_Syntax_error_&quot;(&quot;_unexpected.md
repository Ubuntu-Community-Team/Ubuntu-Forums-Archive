---
title: "/bin/sh: Syntax error: &quot;(&quot; unexpected"
date: 2007-01-19
forum: Installation &amp; Upgrades
---

### Post by ubuntu_jazzbach on 2007-01-19
HI !!!

I'm really GOING CRAZY !!!! I can't compile the ieee subsystem of my Intel/ PRO ipw2200 WIRELESS driver. As soon as I run the make command, I have the following error:

/bin/sh: Syntax error: "(" unexpected
make: *** [check_old] Error 2

I've followed this thread ([http://www.ubuntuforums.org/showthread.php?t=340863&highlight=ipw2200+error](http://www.ubuntuforums.org/showthread.php?t=340863&highlight=ipw2200+error)) and googled the issue but it's no use. I've been trying a whole month to fix this and haven't found any solution.

Please, help me

---

### Post by po0f on 2007-01-19
ubuntu_jazzbach,

From a terminal:
```
[FONT="Courier New"]$ sudo dpkg-reconfigure dash[/FONT]
```

Answer "No".

---

### Post by ubuntu_jazzbach on 2007-01-19
sniff, sniff !!! It didn't work po0f

---

### Post by po0f on 2007-01-19
ubuntu_jazzbach,

Was it a "error: $: command not found" error?  The dollar sign represents your terminal prompt, and is not part of the command.  The command is `sudo dpkg-reconfigure dash`.

If it was another error, post it; maybe we can work through it.

---

### Post by ubuntu_jazzbach on 2007-01-19
Nope, I put the command without the $. Just "sudo dpkg-reconfigure dash" and a blue screen appears asking me if I want to install dash as /bin/sh and I accepted. then it returns to the promp (the $ symbol). then I ran the "make" command and the same error.

---

### Post by po0f on 2007-01-19
ubuntu_jazzbach,

[quote=po0f]Answer "No".[/quote]

---

### Post by ubuntu_jazzbach on 2007-01-19
I've also tried to open the Makefile and add at the very start:
SHELL=/bin/bash

but the same error:

when running the "make" command:

/bin/sh: Syntax error: "(" unexpected
make: *** [check_old] Error 2

---

### Post by po0f on 2007-01-19
ubuntu_jazzbach,

Can you post the Makefile as an attachment in a post?

---

### Post by ubuntu_jazzbach on 2007-01-19
Here it is

---

### Post by po0f on 2007-01-20
ubuntu_jazzbach,

These are the only things I could see that might be a problem (backup the Makefile before attempting these edits):

~line 160:
```
[FONT="Courier New"]	@if [ "$(IEEE80211_INC)" = "" ]; then \[/FONT]
```
might need to be:
```
[FONT="Courier New"]	@if [ "${IEEE80211_INC}" = "" ]; then \[/FONT]
```

~line 170:
```
[FONT="Courier New"]	@if [ "$(shell whoami)" != "root" ]; then \[/FONT]
```
might need to be:
```
[FONT="Courier New"]	@if [ "`whoami`" != "root" ]; then \[/FONT]
```

Like I said, I don't know if this will fix it for you or not.

---

### Post by ubuntu_jazzbach on 2007-01-20
Still doesn't work wit the changes you suggested. I really, really appreciate your effort. Thanks a lot for your time :) 

I've searched the web as well and I found this page suggesting a solution to the problem I have (I've tried it but nothing worked) What do you think of it ??

[http://www.bughost.org/bugzilla/show_bug.cgi?id=1163](http://www.bughost.org/bugzilla/show_bug.cgi?id=1163)

---

### Post by po0f on 2007-01-20
ubuntu_jazzbach,

The solution posted there looks like it would have fixed it, but it obviously didn't in your case.  :)

Have you tried deleting the directory all that stuff is in, re-untarring it into a new directory and making that "SHELL=/bin/bash" change as the first thing you do?

---

### Post by ubuntu_jazzbach on 2007-01-20
IT WORKED !!!! I tar-ed it and moved to /tmp. Untared there and run the "make" command and everything worked perfectly !!!!!

THANKS !!! THANKS A LOT !!!!

---

### Post by po0f on 2007-01-20
ubuntu_jazzbach,

Glad it all worked out for you.  :)

---

