---
title: "Kernel subversion update control"
date: 2019-12-11
forum: Installation &amp; Upgrades
---

### Post by dscoland on 2019-12-11
Hi,

We have decided to install Cylance on some of our linux, non-vendor, Ubuntu distributions.  Unfortunately, Cylance has been rolling out Agents that support only subversions dated back about 1 - 2 months. Ideally we would want to be on the latest kernel subversion. In this case though, we would need to aim for the latest subversion that is supported by the latest version of the Cylance agent.

I've looked for various related threads, but I can't seem to find a concrete answer to address this challenge. Is there a way to control which kernel subversion a Linux distribution we are on? We want to have the ability to upgrade to a specific distribution, without upgrading to the latest, and also to be able to downgrade if possible.

And example would be if currently running Ubuntu 18.0.4.3 LTS on some distributions with a kernel subversion of 4.15.0-70-generic, we would need to downgrade back to 4.15.0-66. 

Is this feasible?

Thanks!
Daniel

---

### Post by dscoland on 2019-12-12
I think I may have answered my own question, but just wanted to confirm with anyone. I searched and confirmed that the following image existing via: **apt-cache search 4.15.0-66**

Then I ran the following:

[FONT=Calibri]**sudoapt-get upgrade linux-image-4.15.0-66-generic**[/FONT][FONT=Calibri][/FONT]

Is this a good way to do it?

Thanks,
Daniel

---

