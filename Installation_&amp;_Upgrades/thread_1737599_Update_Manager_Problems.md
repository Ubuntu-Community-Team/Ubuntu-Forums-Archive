---
title: "Update Manager Problems"
date: 2011-04-23
forum: Installation &amp; Upgrades
---

### Post by Marx Dudek on 2011-04-23
Hi, let me state at the outset that I am a very new Ubuntu user.  My computer proficiency is above intermediate, and I have some rudimentary (and most likely outdated) knowledge of *nix.

I am using a fresh install of Natty Narwhal as the sole OS on an Acer dual-core AMD64 system.

When going to the update manager, it tells me that the last update was 12 days ago.

When selecting "Check", I get "Failed to Download Repository Information".  The details are below.

```
W:Failed to fetch http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/binary-amd64/Packages  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/team-xmbc/ppa/ubuntu/dists/natty/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/team-xmbc/ppa/ubuntu/dists/natty/main/binary-amd64/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

My internet connection is just fine.  Are these outdated locations, and do I need to update them manually?  Or is this expected behavior if there is not an update?

Thanks in advance for your help!
MD

---

### Post by wojox on 2011-04-23
There is no natty repo [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/)

---

### Post by SavageWolf on 2011-04-23
Have you added any non-default repositories? Those ones don't seem to exist.

---

### Post by ivanovnegro on 2011-04-23
Hello and welcome. First its not very convenient to see beginners installing a beta version, can always have some issue.
Ok, now to your problem, I would remove the 404 error packages and then try to update again, the packages are showing an error. You have to edit your sources list and remove them from there.

---

### Post by Marx Dudek on 2011-04-23
@SavageWolf Actually, yes.  Now that you mention it.  I tried installing XBMC, which was unsuccessful.  I think this is the cause.

@ivanovnegro I realize that those who are not tech-savvy can be difficult to assist.  I did approach this question with some trepidation because of this.  I do understand the advice offered here, however, and I believe this should solve my issue.

The best way to learn is to try, and the second best way to learn is by asking questions.  Let me try this and thank you for your help.

---

### Post by Marx Dudek on 2011-04-23
@ivanonegro That's precisely the information that I needed, and I learned something in the process.

Thank you very much.

---

### Post by ivanovnegro on 2011-04-23
> **Marx Dudek said:**
> @ivanonegro That's precisely the information that I needed, and I learned something in the process.

Thank you very much.

No problem, great that it worked.
Yes, it can be cool to test the newest stuff, why not, but sometimes new users go into a beta release and later leave because of too much problems.
Its good to have the will to learn, it makes also sense to use the new interface and to getting used to it instead to learn the old one and then to change again, if you know what I mean if you use Unity.
But also to improve the releases Ubuntu needs testers to file the bugs thats what I am doing right now.

---

### Post by OpenThinking on 2011-12-28
To install XBMC without the 404-error, read the following link:
**[http://www.noobslab.com/2011/09/install-xbmc-on-ubuntu-1110-oneiric.html](http://www.noobslab.com/2011/09/install-xbmc-on-ubuntu-1110-oneiric.html)**

**To Install in Ubuntu 11.10/Linux Mint 12 open Terminal and copy the following commands in the Terminal:**

        sudo apt-get install ubuntu-restricted-extras
        sudo apt-get update
        sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update


**Now adding maverick ppa and installing XBMC enter following commands in Terminal:**

        echo deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) maverick main | sudo tee /etc/apt/sources.list.d/xbmc.list
        sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com --recv-keys 91E7EE5E
        sudo apt-get update
        sudo apt-get install xbmc

---

### Post by MunksterMan2 on 2011-12-30
> **OpenThinking said:**
> To install XBMC without the 404-error, read the following link:
**[http://www.noobslab.com/2011/09/install-xbmc-on-ubuntu-1110-oneiric.html](http://www.noobslab.com/2011/09/install-xbmc-on-ubuntu-1110-oneiric.html)**

**To Install in Ubuntu 11.10/Linux Mint 12 open Terminal and copy the following commands in the Terminal:**

        sudo apt-get install ubuntu-restricted-extras
        sudo apt-get update
        sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update


**Now adding maverick ppa and installing XBMC enter following commands in Terminal:**

        echo deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) maverick main | sudo tee /etc/apt/sources.list.d/xbmc.list
        sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com --recv-keys 91E7EE5E
        sudo apt-get update
        sudo apt-get install xbmc
Worked for me.  I had to change "$(lsb_release -cs).list" to "oneiric" though because I'm using mint instead of the real oneiric.

---

