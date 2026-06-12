---
title: "Problem with my Java installation"
date: 2013-01-14
forum: Installation &amp; Upgrades
---

### Post by fakedave on 2013-01-14
Hello,

I'm writing because I believe I have an issue with my java installation.

My ultimate goal is to install IBM Rational products.

I had installed the 64-bit version with a tutorial from the web.
Then I understood that the 32 bit version is required. Again I removed and installed again the 32-bit release. I had no issue.

However, when I launch the 'install' app from the IBM Installation Manager, the terminal 'hangs' for a couple of seconds and comes back. Nothing else happens.
My chrome and Firefox browsers also tell me that java is not working while I have normally activated it.

I suspect something is screwed up with my java install.

Could someone help me with that ?? How to check?
Sorry for that but I'm a newbie.

---

### Post by fakedave on 2013-01-14
Any good tutorial to make sure I can completely remove the java install I made (from Oracle web site).
I lost the link to the tutorial I used ...

At the same, I'd appreciate another good tutorial to reinstall clean java 1.6 32bit from Oracle?

Thanx

---

### Post by fakedave on 2013-01-15
ok ok ok, with some more investigations I was able to install java.
But I have more questions now:
[LIST]
[*]I have a 64-bit 12.10 system --> can I install a 32-bit java from Oracle? (I failed to do so, only succeeded with 64-bit)
[*]Can I run a 32-bit application with my 64-bit java install?
[/LIST]

My trouble is that I have to install a 32-bit IBM (Rational) software on my computer and that I only seem to be able to install & run 64-bit stuff.
I strongly believe it could work because I did once, a month ago, just before I decided to wipe out my entire installation to restart from fresh (don't ask ...).
I can't seem to make it work again and I don't remember what I did.

](*,)

---

### Post by fakedave on 2013-01-15
Well, this is apparently sorted: I managed to find more information about running 32 bit applications with 64 bit VM.
I installed the package ia32-libs that does the bridge between 32 and 64.

So turned out it works. I'm installing my software as I write.

---

