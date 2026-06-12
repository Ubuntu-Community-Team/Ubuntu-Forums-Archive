---
title: "Problem installing programs"
date: 2010-06-20
forum: Installation &amp; Upgrades
---

### Post by gudrade on 2010-06-20
My friend canceled the upgrade to Ubuntu  10:04 through the update manager (for this version of a problem with the  ATI it).
But after the cancellation happens the next problem, trying to  install something this message appears:

E: Internal  Error, Could Not Perform immediate configuration (2) on mountall

Now appreciate  the attention

---

### Post by Rubi1200 on 2010-06-21
See this bug report:

[https://bugs.launchpad.net/ubuntu/lucid/+source/mountall/+bug/559582](https://bugs.launchpad.net/ubuntu/lucid/+source/mountall/+bug/559582)

By the way, it is usually not a good idea to cancel an upgrade in progress.

You may have to consider a fresh install of Lucid on your machine.

Make sure you backup anything important first.

---

### Post by gudrade on 2010-06-21
[COLOR=#000000][FONT=Times New Roman][FONT=arial][COLOR=#000000]Thanks for the reply.

[/COLOR]The problem is exactly this, can not install Lucid, because when I tested it had a problem with the ATI Radeon X1650 (not sure how it is now after the updates).
When my friend said it was updating and it would take too long, I called to cancel it, as happened some bizarre errors with his machine using Lucid.
Can I tell him to take risks and rely on luck.
Thanks for the help.[/FONT][/FONT][/COLOR]

---

### Post by Mark Phelps on 2010-06-21
> **gudrade said:**
>  .. The problem is exactly this, can not install Lucid, because when I tested it had a problem with the ATI Radeon X1650 (not sure how it is now after the updates).

IF by a "problem", you mean that you can't install the fglrx drivers, or can't upgrade a machine that has the fglrx drivers already installed ... that is not fixed and is not going to be fixed because those drivers are incompatible with Ubuntu 10.04 and your video card.

To do an "upgrade" from an older version of Ubuntu, you would first need to remove the fglrx drivers and replace them with the open source drivers.

---

