---
title: "Problem with nmap install"
date: 2007-11-11
forum: Installation &amp; Upgrades
---

### Post by cstep on 2007-11-11
Greetings to All from a New Linux User;

I am having trouble installing nmap 4.20 onto 6.06 LTS.  When I run the ./configure file the results I get are;  All of the lines "checking for nmap*... are no"
The next lines report a yes.  The last two lines are:
checking build system type ... Invalid configuration 'nmap-4.20': machine name 'nmap' not reconized.

configure:error: /bin/sh ./confige.sub nmap-4.20 failed

A little help to get me going.

Thanks

cstep

---

### Post by eggdeng on 2007-11-11
As far as I can tell, the version in the repos is 4.20.
```
sudo apt-get install nmap
```

---

### Post by mbf2k on 2007-11-21
I am not having success installing nmap through apt-get install. Is it off the package list for some reason??

---

### Post by eggdeng on 2007-11-22
On 6.06, which I'm using, it's listed in Synaptic. You could try ```
apt-cache search nmap
``` If you can't see it, you probably need to enable a repo, (maybe the Backports repo corresponding to your version).

---

