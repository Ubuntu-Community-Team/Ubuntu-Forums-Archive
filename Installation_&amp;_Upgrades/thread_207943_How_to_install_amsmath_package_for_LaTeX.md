---
title: "How to install amsmath package for LaTeX?"
date: 2006-07-02
forum: Installation &amp; Upgrades
---

### Post by Physicist on 2006-07-02
I am new to LaTeX and Ubuntu. I use Kile 3.52 on Ubuntu 6.06.
How to install amsmath package on the system?

BTW, how to install pakcages such that Kile can read Chinese/Japanese/Korean?

---

### Post by Physicist on 2006-07-06
Does anyone know it?

---

### Post by icksa on 2006-09-25
You need to install the tetex-extras package from synaptic

---

### Post by andiii on 2006-09-25
What is kile 3.52? I have 1.91 and thought it would be kind of recent ;)

What Tex System are you using anyway? tetex or Texlive?

---

### Post by hajk on 2006-09-26
I recommend removing all Ubuntu TeX packages and download/install the complete TeXLive2005 distribution (with the possible exception of some language-related parts that you are not going to use) to your /usr/local tree. The tetex distribution is no longer maintained by Thomas Esser, while the Debian TeXLive packages are in various stages of progress -- you'll be running a bit ahead of the herd this way. I've already done it, and it works great!

---

### Post by frisket on 2006-11-19
How did you get over the problem of the dependencies?
If you want to install (or already have installed) Kile, apt-get is going to want to try and resolve the dependency by bringing tetex back.

---

