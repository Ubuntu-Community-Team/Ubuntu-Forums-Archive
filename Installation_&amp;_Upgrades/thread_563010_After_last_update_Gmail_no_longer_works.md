---
title: "After last update Gmail no longer works"
date: 2007-09-29
forum: Installation &amp; Upgrades
---

### Post by tombeard on 2007-09-29
I ran updates a couple of days ago and now Gmail just shows a blank page. I looked at the page source and there was a line about javascript not present. I found a javascript test page but everything worked. I tried a Java test page and it did not work. I reinstalled the Sun Java jre with Synaptic and the test still doesnt work. This is all from Firefox on a 64 bit AMD processor. I'm kinda new at this, any thoughts?

---

### Post by Natr0n on 2007-09-29
Like you said, Gmail uses javascript not Java so there's no reason that the presence or absence of Java would affect Gmail. If you installed the Java Runtime Environment from Synaptic you might have a problem viewing Java's official test page because the Java version in the repositories is not the newest version. Rest assured, Java should work for pretty much everything else.

---

### Post by Natr0n on 2007-09-29
As for Gmail not working you might try going to Edit->Preferences->Content in Firefox and making sure that the "Enable Javascript" box is checked. (Also make sure that the "Enable Java" box is checked for your Java issues.)

---

### Post by tombeard on 2007-09-29
Well, it's working again and I didn't change anything. I'll assume Google broke it and it was just coincidence I had just run updates. Thanks for trying to help.

---

