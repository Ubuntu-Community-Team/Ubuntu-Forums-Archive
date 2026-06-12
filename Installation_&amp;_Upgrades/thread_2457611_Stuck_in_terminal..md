---
title: "Stuck in terminal."
date: 2021-02-05
forum: Installation &amp; Upgrades
---

### Post by sliwkahax on 2021-02-05
Hello, my friend installed Lubuntu on his old laptop. He started from the terminal which suprised me, after logging in he was stuck in it. Could type commands but it didnt enter the desktop mode.
Edit: He used UNetbootin, and whilst the installation he selected Lubuntu Desktop. I used rufus to install the lubuntu iso on my flashdrive and the installer looks very diffrent. We both used the alternate 32-bit install from [https://lubuntu.net/downloads/](https://lubuntu.net/downloads/)
[ATTACH=CONFIG]287908[/ATTACH]

SOLVED: Used the wrong site, he now has a perfectly working Lubuntu, he is really happy with it ngl. :KS

---

### Post by CelticWarrior on 2021-02-05
[https://lubuntu.me/](https://lubuntu.me/) is the official website, the .net one is a cybersqatter. Do NOT download anything from there!

Now, do you really need 32-bit? Support for the last Lubuntu 32-bit ends in April (flavors have only 3 years support).

---

### Post by grahammechanical on 2021-02-05
Older hardware is often not able to run the standard Ubuntu installer with a Graphical User Interface. Some older hardware may not have a DVD drive or USB port and so cannot use the standard Ubuntu/Lubuntu ISO image. It is too large to go on a CD. So, the Alternate installer is used. It is also called the Minimum ISO image.

The basic installation is simply a command line version of Ubuntu. We can add a desktop environment to that as well as making a specific selection of applications to avoid using up too much disc space. We can do this as part of the installation process or after installation.

It seems to me that your friend neglected to select a desktop environment and a user interface. This link shows the images that your friend would have seen to install Lubuntu. I think that after the base system was installed he failed at the Software Selection screen to select either Lubuntu Desktop or Lubuntu Desktop GTK part or Lubuntu Desktop QT part. If he choose minimal install then all that was installed was the base system.

Your friend should re-install and this time select Lubuntu Desktop. Lubuntu GTK is older than Lubuntu QT.  He should choose Lubuntu desktop QT. He will not get any applications but he will get some system utilities which will allow him to update the system and install applications.

[https://www.maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/](https://www.maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/)

The alternative to a re-install is to use commands to install the desktop environment and user interface.

Regards.

---

### Post by guiverc on 2021-02-05
I can't add a lot, mostly just repeat what was said.

It's best not to ask google or a search engine for where to download something, unless you're capable of recognizing *fake* or *fan* sites from the official ones. Rather than the machine google is, you can go to ubuntu.com or specifically [https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours) which will go to the correct site for any Ubuntu flavor such as Lubuntu, it will take you to [https://lubuntu.me/](https://lubuntu.me/) as provided by @CelticWarrior

Lubuntu currently has three supported installers

- **ubiquity** - **Lubuntu 18.04 LTS**;  it reaches EOL in April-203, though the base packages of 18.04 will have a further 2 years of security updates; but it ceases being supported by Lubuntu meaning desktop apps won't be patched.  Latest and last is Lubuntu 18.04.5 LTS

- **alternate** **ISO** - **Lubuntu 18.04 LTS** ; useful for machines that have **768MB** or less of RAM, which won't run the `ubiquity` installer on top of a *live* environment as is required for the standard Lubuntu 18.04 LTS ISO. This ISO should not be used unless absolutely required due to lack of RAM, as it hasn't been updated since initially released in 2018-April.  Post install though, once you've updated your system will be good (using the GA or general kernel by default). 

- **calamares** - all releases since Lubuntu 18.10 have used this, it's a *live* system. 

Installs can also be made using the **netboot**/network-installer as @grahammechanical talked about. It's not a Lubuntu specific installer, but can be used to install Lubuntu too, but defaults to a terminal install only by default, which appears to be what you have.


Are you really using a machine that has 768MB or less of RAM?  All test boxes I used, some of which are as old as from 2003, all came with 1GB of RAM, so how old is your machine?  (and that includes pentium 4, pentium M hardware)

You haven't said if your box is **i386** (32-bit) or **amd64** (64-bit), but the *alternate* ISO was the same for both; for old boxes that have **768MB** or less of RAM (*the expectation is almost no-one has that; with 1GB or more expected, but we're aware a few users still had that*).


I would start by checking where you downloaded your ISO from, given your went to a 3rd party site and not an official Lubuntu or Ubuntu site. Historically, the site has pointed users to `cdimage.ubuntu.com` but I'd check your history & confirm that; plus check what you actually downloaded; as it's provided wrong ISOs before (it's out of Ubuntu/Lubuntu's control being 3rd party). You might be best starting with an official Lubuntu ISO.

---

### Post by ActionParsnip on 2021-02-06
Run:
```

sudo apt-get update 
sudo apt-get upgrade 
sudo apt-get install lubuntu-desktop 
sudo reboot 

```

This will give you a desktop OS. Use a wired connection to your router to make things easier. 

What is the make and model of the system?

---

### Post by sliwkahax on 2021-02-08
> **CelticWarrior said:**
> [https://lubuntu.me/](https://lubuntu.me/) is the official website, the .net one is a cybersqatter. Do NOT download anything from there!

Now, do you really need 32-bit? Support for the last Lubuntu 32-bit ends in April (flavors have only 3 years support).

Yeah we figured it out, but we already downloaded the one from lubuntu.net.
He now has a 64-bit after i found out that he can run it.

---

