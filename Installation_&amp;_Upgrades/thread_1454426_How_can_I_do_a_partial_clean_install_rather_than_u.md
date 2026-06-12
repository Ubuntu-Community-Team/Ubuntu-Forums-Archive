---
title: "How can I do a partial clean install rather than upgrade?"
date: 2010-04-14
forum: Installation &amp; Upgrades
---

### Post by inspired on 2010-04-14
Hi folks,
I have a question that has been on my mind for a few years now!!

I have a compaq nx7010.
It started out with 8.04 or perhaps 8.10.
I upgraded it through to 9.04 when that became available.

I have not upgraded to 9.10 year, because I recall it took me a fair amount of time to get my system working correctly after the 9.04 upgrade. At a guess, audio went down, wifi broke, and that sort of thing.

I am now finding that apps I use are not releasing new versions compatible with 9.04. And I see 10.04 is on its way, and I understand it is best to go from one upgrade to the next rather than jump a release.

Here's my question:
I get the impression it is cleaner and more stable to do a clean install as opposed to an upgrade. I've also seen many people expressing that view. I've always just gone with upgrading because I didn't like the thought of having to set my whole computer up the way I like it, again.

Is there a way to do a clean install that will keep my system the way I like it? For instance, to not have to reconfigure every application?
I have my partitions set up like this:
  ext3   /home
  ext3   /
  linuxswap

Just how much config related stuff is stored in the /home folder? Or is this purely user files?

What is the consensus? Is it better to upgrade or to do a clean install? My intention is to have a stable system that does not require hours of my time to get sound and wifi working, with the latest release on it (so that I can run the latest apps).

With thanks,

Jonathan

---

### Post by wilee-nilee on 2010-04-14
Upgrade or fresh install is a matter of choice personally I think, you will get arguments for both. Personally I generally do fresh installs being that I have everything backed up off my computer.

9.04 doesn't have a upgrade path to 10.04. I would download a live cd maybe put it on a thumb if your computer will boot one, install it with startup disk creator with a persistent file and try it out and see if it works.

There are some ways you can do a fresh install and reload your old installs, when applicable, so hopefully people will pipe in with info. 

Basically it is I believe having a copy of the apt-get list and the additional keys added, then doing a save of the synaptic installs this is run as a script in the new install, after making sure additional repo are in the new apt-get.

---

### Post by oldfred on 2010-04-14
All your personal settings are in /home. There may be a few system settings in /etc.  

If you have installed a lot of apps:
from lovinglinux
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

The only thing is it may install old stuff you do not need. I did this with my install of Karmic where I had upgraded for 3 years. It reinstalled python 2.4 and 2.5 since they were still available but I did not need (or want them). In my case the list produced was massive but I should have housecleaned before reinstalling. Some really old stuff that I should have housecleaned out in synaptic did not reload. 

If you have room, you can make a new 20GB partition and install the new version, keeping your old. You can check how large your current install is. Since /home already is separate it should be pretty easy for you.

---

### Post by inspired on 2010-04-15
Thanks to both of you.
I will take a look at the links on how to easily install the apps I have currently got in use. I can see how it may result in redundant stuff getting installed, so I will clean up the list before reinstalling.

I'll also test the machine out on a live disc.

Should I be concerned about application settings being stored somewhere other than my /home folder? Such as in /apps, as mentioned?

Much thanks...
Jonathan

---

### Post by tommpogg on 2011-07-01
Let's see if I have got it right:
Upgrade

[LIST]
[*]allows to keep your configuration and installed programs
[*]may cause instability problems
[/LIST]
Clean install

[LIST]
[*]configuration and installed programs are lost
[*]no instability problems
[/LIST]

Now, when talking about clean install, most people say that reinstalling programs is not a matter, since it can be done almost automatically by using Synaptic (or apt-get).
This is true, but I believe that the real problems are programs not available in the repositories, e.g. manually installed software, games, professional software, non-free programs.
By a upgrading you can keep these programs too.

The question is: is there a way to perform a clean install while keeping configuration and installed programs (including non-free manually installed software)?

---

