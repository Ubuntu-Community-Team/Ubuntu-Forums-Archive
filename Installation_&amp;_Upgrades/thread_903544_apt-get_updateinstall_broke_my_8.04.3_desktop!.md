---
title: "apt-get update/install broke my 8.04.3 desktop!"
date: 2008-08-28
forum: Installation &amp; Upgrades
---

### Post by cewyattjr on 2008-08-28
> sudo apt-get update
>
> sudo apt-get install

So I ran these, and after a reboot startx just throws me to the console in 8.04.3 on my Sony Vaio laptop.

Another symptom is that any sudo apt-get install pkg returns errors like this:

gconftool-2: undefined symbol: g_option_context_set_translation_domain
dkpg: error processing yelp (--contifgure):
 subprocess post-installatino script returned error exit status 

Thanks for any suggestions... should I reformat and reinstall at this point?  Not sure what else to do, but it kinda sucks that an upgrade breaks it.  :(

-Chuck

---

### Post by oilchangeguy on 2008-08-28
> **cewyattjr said:**
> > sudo apt-get update
>
> sudo apt-get install

So I ran these, and after a reboot startx just throws me to the console in 8.04.3 on my Sony Vaio laptop.

Another symptom is that any sudo apt-get install pkg returns errors like this:

gconftool-2: undefined symbol: g_option_context_set_translation_domain
dkpg: error processing yelp (--contifgure):
 subprocess post-installatino script returned error exit status 

Thanks for any suggestions... should I reformat and reinstall at this point?  Not sure what else to do, but it kinda sucks that an upgrade breaks it.  :(

-Chuck

probably the best thing to do is to back up any data, and do a fresh install. and this time let ubuntu tell you when updates are available. there's no need to do manual updates.

---

### Post by cewyattjr on 2008-08-28
Thanks oilchangeguy!

I wonder if there is a way to reinstall the OS that doesn't require me to repartition and rewrite the boot sector.  I'm installed on a laptop with a grub dual boot w/Vista.

-Chuck

---

### Post by king metal on 2008-09-05
I had this exact same thing happen after updating, so this may be a bug in one of the packages.

And Synaptic is just a GUI for apt. It doesn't matter if you use apt to do the updates manually or let synaptic do them automatically.

---

