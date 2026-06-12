---
title: "Trouble Uninstalling Virtualbox"
date: 2015-03-28
forum: Installation &amp; Upgrades
---

### Post by shai3 on 2015-03-28
I was having trouble with the version of VirtualBox I uploaded through Ubuntu Software Center (4.3.18) so I uninstalled that and installed the latest version from Oracle (4.3.26). I'm getting incompatible kernel errors. 

The un-installation instructions from Oracle don't work... VirtualBox seems like it isn't in the place where it is expected. 

I believe that Software Manager did the installing for me origininally when I clicked on the .deb file that I had downloaded from Oracle Software Center opened up and clicked "install" there.

But now Software Center will not uninstall it. If I try to Install VirtualBox 4.3.18 from the Software Center it warns me there is another version on the machine and that I should uninstall it first. But I don't know how.

 Software Center does give me the choice to "Install it anyway" but I'm don't want to do that.

Thanks in advance for help.

---

### Post by shai3 on 2015-03-28
I did it.

I first I ran:

apt-get --purge remove virtualbox

I still got the same error when trying to install virtualbox in the Software Center. But I saw that it was complaining specificall about virtualbox-4.3

So I ran 


apt-get --purge remove virtualbox-4.3 and that successfully purged it and I could reinstall from the Software Center.

---

### Post by v3.xx on 2015-03-28
For adding/removing packages and other things you may find SPM easier to work with (I do).
[ATTACH=CONFIG]260953[/ATTACH]
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

