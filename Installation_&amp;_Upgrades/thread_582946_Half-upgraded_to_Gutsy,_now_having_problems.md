---
title: "Half-upgraded to Gutsy, now having problems"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Snowcat on 2007-10-20
Hi,
I know that there are a lot of threads regarding problems upgrading to Gutsy, but I haven't seen one that  exactly matches mine.

I used the normal Update Manager and everything worked fine up to about two thirds of the way. Than an error in the package "cupsys" caused the upgrade to stop. After that, I reopened Update Manager, which showed one package left to be installed (cupsys) and then proceeded to install it without a problem.

I restarted my computer, only to have X hang on a blank screen. I logged into recovery mode and reconfigured xserver-xorg, and now X started into what appears to be a Gutsy desktop. **However**, I can no longer see my battery status or my other (fat32) partition, and I'm pretty sure that there are a whole bunch of other problems, since my upgrade wasn't finished when the error occured.

I tried changing repos, running "dpkg --reconfigure -a" and any other dpkg or apt-get command I could think of, but nothing makes Update Manager see that there is more that needs to be installed.

Am I screwed, or is there any way to make my computer understand and resume the upgrade?

Thanks for any replies.

p.s. Just to avoid confusion - my internet (wireless) is working just fine.

---

### Post by Snowcat on 2007-10-20
Update: I managed to fix the partition thing (apparently partition names have changed, yet again).

So far it is only the battery status that is giving me trouble, but I see that others have reported this as well (though I don't have a Dell laptop, but an LG LM40).

Maybe I was too quick to jump to conclusions (and maybe my upgrade is fine after all), but any thoughts about the battery would still be much appreciated.

---

### Post by heldal on 2007-10-21
Dependencies may change between releases. Thus, some packages are temporarily removed in the the process in order to handle changed dependencies. These may not be marked in any way in the package-system and there's nothing to keep track of them anymore after the upgrade-process has aborted.  The complete list of packages to remove, install and upgrade is however logged as part of the analysis done at the beginning of the upgrade. You might want to extract the lists of packages to install and upgrade from /var/log/dist-upgrade/main.log into a file and then try to process each package through apt-get:
```
for pkg in `cat <your-file-with-packagelist>`
do
apt-get install $pkg
done
```
"apt-get install" will only install missing packages (or upgrade of there is a new version). Packages that already are installed will not be touched.

I had a similar problem, and in my case the above resulted in about 20 additional packages being installed.

---

