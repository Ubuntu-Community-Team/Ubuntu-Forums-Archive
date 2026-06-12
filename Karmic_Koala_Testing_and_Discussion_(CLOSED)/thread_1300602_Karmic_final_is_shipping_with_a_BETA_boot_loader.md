---
title: "Karmic final is shipping with a BETA boot loader?"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by edin9 on 2009-10-25
:3

---

### Post by cb951303 on 2009-10-25
and?

---

### Post by edin9 on 2009-10-25
> **cb951303 said:**
> and?

It's a yes or no question. Not 'and'.

---

### Post by arpanaut on 2009-10-25
"You Betcha"
...S. Palin

---

### Post by edin9 on 2009-10-25
> **arpanaut said:**
> &quot;You Betcha&quot;
...S. Palin

Ok thanks.

---

### Post by Joeb454 on 2009-10-25
> **arpanaut said:**
> "You Betcha"
...S. Palin

Testing as per [this thread]("http://ubuntuforums.org/showthread.php?t=1300699").

---

### Post by jpmelos on 2009-10-25
Why are they shipping Karmic final with a Beta boot loader?

Are they so confident it works great in every environment, even though the developers themselves are not confident enough to take it out from beta stage?

If the final release is launched before Ubuntu 10.04, there will be a new CD release of Karmic 9.10.1 with the final boot loader? I think this would be the most correct to do.

---

### Post by Vanishing on 2009-10-25
> **jpmelos said:**
> Why are they shipping Karmic final with a Beta boot loader?

Are they so confident it works great in every environment, even though the developers themselves are not confident enough to take it out from beta stage?

If the final release is launched before Ubuntu 10.04, there will be a new CD release of Karmic 9.10.1 with the final boot loader? I think this would be the most correct to do.

because it works.

---

### Post by autocrosser on 2009-10-25
And if you are upgrading from 9.04 you won't see it by default--UNLESS you want to install it. All NEW installs will have Grub2 by default--not all installs. Grub2 WILL be the default for ALL installs with 10.04.

---

### Post by Regenweald on 2009-10-25
grub2 breaks the same way that grub-legacy broke, when people mess with it. We had teething in the crossover during the Karmic dev cycle. That is normal for any transition. With a default install grub2 should work fine for the vast majority of users. As grub-legacy did.

---

### Post by lswb on 2009-10-25
Well, legacy grub never made it to version 1.0 either. Previous versions of ubuntu have also included beta versions of various software as standard, e.g. Firefox 3.0 in 8.04. And for practical purposes, pulseaudio and Network Manager are beta versions as well.

---

### Post by renkinjutsu on 2009-10-25
> **jpmelos said:**
> Why are they shipping Karmic final with a Beta boot loader?

Are they so confident it works great in every environment, even though the developers themselves are not confident enough to take it out from beta stage?

If the final release is launched before Ubuntu 10.04, there will be a new CD release of Karmic 9.10.1 with the final boot loader? I think this would be the most correct to do.
Wasn't Gmail in Beta for years, with millions of users worldwide?
> **Vanishing said:**
> because it works.
yes.

---

### Post by forcecore on 2009-10-25
and then...

Because it works much better for me too.

---

### Post by areteichi on 2009-10-25
Though I don't recall very many people raising this issue, I think it was more controversial and risky when the previous **_LTS_** (Ubuntu 8.04) was released with Firefox 3.0 beta. I didn't quite understand why they did that especially for the LTS release. It seems to defeat the whole principle and purpose of LTS. I mean imagine if you're working for a company and evaluating which Linux distribution your company should implement. It certainly does not appear very promising when the product promotes itself to be stable and reliable but shipped with a beta software (and web browser in this case, on which virtually every computer user depends).

---

### Post by 23meg on 2009-10-25
> **areteichi said:**
> Though I don't recall very many people raising this issue, I think it was more controversial and risky when the previous **_LTS_** (Ubuntu 8.04) was released with Firefox 3.0 beta. I didn't quite understand why they did that especially for the LTS release. It seems to defeat the whole principle and purpose of LTS. 

Quite the contrary: it was very much in line with the principle and purpose of LTS, in that Firefox 2.x would have been unsupported upstream in a matter of months, and the only way to have a supported browser for the next few years in which the LTS release would have to be supported was to move to 3.x. 

And with GRUB, the only alternative is shipping GRUB Legacy, which is unsupported *now*.

> **=areteichi said:**
> 
I mean imagine if you're working for a company and evaluating which Linux distribution your company should implement. It certainly does not appear very promising when the product promotes itself to be stable and reliable but shipped with a beta software (and web browser in this case, on which virtually every computer user depends).

Anyone being paid to decide which OS a company should use should have the experience to know that "Beta" is not a term that signifies a fixed degree of quality, and should have the search and communication skills to go and learn what state the software is actually in, and why the decision was made to go with it. If she is scared off as soon as she sees the label "Beta", that's a loss the company that hired her.

By the release of Ubuntu 8.04, Firefox 3 was deemed RC quality by Mozilla. "Beta" was just a label.

---

### Post by areteichi on 2009-10-25
> **23meg said:**
> Quite the contrary: it was very much in line with the principle and purpose of LTS, in that Firefox 2.x would have been unsupported upstream in a matter of months, and the only way to have a supported browser for the next few years in which the LTS release would have to be supported was to move to 3.x. 

And with GRUB, the only alternative is shipping GRUB Legacy, which is unsupported *now*.



Anyone being paid to decide which OS a company should use should have the experience to know that "Beta" is not a term that signifies a fixed degree of quality, and should have the search and communication skills to go and learn what state the software is actually in, and why the decision was made to go with it. If she is scared off as soon as she sees the label "Beta", that's a loss the company that hired her.

By the release of Ubuntu 8.04, Firefox 3 was deemed RC quality by Mozilla. "Beta" was just a label.

Ah, I see! Thank you for your detailed response!!
I now feel a lot better about the decisions that have been made on software versions in Ubuntu releases. I guess moving from one version to the next isn't an easy task once a version of Ubuntu is released, so it is better to have the pre-release versions even if they're technically not 'final.'

---

### Post by RAOF on 2009-10-25
> **23meg said:**
> ...
And with GRUB, the only alternative is shipping GRUB Legacy, which is unsupported *now*.
...

And, to be fair, has been essentially unsupported for a number of *years*.

The difference is that now grub2 is good enough to actually replace it.  With the wide-scale testing it'll get from an Ubuntu release (and we've already knocked many significant corners off), all the distros should benefit.  Currently, pretty much each distro has to create and maintain their own separate grub1 patches for ext4, UUIDs, etc.  grub2 supports these things upstream, so everyone wins!

---

