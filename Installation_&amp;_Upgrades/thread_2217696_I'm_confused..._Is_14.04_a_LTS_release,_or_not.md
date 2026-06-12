---
title: "I'm confused... Is 14.04 a LTS release, or not?"
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by steve103 on 2014-04-18
I've downloaded the 14.04 Desktop ISO and am running that in a VM.  Next, I decided to update my server...

My server is configured for the LTS upgrade cycle... In /etc/update-manager/release-upgrades , I have the single non-comment:[INDENT][FONT=fixedsys]Prompt=lts[/FONT][/INDENT]

I had assumed that this would allow me to easily upgrade between LTS releases - giving me a clear (conservative) upgrade path.  The news about a new LTS release couldn't have come at a better time for me... as I want to run scripts that depend upon newer versions of tools than are not, straightforwardly, available under 12.04.  The server is headless and I administer it exclusively from the command line... so, I try:[INDENT][B]

# apt-get update[/B][/INDENT]
[INDENT]Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg[/INDENT]
[INDENT]Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release[/INDENT]
[INDENT]Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources[/INDENT]
[INDENT]Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release.gpg[/INDENT]
[INDENT]Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release.gpg [198 B][/INDENT]
[INDENT]<<< Omitted for brevity>>>
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,649 B][/INDENT]
[INDENT]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex[/INDENT]
[INDENT]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex[/INDENT]
[INDENT]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex[/INDENT]
[INDENT]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex[/INDENT]
[INDENT]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en[/INDENT]
[INDENT]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en[/INDENT]
[INDENT]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en[/INDENT]
[INDENT]Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en[/INDENT]
[INDENT]Fetched 3,891 kB in 16s (243 kB/s)[/INDENT]
[INDENT]Reading package lists... Done[/INDENT]
[INDENT]**# do-release-upgrade -c**[/INDENT]
[INDENT]Checking for a new Ubuntu release[/INDENT]
[INDENT]No new release found[/INDENT]
[INDENT]**# do-release-upgrade -c -d**[/INDENT]
[INDENT]Checking for a new Ubuntu release[/INDENT]
[INDENT]New release '14.04' available.[/INDENT]
[INDENT]Run 'do-release-upgrade' to upgrade to it.[/INDENT]
[INDENT]**# do-release-upgrade**[/INDENT]
[INDENT]Checking for a new Ubuntu release[/INDENT]
[INDENT]No new release found[/INDENT]
[INDENT]**#**[/INDENT]

According to the man-page for do-release-upgrade, the "-d" flag denotes "upgrading to the latest devel release" - which, I assume, means a release other than one which is intended for Long Term Support.  The output from do-release-upgrade is somewhat confusing... I'm hesitating to run do-release-upgrade with a '-d' as I want to be confident that the upgrade will result in a stable, easily maintainable, install.  [The -c option denotes that do-release-upgrade should only check, rather than initiate the upgrade.]

Am I misinterpreting the options to do-release-upgrade?  Is there some bit of configuration I'm overlooking?  Is there a glitch with the way 14.04 has been labelled such that it precludes a clean LTS upgrade from 12.04?

Any hints gratefully received...

---

### Post by grahammechanical on 2014-04-18
Now that 14.04 has been released there is not at the moment a development version of Ubuntu. Over the next few days work will start on 14.10 and if you run do-release-upgrade -d your system will be upgraded to the development branch of 14.10. And yes it will most likely be unstable at some point in the next 26 weeks.

We are not promised that a new release will be available 1 minute after mid-night on release day and yet so many people are complaining that they cannot upgrade to 14.04. The image has to be tested and the code distributed to all the mirror servers. There is often a delay. With so many people rushing to upgrade and download the servers will be slow. An upgrade that should take minutes will take hours. Better to wait. Ubuntu 14.04 will be around for 5 years.

[https://help.ubuntu.com/12.04/serverguide/installing-upgrading.html](https://help.ubuntu.com/12.04/serverguide/installing-upgrading.html)

Regards.

---

### Post by sudodus on 2014-04-18
Yes, 14.04 is a long term support version :-)

But in order to get a smooth ride from the previous LTS version (12.04), I think you will not be prompted to do that until the first point release 14.04.1 LTS in July or August. By that time many bugs will be squashed and the new LTS version will be ready for production platforms.

-o-

This is different from upgrading between previous and next versions, where people who want the latest and greatest software can upgrade directly, assuming these people can stand some bugs. Some people (like me) have one production platform, with an LTS version which is stable, and one or many test platforms with 'the latest and greatest software'. This can be done by dual or multi booting in one computer or with different computers.

---

### Post by bapoumba on 2014-04-18
I see you have both lucid and precise repos in your sources.list. You might want to straighten this up and be all up to date on precise only repos before you upgrade anyway.

---

### Post by steve103 on 2014-04-18
> **sudodus said:**
> Yes, 14.04 is a long term support version :-)

But in order to get a smooth ride from the previous LTS version (12.04), I think you will not be prompted to do that until the first point release 14.04.1 LTS in July or August. By that time many bugs will be squashed and the new LTS version will be ready for production platforms.


Ah-ha... hmmm.  I can understand why the 'normal' upgrade cycle would avoid, by default, pushing me into 14.04 for a few months.  Conversely, I am trying to strike a balance between a maximally stable server (on which I need to install a few tools from source to get acceptably up-to-date facilities) and wanting to deploy the best available packaged LTS release.

If I were installing my server from scratch today, I'd download a 14.04 LTS ISO, and would expect it to stick to the LTS upgrade path over the next few years.  I would like this upgrade path, but I'd like to upgrade 12.04.4 to 14.04 rather than re-install.

It is a 'production' server - but it is one with a very small user-base and one where the age of tools in 12.04.4, very recently, has become a bit of a headache.  

> **grahammechanical said:**
> Now that 14.04 has been released there is not at the moment a development version of Ubuntu. Over the next few days work will start on 14.10 and if you run do-release-upgrade -d your system will be upgraded to the development branch of 14.10. And yes it will most likely be unstable at some point in the next 26 weeks.

We are not promised that a new release will be available 1 minute after mid-night on release day and yet so many people are complaining that they cannot upgrade to 14.04. The image has to be tested and the code distributed to all the mirror servers. There is often a delay. With so many people rushing to upgrade and download the servers will be slow. An upgrade that should take minutes will take hours. Better to wait. Ubuntu 14.04 will be around for 5 years.

[https://help.ubuntu.com/12.04/serverguide/installing-upgrading.html](https://help.ubuntu.com/12.04/serverguide/installing-upgrading.html)


You are echoing my worries about doing a release-upgrade with the "-d" flag.  It is interesting that this page suggests something different:

  [http://www.cyberciti.biz/faq/howto-upgrade-to-ubuntu-14-04-from-ubuntu-13-10-or-12-04/](http://www.cyberciti.biz/faq/howto-upgrade-to-ubuntu-14-04-from-ubuntu-13-10-or-12-04/)

What I'm trying to establish is how I can ask my 12.04.4 LTS server install to upgrade to 14.04 and to track the LTS updates - rather than the development updates... just as I'd expect of a server installed with the fresh 14.04 ISO I've already downloaded.

Is this an issue of mirrors being up-to-date?  If so, how do I specify which mirror I want it to use?

Will an upgrade (as opposed to a re-install) only be available in a few months?

> **bapoumba said:**
> I see you have both lucid and precise repos in your sources.list. You might want straighten this up and be all up to date on precise only repos before you upgrade anyway.

Yes - I think the Lucid ones remained after I upgraded to Precise... I've fixed that now... It makes no difference.

---

### Post by sudodus on 2014-04-18
> **steve103 said:**
> 
It is a 'production' server - but it is one with a very small user-base and one where the age of tools in 12.04.4, very recently, has become a bit of a headache.  


In this case, I think you have a good reason to upgrade. But remember that it is risky, and ***backup*** your server before starting the upgrade. [COLOR=#ff0000]I do not know much about ***servers***, so I hope that someone who knows will read this and chip in to help you.[/COLOR]

---

### Post by steve103 on 2014-04-18
> **sudodus said:**
> In this case, I think you have a good reason to upgrade. But remember that it is risky, and ***backup*** your server before starting the upgrade. [COLOR=#ff0000]I do not know much about ***servers***, so I hope that someone who knows will read this and chip in to help you.[/COLOR]

I'm confident that I want to upgrade... but I want to avoid making a 'silly mistake'.  I am particularly worried about using the '-d' flag - which, I suspect, would result in installation of a configuration that is far more bleeding-edge than I intend.

I'm still not clear why do-release-upgrade is not behaving as I'd expect.  I'm not clear what mirror it is talking to.  I'm aware that some instructions suggest "-d" forces the upgrade - but other documentation suggests that this option will install a version of a 'lower quality' than the release.

I'd love to hear from anyone who has successfully upgraded 12.04.4 to 14.04...

---

### Post by sudodus on 2014-04-18
I don't think the -d option will activate any bleeding edge repository or ppa.

I have used it during the development of Lubuntu Trusty. It will upgrade to the 14.04 LTS standard, as it is in the iso files (previously the daily iso files, now the released iso files). Anyway, that can be checked after the installation (so with a backup you can easily restore your system).

---

### Post by steve103 on 2014-04-18
> **sudodus said:**
> I don't think the -d option will activate any bleeding edge repository or ppa.

Many thanks for your words of encouragement.  I've pressed ahead with 'do-release-upgrade -d' with fingers and toes crossed...

I'll blame you if it goes 'fubar'. :)

---

### Post by sudodus on 2014-04-18
I think it will work, still I hope you have a good backup.

Good luck :-)

---

