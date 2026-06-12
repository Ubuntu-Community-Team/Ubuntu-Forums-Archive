---
title: "gnome blank/dead after upgrade"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by jema on 2008-10-31
When I login in, even in failsafe gnome things just sit there.

Just the arrow cursor on screen.

---

### Post by jerrylamos on 2008-10-31
Might be the same black screen problem I've been getting with Intel graphics since Aug 13.  Excerpting Developers comments from my Launchpad Bug #259385:

"== Desktop effects and Intel 830MG and 845G video cards ==

There is a bug in the intel video driver for the older intel 830 and 845 integrated video cards that are used on laptops like the IBM R30. Desktop effects with compiz will not work on those chips and freeze the system."

From what I've seen on the posts there are a LOT More chips that have symptoms like this.

My workaround is:
Boot in rescue mode
select root shell prompt
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit
resume

If that works you're O.K. except no special visual effects.  If you want to try compiz again, install with Synaptic.

Jerry

---

