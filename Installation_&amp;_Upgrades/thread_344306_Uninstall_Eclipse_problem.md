---
title: "Uninstall Eclipse problem"
date: 2007-01-22
forum: Installation &amp; Upgrades
---

### Post by mrwooster on 2007-01-22
Hi,

I installed eclipse using apt-get, I then attempted to install several plugins from the eclipse website, the result of which eclipse is now not working - I get errors all over the place.

I now want to completely unistall eclipse and reinstall it - but I can't seem to do it.

I have used apt-get remove eclipse, but it says it is only going to remove 377kb of data, not the full 100mb of eclipse, and when I do remove it, the files in /usr/share/eclipse are still there. I tried removing the files in /usr/share/ but that did not work either - it still only re-installed the 377kb of data and then eclipse did not work at all (I only moved the files and later restored them to /usr/share/ so now am back to the origional problem).

I have tried apt-get clean and apt-get autoclean but it still does not seem to work.

How do I **completely** remove eclipse and reinstall it?

Thanks

Guy

---

### Post by jstableford on 2008-02-05
I am having the same issue - any resolution yet?

---

### Post by Timbo337 on 2008-02-12
I managed to use Synaptic to completely uninstall eclipse and its dependencies. 109mb was freed. I'm not sure what the apt-get equivalent of this is, though.

---

### Post by badong on 2008-03-10
Hi,

I am not sure if this is the equivalent but it worked for me.

```
sudo apt-get autoremove eclipse
```

---

### Post by x86macro on 2008-04-30
that worked for me as well.  thanks!  somehow my entire install of eclipse fell to pieces.  now i can start fresh.

---

### Post by noletters on 2008-06-23
worked for me too! thanks

---

