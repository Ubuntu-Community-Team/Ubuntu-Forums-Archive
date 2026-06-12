---
title: "Removing a PPA completely?"
date: 2017-02-21
forum: Installation &amp; Upgrades
---

### Post by cogset on 2017-02-21
I've added a couple of PPAs a while ago to my Trusty installation, now  thinking again about it I'd like to completely remove those, as in replacing the packages installed by those PPAs with default Trusty versions and revert this installation to a standard Trusty version. 

 One of those was the menulibre PPA, which I don't care much about since I've learned to manually edit the config files in Lubuntu to customize the menus - the other one was  a multimedia PPA which supplied stuff not yet available in Trusty and more advanced versions of available packages. 

 I'm worried about this one, since I can see I have some stuff installed (libraries, codecs) that I'm afraid would break something if removed and replaced. 

 What would be the best way to proceed here? I can use manual procedures if needed, such as first editing my sources to remove the PPA lines, then track down the packages installed by it and remove them, and  finally install the default packages.

  But is that advisable? Should I use automated tools instead, such as ppa-purge?   Of course I'd be taking a backup before, just in case: if anything, I'm going to keep my configuration files for the applications that I'm going to reinstall, and I guess that --purge remove is going to get rid of those.

---

### Post by ajgreeny on 2017-02-21
If you wish to do this manually, it is certainly possible, but not so straightforward as using ppa-purge which carries out all the actions automatically, and is probably the safest way to proceed.

If you really want to do it manually it is probably easiest using synaptic.
Using that you can use the Origin filter in the left hand pane to see what is installed from each ppa that you want to remove.
Check those packages for removal and see what else may be taken with them; this is where it get problematical as some of those packages may be essential for the OS and also remove a lot of dependency linked packages, but if no extras are taken, continue, taking note of exactly what is removed.

Now go to Settings -> Repositories in the synaptic menu and disable that ppa from the Other Software tab, and finally refresh the repositories and install everything that was removed previously.

As you can see, it is a bit of a palaver, and I suggest not worth the hassle when ppa-purge will do it all for you with a simple command.

---

### Post by cogset on 2017-03-09
Yes, that definitely looks like an exercise...  On regard to this  > not worth the hassle when ppa-purge will do it all for you with a simple command  I've never used it, will it really remove all the stuff from the PPA and then replace it with packages from the official repository *without breaking anything* in one go ? Is that tried and tested ?

---

### Post by DuckHook on 2017-03-09
@cogset

With a 2 week hiatus between ajgreeny's post and your reply, please don't expect a response. I myself unsubscribe from threads if the OP hasn't responded in 4 days. It's the only way to manage the myriad threads that we juggle daily.

As for your question: there are no guarantees, but I've used ppa-purge for a long time and it's always worked very nicely for me. **CAVEAT** I refuse to add more than two or three PPAs because "thar be dragons". So my data set is admittedly a small one. However, almost every staff member recommends it, and there are few if any issues reported on these forums from people who have come to a sad state because of it. On the contrary, the people who report good success, even in complex cases, is high. 

Like all recommendations, when in doubt, Google for further knowledge and caution.

---

### Post by jis on 2017-03-16
I'd suggest you try my branch of ppa-purge. It has a simulation option, so it is safer to try. See more information [here]("https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2017-March/017342.html").

---

### Post by cogset on 2017-03-16
Alright, thanks everyone.

---

### Post by SeijiSensei on 2017-03-16
For a brute-force method, use "sudo rm" to delete the corresponding *.list and *.save file(s) from /etc/apt/sources.list.d/.  That won't remove any installed software from the system, but it will remove the PPA.  Run "sudo apt-get update" to finish the task.

---

### Post by jis on 2017-03-17
As for removing completely, ppa-purge does not actually purge packages currently, just remove. An option to purge could be added to it. It would not purge the packages that it downgrades even then.

---

### Post by cogset on 2017-04-07
> **SeijiSensei said:**
> For a brute-force method, use "sudo rm" to delete the corresponding *.list and *.save file(s) from /etc/apt/sources.list.d/.  That won't remove any installed software from the system, but it will remove the PPA.  Run "sudo apt-get update" to finish the task. 

  That sounds really definitive - however, after "apt-get update" , I guess you still have to run "apt-get upgrade" followed possibly by "apt-get dist-upgrade" to finish the job?

  Unless, the method you are suggesting would just "freeze" the already installed packages from the PPA(s) but not remove them ?

---

### Post by SeijiSensei on 2017-04-07
Yes, you would still have everything that was installed, but they would no longer be updated from the PPAs.
 
Running "upgrade" wouldn't matter.  That would upgrade all the packages for which there are still repositories but do nothing with the packages in the now disabled repositories.

If you want a more careful approach, I'll sometimes create a "disabled" directory under /etc/apt/sources.list.d/ and move the appropriate PPA files into that.  Then if you want to bring something back, you just need to move it out of the disabled directory.

---

