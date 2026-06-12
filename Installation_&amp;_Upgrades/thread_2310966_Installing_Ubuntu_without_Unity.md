---
title: "Installing Ubuntu without Unity?"
date: 2016-01-23
forum: Installation &amp; Upgrades
---

### Post by hanix2 on 2016-01-23
Hi there, would it be possible to install Ubuntu without Unity and instead another interface? Let's say one wouldn't want to use Xubuntu to have a Ubuntu XFCE installation, would it be possible to skip unity install altogether and install another user interface entirely in a way similar to how Debian handles it? Is the Ubuntu installer really that strict, surely Canonical wouldn't think to limit us to just Unity. It seems rather complicated why I would need such a thing, but some companies require vanilla Ubuntu(flavors/spin-offs are explicitly not allowed) for warranty installations but the desktop environment differs between computers. Also Unity must be skipped entirely during installation, so installing a desktop environment post-install then using apt-get remove wouldn't be allowed. Thanks in advanced ;).

---

### Post by Petro Dawg on 2016-01-23
Just a thought, and I never tested this.. but you might be able to use "Ubuntu Server" and then add a GUI after installation.  From what I understand, Ubuntu Server is just a stripped down version of vanilla Ubuntu without a GUI and some extra server tools installed by default.

---

### Post by hanix2 on 2016-01-23
Never actually thought about that. Seems similar to Arch Linux, I'll have to look into it!

---

### Post by QIII on 2016-01-23
A minimal install would be even better if you are not interested in having the server components.

You can just download the minimum iso and build from there as you wish.

---

### Post by grahammechanical on 2016-01-23
I think we are misunderstanding something here.

Ubuntu is the Linux distribution. What we get with Ubuntu is what the Ubuntu developers decide Ubuntu should be like. Ubuntu is not meant to be a multi-UI distribution. But Ubuntu is FOSS and if some developers want to take Ubuntu and build another UI on to it, then they are free to do so. And that is why we have several Ubuntu family members.

Ubuntu; Xubuntu; Kubuntu; Lubuntu; Ubuntu Gnome; Ubuntu Mate; Ubuntu Studio; Mythbuntu; Edubuntu. We have choice. And yes the Ubuntu installer is really that strict. The purpose of the Ubuntu installer is to install Ubuntu + Unity. The purpose of the Xubuntu installer is to install Xubuntu = Ubuntu + Xfce. And so on. It is actually the same installer called Ubiquity but tailored for each family member. Get the picture?

Now, if we want we can do it the hard way. We have the Ubuntu Minimal CD. This simply installs Linux and then we download from the internet whatever else we need. This type of installation is also called a Network Install. We get to choose the UI and so on.

> To install, boot your computer from the the mini iso and select  "Install" at the prompt.  You can then follow the instructions from the  text-based installer.  On the software selection screen, you can select  from a number of collections of software such as different desktop  environments (kde, xfce, etc), a multitude of different servers,  multimedia creation tools, media center (mythbuntu), etc.  You can also  select "Manual package selection" which will take you to aptitude.  You  may also select nothing and just continue to finish the installation.   If you selected nothing, upon reboot you will arrive at a cli prompt;  from here you can fully customize your new system.
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Ubuntu server will install by default server related applications which are not part of the Ubuntu desktop install. With Ubuntu server we will not get by default desktop related applications. They will also have to be installed by the user. More is needed than simply installing a desktop UI.

> so installing a desktop environment post-install then using apt-get remove wouldn't be allowed.

If the employer's policy is to provide computers with Ubuntu + Unity installed then a Multi-UI ISO image would not be part of that employer's provisioning requirements. 

Regards.

---

### Post by hanix2 on 2016-01-23
> **grahammechanical said:**
> I think we are misunderstanding something here.

Ubuntu is the Linux distribution. What we get with Ubuntu is what the Ubuntu developers decide Ubuntu should be like. Ubuntu is not meant to be a multi-UI distribution. But Ubuntu is FOSS and if some developers want to take Ubuntu and build another UI on to it, then they are free to do so. And that is why we have several Ubuntu family members.

Ubuntu; Xubuntu; Kubuntu; Lubuntu; Ubuntu Gnome; Ubuntu Mate; Ubuntu Studio; Mythbuntu; Edubuntu. We have choice. And yes the Ubuntu installer is really that strict. The purpose of the Ubuntu installer is to install Ubuntu + Unity. The purpose of the Xubuntu installer is to install Xubuntu = Ubuntu + Xfce. And so on. It is actually the same installer called Ubiquity but tailored for each family member. Get the picture?

Now, if we want we can do it the hard way. We have the Ubuntu Minimal CD. This simply installs Linux and then we download from the internet whatever else we need. This type of installation is also called a Network Install. We get to choose the UI and so on.


[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Ubuntu server will install by default server related applications which are not part of the Ubuntu desktop install. With Ubuntu server we will not get by default desktop related applications. They will also have to be installed by the user. More is needed than simply installing a desktop UI.

Regards.

Awesome, thank you for the answers everyone!

---

### Post by Petro Dawg on 2016-01-23
I completely forgot about the Minimal Install or else I would have suggested it, thanks QIII and grahammechanical.  +1 for that option.

---

### Post by sudodus on 2016-01-23
> **Petro Dawg said:**
> Just a thought, and I never tested this.. but you might be able to use "Ubuntu Server" and then add a GUI after installation.  From what I understand, Ubuntu Server is just a stripped down version of vanilla Ubuntu without a GUI and some extra server tools installed by default.

This is actually a good idea, which is used by me and several other people. If you do not install any server package, Ubuntu Server will give you a simple text-screen system, which is almost the same as what you get via the Ubuntu mini.iso. It is an advantage if you want to install from the iso file more than once, because you download several packages only once (while mini.iso must download them every time you install). In both cases you can install the desktop packages after rebooting into the simple text-screen system, for example using the meta-package 'xubuntu-desktop'.

```
sudo apt-get install xubuntu-desktop
```

But you can also ***make your own custom desktop environment and set of application programs*** by installing each program package individually.

-o-

There is another particular advantage with Ubuntu Server: It can install a system in UEFI mode (while mini.iso cannot do it).

---

