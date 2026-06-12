---
title: "edgy installer - grub location"
date: 2007-01-30
forum: Installation &amp; Upgrades
---

### Post by bvc on 2007-01-30
I read the alternate desktop iso allows for grub to be installed where ever you tell it. I assumed that was normal and would be the case for the regular/standard desktop iso, but since it was said for the alternate it made me wonder....

can this not be done with the standard desktop iso?

I know about the 'using previous partition' bug which is why I looked into the alternate, but certainly such a standard option is also available in the standard desktop iso? I'm dialup and do not want to have to download another 700MB iso :) 

I need gtk 2.10 and the devel metacity to check all my themes and such and for modifying some metacity themes to have 2 and 3px round corners. Yea!

Thanks you for any info!

---

### Post by louieb on 2007-01-30
Yea you can change it on the Live CD, but its hidden pertly well. On the screen just before the install begins buried in the text above the install button you will see a link that looks something like this _[COLOR=Blue](hd0)[/COLOR]_ just click on it to change where grub is installed.

---

### Post by bvc on 2007-01-30
> **louieb said:**
> Yea you can change it on the Live CD, but its hidden pertly well. On the screen just before the install begins buried in the text above the install button you will see a link that looks something like this _[COLOR=Blue](hd0)[/COLOR]_ just click on it to change where grub is installed.Thank you very much for the confirmation! I figured it was somewhere as it usually is. I've done a 100+ installs of various distros but with some of the strange things that have been done and considered acceptible for a release, I couldn't help but doubt, and I just am not into fixing and tinkering like I used to be and didn'twant to have to go that route blindly.

---

### Post by gtp on 2007-01-30
This is very similar to my question, but I need a little more explanation, please.  In my case, I want grub to be installed on the same partition as Ubuntu, which is partion 6 on my primary drive (hda6).  What do I type in instead of (hd0).  Do I enter 'hda6', or maybe (hd0,5)?

---

### Post by louieb on 2007-01-30
> **gtp said:**
> This is very similar to my question, but I need a little more explanation, please.  In my case, I want grub to be installed on the same partition as Ubuntu, which is partion 6 on my primary drive (hda6).  What do I type in instead of (hd0).  Do I enter 'hda6', or maybe (hd0,5)?
Good guess. In grub speak hda6 would be (hd0,5). I think either would work but I have never tried hd**  to be safe use (hd0,5).
Check out the Dual Boot link in my signature.

---

### Post by gtp on 2007-01-31
It worked great with (hd0,5).

---

