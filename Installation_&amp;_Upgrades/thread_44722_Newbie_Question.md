---
title: "Newbie Question"
date: 2005-06-27
forum: Installation &amp; Upgrades
---

### Post by the_pc_dude on 2005-06-27
I want to know I'm trying to install an new kernel and I go an type in the command to make sure it's there and it says it is then I use the cd command to change the dir to /usr/src/linux It says not such an file or dir. This is my question can I make an linux dir there an install it in there

---

### Post by apollo2011 on 2005-06-27
Why are you trying to install a new kernel from source? You probably shouldn't be doing that unless you are doing some kind of testing, or are having a very serious problem.

---

### Post by kvidell on 2005-06-27
[QUOTE=apollo2011]Why are you trying to install a new kernel from source? You probably shouldn't be doing that unless you are doing some kind of testing, or are having a very serious problem.[/QUOTE]
 Or just like to compile your own kernels like me :) I like to tweak certain features out of it to make it run a little bit smoother (like appletalk and IPv6. yech)

the_pc_dude: move the source .tar.bz2 to /usr/src, untar it so that you have /usr/src/linux-2.6.11.12/ or whatever and do the following:

ln -s /usr/src/linux-2.6.11.12 /usr/src/linux

It's a symlink, not an entire directory :) It's all you'll need.

Might I ask what method you're using to compile?
- Kev

---

### Post by apollo2011 on 2005-06-27
[QUOTE=kvidell]Or just like to compile your own kernels like me :) I like to tweak certain features out of it to make it run a little bit smoother (like appletalk and IPv6. yech)
[/QUOTE]

True, I probably didn't word my post right.  Given he called it a newbie question, most newbies (and even someone like me in between newbie and advanced developer) wouldn't be doing that so thats how I interpreted that, not that he might not be interested in doing that.  :razz:

---

### Post by kvidell on 2005-06-27
[QUOTE=apollo2011]True, I probably didn't word my post right.  Given he called it a newbie question, most newbies (and even someone like me in between newbie and advanced developer) wouldn't be doing that so thats how I interpreted that, not that he might not be interested in doing that.  :razz:[/QUOTE]
 Oh... good point...
Hm...
Yea... now that you mention it, helluva 'newbie' question ;P

---

### Post by the_pc_dude on 2005-06-27
I've saved some tutorials on new kernel installations it didn't show how to install an new kernel source to an new dir.  I won't install an new kernel unless I  have to.
P.S just wanting to know

---

