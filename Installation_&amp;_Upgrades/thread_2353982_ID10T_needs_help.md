---
title: "ID10T needs help"
date: 2017-02-27
forum: Installation &amp; Upgrades
---

### Post by ergarcia1970 on 2017-02-27
OK, I&#8217;m an ID10T, seriously. I installed Ubuntu because a friend said it was free & relatively virus free. I don't want to have to get a doctorate in software engineering to update my Unix OS. So here's my problem. I get this error message:

Failed to download repository information.

so I tried this in terminal and here is what I got:

```
eric@TARDIS-OptiPlex-745:~$ sudo apt update
[sudo] password for eric: 
Get:1 [http://pubmirrors.dal.corespace.com/ubuntu](http://pubmirrors.dal.corespace.com/ubuntu) xenial InRelease [247 kB]
Get:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]     
Get:3 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease [11.5 kB]           
Get:4 [http://pubmirrors.dal.corespace.com/ubuntu](http://pubmirrors.dal.corespace.com/ubuntu) xenial-updates InRelease [102 kB]
Err:1 [http://pubmirrors.dal.corespace.com/ubuntu](http://pubmirrors.dal.corespace.com/ubuntu) xenial InRelease              
  At least one invalid signature was encountered.
Err:3 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease
  At least one invalid signature was encountered.
Err:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease
  At least one invalid signature was encountered.
Err:4 [http://pubmirrors.dal.corespace.com/ubuntu](http://pubmirrors.dal.corespace.com/ubuntu) xenial-updates InRelease
  At least one invalid signature was encountered.
Reading package lists... Done
N: Ignoring file '50unattended-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:29 and /etc/apt/sources.list.d/precise-partner.list:4
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:29 and /etc/apt/sources.list.d/precise-partner.list:4
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:29 and /etc/apt/sources.list.d/precise-partner.list:4
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:29 and /etc/apt/sources.list.d/precise-partner.list:4
W: Target DEP-11 (partner/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:29 and /etc/apt/sources.list.d/precise-partner.list:4
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:29 and /etc/apt/sources.list.d/precise-partner.list:4
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:29 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:29 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:29 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:29 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11 (partner/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:29 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:29 and /etc/apt/sources.list.d/xenial-partner.list:4
W: GPG error: [http://pubmirrors.dal.corespace.com/ubuntu](http://pubmirrors.dal.corespace.com/ubuntu) xenial InRelease: At least one invalid signature was encountered.
E: The repository 'http://pubmirrors.dal.corespace.com/ubuntu xenial InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease: At least one invalid signature was encountered.
W: GPG error: [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease: At least one invalid signature was encountered.
E: The repository 'http://security.ubuntu.com/ubuntu xenial-security InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: [http://pubmirrors.dal.corespace.com/ubuntu](http://pubmirrors.dal.corespace.com/ubuntu) xenial-updates InRelease: At least one invalid signature was encountered.
E: The repository 'http://pubmirrors.dal.corespace.com/ubuntu xenial-updates InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:29 and /etc/apt/sources.list.d/precise-partner.list:4
```

I have no freaking idea what Any of this crap means. I just want to keep my software up to date. So does anyone have any simple, easy to follow instructions for me to do that? Even if it's " You're an id10t, uninstall Ubuntu & get Windows instead".

This is the version I am running: Ubuntu 16.04 LTS. Thank you for your time, patience, and assistance.

---

### Post by oldfred on 2017-02-27
What is this ppa?
[http://pubmirrors.dal.corespace.com/ubuntu](http://pubmirrors.dal.corespace.com/ubuntu)

Often ppa to get unsupported software can cause issues, just like installing unknown software in Windows.

I would first comment that out and see if it works.

If you have installed synaptic, a gui for managing packages that shows more details than software center, it is relatively easy to turn off a ppa.

Otherwise you have to use command line/terminal to comment out or delete.

ls -l /etc/apt/sources.list.d

You can manually edit file and add # to comment out temporarily.

---

### Post by RobGoss on 2017-02-27
If you notice from the errors you're receiving it's showing which ones needs to be removed. Open up Soft & Updates, click on Other software, then uncheck the ones that are producing the errors and remove them

Then try updating your system again

---

### Post by ergarcia1970 on 2017-03-08
> **oldfred said:**
> What is this ppa?
[http://pubmirrors.dal.corespace.com/ubuntu](http://pubmirrors.dal.corespace.com/ubuntu)

Often ppa to get unsupported software can cause issues, just like installing unknown software in Windows.

I would first comment that out and see if it works.

If you have installed synaptic, a gui for managing packages that shows more details than software center, it is relatively easy to turn off a ppa.

Otherwise you have to use command line/terminal to comment out or delete.

ls -l /etc/apt/sources.list.d

You can manually edit file and add # to comment out temporarily.

Thank you but HUH?
I really don't know what you mean by "what is this ppa?" I just typed in a command on Terminal & this is what I got. I have no idea why it used that ppa or even how to change it. Sorry.
I'm sorry I only kinda, sorta know what you mean. Comment what out? And how do I do that? Please keep in mind I know next to nothing about Ubuntu. I'm a point & click kind of user. I have Synaptic but I don't really know how to use it. I don't even know what ppas to turn of or even how to do that. Sorry. Can you dumb it down for me?
Thank you.

---

### Post by ergarcia1970 on 2017-03-08
Soft & Updates?
Sorry.
I opened Software Updater & unchecked everything under Other Software tab & still got the same message.
I&#8217;d leave or post screen caps of the system let me but it won't sorry.

---

### Post by oldfred on 2017-03-08
And if not repository make sure it is a trusted site.
always check for software in this order: official repos > PPAs > .deb files > source, weird installers 

sudo add-apt-repository universe

A PPA is a way to add a repo from a trusted, cryptographically signed, location, to your ubuntu system. It is why we avoid downloading .deb files, avoid using install.sh and avoid tar.gz files to install software. With a trusted, updated PPA, managing software isn't any different than managing software from the offical repos. The only time it is complex is adding the PPA and when you do a release upgrade. The release upgrade process will remove unofficial PPAs (comment them out). 

New users should really only install from Ubuntu's own repository, at least until they understand a bit more on how Linux differs from Windows.

If you do not have synaptic, you probably cannot add it. Best to add it as one of first applications you install.
sudo apt install synaptic

Then it is easy to turn on/off ppa and other software. Software Center hides a lot to things to make it "Easier", which to me is more difficult.
See attached.

If no synaptic you have to use command line.

Show ppas and then edit one of them, if you add # that comments it out, screenshots show the three ppas I have, Boot-Repair, kmymoney & Apple iphone drivers:
ls -l /etc/apt/sources.list.d/
sudo nano /etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-xenial.list
> deb [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) xenial main
# deb-src [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) xenial main




      
 ls -l /etc/apt/sources.list.d/

---

### Post by ergarcia1970 on 2017-04-19
I want to thank everyone who replied. What I was hoping for was some simple, easy instructions on how to fix the problem. To be honest I have no idea what most of the responses mean or even what to do next. I'm one step away from wiping the HD and going to MS Windows. Does anyone know where I can find some simple easy instructions to update Ubuntu. Or maybe someone who can help me in Houston?
Thank you.

---

### Post by oldfred on 2017-04-19
You must have installed that ppa from some random possibly unreliable site.

You just need to then uninstall the ppa.
Often easier then to just comment it out or uncheck in Software & Updates.
Just uncheck all ppa. See screenshot for my PPA.

---

