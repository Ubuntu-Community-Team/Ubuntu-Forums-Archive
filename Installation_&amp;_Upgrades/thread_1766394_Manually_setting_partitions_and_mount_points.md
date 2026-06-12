---
title: "Manually setting partitions and mount points"
date: 2011-05-24
forum: Installation &amp; Upgrades
---

### Post by brad1138 on 2011-05-24
I have figured out manually setting the swap partition and setting "/" as the mount point for the primary partition during install. 

If during install, I want to create another partition to keep the OS separate from installed programs and such, to be able to do a clean install every 6 months and not loose everything (or anything) I have done prior.

How do I do that?

Thanks,
Brad

---

### Post by Mr. Shannon on 2011-05-24
In Linux, programs are mixed in with the OS, so I don't think that you can reinstall the OS without losing your programs.  However, if you make a separate partition and have it mounted as /home then you can reinstall without losing your data and I think your program settings.

A solution to getting all your packages back on the next installation is to make a text file with the names of all the packages you wan't to have reinstalled (all on one line with spaces in between).  Like if you only wanted gimp, chromium-browser, and gvim then you would make a text file that contained
```
gimp chromium-browser gvim
```
Then when you wanted to reinstall the packages you would type in a terminal
```
sudo apt-get install `cat /path/to/package/list/file`
```

Note: Packages come and go from the repositories so you may have to edit your package list file when the above code reports that a package does not exist.

Also you can perform an upgrade from one version of Ubuntu to another.  I think that will keep your software, but I don't think that it is a true reinstall.

---

### Post by brad1138 on 2011-05-24
> **Mr. Shannon said:**
> In Linux, programs are mixed in with the OS, so I don't think that you can reinstall the OS without losing your programs.  However, if you make a separate partition and have it mounted as /home then you can reinstall without losing your data and I think your program settings.

A solution to getting all your packages back on the next installation is to make a text file with the names of all the packages you wan't to have reinstalled (all on one line with spaces in between).  Like if you only wanted gimp, chromium-browser, and gvim then you would make a text file that contained
```
gimp chromium-browser gvim
```
Then when you wanted to reinstall the packages you would type in a terminal
```
sudo apt-get install `cat /path/to/package/list/file`
```

Note: Packages come and go from the repositories so you may have to edit your package list file when the above code reports that a package does not exist.

Also you can perform an upgrade from one version of Ubuntu to another.  I think that will keep your software, but I don't think that it is a true reinstall.

Thanks, the problem with upgrading is it commonly doesn't work (I have had that conversation in this forum many times). I usually try the upgrade, but if it doesn't work (more often than not) I have to do a full re-install.

Thanks for the other advise. I was fairly sure I have seen others say they have done what I described, but maybe not.

Also, I use 11.04 w/Gnome. I am installing 10.04 LTS (Gnome) on the rest of the families computers.

Brad

---

