---
title: "PPAs needed for Ubuntu 21.04"
date: 2021-05-06
forum: Installation &amp; Upgrades
---

### Post by s9032g@comcast.net on 2021-05-06
What ppas should I have for Ubuntu 21.04? I now have Canonical Partners adn the ppa for Chrome Stable checked. If I activate any other ppa, sich as "launch pad........hirsute main" I get a message that no repository info is available from this ppa. I have waht is supposed to be the best Mirror activated.

---

### Post by deadflowr on 2021-05-06
It's probably best to understand that PPAs are a specific type of 3rd party repository.
Like fingers and thumbs, PPAs are 3rd party repositories but not all 3rd party repositories are PPAs.
PPAs are specific repositories from launchpad, anything else is a 3rd party repository.

That said, PPA archives are created by any user who wants to create one and can, and have, only created ones for certain releases.
There is no guarantee that any PPA will be created for any given release, that is solely up to the PPA creator to decide.

It's best to check the PPA's homepage on launchpad to see it has been built for the release.
(You can do so by scrolling down to the top of the package list and click on the dropdown option that says *Published in [Any Series] Filter*
(click on the Any Series to reveal the list of Ubuntu releases supported by the PPA. clicking on Filter will load the page specific to that release.)

Checking the filtered out archives for a release will also list all currently listed packages in that release's archives, as sometimes a PPA will have packages for one release,
but not for a another. And vice versa.

---

### Post by s9032g@comcast.net on 2021-05-06
The ppas that I had apparently came in with my clean install, yet they caused an error in soft ware updates. Strange?

---

### Post by mikewhatever on 2021-05-06
Actually, PPAs are not needed, and Canonical Partners  is an official repository.

---

### Post by deadflowr on 2021-05-06
Canonical Partners might be more or less useless now, as adobe-flashplugin is no more.
It might have 1 or 2 extremely outlier packages in it still usable, but that's probably it.
You can live life fine without it so feel free to disable it, if it isn't already.

Also, Ubuntu ships with zero PPAs or 3rd party repositories installed.
Do you have listing of the PPAs or 3rd party repositories that the system came with?

---

### Post by rbmorse on 2021-05-06
The google Chrome browser installer adds the dl.google.com repo while installing Chrome to facilitate automatic updating.

---

### Post by s9032g@comcast.net on 2021-05-07
I am wrong that some ppas came with the install. Google stable i know about. The one that I didn't connect was teegee2008 etc which I realize now is TimeShift by Tony George. Of course I installed that. The thing is that the teegee2008 ppas also say hirsute, and so seem to belong; however when they are checked they cause software update to hang up. My solution for now is to leave them unchecked.

---

### Post by ajgreeny on 2021-05-07
Not sure if this is now solved for you but please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. 

It is a great help to other users searching the forum.

---

### Post by CatKiller on 2021-05-07
> **s9032g@comcast.net said:**
> The thing is that the teegee2008 ppas also say hirsute, and so seem to belong
The upgrade process changes the release codename for all repositories to that of the release you're upgrading to, and then disables all third-party repositories. This is entirely automatic, doesn't check that a repository for the new codename actually exists (since it necessarily won't for all of testing, and likely for some time after release, even for well-maintained and non-abandoned repositories), and has absolutely no way of telling whether using that repository continues to be a good idea.

And it generally *isn't* a good idea; the primary reason to use a third-party repository is to have newer versions of packages than are included in the standard repositories, but you've just switched to using the newest standard repositories. You'll need to do all the checking about whether using each third-party repository is sensible and necessary that you did when adding it in the first place, and your default position should be that it's neither sensible nor necessary.

---

### Post by s9032g@comcast.net on 2021-05-07
a suggestion from "10 things to do after loading ubuntu 21.04"

8. Install Timeshift
Everyone should make sure to create a restore point of their system and make schedule backup always. This is a recommended step for all in case something is broken in your system so that you can roll back to an earlier stable state. To do that you need Timeshift. Timeshift is a very handy tool and easy-to-use application that helps you to create a restore point in your Ubuntu system. This application is available in a PPA. To install, simply run the below commands in the terminal and run.

sudo add-apt-repository -y ppa:teejee2008/ppa
sudo apt update
sudo apt install timeshift

---

### Post by deadflowr on 2021-05-07
The [teegee2008 ppa]("https://launchpad.net/~teejee2008/+archive/ubuntu/ppa") currently has no hirsute archive, so it has no functional use.
Timeshift does have a separate PPA here: [https://launchpad.net/~teejee2008/+archive/ubuntu/timeshift]("https://launchpad.net/~teejee2008/+archive/ubuntu/timeshift")

That said, it's moot since timeshift is in the normal repositories and is also a newer version than the PPA.

---

