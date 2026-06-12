---
title: "Kernel Comparisons: 2.6.35-* vs. 2.6.2x-*"
date: 2011-03-07
forum: Installation &amp; Upgrades
---

### Post by teward on 2011-03-07
I've got two systems, one with 10.10 and one with 10.04.2 LTS.

The 10.10 system has the 2.6.35 series of kernels, the 10.04 system has 2.6.29 (i think) series of kernels.

Is there any way to get a 2.6.35 kernel onto the 10.04 system?  if so, what package(s) are needed for it to operate, assuming its possible to get said kernel onto the system?

---

### Post by jocko on 2011-03-07
10.04 have a 2.6.32 kernel, not 2.6.29.
There may be a backported maverick kernel in the lucid repos.
Have you enabled all repos?
Open up synaptic (System-->Administration-->Synaptic package manager).
Under Settings-->Repositories, open the third tab (updates) and make sure the "security", "updates" and "backports" repos are enabled.
Reload the package information and do a search for "linux-". You should find a 2.6.35 kernel...

---

### Post by teward on 2011-03-07
> **jocko said:**
> 10.04 have a 2.6.32 kernel, not 2.6.29.
There may be a backported maverick kernel in the lucid repos.
Have you enabled all repos?
Open up synaptic (System-->Administration-->Synaptic package manager).
Under Settings-->Repositories, open the third tab (updates) and make sure the "security", "updates" and "backports" repos are enabled.
Reload the package information and do a search for "linux-". You should find a 2.6.35 kernel...

Will that kernel operate correctly, and will  GRUB2 identify it?

Also, whats the PAE-enabled kernel (same series of kernel as described above) require to run?

---

### Post by teward on 2011-03-07
NOTE: I've installed the most recent 2.6.35 kernel i could find in the lucid backports, going to see if it works right in a few minutes.  Wish me luck :P


***EDIT***

It seems to be working right, the only problem now is i've got the 2.6.32 and the 2.6.35 kernels :P  Time to do some cleanup of my packages :cool:

---

### Post by mikewhatever on 2011-03-07
Why do you want 2.6.35? Doesn't the default kernel do the job? If you are after the latest version, it's actually 2.6.37, and 2.6.38 is probably going to make it out by the end of the month.

---

### Post by teward on 2011-03-07
> **mikewhatever said:**
> Why do you want 2.6.35? Doesn't the default kernel do the job? If you are after the latest version, it's actually 2.6.37, and 2.6.38 is probably going to make it out by the end of the month.

The latest version doesnt seem to be available on the Lucid repos (from what i've searched, even in backports).

And for the record, i like to test newer kernels on slightly older versions of distros in an experimental environment ;P

---

