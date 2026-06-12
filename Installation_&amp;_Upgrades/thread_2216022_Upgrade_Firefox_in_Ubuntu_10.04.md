---
title: "Upgrade Firefox in Ubuntu 10.04"
date: 2014-04-09
forum: Installation &amp; Upgrades
---

### Post by mamboknave on 2014-04-09
Although I'll have to upgrade Ubuntu to the newest LTS, I need to stick to the 10.04 for a few more months.

Meanwhile, I need to update firefox (currently v20.0) to the v28.0 and that's not possible (in 10.04) through the various apt-get update, apt-get upgrade, etc...

I need a true installation at system level, not in my home directory.

How can I do that?

---

### Post by Double.J on 2014-04-09
Hi there!

i'm afraid 10.04 desktop is end of life: only server release support now. Add to that ff28 is the latest, and it's just unlikely there's going to be a repo for it. I have read that through either backports or the mozzilla ppa you can get up to 24?

there's a guide [here]("http://tutorialforlinux.com/2014/03/05/how-to-install-latest-firefox-27-on-linux-ubuntu-10-04-lucid-lts-3264bit-easy-visual-guide/") on how to install the tarball, but like I say it's not looking hopeful that someone is going to be maintaining a repo now.

hope it helps

Jj

please do bear in mind that support ended for 10.04 11 months ago and this system is unpatched for security and bugs.

---

### Post by su:bhatta on 2014-04-10
> **mamboknave said:**
> Although I'll have to upgrade Ubuntu to the newest LTS, I need to stick to the 10.04 for a few more months.

Meanwhile, I need to update firefox (currently v20.0) to the v28.0 and that's not possible (in 10.04) through the various apt-get update, apt-get upgrade, etc...

I need a true installation at system level, not in my home directory.

How can I do that?

If you want an updated browser, you can download the tarball from here: [http://nightly.mozilla.org/](http://nightly.mozilla.org/)
It wont be  a system level install. But at least you will have some security.
You dont have to install it.Just extract the contents into a folder and run the Firefox-trunk or Nightly executable by double clicking on it.

The tarball comes with all the dependencies and all, hence you will get the Nightly build of Firefox running, without installing.

Hope this helps.

---

