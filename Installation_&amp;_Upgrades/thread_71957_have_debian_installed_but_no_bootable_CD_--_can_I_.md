---
title: "have debian installed but no bootable CD -- can I use dselect to switch to Ubuntu?"
date: 2005-10-04
forum: Installation &amp; Upgrades
---

### Post by RwL on 2005-10-04
the subject pretty much says it all. Can I just edit my sources and essentially use dselect to turn this into a Ubuntu system?

If so, please explain in a bit of detail -- total noob, but a determined one, over here.

---

### Post by brentoboy on 2005-10-04
the short answer is "yes" you can do it.

put the ubuntu sources.list in your apt settings.

as root:
apt-get update
apt-get dist-upgrade

apt-get install ubuntu-desktop
(that will give you the default ubuntu apps)

---

### Post by RwL on 2005-10-05
Seemed like it was working but at the last step (install ubuntu-desktop)

E: broken packages.

How to, uh, fix those?  ;^)

EDIT: to be more clear, before that error message there's a long list of dependencies like:

Depends: [file] but it is not going to be installed.

The list looks alphabetical, with the top of my screen showing a few files/packages starting with t (ttf-bitstream-vera and other fonts) and ending with zenity... I can't seem to page up to look at the full list and I have no clue how to resolve these dependency issues. Help anyone?

---

### Post by RwL on 2005-10-06
Anyone? Before I pull my hair out? ;^)

I'm a linux noob but have just enough experience with Debian to be really frustrated right now -- isn't it supposed to just go get the dependencies? Why is it refusing to do that?

---

### Post by az on 2005-10-06
Make sure that you have removed any debian repositories and that you only have debian ones.  If your debian system awas up to date, use Breezy, not hoary, to avoid the problems you describe.

---

### Post by RwL on 2005-10-07
Thanks for the help brentoboy and azz... but dealing with this was getting to be too much of  a headache; so I started fresh with the [Smart Boot Manager]("http://linux.simple.be/tools/sbm"), an amazing tool, and used that to boot from a burned Hoary install CD -- wish I'd know about that in the first place, it was so much easier! -- and now I'm up and running on a little old Compaq Armada 4210T. Nice.

---

