---
title: "Feisty to Hardy upgrade - how to identify additonal packages?"
date: 2008-04-21
forum: Installation &amp; Upgrades
---

### Post by parkejr on 2008-04-21
Hi,

going to upgrade from feisty to hardy in a few days. My feisty system has a load of additional packages, that I've installed over the last wee while (some are downgrades, for compatibility). Is there a quick way I can call up a list of everything thats present on my current system, and compare it to what a current, fully up-to-date raw feisty install would look like?

The idea is that I could generate a list of stuff to get after once i've moved to hardy, not do it as I discover things don't work in the coming weeks?

Many thanks,

Jeff.

---

### Post by sc00ter on 2008-04-21
I'm in the same boat, from experience it is probably a good idea to strip back your Feisty install to ubuntu approved packages/repositories only. 

Part of this house-keeping exercise is to launch Synaptic Package Manager and select "Origin". This will categorize all installed packages which will aid in locating custom packages which are outside the Ubuntu core repositories and ease the pain in removing packages that may cause problems during the upgrade.

You'll probably need to comment out any 3rd party repos (I think the upgrade manager does this anyway) in the /etc/apt/sources.list.

Things like Compiz Fusion that may have come from Trevino etc. will need to be removed too.

If you've used Automatix, then it's best remove any trace of it from your system too before upgrading as this is known to cause problems.

I don't know about custom/compiled applications, how these will be treated. They'll either continue to work or will need re-compiling from source once you've finished upgrading.

Lastly and most importantly, BACKUP your system. I've used Clonezilla in the past to backup a system, which works well at creating disk images over a network, but you may have your own preferred backup process.

Does anyone else have any experiences upgrading from Feisty -> Gutsy -> Hardy ??

---

### Post by parkejr on 2008-04-21
Thanks sc00ter - I'm now thinking I might just go for a fresh install. Still leaves me with the problem of identifying packages I've added myself

---

### Post by sc00ter on 2008-04-21
In Synaptic Package Manager, select **Origin**. Basically the categories that begin with **Local** are the ones you can safely assume are the packages you've installed manually. 

For example:

Local/main
Local/universe
... etc.

---

