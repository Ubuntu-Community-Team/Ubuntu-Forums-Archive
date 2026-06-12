---
title: "passing arguments to apt-get"
date: 2007-02-15
forum: Installation &amp; Upgrades
---

### Post by jake3988 on 2007-02-15
Hi.  Pretty simple question that apparently no one has answered and isn't in any help.

If I want to install links with graphics enabled, how to I pass '--enable-graphics' to apt-get or aptitude?

Thanks!

---

### Post by meng on 2007-02-15
Explain in more detail what you are trying to do please.
"install links with graphics enabled"
??? perhaps I'm just unaware of this functionality

---

### Post by jake3988 on 2007-02-15
It doesn't matter.  AT ALL.


Plenty of programs look for different arguments to be passed.  Does this mean since the package is already compiled and in a package I have to download the source and pass the argument there?

I guess I'll just try that.

Edit:  Actually, the version of links in the apt-get is ancient so I can't do it to that anyway.  But I still would like to know if downloading source is the only method of passing arguments.

---

### Post by meng on 2007-02-15
I'm sorry to have angered you with my response, I was trying to help, but I didn't understand the question. Good luck!

---

### Post by meng on 2007-02-15
Oh you mean links the web browser! I didn't understand before.
Check out links2

sudo apt-get install links2

then try executing it like this:
links -g

I haven't tried this myself, just did some googling.

---

### Post by jake3988 on 2007-02-18
That's phenominal and great but it STILL doesn't answer my question.


Is there a way to pass arguments to apt-get or must I fetch the source and install it?

---

