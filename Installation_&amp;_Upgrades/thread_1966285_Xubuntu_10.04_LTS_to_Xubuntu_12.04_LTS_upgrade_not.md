---
title: "Xubuntu 10.04 LTS to Xubuntu 12.04 LTS upgrade not available"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by v200 on 2012-04-26
I am using Xubuntu 10.04 LTS
In the upgrade settings I have selected "Long Term Releases" only.
In my update server I had tried the ubuntu main server, India server (in.archive.ubuntu.com because I am located in India), I also let ubuntu select the best server for me... it selected one in China.

After trying all those servers I still did not get the Xubuntu 12.04 upgrade in my upgrade manager... When I switch upgrade settings to "Normal releases" I do get the 10.10 upgrade but I don't wanna do that. I also don't want to switch to ubuntu then upgrade and then switch to xubuntu.

Did anybody else see this problem? Or am I doing something wrong? Or is the upgrade option not available for Xubuntu users yet? :(

Edit: I also noticed that on [http://xubuntu.org/upgrading/](http://xubuntu.org/upgrading/) page does not display the 12.04 upgrade.

---

### Post by techsupport on 2012-04-26
You can't get to 12.04 from there.  You would need to do a fresh install of Ubuntu and add the Xubuntu desktop environment. Users are reporting issues with the live boot disc of Xubuntu 12.04 at the moment, so you are better off just installing Ubuntu 12.04, and adding the Xubuntu Team PPA and installing the Xubuntu Desktop Environment on top of Ubuntu 12.04 and removing Ubuntu desktop.

:guitar:

---

### Post by v200 on 2012-04-26
Thanks for the help techsupport. I appreciate it. I'll go for the fresh install of ubuntu and then switch to xubuntu.

---

### Post by techsupport on 2012-04-26
> **v200 said:**
> Thanks for the help techsupport. I appreciate it. I'll go for the fresh install of ubuntu and then switch to xubuntu.

Here you go:

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

---

### Post by sasciame on 2012-05-07
Is there another option if we do not want to do a fresh install?

---

### Post by vVvSHADOWvVv on 2012-05-07
> **techsupport said:**
> You can't get to 12.04 from there.  You would need to do a fresh install of Ubuntu and add the Xubuntu desktop environment. Users are reporting issues with the live boot disc of Xubuntu 12.04 at the moment, so you are better off just installing Ubuntu 12.04, and adding the Xubuntu Team PPA and installing the Xubuntu Desktop Environment on top of Ubuntu 12.04 and removing Ubuntu desktop.

:guitar:

NOW it's solved.

This is incorrect, you must sequentially upgrade from 10 to 11 to 12. There is no need to do a fresh install. Please stop posting solutions that are incorrect without reading the Ubuntu docs!

&#7780;&#11367;&#480;&#7430;&#336;&#412;
shadowsgovernment.com

---

### Post by mips on 2012-05-07
> **vVvSHADOWvVv said:**
> NOW it's solved.

This is incorrect, you must **sequentially upgrade from 10 to 11 to 12**. There is no need to do a fresh install. Please stop posting solutions that are incorrect without reading the Ubuntu docs!


Good luck with that, if one upgrade can bork as system imagine what four can do...
Then there is the time and bandwidth wasted...

---

### Post by vVvSHADOWvVv on 2012-05-07
> **mips said:**
> Good luck with that, if one upgrade can bork as system imagine what four can do...
Then there is the time and bandwidth wasted...

I have never had an issue except small ones. the reason that many dist upgrades fail is becuase the host system isn't fully updated prior to the dist upgrade

&#7780;&#11367;&#480;&#7430;&#336;&#412;
shadowsgovernment.com

---

### Post by sasciame on 2012-05-07
> **vVvSHADOWvVv said:**
> NOW it's solved.

This is incorrect, you must sequentially upgrade from 10 to 11 to 12. There is no need to do a fresh install. Please stop posting solutions that are incorrect without reading the Ubuntu docs!

&#7780;&#11367;&#480;&#7430;&#336;&#412;
shadowsgovernment.com


So the proper way to upgrade from one LTS release to another is to go from 10.04 to 10.10 to 11.04 to 11.10, to 12.04?

This doesn't seem right.  Why would there be an option in the Update Manager to only show when LTS upgrades are available, (only to not show it)?  I am still relatively new at this, so I could be missing something here :p    

I just want to make sure that is correct before I do 4 upgrades.

---

### Post by vVvSHADOWvVv on 2012-05-07
> **sasciame said:**
> So the proper way to upgrade from one LTS release to another is to go from 10.04 to 10.10 to 11.04 to 11.10, to 12.04?

This doesn't seem right.  Why would there be an option in the Update Manager to only show when LTS upgrades are available, (only to not show it)?  I am still relatively new at this, so I could be missing something here :p    

I just want to make sure that is correct before I do 4 upgrades.


I just remember reading this on an Ubuntu doc at one point.
&#7780;&#11367;&#480;&#7430;&#336;&#412;

---

### Post by Slim Odds on 2012-05-07
> **vVvSHADOWvVv said:**
> I just remember reading this on an Ubuntu doc at one point.
&#7780;&#11367;&#480;&#7430;&#336;&#412;
You read wrong.... LTS to LTS is supported (for Ubuntu anyway).

---

### Post by Clancy_s on 2012-05-08
> **Slim Odds said:**
> You read wrong.... LTS to LTS is supported (for Ubuntu anyway).

For Ubuntu the PP release notes say that direct upgrade 10.04 LTS to 12.04 LTS will be coming in July, after the .1 fixes for 12.04.  It will then show up in the 10.04 update manager.

I suspect the same thing applies to Xubuntu though I've not specifically checked.

In the release notes they also gave a link to instructions on how to upgrade now if  you don't want to wait but it seemed too much of a fuss for me, so I'm waiting for July.

hth

---

### Post by Slim Odds on 2012-05-08
> **Clancy_s said:**
> For Ubuntu the PP release notes say that direct upgrade 10.04 LTS to 12.04 LTS will be coming in July, after the .1 fixes for 12.04.  It will then show up in the 10.04 update manager.

I suspect the same thing applies to Xubuntu though I've not specifically checked.

In the release notes they also gave a link to instructions on how to upgrade now if  you don't want to wait but it seemed too much of a fuss for me, so I'm waiting for July.

hth
Thanks for the clarification.... I think that anyone who waited two years to upgrade can wait a little longer....

---

### Post by RockTeam on 2013-02-27
Should I worry about upgrade from Xubuntu 10.04 to 12.04? Is it possible  to lose something (applications or something else) as a result of an upgrade? What there is concern?

Of course the main rule is to make backup first. But anyway I asked this questions because I haven't practiced it that task yet. Thanks!

---

