---
title: "How should I plan a fresh install"
date: 2011-01-06
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2011-01-06
I have just been through a reinstall of 10.10. Crashes had made it unstable. 

My /home is on a separate partition.

I saved the synaptic markings to a separate partition.

Reformatted the boot partition, did the fresh install  and then loaded back the markings into synaptic. 

At that point my troubles started. The repositories were not saved by synaptic and so much of the marked files could not be loaded.

It has taken me days to rebuild the system.

**What should I have done to make the fresh install easy and bring back my installed programs?**

---

### Post by garvinrick4 on 2011-01-06
I am missing something I think, did you not set up your repositories including ppa's before
you tried to install packages located in those repositories.

---

### Post by Robbyx on 2011-01-06
> **garvinrick4 said:**
> I am missing something I think, did you not set up your repositories including ppa's before
you tried to install packages located in those repositories.

No, because it did not occur to me that synaptic would offer a marking saving system that would not come with the repositories. 

By the time I realised that I should have saved the repository details they had been formatted out. **Is there a program that will save not only the markings, but the repositories, the authentication codes and any extra files installed via the software centre?**

---

### Post by garvinrick4 on 2011-01-06
I myself have never heard nor read anything about a tool to automatically copy repositories 
and reload them but you can make a copy of /etc/apt/sources.list
onto a flash drive or something similar and use that. Keys will have to be installed I am sure.

---

### Post by Robbyx on 2011-01-06
I realise there are other problems. For example one of my partitions is not being recognised. So I should have copied fstab, but didn't and it is pain to work out what to do after a few years of not thinking about it.

I wonder where the authentication codes are stored for the other software sources.

I can't believe I have had so much trouble from this fresh install when people often recommend it when there is a new Ubuntu version. [B]How are they avoiding all the trouble I have experienced?

[/B]

---

### Post by garvinrick4 on 2011-01-06
I think it just takes getting used to. You kind of get into a habit of setting up your repositories first. Then:
sudo apt-get install ubuntu-restricted-extras
sudo apt-get update && sudo apt-get upgrade
While all that is going on can set up panels and
main-menu. appearance and keyboard shortcuts and such.
Then install media players and any other individual
packages you use. Seems to take about an hour to get
one right and about 4 or so gig in size. It is just plain old
repititon I would have to say. Each seems to have their own style.
But repositories have to be #1 in each. 
# Do not think I can remember not having a partition recognized.

---

### Post by presence1960 on 2011-01-06
> **Robbyx said:**
> No, because it did not occur to me that synaptic would offer a marking saving system that would not come with the repositories. 

By the time I realised that I should have saved the repository details they had been formatted out. **Is there a program that will save not only the markings, but the repositories, the authentication codes and any extra files installed via the software centre?**

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

Try that, I have used it to rebuild my /etc/apt/sources.list

First make a copy of your sources.list file. Then use that link and go to your original sources.list and remove what is in there and copy/paste the output from the sources.list generator page. Click save on the toolbar and close the file. You should be good to go.

---

