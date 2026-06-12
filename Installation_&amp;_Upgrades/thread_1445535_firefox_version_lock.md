---
title: "firefox version lock"
date: 2010-04-02
forum: Installation &amp; Upgrades
---

### Post by pumpkinbeer on 2010-04-02
Hello,
I'm in Hardy 64-bit, I'm trying to downgrade firefox to 3.5.X.  Synaptic keeps installing 3.6.2  How do I stop this and force it to install 3.5.X.   Force Version is greyed out.

The packages available are firefox-2, firefox-3.0, 3.1, 3.5 and 3.6, but under the "Latest Version" column is states 3.5.8 for every package less or equal to 3.1 and it states 3.6.2 for all packages greater or equal to 3.5.

Ive tried installing 3.1, which I thought would install 3.5.8 but that didn't happen, it still installed 3.6.2

Help... What am I doing wrong, I've wasted a 3/4 of a day on this issue. 

System is fully updated.

Following is my list of package repositories.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main universe restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe main multiverse restricted #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe main multiverse restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security universe main multiverse restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe main multiverse restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe main multiverse restricted

deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) hardy main
deb [http://ppa.launchpad.net/wvengen/ppa/ubuntu](http://ppa.launchpad.net/wvengen/ppa/ubuntu) hardy main
deb [http://ppa.launchpad.net/ubuntu-burning/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-burning/ppa/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/ubuntu-burning/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-burning/ppa/ubuntu) hardy main

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) hardy main

Thanks in advance
I may not be able to reply to any answers until Monday.

---

### Post by mikewhatever on 2010-04-02
Does the ppa you used to get a newer firefox has the version you want? If it doesn't, you are out of luck. Anyway, what's wrong with 3.6?

---

### Post by pumpkinbeer on 2010-04-05
>Does the ppa you used to get a newer firefox has the version you want?

I assume it does since it shows up in Synaptic 3.5.  How can I verify that?

>what's wrong with 3.6?

Vmware webaccess plugin not working, I haven't found another way to get to the virtual machines in 64-bit linux.

---

### Post by mkvnmtr on 2010-04-05
Look in synaptic to see which launchpad repository has the Firefox you do not want. Disable it . Uninstall it with complete removal. Then find in synaptic the version you want and install it. That should be all you need to do.

---

### Post by pumpkinbeer on 2010-04-05
I'm trying to use the ubuntu-mozilla-daily ppa for hardy.  I believe it contains many versions (listed on [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)) but will only install the 3.6 version.  I can't install the 3.5.

Is there another PPA I should be using?  I don't see one by searching the ppa list on the above site.

---

### Post by mkvnmtr on 2010-04-05
You should be working in synaptic. Type firefox in the search box. You should then see all the firefox apps that are available. Look for the one installed. Look to see which repository it comes from. Then at the top of synaptic open the window for repositories. Find that repository. Click on it so the check mark is not checked.Reload. Then uninstall every thing that says Firefox that you found when you searched for firefox.

Then use synaptic to find the version of Firefox that you wish to install. Install it. Open it to check if it is the version you want it to be.

---

### Post by pumpkinbeer on 2010-04-05
OK - I have never used Synaptic in that manner, with the search.  I always use the "All" and click on the package list and type to find the package I want.  Doing it my old way, all the versions show up.  Doing it as you (mkvnmtr) described below now makes sense, at least the Force Version is not greyed out.  However I don't have 3.5.X available to be forced, so I guess I need a repository that has that version.   

And... is there an easy way to see what repository a package comes from in Synaptic?  The properties list shows maintainer but not repository name.  Is it part of the package name for standard packages?

I am trying to use the ubuntu-mozilla-daily repo.  They have 3.5 listed on the website.  Why do all the versions show up in the "All" list in the package column, but then they aren't really available (to be forced)?  I see 2, 3.0, 3.1,3.5, 3.6 and 3.7.  Is there a writeup on this somewhere?

---

### Post by mkvnmtr on 2010-04-05
if you type Firefox en the quick search box and then on the left click on orgin you will see the repositories you have enabled. As you click on each one you will see what Firefox apps it has. I am on my 9.04 now . The launchpad net/universe has 3.5. Other launchpad repositories have others. I believe on my 9.10 3.5 is standerd repositories and not launchpad. You will need to look on your system.
If you do a complete removal of what you have in synaptic and then install what you want you should get it.
Getting used to synaptic lets you work with your system very well. Spend a little time exploring it. It will be worth while.

---

