---
title: "2GB RAM with generec-pae kernel upon installation"
date: 2012-05-22
forum: Installation &amp; Upgrades
---

### Post by Prescilla on 2012-05-22
Hello Linux nation!

I have just recently installed Ubuntu 12.04 LTS.

After installation, I've checked what is my kernel version by typing [FONT=Courier New]**uname -r**[/FONT] from a terminal and it says [FONT=Courier New]**3.2.0-23-generic-pae**[/FONT].

What I don't understand is that I only have 2GB of RAM and I really don't need to use pae kernel or should I?

Does this mean that it is okay to use pae kernels with only 2GB of RAM.
I've read in a document that pae is only recommended for systems with at least 4GB of RAM.

How do I get back to a non-pae generic kernel???
Please help.

---

### Post by carl4926 on 2012-05-22
pae is for 32 bit installs that have more than 3GB RAM
but 32 bit install default to pae
which is fine

---

### Post by grahammechanical on 2012-05-22
I only have 1GB RAM but it is with a 64bit CPU so I run 64bit Ubuntu (AMD64) which has the ability to use more than 4GB as standard.

I think that from 12.04 onwards we will not be able to download a version of Ubuntu that is 32bit non-pae. There is not one available.

If the article said this:

> I've read in a document that pae is only recommended for systems with at least 4GB of RAM.

Then it is misleading. The article should say that it **is** recommended to install a pae kernel for systems with more than 4GB of RAM.

How is the OS working? Fine? Then what is your worry. Think of this, imagine that one day you decide to upgrade the RAM and you put more than 4GB in, well, you wont need to reinstall Ubuntu with a pae kernel. Which you would have to do if you had installed a non-pae kernel Ubuntu.

Regards.

---

### Post by Prescilla on 2012-05-22
Thanks for the quick response.

Well, my Ubuntu seems to be working fine. No trouble so far.
I'm still installing applications.

So, no worries then. Thank you again.

---

