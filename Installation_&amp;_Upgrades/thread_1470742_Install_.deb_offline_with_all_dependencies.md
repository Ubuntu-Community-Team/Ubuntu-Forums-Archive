---
title: "Install .deb offline with all dependencies"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by finito on 2010-05-03
I was able to do this before but, I can't remember where I found the link.

I think is was a script or something. It would get all the files that the .Deb will need and make an installer.

Please help.

P.S. I have Ubuntu 64-bit the PC that need the install is a 32-bit both are 10.04.

Thanks

---

### Post by amsterdamharu on 2010-05-03
If the program you want to install is in synaptic you can choose download script. You select the software you want to install and then under file -> "generate package download script"

If you installed the programs on another computer chances are that all the deb files are still in /var/cache/apt/archives
you can copy those files to /var/cache/apt/archives of the "offline" computer and use synaptic to install the software. It will not download anything that's already in cache.
One problem with this is that you need to refresh the list in synaptic to the latest package versions (as I assume you did on the machine where you got the debs from) otherwise the "offline" machine might try to download older versions. You can do this by pressing the reload button in synaptic but the computer needs to be online to download package information.

If you put the deb files in /var/cache/apt/archives and try to install another deb by clicking on it, the installer will only try to download deb files that are not in the archives. This way might be the easiest.

To copy the deb files you can press alt + F2 and type "sudo nautilus" you now run nautilus as root and copy the deb files somewhere. Select them and right click to change access rights for others so you will be able to burn them on a cd/copy to usb as a normal user. To copy the files **to** the "offline" computer you can run nautilus as root again because a normal user is not able to copy to /var/cache/apt/archives.

---

