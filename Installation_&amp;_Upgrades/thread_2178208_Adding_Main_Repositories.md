---
title: "Adding Main Repositories"
date: 2013-10-02
forum: Installation &amp; Upgrades
---

### Post by MartianTek3 on 2013-10-02
Hello, 
I recently just upgrade to 13.04 64bit (from 12.10) but ever since then installing PPAs have become a nightmare. 

After ```
sudo apt-get update
``` 

I received this: 
```
W: Failed to fetch bzip2:/var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_raring_main_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_raring_main_binary-i386_Packages  Hash Sum mismatch


W: Failed to fetch bzip2:/var/lib/apt/lists/partial/ppa.launchpad.net_linrunner_tlp_ubuntu_dists_raring_main_binary-amd64_Packages  Hash Sum mismatch


E: Some index files failed to download. They have been ignored, or old ones used instead.



``` 

Also in Synaptic this message: 

```
 E: The value 'stable' is invalid for APT::Default-Release as such a release is not available in the sourcesE: _cache->open() failed, please report.
``` 

I believe the problem is that I deleted the MAIN repository (Canonical) for 13.04 [ATTACH=CONFIG]246679[/ATTACH]   

Goal: To find answers to restoring the PPA so that I can install TLP(power manager) and other software 

-MartianTek3

---

### Post by grahammechanical on 2013-10-02
My guess is that your link to the repository of the PPA is incorrect. It is always best to remove any PPAs before Upgrading to avoid issues like this. From the Launchpad page ofr this PPA i see this

> [COLOR=#333333][FONT=Ubuntu Mono]deb [/FONT][/COLOR][http://ppa.launchpad.net/linrunner/thinkpad-extras/ubuntu](http://ppa.launchpad.net/linrunner/thinkpad-extras/ubuntu)[COLOR=#333333][FONT=Ubuntu Mono] [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]raring[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono] main 
[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]deb-src [/FONT][/COLOR][http://ppa.launchpad.net/linrunner/thinkpad-extras/ubuntu](http://ppa.launchpad.net/linrunner/thinkpad-extras/ubuntu)[COLOR=#333333][FONT=Ubuntu Mono] [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]raring[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono] main [/FONT][/COLOR]

[https://launchpad.net/~linrunner/+archive/thinkpad-extras](https://launchpad.net/~linrunner/+archive/thinkpad-extras)

If you open the Ubuntu Software tab in that utility you may see that the Main repository is still there. See, the tick mark against Canonical-supported free and open source software (main).

Regards.

---

### Post by MartianTek3 on 2013-10-06
Ok I did that, the main was checked. Perhaps I have to reset the APT? 

How can i edit the repository text file?

---

