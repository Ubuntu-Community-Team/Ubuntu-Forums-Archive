---
title: "Wine for AMD64 system"
date: 2011-09-07
forum: Installation &amp; Upgrades
---

### Post by hakunamatata_007 on 2011-09-07
Hi All,
Recently I have installed the [Ubuntu 10.04 LTS]("https://help.ubuntu.com/10.04/index.html") for 64 bit on my system. Now I am installing the necessary softwares as per my requirements. While installing softwares, I found that the double click on .exe file is not working. Moreover, it shows the error **"An error occurred while loading the archive"**.
I googled the term and found ([http://ubuntuforums.org/showthread.php?t=1204895](http://ubuntuforums.org/showthread.php?t=1204895)) that it requires Wine software to run .exe file on ubuntu. 
I tried to install the wine software from Ubuntu Software Center but I found that wine is not available for amd64 computer.

Please suggest me how to proceed further.

Thanks and Regards,
Hirdesh

---

### Post by catlover2 on 2011-09-07
What does


```
sudo apt-get install wine
```
output?

---

### Post by oldos2er on 2011-09-07
> **hakunamatata_007 said:**
> I tried to install the wine software from Ubuntu Software Center but I found that wine is not available for amd64 computer.


Sure it is, 
[http://packages.ubuntu.com/search?keywords=wine&searchon=names&suite=lucid&section=all](http://packages.ubuntu.com/search?keywords=wine&searchon=names&suite=lucid&section=all)

Check Synaptic, Settings, Repositories, and make sure all repositories are enabled.

---

### Post by Mark Phelps on 2011-09-08
Also, understand that SOME Windows .exe files are not executables, but rather, self-extracting archives.  If you're trying to run such files, they may not work even after installing Wine.

Also, BEFORE you install Wine, do yourself a favor and go to the WineHQ website and look through the Application Compatibility Database tool they have.  Look up the individual Windows apps and versions you want to use.  You will be able to tell by their ratings (Garbage -- to -- Platinum) how well they work with Wine.

IF your apps are rated Garbage, or not listed, then installing Wine is going to be a waste of your time.

---

