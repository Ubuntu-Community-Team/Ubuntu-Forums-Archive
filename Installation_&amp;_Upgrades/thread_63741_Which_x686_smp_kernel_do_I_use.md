---
title: "Which x686 smp kernel do I use"
date: 2005-09-08
forum: Installation &amp; Upgrades
---

### Post by niw_uk1964 on 2005-09-08
I'm not clear as to which kernel package to use on my dual PII-333 sytem. Can someone advise please?

Cheers!

Nige.

---

### Post by hod139 on 2005-09-08
[QUOTE=niw_uk1964]I'm not clear as to which kernel package to use on my dual PII-333 sytem. Can someone advise please?

Cheers!

Nige.[/QUOTE]

I assume you mean which kernel-image to run?  Even if this is correct, I'm not sure where the confusion is.  I would install the meta-package linux-image-686-smp.

---

### Post by niw_uk1964 on 2005-09-08
[QUOTE=hod139]I assume you mean which kernel-image to run?  Even if this is correct, I'm not sure where the confusion is.  I would install the meta-package linux-image-686-smp.[/QUOTE]

Well I wasn't sure because installing a then rebooting has trashed my system on a couple of occasions so, I assumed II had buggered things up. Presumably I just dowload using either synaptic of sudo apt-get filename in a terminal session?

---

### Post by hod139 on 2005-09-08
[QUOTE=niw_uk1964]Well I wasn't sure because installing a then rebooting has trashed my system on a couple of occasions so, I assumed II had buggered things up. Presumably I just dowload using either synaptic of sudo apt-get filename in a terminal session?[/QUOTE]

Correct.  You can use synaptic and search for linux-image-686-smp or use the command line:

```

sudo apt-get update
sudo apt-get install linux-image-686-smp
sudo reboot

```

---

### Post by niw_uk1964 on 2005-09-08
Ok. Thanks for that. I'll give it a go now.

---

### Post by varunus on 2005-09-08
Make sure to install the restricted modules too...probably a good idea.

---

### Post by Leif on 2005-09-09
install linux-686-smp instead of linux-image-686-smp. that way you'll get all the dependencies you could need.

---

