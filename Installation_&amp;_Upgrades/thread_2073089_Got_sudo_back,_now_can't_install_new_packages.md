---
title: "Got sudo back, now can't install new packages"
date: 2012-10-18
forum: Installation &amp; Upgrades
---

### Post by AussieGuy on 2012-10-18
After booting into my 12.04 system with a live CD and fiddlin' about, I've managed to add myself back to the sudo group.

But I get errors when using apt-get.  Here's an example:

--
>> sudo apt-get install libtiff4-dev

<... a whole lotta stuff ...>

Errors were encountered while processing:
 texlive-binaries
 <... and other texlive packages ...>

E: Sub-process /usr/bin/dpkg returned an error code (1)
--

Clearly something, sometime, went wrong with my texlive installation and it's hanging about causing strife whenever I attempt to install another package.  What are the best ways of getting round this?

Thanks,
-A.

---

### Post by funicorn on 2012-10-19
The given example fails to tell the error is from apt-get or texlive.

You need to give other examples.

---

### Post by drmrgd on 2012-10-19
Yes, please post the entire output from the command.  The actual error description is likely to be in the text that you omitted from your post.

---

