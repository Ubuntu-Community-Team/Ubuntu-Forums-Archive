---
title: "Re-Installing Ubuntu Want to keep Packages"
date: 2007-06-26
forum: Installation &amp; Upgrades
---

### Post by lord bacon on 2007-06-26
As title says, i want to reinstall Feisty as many programs are broken, but i dont want to have to downlaod the programs i have already installed. I also dont want to have all these programs on the new install. so what i want to know is how to back up all my current packages, tehn once i reinstall i can select which of the packages to reinstall. is this possible, ad if yes how.

thanks lord bacon

---

### Post by IanW on 2007-06-26
The .deb file for every package you've  ever installed or updated is held in /var/cache/apt/archives.
Burn the ones you want to keep onto a cd or dvd and then use gdebi to reinstall them once you've reinstalled Ubuntu.

---

### Post by mneisen on 2007-06-26
Hi everyone!

> **IanW said:**
> The .deb file for every package you've  ever installed or updated is held in /var/cache/apt/archives.
Burn the ones you want to keep onto a cd or dvd and then use gdebi to reinstall them once you've reinstalled Ubuntu.

I think this is not quite the right way to do it. If lord bacon has even once done a
```

sudo apt-get clean

```
to save some space then the *.deb-packages in /var/cache/apt/archives do not resemble the installed collection of applications anymore. To burn the *.deb-files to CD-ROM/DVD or copy to an external HD is a good way to save some bandwidth after re-install, though, so I recommend that, too.

> **lord bacon said:**
> As title says, i want to reinstall Feisty as many programs are broken, but i dont want to have to downlaod the programs i have already installed. I also dont want to have all these programs on the new install. so what i want to know is how to back up all my current packages, tehn once i reinstall i can select which of the packages to reinstall. is this possible, ad if yes how.

I would recommend the following:
```
sudo dpkg -l | grep ^ii | awk '{print $2}' > paket-list
```

This gives you a list of all installed packages on your system. You may edit this file to remove the packages you do not want to keep after re-installaing Feisty.

After re-installing, you may want to copy the *.deb-files you saved to CD/DVD/ex-HD back to /var/cache/apt/archives, set the right permissions (I guess 700 and owner root:root) and run
```
for paket in $(cat paket-list); do
  echo $paket;
  sudo apt-get install $paket;
done

```

You might also want to have a look at [my little blog entry]("http://node-0.mneisen.org/2007/04/17/erzeugen-einer-liste-installierter-pakete-auf-einem-kubuntu-system/") - although it is in German (sorry!),

Hope that helps.

Kind regards
Martin Eisenhardt

---

