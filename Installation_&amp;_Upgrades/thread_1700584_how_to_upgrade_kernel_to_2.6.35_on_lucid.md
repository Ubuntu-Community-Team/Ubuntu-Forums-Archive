---
title: "how to upgrade kernel to 2.6.35 on lucid"
date: 2011-03-05
forum: Installation &amp; Upgrades
---

### Post by MishMich on 2011-03-05
I read recently about security flaws in the ubuntu kernel, and when I checked my kernel, it is 2.6.32-29-generic.  I looked in synaptic, and I have the linux-generic meta-package - which should ensure upgrade to the latest kernel, and yet this is not being updated when I run update manager.  There is a linux-image-2.6.35-25-generic, but the advice is not to install this directly (to avoid breaking dependencies, etc.), but to install the meta-package instead.  Yet, the meta-package doesn't seem to be doing what is should do.

Thanks.

---

### Post by MishMich on 2011-03-05
also, I notice I have several kernel versions marked as installed going back to 2.6.27-17.  Am I right in thinking these can be removed (as in housecleaning) via synaptic?

---

### Post by mörgæs on 2011-03-05
If you have 2.6.27, it indicates that your system was originally 8.10, and that it has been upgraded three times to 10.04. 

You can remove everything but the latest 2-3 kernels, but as they are small you will not free much space. 

Are you sure that the security flaws you talk about in 2.6.32 are found in -29?

---

### Post by MishMich on 2011-03-05
No idea:

[http://www.zdnet.com.au/ubuntu-peppered-with-holes-339310663.htm](http://www.zdnet.com.au/ubuntu-peppered-with-holes-339310663.htm)

Mish

---

### Post by wojox on 2011-03-05
Open your terminal and copy and paste:

```
sudo apt-get update; sudo apt-get upgrade; sudo apt-get dist-upgrade
```

Then reboot your computer and run uname -a

---

### Post by bumder on 2011-03-06
> **wojox said:**
> Open your terminal and copy and paste:

```
sudo apt-get update; sudo apt-get upgrade; sudo apt-get dist-upgrade
```Then reboot your computer and run uname -a

would that not just update you from 10.04 to 10.10?


i've started a similar thread on this at [http://ubuntuforums.org/showthread.php?t=1700701](http://ubuntuforums.org/showthread.php?t=1700701)

---

### Post by tgm4883 on 2011-03-06
> **bumder said:**
> would that not just update you from 10.04 to 10.10?


i've started a similar thread on this at [http://ubuntuforums.org/showthread.php?t=1700701](http://ubuntuforums.org/showthread.php?t=1700701)

Nope, dist-upgrade installs new dependencies

---

### Post by mörgæs on 2011-03-06
> **MishMich said:**
> No idea:

[http://www.zdnet.com.au/ubuntu-peppered-with-holes-339310663.htm](http://www.zdnet.com.au/ubuntu-peppered-with-holes-339310663.htm)

Mish

This is really bad journalism. 

There seems to have been some bugs regarding the server installs, but now they are fixed. Are you running a server? 


And this nonsense about vulnerabilities if having 'local access': If you are on a local machine, you can boot a live CD and get access to everything. It has been like that from the first Ubuntu, and that is how it should be. 

If you want to keep files private, the only effective measure is encryption.

---

### Post by Baldrick_NZ on 2011-05-23
> **tgm4883 said:**
> Nope, dist-upgrade installs new dependencies

So, if I run that sudo upgrade script, will my current version still show up in Grub as well on reboot? IE: Will I have the option of the new kernel, my current one along with any other OS I might have, or will it delete my current kernel?

Cheers...

---

### Post by mörgæs on 2011-05-23
If the upgrade command works as intended, you will upgrade to the next release of Ubuntu (10.10, by default on 2.6.35) but still have the old kernels to choose from.

Reality however is that these upgrades often break. Be ready for a clean install to solve the problem.

But... given your signature, it seems like you are staying with 10.04 (which is a good idea anyway). How come you ask about upgrades?

---

### Post by TiberiusT on 2011-05-23
Morgaes,

Apologies for jumping in here but I posted this [http://ubuntuforums.org/showpost.php?p=10844573&postcount=1](http://ubuntuforums.org/showpost.php?p=10844573&postcount=1) query abt nolapic requirement for my X58 mobo

I am without a response so far. Further reading has suggested that a kernel upgrade to 36 or above might solve my problem, but does that mean such an updgrade would lead to me using 10.10? If that's the only way to get it working then I might as well do a clean install of 10.10. 

Tks

T

---

### Post by Baldrick_NZ on 2011-05-23
> **mörgæs said:**
> How come you ask about upgrades?

Thanks for that.

I guess anything that could make things smoother or faster running is always a good thing. 

My signature is merely my own personal opinion regarding 11.04 having tried it. There seemed to be too many things that needed to be corrected, it wasn't as 'out of the box' user friendly as 10.04 on my machine, so it disappeared. I don't like that Unity (in its current form) is un-customisable. I'm really a fan of having a desktop that way I want it, not the way someone else wants me to have it, which was a huge pull for me to Ubuntu in the first place.

I think Canonical have a long way to go before Unity will be bug-free. Not to say that Gnome is, but with more years on it than Unity, Gnome's bugs aren't as major.

For me, I don't like the idea of upgrading with every release. At least not until the new release has proven itself for stability and reliability and has features that I consider worth upgrading to. As long as I get regular LTS security updates, I'm happy to wait for the next LTS release.

---

