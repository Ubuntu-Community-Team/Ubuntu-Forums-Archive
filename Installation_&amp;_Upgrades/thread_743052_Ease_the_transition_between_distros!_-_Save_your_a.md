---
title: "Ease the transition between distros! - Save your app list!"
date: 2008-04-02
forum: Installation &amp; Upgrades
---

### Post by cisforcojo on 2008-04-02
I just wrote a script I call WNaRD (_W_e _N_eed _a_ _R_olling _D_istro) :)

This script saves your current list of applications (taken from Synaptic) into a file on your Desktop. After you install the new version of Ubuntu, you can re-run this script with the saved application list and it will find and install all the applications you were previously using. 

NOTE: 
   1. You should back up your /etc/apt/sources.list file to be able to find old repos you may have added.
   2. This program will not install something that isn't in the repos (for example, something you got from [http://www.getdeb.net](http://www.getdeb.net)) or something you built from source.
   3. It does not retain your application settings. However, you can (and probably should) keep your /home directory on a separate partition so when you do a fresh install, all of your application settings will still remain.

To run: 
```
chmod +x wnard.sh
./wnard.sh
```

I realize it's all this just to do 3 lines of actual code, but it's just to make everyone's life easier. If you have any suggestions or ideas on ways to make it better, feel free to mention it/do it yourself! (Just give me credit for the original work)

Enjoy!

---

### Post by someonestolemyname on 2008-04-07
This is actually really nice. I was unsure of how to do this, and your script worked perfectly. Thanks!

Daniel

---

### Post by erginemr on 2008-04-07
Great idea that, when rough edges are ironed out, will be the cure for many Ubuntu users upgrading but still wanting to do a clean install. I have a few reservations, though. Here are a few excerpts taken from the output of the script in my Gutsy system:
```
...
gcc-4.2-base					install
compizconfig-settings-manager			install
linux-headers-2.6.22-14				install
linux-headers-2.6.22-14-generic			install
python2.5					install
python2.5-dev					install
...
```
Looking at this list, I am afraid taking just a snapshot of currently installed packages might have some trivial to essential side effects. Considering this bunch of packages:

1. Starting with **gcc**; there are several versions of gcc available for different versions of Ubuntu and forcing the installation of ver.4.2 may be redundant if another version is installed by default in the subsequent release.

2. For **ccsm**; Compiz is revolving at an incredible speed, so are its sidekicks (i.e. programs designed to tweak them). So, a tweaker such as ccsm useful in one Compiz version may have no effect (or worse may break it) in a later version.

3. As for **linux-headers-2.6.22-14**; Hardy will have a later kernel installed and installing v.2.6.22-14 (if available in Hardy repos) would add its files and menu items (grub) and would be redundant (or worse might not work in Hardy due to incompatibility with other installed packages).

4. Finally, regarding **python2.5**; during Feisty times, I remember to have seen an Ubuntu based distro, where python2.4 and python2.5 co-existed just because some programs were dependent on 2.4 and some on 2.5. I don't know if a Python version 2.6 is out, but having both versions installed seems redundant again, let alone the extra hard drive space used.

So, I think we should focus on such issues for a while, before using the script you have developed on a large scale (again a great idea, I was also craving for such a thing for a long time).

---

### Post by cisforcojo on 2008-04-08
That's an excellent point for the kernel packages. I'd never even considered that. There's little reason for MOST people to want to hold onto old kernels. I'll see what I can do to remove all kernel entries from the list. They also just make the update process a LOT longer for something you are 99% sure not to use. I agree with the gcc point as well. As for python, I have python 2.4 AND 2.5 on my Gutsy system right now. I don't use Compiz (I did in the past) but I doubt the ccsm package will cause conflicts; you'll be downloading from the new Hardy repos.

This is not meant to be used as a widespread replacement. It'd be great if Canonical implemented this idea itself in a much better looking way and efficient way :)
Ideally, I'd like to organize the packages into essentially the Ubuntu menu catagories (Accessories, Games, Graphics, etc.) and provide a GUI so you could easily select from a tree-based organization what packages you wanted to re-install. This script is only the concept in its most basic form.

Thanks for the interest! I'd be very interested to hear any critiques/ideas you might have for the script!

---

