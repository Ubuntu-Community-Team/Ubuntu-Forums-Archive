---
title: "Long term support? what about new hardware?."
date: 2007-01-26
forum: Installation &amp; Upgrades
---

### Post by ra1n on 2007-01-26
Hello folks
this post it's a little complain about how new hardware gets supported in dapper, or better, ho new hardware doesn't gets supported.
Yesterday I wrestled with a n-force 430 mobo in order to get dapper working on it, at last I won, but in order to get everything working I've got to install Feisty 2.6.20 kernel in order to get ethernet (forcedeth driver supports the nf430 only in 2.6.18 kernel I think) and audio(same for the snd-hda-intel driver that recognise 430 card only in the latest alsa drivers)and hack a little the feisty nvidia-glx package (in order to install it on dapper and to match it with the kernel interface).
If dapper its the supported distro, why the kernel cannot be easily updated to support new hardware?

---

### Post by PriceChild on 2007-01-26
This is just one of those little compromises that have to be taken...

In order to make a rock-solid system for the majority of users... you can't change things for those with newer hardware for fear of breaking everything.

---

### Post by ra1n on 2007-01-26
> **PriceChild said:**
> This is just one of those little compromises that have to be taken...

In order to make a rock-solid system for the majority of users... you can't change things for those with newer hardware for fear of breaking everything.

Right, but seems to me that ubuntu folks got too much fear of breaking anything, while it's a pity that dapper users cannot get updated firefox or oo.o but hardware support it's an important thing to support, since hardware evolves fast, at least they could provide backported kernels, or backported patches, just for the brave :D  or stop the LTS thing and go ahead with scheduled updates like edgy->feisty

---

### Post by meng on 2007-01-26
I'm not sure what you're asking for here, since Edgy and Feisty (testing) are obviously available for folks like you. Most folks using Dapper like it the way it is, and wouldn't mind backports for some things (Firefox, OpenOffice), but aren't desperate for them either, and don't want new kernels to break on them. Dapper will always be less cutting-edge than Edgy or Feisty, that's the whole point.

---

### Post by ra1n on 2007-01-26
> **meng said:**
> I'm not sure what you're asking for here, since Edgy and Feisty (testing) are obviously available for folks like you. Most folks using Dapper like it the way it is, and wouldn't mind backports for some things (Firefox, OpenOffice), but aren't desperate for them either, and don't want new kernels to break on them. Dapper will always be less cutting-edge than Edgy or Feisty, that's the whole point.

Well, the first thing I said it's that mine it's a complain :D 
What I'm saying here it's that folks that try to install dapper(because it's supported for more time than edgy, or because they got it via free shipit cds since shipit doesn't ship edgy, for example my university distributes shipit cds) on cutting edge hardware (like my pcs with the nforce430) simply cannot because either the installer will fail (like dapper one because it tries to use the nv driver instead of vesa, and the geforce 6150 isn't supported by dapper's xorg) or doesn't recognize most of their hardware, for the nforce 430 this is true even for edgy.
I've been able to backport feisty kernel, but not every people it's able to do that (have a look here for the 430: [http://ubuntuforums.org/search.php?searchid=13454276](http://ubuntuforums.org/search.php?searchid=13454276) ).
Firefox or openoffice aren't a great problem, i agree, but hardware support is...

---

