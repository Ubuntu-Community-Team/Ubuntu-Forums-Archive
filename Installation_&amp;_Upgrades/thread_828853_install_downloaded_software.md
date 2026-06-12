---
title: "install downloaded software"
date: 2008-06-14
forum: Installation &amp; Upgrades
---

### Post by ffoeg on 2008-06-14
Hello. I'm trying to install downloaded software It came in a tar file. I extracted the files to a folder. How can I user apt-get to install this software? I've tried the ./configure method. When I try to run "make" after ./configure it tells me "make: *** No rule to make target `install'.  Stop."

So, I'd like to use the apt-get method if possible. But, from what I've researched, I'd have to have an online source of these installation files to do that. Is that true?

Thanks

---

### Post by Partyboi2 on 2008-06-14
What program are you trying to install?

---

### Post by ffoeg on 2008-06-14
openvpn downloaded from openvpn.net

---

### Post by Tomatz on 2008-06-14
When you ./configure you need to look for dependancys you need to compile the app. It will tell you what dependancys you need at the end of the ./configure process. Then just install the dependancys via apt or synaptic.

---

### Post by ffoeg on 2008-06-14
I'll look into that, Thank you for the info. But speaking of the./configure method, the directions from the openvpn site say to "n cd to the top-level directory and type:
./configure
make
make install"
By "top-level directory" do you think they mean the top level of the folder that I extracted the files to?

Thanks

---

### Post by Tomatz on 2008-06-14
> **ffoeg said:**
> I'll look into that, Thank you for the info. But speaking of the./configure method, the directions from the openvpn site say to "n cd to the top-level directory and type:
./configure
make
make install"
By "top-level directory" do you think they mean the top level of the folder that I extracted the files to?

Thanks

The actual folder the files are in ;)

---

### Post by ffoeg on 2008-06-14
so when running ./configure, and it says "checking for (something) ..." and it says "no" right after, that identifies what I have to install?

Thanks

---

### Post by Tomatz on 2008-06-14
> **ffoeg said:**
> so when running ./configure, and it says "checking for (something) ..." and it says "no" right after, that identifies what I have to install?

Thanks

Yes

Also the readme (in the extracted folder) usually says which dependancys you will need ;)

---

### Post by Partyboi2 on 2008-06-14
openvpn is in the ubuntu repo's you can install it by synaptic package manager or from a terminal
```
sudo apt-get install openvpn
```
unless of course there is a reason you need to compile it. :)

---

