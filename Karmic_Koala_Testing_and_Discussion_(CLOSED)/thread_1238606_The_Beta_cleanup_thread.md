---
title: "The Beta cleanup thread"
date: 2009-08-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Regenweald on 2009-08-12
Hello All:
what i would appreciate in this thread is the testers of the forum donating their knowledge of the techniques of final release cleanup in the transition from Beta to Final. At the beginning of alpha cycle i went through 3 installs to get karmic on properly and the 6 mth re-install is of concern to me with the lifespan of my '/' partition.

Enough for the introduction, this is what I know, how i maintain my alphas and the reasoning behind my actions.

```

sudo aptitude update

and

sudo aptitude safe-upgrade

```
i use aptitude for it's intelligent handling of dependencies and the fact that it removes all packages installed with anything i may have installed. apt-get autoclean becomes redundant.

After updates, once aptitude reports a package/kernel obsolete, I use synaptic sorted by 'status' to remove all obsolete and residual config packages by using the 'mark for complete removal' option. (this is generally after the most current kernel has run stable for at least a week)

Deborphan-gtk is a useful tool for removal of orphaned .deb files, but again, with consistent use of aptitude even running deborphan seems 'just for kicks'. I have also installed Bleachbit, but i would be lying if i said it proved especially useful in the way in which i use my pc.

Through online scouring i have found that by deleting .gnome2 and .gnome2_private one can 'reset' all gnome settings. What i would like to know is how far one can go with deleting the hidden config folders in /Home to use as a 'hard reset'. Ideally I would perform the final updates from RC to final, delete the config folders from /Home, then log out and back in and have the new configs created.

As for the filesystem itself, from Bin to Var, what can be done in this area to refresh and cleanup a system ? Through the terminal of course.
removal of old .ko files etc. Here is where i would appreciate experienced input.

So what are your tricks of the trade ?

Many Thanks.

---

### Post by taavikko on 2009-08-13
> **Regenweald said:**
> Hello All:

After updates, once aptitude reports a package/kernel obsolete, I use synaptic sorted by 'status' to remove all obsolete and residual config packages by using the 'mark for complete removal' option. (this is generally after the most current kernel has run stable for at least a week)


Synaptic is obsolete IMHO
One can use for obsolete and locally created packages
```
aptitude search ~o
```
And then removing them by hand via aptitude purge
for prettier list use "awk"

Residual config removal
```
sudo aptitude purge `dpkg -l |grep "^rc" |awk '{print $2}'`
```


> 
Through online scouring i have found that by deleting .gnome2 and .gnome2_private one can 'reset' all gnome settings. What i would like to know is how far one can go with deleting the hidden config folders in /Home to use as a 'hard reset'. Ideally I would perform the final updates from RC to final, delete the config folders from /Home, then log out and back in and have the new configs created.


I prefer removing things in my ~/ in recovery or gdm stopped
CAUTION: only when actually needed! and the affected only.

There really isn't need to rm ~/.* until something is b0rked.

---

### Post by autocrosser on 2009-08-13
I'll be real honest & say that I really don't bother much about cleanup---sure I go thru & prune the really dead stuff out of my /home, but as for the main system...I know it will be b0rked at least once per cycle so I keep a "clean" backup to move to in case--even so I generally re-install about Alpha 4 or so every time...

Why Alpha 4? Most of the heavy crash-n-burn has already happened & generally after 4 most of the stuff is heading for freeze--sure, there are last minute breakage to work thru--but that IS why we are here--yes?  So I generally figure that any install that is on my "testing" drives (I have 2--labeled testing1 & testing2) will reinstall very regular--I have another drive that is just for backups & a 4th that had a 32 & 64 bit last release install on them--they go thru "normal" 6 month upgrades to make sure that the upgrade path looks good & as a final backstop in case I b0rk both testing installs--happened about 2 releases ago--was glad to have that stable 32 bit to fall back on!!!!

I sync all my user folders every couple of weeks & chroot into all the mains weekly--I know I can drop into any one of them at a moments notice & be up & running within 5/10 minutes......I know it sounds a bit much, but I don't loose data & baring a major system death--always have a bootable system to get into.

---

### Post by plun on 2009-08-13
More basic check commands 

Packages can be lost during a development

```
sudo apt-get install ubuntu-desktop
```

Empty the cache which can be big

```
sudo apt-get clean
```

---

### Post by Regenweald on 2009-08-18
Went away for a day trip and lost my thread. Thanks for the feedback all :) From what you have said it seems my concern over cruft in / itself is unfounded or at least not as major a concern as i initially thought.

I'll use the commands you provided to continue maintaining my alphas.

---

### Post by nhasian on 2009-08-18
if you have a lot of kernels listed in grub you can go to System->Administration->Computer Janitor to get rid of them.

sometimes when a new kernel is downloaded it doesnt get added to grub you can do it manually with 

```
sudo update-grub
```

---

### Post by slakkie on 2009-08-19
These are my functions to clean up Ubuntu a bit:

```

rmkernel() {
    sudo aptitude purge $(dpkg -l | egrep "linux-(image|headers)" | egrep -v  "$(uname -r | sed -e 's/-generic//' -e 's/-server//' -e 's/-virtual//')|linux-(image|headers)-(generic|server|virtual)" | awk '{print $2}')
    purge_pkg
}

purge_pkg() {
    sudo aptitude purge $(dpkg -l | grep '^rc' | awk '{print $2}')
    sudo aptitude clean
}

```

---

