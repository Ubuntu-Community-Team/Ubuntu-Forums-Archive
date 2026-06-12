---
title: "Installing packages from source with apt"
date: 2011-08-21
forum: Installation &amp; Upgrades
---

### Post by Z_God on 2011-08-21
Sometimes I want to install a package from a PPA which does not have all binaries for my version of Ubuntu. For example I'm running Lucid and it only includes Natty binaries. What I do then after adding the repository to my system is:
apt-get -b source <packagename>

And install the generated debs manually. I do this for all packages that have failed dependencies because the binaries depend on newer library versions. Other packages, I can often install directly from the repository.

This all works fine except that for these manually installed packages, there is always an upgrade reported from the repository even though it obviously has the exact same version number as the package I have already installed. When doing an actual 'apt-get upgrade' these packages are always skipped, because their dependencies are not resolved. They keep being listed as upgradable though.

Does anyone know what I can do against that or otherwise know what the proper way is to install packages from source?
Thank you very much in advance for your reply!

---

### Post by dino99 on 2011-08-21
why not choosing dist-upgrade instead of your tweaks, they will break a day or an other, be sure.

---

### Post by Frogs Hair on 2011-08-21
It is possible to lock your package versions from the synaptic package manager , but this will affect all packages .  Other non related packages won't update normally .

You're caught in a catch 22 , packages can be upgraded but can not upgrade because they are already installed . Broken packages won't / can't be fixed because of missing dependencies .

To avoid this you would need to find a compatible version of the PPA or learn how to create/modify the PPA to work with your version of Ubuntu.

From the synaptic package manager you can find out what the needed dependencies are by looking in package properties .  

I was wondering what if any benefits installing these packages has had ?

---

### Post by Z_God on 2011-08-22
> **dino99 said:**
> why not choosing dist-upgrade instead of your tweaks, they will break a day or an other, be sure.
Two reasons. I have experienced many issues with non-LTS versions of Ubuntu, which is why I prefer to stay with LTS versions. I also ran Natty on this system and it immediately gave me problems that I did not have with Lucid. The second reason is that I have to support quite a lot of systems of others as well and with too many different Ubuntu versions, I cannot keep up. The LTS versions of Ubuntu are *very* stable in my experience :)

> **Frogs Hair said:**
> To avoid this you would need to find a compatible version of the PPA or learn how to create/modify the PPA to work with your version of Ubuntu.
True, I should really learn how to create PPAs on Launchpad. I have always done backporting manually and never bothered to look into creating a PPA. I guess that's what I should do.

> **Frogs Hair said:**
> I was wondering what if any benefits installing these packages has had ?
I installed cdemu from this PPA: [https://launchpad.net/~cdemu/+archive/ppa](https://launchpad.net/~cdemu/+archive/ppa)

For now I have the solution to only have the deb-src line in my apt configuration. I think I should indeed just learn how to set up a PPA.

Thanks a lot for your suggestions!

---

