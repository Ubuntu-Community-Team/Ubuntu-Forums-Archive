---
title: "Problem installing ubuntu-desktop base from command line"
date: 2008-10-21
forum: Installation &amp; Upgrades
---

### Post by tstack77 on 2008-10-21
I am trying to install the ubuntu-desktop for my server but only want to install the base without the recommends.

"sudo apt-get install --no-install-recommends ubuntu-desktop" doesn't work, it still wants to install the complete desktop package.

Where am i going wrong?

---

### Post by aysiu on 2008-10-21
I don't know. Maybe try *aptitude* instead of *apt-get*? ```
sudo aptitude update
sudo aptitude install --without-recommends ubuntu-desktop
```

---

### Post by tstack77 on 2008-10-21
Thanks for the suggestion but that didn't work either. Doesn't seem right/possible, but could this be a bug?

So strange

---

### Post by aysiu on 2008-10-21
How do you know the recommended packages are also coming in?

---

### Post by tstack77 on 2008-10-21
The first time I tried installing with the --no-install-recommends it installed the full desktop. Since it was on a fresh install I simply started over and then checked the download/new usage size (442MB/1810MB) of the ubuntu-desktop package. 

All the attempts so far are showing the same sizes so I've aborted them.



EDIT: Not sure if this makes any difference, but I have the OS installed on a 4GB cf card (why I don't want to use any unnecessary extra space).

---

### Post by tstack77 on 2008-10-21
I found ([THIS]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=485881")) from June in the debian bug logs:

"apt-get --no-install-recommends disables the behavior of
APT::Install-Recommends, but does not disable any configured
APT::Install-Recommends-Sections. This is rather perplexing 
to users who don't understand the details of how APT manages 
its configuration."

I myself am a perplexed user that doesn't understand the details of how APT manages its configuration :)

Is there any way to override/disable configured install-recommends-sections?

---

### Post by tstack77 on 2008-10-22
I don't see ANY documentation about this in the man page...any ideas of a workaround?

---

