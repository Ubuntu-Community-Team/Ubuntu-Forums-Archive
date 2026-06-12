---
title: "Installing RTAI with Adept Manager"
date: 2008-04-21
forum: Installation &amp; Upgrades
---

### Post by reg2117 on 2008-04-21
Forum Members,
   I am setting up a machine to run real-time threads using the RTAI patch and noticed the RTAI patch listed in the packages in adept manager. 

**Can someone point me in the right direction for reading more about installing the RTAI patch with adept manager (as opposed to following the instructions from [[COLOR="Blue"]www.rtai.org[/COLOR]]([COLOR="Blue"]www.rtai.org[/COLOR]), ie downloading/compiling a vanilla kernel....)? **

   There are no hits in the ubuntu wiki for RTAI and nothing specific to installation of RTAI with adept manager in the forum posts.
    Specifically, I want to patch the kernel with RTAI and set up the adept_manager to freeze the kernel such that future updates do not break the RTAI patch. 

[B]If I use the adept_manager, do I need to compile a vanilla kernel separately beforehand or is this automated? 
Can I set up the grub to select between a patched and non-patched kernel if I install the RTAI patch with the adept_manager?[/B]

Any direction to using adept_manager for the installation would be much appreciated.

---

### Post by JCSalomon on 2008-06-05
&#8195;I’ve been looking to do much the same thing; did you end up getting any help?
—Joel

---

### Post by reg2117 on 2008-06-12
> **JCSalomon said:**
> &#8195;I’ve been looking to do much the same thing; did you end up getting any help?
—Joel

No help as of yet. 

I did try the installation using the adept_manager without downloading/installing the vanilla kernel. This did not result in a successful patch and is not worth attempting.

---

