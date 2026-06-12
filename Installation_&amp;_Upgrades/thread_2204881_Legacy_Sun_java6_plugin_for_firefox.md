---
title: "Legacy Sun java6 plugin for firefox"
date: 2014-02-10
forum: Installation &amp; Upgrades
---

### Post by 1clue on 2014-02-10
Hi.

I need to install a legacy java plugin for supporting an existing product.  This box is a VM, it's NOT going to be on the net and will be backed up so that if something happens we can revert easily.

Here's the deal:
[LIST=1]
[*]Customer has an old version of our applet but still is under a support contract.
[*]We have a build box which is specific to that customer (java6 compiler, everything)
[*]We just discovered that the web browser doesn't actually have the java6 plugin on it.
[*]I have the JRE installed (NOT a PPA) and it's working.
[*]The plugin is not registered in Firefox.
[/LIST]

Please don't go through the "you should upgrade to Java 7" thing.  We have.  We also have a few customers who don't want to upgrade their product but we're still contractually obligated to support them.  I know all the risks, I've made sure they do too.  Everything is being run behind a firewall.  It MUST be sun/oracle java6.

I know we did this before but I can't find a system which is not broken right now, which means something updated and broke the existing installations.  I can't remember where the symbolic links go.

Can anyone help?

Thanks.

---

