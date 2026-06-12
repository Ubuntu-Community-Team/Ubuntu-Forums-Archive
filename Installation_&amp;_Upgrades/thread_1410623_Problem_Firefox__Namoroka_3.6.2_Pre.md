---
title: "Problem: Firefox / Namoroka 3.6.2 Pre"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by 8bitx64 on 2010-02-18
Hey,

Recently I made the mistake of upgrading my firefox from a stable 3.5 to the unstable / newer 3.6.2 pre-release.  As a result this has just been a pain in my side.  I want firefox 3.5 back but I do not know what to do to undo what has been done to get 3.5 back.  Aside from a full system re-install, I dont want to do, I am stuck.

Any ideas / suggestions / good-will comments to help me out?

Thanks.

I am on Ubuntu 9.10 x64bit

---

### Post by wrose51106 on 2010-02-19
Open synaptic, search and destroy anything firefox related.

open a terminal and run:

sudo apt-get update

sudo apt-get install firefox-3.5

-Bill

---

### Post by 8bitx64 on 2010-02-19
Hey Bill,

Thank you for the suggestion.  I followed the simple instructions to the letter and when it reinstalled it did so using 3.6.2pre, not 3.5.

Any other suggestions?

---

### Post by 8bitx64 on 2010-02-19
I got creative and I started playing around with some options (and other things I read) with no success.

Went to Synaptic Package Manager and tried "Force Version".  Selected the version I wanted (there are 3).

After I do that I get an error message:
E: Unable to correct problems, you have held broken packages.
E: Unable to lock the download directory

So, I went back to synaptic and selected Edit -> Fix broken packages, which seemed to do nothing.

Then I followed the directions as before of complete removal, update, reinstall and it keeps force pushing it to version 3.6.2.

So, this is where I am stuck... Any advice?

I am not a total novice to Ubuntu, but I still have LOTS to learn. LOTS!

---

### Post by 8bitx64 on 2010-03-01
Can anyone offer any advice on how to completely 100% remove firefox?  I want to use it, however when ever I do the sudo apt remove firefox and reinstall, it reinstalls 3.6.  I would prefer to use 3.5.  Have had some stability issues with 3.6

Any assitance would be appreciated.  :KS

Thanks!

---

### Post by anglican on 2010-03-02
> **8bitx64 said:**
> Can anyone offer any advice on how to completely 100% remove firefox?  I want to use it, however when ever I do the sudo apt remove firefox and reinstall, it reinstalls 3.6.  I would prefer to use 3.5.  Have had some stability issues with 3.6

Any assitance would be appreciated.  :KS

Thanks!

After you've removed firefox as per the instructions above you also need to remove the repo from which 3.6 is being installed, otherwise every time you install firefox you will get 3.6 as it is the newest version. In synaptic go to settings->repositories and uncheck ubuntu-mozilla-daily in the Third Party tab. Then install firefox and you'll get the stable version from the main repository.

H

---

### Post by mkvnmtr on 2010-03-02
You might also need to remove the .mozilla folder from your home directory. Before youn reinstall 3.5.

---

