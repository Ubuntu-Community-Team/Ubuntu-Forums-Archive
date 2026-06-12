---
title: "&quot;Broken packages&quot; error when trying to install gitk"
date: 2009-12-25
forum: Installation &amp; Upgrades
---

### Post by Jacolyte on 2009-12-25
```
blaine@blaine-laptop ~/devel/ruby/rbjacolyte $ sudo apt-get install gitk
[sudo] password for blaine: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gitk: Depends: git-core (< 1:1.6.3.3-.) but 2:1.6.2.4-1~avh1~intrepid1 is to be installed
E: Broken packages
```

git version 1.6.2.4

---

### Post by raymondh on 2009-12-25
> **Jacolyte said:**
> ```
blaine@blaine-laptop ~/devel/ruby/rbjacolyte $ sudo apt-get install gitk
[sudo] password for blaine: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gitk: Depends: git-core (< 1:1.6.3.3-.) but 2:1.6.2.4-1~avh1~intrepid1 is to be installed
E: Broken packages
```

git version 1.6.2.4

Access synaptic.  On the left column, there is a tab BROKEN.  Open it and ask synaptic to 'fix broken'.  See if this works.

---

### Post by Jacolyte on 2009-12-27
I've fixed it. The fix was pretty obvious, too. I looked up git-core and highlighted it, selected Package -> Force version, and set it to 1:1.6.3.3, which is what gitk depends on.

Gitk and git-core are now happily installed. Thanks for the help.

---

