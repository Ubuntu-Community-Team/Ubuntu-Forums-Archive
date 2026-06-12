---
title: "what option should I choose"
date: 2007-01-10
forum: Installation &amp; Upgrades
---

### Post by ihopeto on 2007-01-10
I am new to ubuntu...actually I downloaded the LAMP server and just waiting for it to boot.

But in reality I need some advice...I need the four core pieces of software but I need to have the ability to recompile  php with the gdlib and the zlib and mysql to get the of the image functions.  Most of the prepackaged server CD's dont have all source for that....so what would be the best option for me to go with...

I need apache, mysql, samba, php with gdlib, jpeg and zlib ....

Please let me know which way I should go!

Thanks
Brian

---

### Post by K.Mandla on 2007-01-10
> **ihopeto said:**
> I am new to ubuntu...actually I downloaded the LAMP server and just waiting for it to boot.

But in reality I need some advice...I need the four core pieces of software but I need to have the ability to recompile  php with the gdlib and the zlib and mysql to get the of the image functions.  Most of the prepackaged server CD's dont have all source for that....so what would be the best option for me to go with...

I need apache, mysql, samba, php with gdlib, jpeg and zlib ....

Please let me know which way I should go!

Thanks
Brian
Hi Brian. After your installation you should be able to download the source for any and all of those files from the repositories.

Of course, a LAMP server install will put most of those packages into place for you automatically, so you might want to start with a command-line installation and recompile manually. Don't forget you'll need to install *build-essential* to compile.

---

