---
title: "Strange aptitude/adept problem?"
date: 2006-10-07
forum: Installation &amp; Upgrades
---

### Post by gila_monster on 2006-10-07
Well, today was an adventure. I spent a good portion of it reparitioning the hard drive in my lappy and moving /home to its own partition. This succeeded, eventually. In the process, I ended up putting a fresh, clean installation of kubuntu on the box. Everything boots.

The problem is that adept (and aptitude) only shows me installed packages. I see NOTHING for anything not installed already. Thus, I can't install Firefox or Thunderbird or what have you from the repositories. (Yes, I know I can install manually, but repositories are generally a good thing.) This limits me in maintaining my box, and it makes me wonder how difficult the upgrade to Edgy is going to be later this month.

I did have some problems getting the internet working after the install (had to change default device and add some DNS settings that should have come with DHCP but for some reason didn't). Could this be causing problems for aptitude?

Thanks much for your attention. Someday maybe I'll be able to answer more questions than I ask.

gila

---

### Post by Jon F on 2006-10-07
Yes I have just installed KUbuntu and had the same problem. I'm new to all this but I managed to get it to work.

What I think you need to do is set up the repositories on adept manually.

So open Adept by going to menu->System->Adept(Pakage Manager)

Then select "Manage Repositories" on the "Adept" menu.

Enable some of the "dep" entries on the repository list by right mouse clicking on the list. Then click fetch updates.

Now close Adept and open menu->Add-Remove programs. And it should allow you to install.

Jon

---

### Post by gila_monster on 2006-10-07
Thanks, Jon, that did the trick! I am much obliged.

gila

---

