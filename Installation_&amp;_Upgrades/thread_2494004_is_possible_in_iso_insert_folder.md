---
title: "is possible in iso insert folder?"
date: 2024-01-02
forum: Installation &amp; Upgrades
---

### Post by faustf2 on 2024-01-02
Hello everyone, is it possible to include a folder with a series of  scripts and files inside an ISO file, so that upon the first boot, it  runs the installation and customization after logging in? Thank you.

---

### Post by TheFu on 2024-01-02
Canonical has been screwing with this basically, every release.  

cloud-init is the most recent method supported.  [https://discourse.ubuntu.com/t/automated-server-installation/16612](https://discourse.ubuntu.com/t/automated-server-installation/16612)
This is normally handled using an NFS, HTTP or tftp server that are discovered during installation time or with a network installer.   I don't know the exact command.  The config file has changed over time to be less clear so that lots of complex stuff can be handled. 

[https://cloudinit.readthedocs.io/en/latest/tutorial/index.html](https://cloudinit.readthedocs.io/en/latest/tutorial/index.html)
[https://cloudinit.readthedocs.io/en/latest/reference/examples.html](https://cloudinit.readthedocs.io/en/latest/reference/examples.html)
[https://www.pugetsystems.com/labs/hpc/How-To-Make-Ubuntu-Autoinstall-ISO-with-Cloud-init-2213/](https://www.pugetsystems.com/labs/hpc/How-To-Make-Ubuntu-Autoinstall-ISO-with-Cloud-init-2213/)

You don't have to re-master the ISO. Support for this is built-into existing ISOs.

There's also an OEM model.  [https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)   and [https://askubuntu.com/questions/36671/how-do-i-pre-install-ubuntu-for-someone-oem-install](https://askubuntu.com/questions/36671/how-do-i-pre-install-ubuntu-for-someone-oem-install)

---

### Post by faustf2 on 2024-01-02
but i not  want  use cloud  or network in general i want inject  inside of  iso and  after instal at  first login  run my script ,  thanks  for rply

---

### Post by guiverc on 2024-01-02
The ISOs themselves are a *read only **squashfs* so they cannot be changed, and that is intentional.

You can modify them though; expand the ISO, change it then re-master a new ISO.

[https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)

You gave no clear Ubuntu details though, as Ubuntu has used multiple installers (*di & ubiquity use one format, ubuntu-desktop-installer & subiquity do it a little differently*) so follow the correct instructions for whichever Ubuntu product/release you're trying to use.

---

### Post by MAFoElffen on 2024-01-02
What guiverc described previously is how it is done 'now' and how it is evolving even more, as each installer comes out, with using cloud-init. What he linked to is the older installer ubuiquity, which is not used for Ubuntu any more. Noble, in April, is Subiquity.

You can do autoinstall.yaml and with the late commands, copy in the script folder with your scripts... or just run the scripts straight from the late commands. You can create a cloud-init ISO to plug in alongside your installer LiveUSB. That works without having to having to point to a network link for it. Or you can add a directory for your cloud-init inside the ISO for the installer LiveUSB

I am just finishing up on getting a patch pushed through to fix getting the late commands back working for the autoinstaller: 
[https://bugs.launchpad.net/subiquity/+bug/2040654](https://bugs.launchpad.net/subiquity/+bug/2040654)
[https://ubuntuforums.org/showthread.php?t=2491776](https://ubuntuforums.org/showthread.php?t=2491776)

After 22.04, Ubuntu uses a different installer. The system-image is inside of the Snap Package 'ubuntu-desktop-installer'. The system image is inside that Snap as an archive, which then gets extracted to the Live Env's /tmp directory, then rsync'ed to the intsall's filesystem framework... So it's now more buried inside the ISO image > inside that Snap Package > inside another archive file. So to do that, you would have to extract the ISO, then extract the Snap, then extract that system archive file... to add that, then change the installer script to run your scripts from inside the chroot... Then prevent the installer from doing a git refresh so it doesn't get replaced. 

Loads of room for that to fail outright from many angles. Just because it is remotely possible does not make that a good idea at all.
My recommends, learn curtin, and cloud-init. That is the direction that it now works.

---

### Post by faustf2 on 2024-01-02
Wow, more complicated than this...noo? In Windows, you put everything inside a  folder, remaster it, and you're ready to go. Obviously, there isn't a  tool that you give the ISO to and it does everything for you, right?"

---

### Post by jeremy31 on 2024-01-02
You could use cubic to make a custom ISO

---

### Post by Jaxilian on 2024-03-04
I used this script as base for making my autoinstall images, but expanded it to support two user-data files. I am not so good programmer so I used AI to fix it for me.
[https://raw.githubusercontent.com/covertsh/ubuntu-autoinstall-generator/main/ubuntu-autoinstall-generator.sh](https://raw.githubusercontent.com/covertsh/ubuntu-autoinstall-generator/main/ubuntu-autoinstall-generator.sh)

---

