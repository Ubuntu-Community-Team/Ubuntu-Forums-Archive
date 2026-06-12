---
title: "MonoDevelop 0.14 on Edgy?"
date: 2007-06-27
forum: Installation &amp; Upgrades
---

### Post by Bobbafett on 2007-06-27
Hello Everybody,
I am running a machine with Edgy and I downloaded and successfully installed Mono 1.2.4 from source.
Then I tried to the same with libgdiplus 1.2.4, however when the ./configure finishes it states that there is no GIF support and that should look at [http://sourceforge.net/projects/libgif](http://sourceforge.net/projects/libgif) which actualy DOES NOT EXIST :???:
I have been looking for this libgif without any luck. So some help as to where to find it would be great.

I am also planning on install latest MonoDevelop 0.14 but apparently all MonoDevelop 0.14 Installation Guides are oriented to Feisty Fawn.... Not to mention the MonoDevelop available in Synaptic which is very old.

So, I would like to know if anyone has been able to successfully install MonoDevelop 0.14 in Edgy , what dependencies are there to look for and what problems he/she encountered in the process.

Thanks a lot

BobbaFett

---

### Post by Bobbafett on 2007-06-28
Apparently got the libgdiplus 1.2.4 issue resolved: The reference to libgif made by configure actually refers to **giflib**, which is available in Synaptic. I installed that one and now ./configure is happy with the GIF dependency.

Still, I need some suggestions on installing MonoDevelop 0.14 on Edgy :p

---

