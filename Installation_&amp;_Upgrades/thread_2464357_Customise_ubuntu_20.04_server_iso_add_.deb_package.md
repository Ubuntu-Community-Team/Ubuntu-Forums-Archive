---
title: "Customise ubuntu 20.04 server iso add .deb packages to iso"
date: 2021-06-30
forum: Installation &amp; Upgrades
---

### Post by raossabe on 2021-06-30
I'm attempting to add .deb packages to the ubuntu-server 20.04.2 ISO file for an offline installation.

I have tried the instructions at the following URL:s but to no success.

[https://www.neteye-blog.com/2018/06/custom-ubuntu-iso-image-for-unattended-and-offline-installation/](https://www.neteye-blog.com/2018/06/custom-ubuntu-iso-image-for-unattended-and-offline-installation/)
[https://help.ubuntu.com/community/InstallCDCustomization#Modify%20pool%20structure%20to%20include%20more%20packages](https://help.ubuntu.com/community/InstallCDCustomization#Modify%20pool%20structure%20to%20include%20more%20packages)

Are there any better/newer documentation that describes how to add .deb packages to an iso file?

---

### Post by tea for one on 2021-06-30
You may wish to explore Cubic ([COLOR="#0000FF"]C[/COLOR]ustom [COLOR="#0000FF"]Ub[/COLOR]untu [COLOR="#0000FF"]I[/COLOR]so [COLOR="#0000FF"]C[/COLOR]reator)

[https://launchpad.net/cubic](https://launchpad.net/cubic)

---

### Post by MAFoElffen on 2021-06-30
A tip from experience on doing that and creating my own distro's in years past.

What helped me and what I migrated to for doing installs in the dark:
 - I gave up on doing the work on a live machine. It added a lot to my day-to-day machine that added a lot of "bloat". I ended up creating a VM(s) to do the work on.
 - For those Images, that were meant for "me", to install without a network connection, I added a pointer in the source.list to a local repo.
 - Once I created those install images, I added them to an Easy2Boot drive.
 - On that Drive, I created a local repo, which for all my images, there was only one local repo to keep updated... That saved my soooo much work and upkeep.

That way, I could install a myriad of flavors locally, without an active internet connection, and have "current" repo files... Without having to update those images just because of repo updates.

Just a thought...

---

### Post by raossabe on 2021-07-01
> [COLOR=#000000]You may wish to explore Cubic ([/COLOR][COLOR=#0000FF]C[/COLOR][COLOR=#000000]ustom [/COLOR][COLOR=#0000FF]Ub[/COLOR][COLOR=#000000]untu [/COLOR][COLOR=#0000FF]I[/COLOR][COLOR=#000000]so [/COLOR][COLOR=#0000FF]C[/COLOR][COLOR=#000000]reator)[/COLOR]

[https://launchpad.net/cubic](https://launchpad.net/cubic)


My end goal is to be able to use the iso as a repository. I've looked into cubic and it doesn't seem to have the ability to add packages to the iso-pool it just has the ability to install packages to the environment that is being installed.

---

### Post by MAFoElffen on 2021-07-01
> **raossabe said:**
> My end goal is to be able to use the iso as a repository...
The full repository for a release or your own collection of favored packages?

Like I said, I do on an USB drive... The reason why? Because a release repo is between 280GB to 300GB. I use apt-mirror for that...

Then if I want something lighter, I take the packages I want (a subset) and add them to a compresed repo package file with apt-scanpackages, piped through gzip into Packages.gz... That utility will take any deb you put into a "directory", and put it into a package file.

Either way, you can point a line in the sources.list to the local repo as trusted (because it's local) with a file pointer.

At least that's the "summarized version." I can go into details if you are interested.

If you look at the old Repo to CDROM page in the Ubuntu Wiki, I think it still says for 10.04 that it took over 39 disks. But that was back when the repo was a lot smaller. That's why I went to USB drives. LOL

---

