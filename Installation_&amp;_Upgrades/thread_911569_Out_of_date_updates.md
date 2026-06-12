---
title: "Out of date updates"
date: 2008-09-05
forum: Installation &amp; Upgrades
---

### Post by alsamman on 2008-09-05
Hey everyone,

Every time I boot the computer, I always get this error icon on my panel that says: "The update information is outdated. This may be cause by network problems. Please update manually by clicking on this icon and then selecting 'Check'. When I do click the icon and click Check, I get this error:
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://repository.akirad.net/dists/akirad-hardy/main/binary-i386/Packages.gz](http://repository.akirad.net/dists/akirad-hardy/main/binary-i386/Packages.gz)  500 Internal Server Error

Some index files failed to download, they have been ignored, or old ones used instead.

How can I get rid of this error?

Thanks

---

### Post by iaculallad on 2008-09-05
On your terminal, try issuing the command below:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by alsamman on 2008-09-05
> **iaculallad said:**
> On your terminal, try issuing the command below:

```
sudo apt-get update && sudo apt-get upgrade
```

I tried, still get this error,
W: Failed to fetch [http://repository.akirad.net/dists/akirad-hardy/main/binary-i386/Packages.gz](http://repository.akirad.net/dists/akirad-hardy/main/binary-i386/Packages.gz)  500 Internal Server Error

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by iaculallad on 2008-09-05
Ok. Try changing your download Server. System->Administration->Software Sources, under "Ubuntu Software"tab. Try changing the "Download From:" to point to "Main Server". Click on Close and select the Reload button on the next window that pops out. When finished, drop to your terminal and re-issue:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by alsamman on 2008-09-05
> **iaculallad said:**
> Ok. Try changing your download Server. System->Administration->Software Sources, under "Ubuntu Software"tab. Try changing the "Download From:" to point to "Main Server". Click on Close and select the Reload button on the next window that pops out. When finished, drop to your terminal and re-issue:

```
sudo apt-get update && sudo apt-get upgrade
```

still same problem:( Thanks for the effort though

---

### Post by oldos2er on 2008-09-05
Can you please post the output from "cat /etc/apt/sources.list"?

---

### Post by kostkon on 2008-09-05
> **alsamman said:**
> I tried, still get this error,
W: Failed to fetch [http://repository.akirad.net/dists/akirad-hardy/main/binary-i386/Packages.gz](http://repository.akirad.net/dists/akirad-hardy/main/binary-i386/Packages.gz)  500 Internal Server Error

E: Some index files failed to download, they have been ignored, or old ones used instead.
You are using the repo of *Cinelerra*, right? Try disabling it from *System -> Administration -> Software Sources* in the *Third-Party Software* tab. Press *Close* and then *Reload*.

---

### Post by alsamman on 2008-09-05
> **kostkon said:**
> You are using the repo of *Cinelerra*, right? Try disabling it from *System -> Administration -> Software Sources* in the *Third-Party Software* tab. Press *Close* and then *Reload*.

Thanks, that worked.
However, won't I need to have it enabled for Cinelerra to update?

---

### Post by iaculallad on 2008-09-05
> **alsamman said:**
> Thanks, that worked.
However, won't I need to have it enabled for Cinelerra to update?

You could try renewing your Akirad repository by doing the commands below using your terminal:

For Gutsy:
```
sudo wget http://akirad.cinelerra.org/dists/gutsy.list -O /etc/apt/sources.list.d/akirad.list
wget -q http://akirad.cinelerra.org/dists/akirad.key -O- | sudo apt-key add - && sudo apt-get update

```

For Hardy:
```
sudo wget http://akirad.cinelerra.org/dists/hardy.list -O /etc/apt/sources.list.d/akirad.list
wget -q http://akirad.cinelerra.org/dists/akirad.key -O- | sudo apt-key add - && sudo apt-get update

```

---

