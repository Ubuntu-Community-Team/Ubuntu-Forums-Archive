---
title: "Need help with instalation on old laptop"
date: 2006-11-19
forum: Installation &amp; Upgrades
---

### Post by raith94 on 2006-11-19
Hi, I have recently attempted to load xubuntu on a old Compaq Presario 800. During the instalation it fails to recognise my internet connection and once instalation is completed this problem continues. Also sound and video are not recognised(I had previously thought i could solve this problem once i connected to the internet but it appears this may be a symptom of the problem). 

Having done lots of reading over the weekend it appears i need to use "8139too" but im unsure when or where i add this or at what point in the instalation.

Any help will be great!

Thanks

---

### Post by K.Mandla on 2006-11-19
I was under the impression that the 8139too module was loaded as part of the default kernel. If I give my machine this command ...

```
sudo modprobe -l 8139too
```
I get 8139too.ko as output. I suppose you could check that on your machine too. 

What kind of hardware is inside your computer? I tried to google for an 800, but it gets mixed in with a lot of other stuff.

---

### Post by raith94 on 2006-11-19
Yes ive just typed that and it has given that output too!
So im now completely lost as to whats going on.
Do i need to load it or set it to alias?

Its a Realtek 8139 ethernet controller in the machine

---

### Post by K.Mandla on 2006-11-19
And how old is the laptop? I know there are some kernel issues in the 2.6+ series that cause problems for PCMCIA stuff.

The easiest way to check this, to be honest, might be to download a copy of DSL (or Slackware, perhaps), and see how they fare on your laptop. I believe both of those distros stick to the 2.4+ series kernels. 

Read [this thread]("http://www.ubuntuforums.org/showthread.php?t=125334") and see if it's similar to what you're experiencing. It's a little long, but if you use an older laptop, it's very worth it.

---

