---
title: "partner repository enabled but apps don't appear in synaptic"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by mluntz on 2009-12-03
I am running Jaunty amd64 and have enabled the partner repository using the software sources gui. I have checked and verified that the partner repository shows up un-commented in sources.list. But in spite of that the application that I am looking for (acroread) does not show up in synaptic, nor do other applications from that repository. I have verified that acroread is in the partner repository and have manually downloaded the deb.

In looking for acroread I also enabled the medibuntu repository and the applications in that repo show up in synaptic. But why do none of the applications in the partner repo show up in synaptic? I get no error messages at all.

---

### Post by gadolinio on 2009-12-03
Can you install the .deb you downloaded?

---

### Post by dnairb on 2009-12-03
Have you refreshed the repository list?

In terminal:

sudo apt-get update

---

### Post by mluntz on 2009-12-03
I started to install the deb, but got a warning that I should really install from the repositories so I aborted the install until I looked into this further.

I think I refreshed the repository list using Reload button in the synaptic GUI, but did not try from a terminal. Would using the Reload button have accomplished the refresh or must it be done from a command window?

---

### Post by dnairb on 2009-12-03
> **mluntz said:**
> I think I refreshed the repository list using Reload button in the synaptic GUI, but did not try from a terminal. Would using the Reload button have accomplished the refresh or must it be done from a command window?

Both methods do the same.

---

### Post by mluntz on 2009-12-03
So does anyone have any other suggestions on how to get the packages to appear in synaptic. Alternatively, what is the advisability of installing from the downloaded deb. The message I get when clicking the deb file is
 **"Same version is available in a software channel. You are recommended to install the software from the channel instead."**

---

### Post by wilee-nilee on 2009-12-03
The Canonical repos have acroread so if you have them ticked on run in the terminal.
sudo apt-get update
then
sudo apt-get install acroread.

---

### Post by mluntz on 2009-12-03
> **dnairb said:**
> Both methods do the same.

Perhaps they should both do the same, but if so then there may be a bug in software sources. After I did an apt-get update the files in the partner repo showed up in synaptic.

---

### Post by wilee-nilee on 2009-12-03
> **mluntz said:**
> Perhaps they should both do the same, but if so then there may be a bug in software sources. After I did an apt-get update the files in the partner repo showed up in synaptic.


You first said you thought you did a update you obviously didn't there is no bug except between the screen and the chair. I say this as a joke of course. ;)

---

### Post by mluntz on 2009-12-04
> **wilee-nilee said:**
> You first said you thought you did a update you obviously didn't there is no bug except between the screen and the chair. I say this as a joke of course. ;)

I am not trying to be contentious; I am just asking for information. An earlier responder stated that the reload button in synaptic does the same thing as running apt-get update. Was his information incorrect? Based on my experience only apt-get update will pick up the files in the partner repo. If that is the case, what is the function of the reload button in synaptic?

---

