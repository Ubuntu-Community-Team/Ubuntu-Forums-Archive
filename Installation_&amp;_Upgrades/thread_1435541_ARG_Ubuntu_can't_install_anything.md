---
title: "ARG: Ubuntu can't install anything"
date: 2010-03-21
forum: Installation &amp; Upgrades
---

### Post by Tom_ZeCat on 2010-03-21
I'm on an old clunker Pentium III maxed out at 256 MB of RAM.  Still, Ubuntu 7.10 runs on at, as does Amarok 1.4.  

I wanted to install OpenOffice Writer and OpenOffice Spreadsheet on it.  I go to: 

> Applications ===> Add/Remove

And I choose OpenOffice Writer and Spreadsheet from the menu and click to install.  I first get a warning: 

> Can't be authenticated

And some other text to the effect that this program is unknown and to be cautious.  Well, there's no program more known to be safe than OpenOffice.  So I go ahead and approve the install.

After it searches for a while, I get: 

> W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_2.3.0-1ubuntu5.5_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_2.3.0-1ubuntu5.5_i386.deb)
  404 Not Found [IP: 91.189.88.37 80]


And some other "failed to fetch" problems.  Then I get:

> Application installation failed

I get the same problem with absolutely any software I choose from the list.  I also tried in the Synaptec Package Manager and had the same problems.  I checked to make sure I was connected to the Internet okay.  I am.  I'm on this forum on the same PC.  

I don't get why all programs are failing to install.  Any insight is appreciated.

---

### Post by sanderd17 on 2010-03-21
This is something weird. Maybe there are some problems with the server. Can you select another server in your software sources? I've had some problems before with the belgian server but it were only speed issues and some timeout errors.

Can you check if the package files are downloaded? Normally they are in the /var/cache/apt/archives directory as deb files.

If this doesn't work, are you able to install an application when you use it's deb file?

---

### Post by Tom_ZeCat on 2010-03-21
> **sanderd17 said:**
> This is something weird. Maybe there are some problems with the server. Can you select another server in your software sources? I've had some problems before with the belgian server but it were only speed issues and some timeout errors.

Can you check if the package files are downloaded? Normally they are in the /var/cache/apt/archives directory as deb files.

If this doesn't work, are you able to install an application when you use it's deb file?

There's nothing in that directory except for a file named "lock" and an empty directory named Partial.  

My network is a simple wired network based on a D-Link Ethernet router.  The install system works just fine on my other Ubuntu machine, which is on the same network and is an Ubuntu 8.4 machine.  I've also switched the physical locations of these two machines (meaning they switched router ports) and I get the same result.  The 8.4 machine can update, but the 7.1 machine cannot.  

I've considered reinstalling Ubuntu 7.1 on this machine, but that would wipe out my very large music collection, and on a machine this old and slow, it would take quite a lot of time to recopy it and reinstall Amarok, that is, IF Amarok would reinstall.

---

### Post by sanderd17 on 2010-03-21
Well ubuntu 7.10 isn't supported anymore, see [http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Release_history]("http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Release_history"). Therefore cannonical doesn't have to keep there servers online.

So I guess you'll better upgrade to another version. Maybe wait a month until the next LTS comes out.

---

### Post by ajgreeny on 2010-03-21
Ubuntu 7.10 is no longer supported so there are no available repos to update it or install anything any more.

I'm afraid you will have to use a more recent version and suggest you look at 9.10, using either xubuntu, lubuntu (this is only in beta at present, but will soon be available) or use the minimal install CD and add a lightweight desktop manually, eg openbox, in order to get a good updated system, but still very lightweight.

Come back for more details if you need to.

---

### Post by arpanaut on 2010-03-21
The problem is that 7.10 has reached end of life some time age and it's repositories are no longer active
You will need to edit your sources list refresh and you will be able to install again.

> Re: Older Ubuntu Repositories Accessible?
As mentioned above, they are moved to old-releases, so you can edit your /etc/apt/sources.list and change all the URLS (for example from archive.ubuntu.com to old-releases.ubuntu.com).

As to the reasons why; old Ubuntu releases no longer receive updates, bug fixes, or security patches. It is not safe or supported to use Ubuntu releases past their "end of life."

---

### Post by Tom_ZeCat on 2010-03-21
Okay, that explains it.  The thing is, this old computer doesn't get used much.  It's been pressed into service because my main computer is in the shop having its power supply replaced.  

If I don't want to upgrade its OS, I could just manually install OpenOffice, right?

---

### Post by viper250 on 2010-03-21
see if you can install ubuntu lite or wirescut linux they should run fine on the old one

---

### Post by Miljet on 2010-03-21
If you don't want to update the operating system, it will be easier to do as arpanaut suggests and change your /etc/apt/sources.list file.
> you can edit your /etc/apt/sources.list and change all the URLS (for example from archive.ubuntu.com to old-releases.ubuntu.com).

---

### Post by Tom_ZeCat on 2010-03-21
> **Miljet said:**
> If you don't want to update the operating system, it will be easier to do as arpanaut suggests and change your /etc/apt/sources.list file.

Okay, that's probably the best solution.  Here are the non-commented lines from my sources.list file: 

> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

Do I change it to this?:

> deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by 5735guy on 2010-03-22
Still running Ubuntu 7.10 is not such a bad thing as it was a fine release of the distro. even though support has now ended

You will receive no security updates however I have no problems running Ubuntu 7.04

You may want to replace the repositories as Ubuntu 7.10 is now archived under old-releses

Here are the repositories

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy main restricted
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy universe
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-updates universe
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

To replace the original Ubuntu 7.10 repositories open a Terminal and submit the following command

sudo gedit /etc/apt/sources.list

Delete the original repositories and replace with the ones I have given above

SAVE and close

Back in the Terminal

sudo apt-get update


By doing this you will be able to continue using the Synaptic Package Manager along with other features.

---

