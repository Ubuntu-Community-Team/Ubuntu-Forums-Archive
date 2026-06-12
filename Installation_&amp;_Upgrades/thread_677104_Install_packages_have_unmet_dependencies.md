---
title: "Install packages have unmet dependencies"
date: 2008-01-24
forum: Installation &amp; Upgrades
---

### Post by Mysticpriest on 2008-01-24
I am getting an icon in my top panel saying : "Install packages have unmet dependencies" 
I can't use the Add/Remove utility in Applications, I can't open the Synaptic Package Manager either. I get this message : 

"**An error occured**. 
E: Type '“deb' is not known on line 56 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report."

I am also trying to install IRC, I get the following:

"**Software index is broken**
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'."
-------------------------------------

I am a noob with Linux. I need detailed advice on how to fix this. I don't know how to edit files, I don't know the Linux Terminal commands.
Thanks
Thanks

---

### Post by Rocket2DMn on 2008-01-24
Something is clearly wrong with your sources.list file.  Can you post the contents here?
```
cat /etc/apt/sources.list
```

---

