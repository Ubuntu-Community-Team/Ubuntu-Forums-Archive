---
title: "Ubuntu 9.1.0 Update Manager Error"
date: 2009-12-01
forum: Installation &amp; Upgrades
---

### Post by abhishes on 2009-12-01
Hello Everyone,

On my Ubuntu 9.1.0 machine the update manager prompts me to install recommended updates. when I click yes, I get the following error 

"Not all updates could be installed. Run a partial upgrade, to install as many updates as possible"

[IMG]http://farm3.static.flickr.com/2715/4150376815_db5be623b8_o.png[/IMG]

Now when I do click on the partial upgrade button, it comes up with another message

[IMG]http://farm3.static.flickr.com/2799/4151135414_fd18602aff_o.png[/IMG]

I have searched and found that though many people have faced this issue, they have only solved it by re-installation of the OS.

Is there any better way of solving this?

Regards,
Abhishek

---

### Post by abhishes on 2009-12-08
any help on this matter? why are all the upgrades failing on my machine?

---

### Post by MelDJ on 2009-12-08
hi there
it seems you have broken packages. go to synaptic and press edit-fix broken packages to fix them.
but i don't understand why it is running upgrade though. did you update from 9.04?

---

### Post by harbingerofdoom on 2009-12-09
i am getting the same thing on my system and when i run apt from cli i get the following notice:

The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic sreadahead xbmc
  xbmc-skin-confluence xbmc-skin-pm3-hd xbmc-web-pm3

also, once i get done running apt from cli, nothing seems to have gone wrong, everything works like its supposed to and my update manager notification goes away until it picks up on a new update.


last time i let synaptics do its partial upgrade it screwed things up so badly that i had to reinstall the entire OS from scratch.

---

### Post by harbingerofdoom on 2009-12-12
c'mon... someones gotta have some kind of information on this problem...

need more info? okay... lemme know what you need..


beuller? beuller?

---

### Post by abhishes on 2009-12-12
>  don't understand why it is running upgrade though. did you update from 9.04?

No I did a fresh installation of 9.1.0 still I am getting this error.

I tried to the "fix broken packages" option... but I still got the same error. Can someone help me please?

---

### Post by harbingerofdoom on 2009-12-16
well,

i guess that means the actual answer is "shouldnt have used 9.10"

---

### Post by Alexandre Putt on 2009-12-19
You should examine what packages are causing problems. In any case I think it is too early to update the system. You should wait till 10.x is officially released (though installing "important security updates" is reasonable). At the moment I believe not all replacements for the packages are available, and this may be causing a few dependency problems.

---

