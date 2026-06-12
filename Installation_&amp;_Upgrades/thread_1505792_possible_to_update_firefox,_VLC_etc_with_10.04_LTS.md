---
title: "possible to update firefox, VLC etc with 10.04 LTS ?"
date: 2010-06-09
forum: Installation &amp; Upgrades
---

### Post by AM_SOS on 2010-06-09
hi all,

am planning to upgrade soon from 9.10 to 10.04. i also hope to use 10.04 till the next LTS version is released.

i just want to clarify as to what will happen when new versions and releases of firefox, VLC etc are put out ?

will i be able to update my applications to the latest versions ? or will there be risks involved ?

thanks !

---

### Post by snowpine on 2010-06-09
Ubuntu 10.04 will receive minor updates (bug fixes and security patches) through April 2013. You will never receive major updates that introduce new features and functionality; in other words, 10.04 will always use (bug-fixed) software from April 2010. (The one exception to this is Firefox; Canonical has a new policy of keeping Firefox current to prevent security problems.)

If you want to use the latest version of an application, you have a few options. The easiest in my opinion is to add a "PPA" to your sources list. This is basically a one-application repository that will give you the latest version. Obviously this is completely unsupported by Canonical; you are on your own if you add unofficial software sources and encounter bugs/stability problems.

Launchpad is the best source for PPAs: [https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)

You might also check the application's home page; some of them (VirtualBox and Opera just off the top of my head) have their own repositories for Ubuntu users.

ps In my opinion, LTS is a terrible choice for users who always want the latest applications. You should upgrade every 6 months to the new release to stay current. This is easier and more stable than adding dozens of PPAs and 3rd party software sources. LTS is a good choice if you want stable application versions, maybe with one or two important applications kept current through PPAs. All just my opinion of course. :)

---

### Post by AM_SOS on 2010-06-10
-thanks for your lucid reply! i use ubuntu for basic stuff. for movies etc i use VLC, firefox for internet, adobe reader, and open office word. so given my usage it shouldn't be a bad idea to stick with 10.04 LTS, right ?
however, i would really like to be able to go with the latest versions of these softwares. but you say that for LTS canonical allows this only for firefox. so i am not sure how i would be able to keep other programs updated.
one of the reasons i am so keen on keeping abreast with the latest versions/releases is because i had experienced problems with playing movies etc in the past. sometimes the codecs were missing etc etc.
so i have sort of developed a rule of thumb by which i try to go for the latest versions of the softwares i use. comments ?

-if i stick to 10.04 for now, will i be able to skip 10.10 and upgrade directly to 11.04 when it is released ? by direct upgrade i mean the online upgrade provided by update manager......

-can you tell me more about PPA ? e.g. i prefer using VLC media player. so am i using PPA ? should one ideally stay away from non - canonical maintained applications ?

thanks !

---

### Post by snowpine on 2010-06-10
You can use PPAs to get the latest versions of specific applications: [https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)

You can also get new versions of applications straight from the source, for example VLC: [http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)

Canonical supports only the applications in their official repositories, which are a little out of date, but are well-tested and known to be stable. Use PPAs and 3rd party sources at your own risk.

I do not think you'll be able to skip directly from 10.04 to 11.04 (but since 11.04 doesn't exist yet, we don't know for sure).

---

