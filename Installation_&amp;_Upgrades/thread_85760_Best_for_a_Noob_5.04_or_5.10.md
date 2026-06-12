---
title: "Best for a Noob: 5.04 or 5.10?"
date: 2005-11-03
forum: Installation &amp; Upgrades
---

### Post by Ubuntist on 2005-11-03
I was about to replace my Mandriva installation with Ubuntu 5.10 in the hopes that Ubuntu will be easier for a noob like me to maintain.

Then I noticed a couple of posts to the effect that 5.10, still being quite new,might be having some teething problems and lacks both make and a gcc compiler.  I know I'm going to need gcc to install one key application (the R statistics package).  So I'm wondering if maybe I should install 5.04 instead.

Any recommendations?  Does 5.04 have gcc and make?  Is it likely to give me less trouble than 5.10?

Thanks...!

---

### Post by mcduck on 2005-11-03
Install 5.10. It doesn't lack GCC any more than 5.04 does, it just isn't installed by default but you can get it and everything else needed for compiling with 'sudo apt-get install build-essentials'

---

### Post by tseliot on 2005-11-03
[QUOTE=Ubuntist]I was about to replace my Mandriva installation with Ubuntu 5.10 in the hopes that Ubuntu will be easier for a noob like me to maintain.

Then I noticed a couple of posts to the effect that 5.10, still being quite new,might be having some teething problems and lacks both make and a gcc compiler.  I know I'm going to need gcc to install one key application (the R statistics package).  So I'm wondering if maybe I should install 5.04 instead.

Any recommendations?  Does 5.04 have gcc and make?  Is it likely to give me less trouble than 5.10?

Thanks...![/QUOTE]
You can install anything you need (gcc,etc.) thanks to Synaptic. Try 5.10, you won't regret it.

---

### Post by HJThis on 2005-11-03
Hello,Ubuntist & Welcome

Just like to add that being a bigtime newbie myself
that after using Suse9-10 & then trying Ubuntu after
seing it run on a friends PC i had to have it.

& i have to say i love it not hard at all plus you
have great help here at the forums from members
like the one that just replyed to you.

i say go for it Ubuntu is an A+ in my book & it helped
me kill Windows for good, yes no going back for me:):

Best of luck

---

### Post by Ubuntist on 2005-11-07
mcduck, tseliot & HJThis,

Thank you very much!  I've DL'ed 5.10 and will be attempting its installation shortly.

---

### Post by Topsiho on 2005-11-08
[QUOTE=mcduck]Install 5.10. It doesn't lack GCC any more than 5.04 does, it just isn't installed by default but you can get it and everything else needed for compiling with 'sudo apt-get install build-essentials'[/QUOTE]

Just a little correction here in order to avoid some frustration that I myself suffered :) :

'sudo apt-get install build-essential'

Drop the 's' from essentials.

When asked for a password you just have to use your user password that you entered (twice) during the install, this is not always clear to a person new to Ubuntu.

And play with synaptic to see tons and tons of programs you can install ..... 

Topsiho

---

