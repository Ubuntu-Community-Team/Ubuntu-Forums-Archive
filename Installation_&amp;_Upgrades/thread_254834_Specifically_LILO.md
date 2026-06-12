---
title: "Specifically LILO"
date: 2006-09-10
forum: Installation &amp; Upgrades
---

### Post by bigbearomaha on 2006-09-10
Hello, I have searched lilo in these posts, but these all either didn't address my question or it was addressed indirectly.  I was hoping to find specific information as how to replace grub with LILO after install.  I have tried to dl from repos and install via symantic, but it failed to install successfully.  my experience ends there.  Can someone help me to replace grub with LILO please?

Big Bear

---

### Post by croak77 on 2006-09-11
Can you post any error message you got?

Out of curiosity, why do you want to switch to lilo? I think most people prefer grub over lilo unless grub doesn't work on you system.

---

### Post by amo-ej1 on 2006-09-11
installing lilo simply comes to
a) getting the package
b) installing the package
c) creating a /etc/lilo.conf (define the kernel image and other paramters)
d) run 'lilo'

offcourse most steps require root access. The 'lilo' command will check at runtime if the /etc/lilo.conf file is correct, if all files can be found etc etc if any of those sanity checks fail lilo won't be installed.

But some error messages would indeed be useful

---

### Post by bigbearomaha on 2006-09-11
well,

Mostly I am trying to change to LILO just to do it.  learn something more if you will.

As far as errors, I get just those which say can't find video parameters used by current system. I will place exact copies of msgs next time I try to install.

It seems i am still a bit off as to where files are placed when they are dl and "installed" as I seem to keep losing them.  LOl

thank you for your responses thus far.

Big Bear

---

