---
title: "Issue upgrading from EOL release 17.04"
date: 2018-08-13
forum: Installation &amp; Upgrades
---

### Post by fredericr on 2018-08-13
I am trying to upgrade from the unsupported 17.04 release.
I have diligently (I think) followed these instructions:
[https://help.ubuntu.com/community/EOLUpgrades/](https://help.ubuntu.com/community/EOLUpgrades/)

My sources.list looks as follows:
```
## EOL upgrade sources.list
# Required
deb http://old-releases.ubuntu.com/ubuntu/ zesty main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ zesty-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ zesty-security main restricted universe multiverse

# Optional
#deb http://old-releases.ubuntu.com/ubuntu/ zesty-backports main restricted universe multiverse
```

And every step completed successfully.  But 'sudo do-release-upgrade' still does not work:
```
sudo do-release-upgrade
Checking for a new Ubuntu release
Your Ubuntu release is not supported anymore.
For upgrade information, please visit:
http://www.ubuntu.com/releaseendoflife
Get:1 Upgrade tool signature [819 B]                                                                 
Get:2 Upgrade tool [1,258 kB]                                                                        
Fetched 1,258 kB in 0s (0 B/s)                                                                       
authenticate 'bionic.tar.gz' against 'bionic.tar.gz.gpg' 
extracting 'bionic.tar.gz'
Reading cache
Checking package manager
Cannot upgrade 
An upgrade from 'zesty' to 'bionic' is not supported with this tool. 
```

Any clue what else I should be looking at?

Thanks!

---

### Post by DuckHook on 2018-08-13
Welcome to the forums, fredericr.

Please do not use unusual formatting because it is difficult to read, especially on small screens such as mobile devices. It is best to post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar. I have edited your post to clean this up.

With respect to your problem, you got most of it right. Thank you for trying your researched solution before requesting help. Unfortunately, Ubuntu has made a minor change to their directory structure which has gummed up the instructions in your linked solution. The new directory is just different enough to trip everyone up. It is:```
deb http://old-releases.ubuntu.com/ubuntu/dists/ &#8230;
```Note the need for the additional subdirectory. The remainder of each line is accurate. So change all of your lines to include the /dists/ subdirectory and then try:```
sudo apt update && sudo apt full-upgrade
```&#8230;prior to:```
sudo do-release-upgrade
```

I don't know why the devs decided to change a directory structure that was perfectly fine before, but hopefully, this minor tweak is all that is needed for you.

---

### Post by fredericr on 2018-08-13
Thanks for your quick reply, DuckHook!

I have added the /dists/ directory, though now, 'sudo apt update' trips a bit further:

```

Ign:5 http://old-releases.ubuntu.com/ubuntu/dists zesty-updates InRelease
Ign:6 http://old-releases.ubuntu.com/ubuntu/dists zesty-security InRelease
Err:8 http://old-releases.ubuntu.com/ubuntu/dists zesty Release
  404  Not Found [IP: 91.189.88.41 80]
Err:9 http://old-releases.ubuntu.com/ubuntu/dists zesty-updates Release
  404  Not Found [IP: 91.189.88.41 80]
Err:10 http://old-releases.ubuntu.com/ubuntu/dists zesty-security Release
  404  Not Found [IP: 91.189.88.41 80]
Reading package lists... Done
E: The repository 'http://old-releases.ubuntu.com/ubuntu/dists zesty Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://old-releases.ubuntu.com/ubuntu/dists zesty-updates Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://old-releases.ubuntu.com/ubuntu/dists zesty-security Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

Do you know what the issue could be?   Thanks again.

[edit: the new error seems related to [https://ubuntuforums.org/showthread.php?t=2382832](https://ubuntuforums.org/showthread.php?t=2382832) so I'll also take a look at this one]

---

### Post by DuckHook on 2018-08-13
You are missing the trailing slash after:```
&#8230;dists/
```&#8230;please look at my prior example carefully. Yes, it is a rather persnickety nit, but exact syntax is crucial to Linux.

---

### Post by Impavidus on 2018-08-14
Are you sure you want to upgrade? 17.10 is dead too, so you must use a double upgrade or the non-standard jump from 17.04 to 18.04. A fresh install will probably work better.

---

### Post by fredericr on 2018-08-14
Thanks DuckHook.  I do have the trailing slash though:

```

deb http://old-releases.ubuntu.com/ubuntu/dists/ zesty main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/dists/ zesty-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/dists/ zesty-security main restricted universe multiverse


```

But for some weird reason, I still get the error I mentioned above, which shows no mention of that slash :-/
Is it possible that it is being escaped somehow?

---

### Post by fredericr on 2018-08-14
Thanks for your comment Impavidus.  I was thinking of going to 18.04, is that not recommended?

---

### Post by Impavidus on 2018-08-14
18.04 was released after 17.04 reached end-of-life, so obviously a direct upgrade from 17.04 to 18.04 was never tested and the tools for a smooth upgrade were never made. An upgrade directly from 17.04 to 18.04 may work, but complications are more likely than in case of a supported upgrade – and there are many people who recommend even against supported upgrades (not me, BTW). Don't waste too much time troubleshooting this issue. More issues may come. A fresh install is faster.

---

### Post by DuckHook on 2018-08-14
> **Impavidus said:**
> …A fresh install will probably work better.

> **Impavidus said:**
> …Don't waste too much time troubleshooting this issue. More issues may come. A fresh install is faster.

&#8593;++

---

### Post by fredericr on 2018-08-14
Thank you both for your help.  I will try a new install.

---

