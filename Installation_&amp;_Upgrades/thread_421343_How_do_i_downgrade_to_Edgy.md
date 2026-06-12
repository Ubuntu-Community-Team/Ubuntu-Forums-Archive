---
title: "How do i downgrade to Edgy?"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by creamcheeze77 on 2007-04-24
Hi, i recently upgraded to Feisty from Edgy and it simply will not work.  I can't get X to work and the kernel won't even load (i have to use the older kernel to even find out that X doesnt work), so is it possibly to downgrade back to Edgy without losing any of my files? i would have to do this through the terminal since gnome won't start up.  thanks in advance

---

### Post by Big Ed on 2007-04-24
I'm sure that there is a way to downgrade back to Edgy, but it would take more knowledge of apt-get than I have.

What's going on with your installation of Feisty?  Do you have the new kernel installed but it just won't boot?  Are you missing other packages?

Try opening a terminal and using "sudo apt-get dist-upgrade".

That should get you kernel in.  Assuming that /etc/apt/sources.list has all Feisty and no Edgy in the uncommented lines.

HTH,
Ed

---

### Post by H.E. Pennypacker on 2007-05-06
If you do decide on downgrading, your best option is to re-install Edgy.  You'd do this by starting the LiveCD, and do everything as you had done the first time, but this time, you do NOT reformat your home partition,  Again, DO NOT format your home partition, and any other partitions that have valuable content.

You'll have to format swap and root.  

Good luck.  Give re-installation an option, because Feisty may prove to be too difficult to bother with.

---

