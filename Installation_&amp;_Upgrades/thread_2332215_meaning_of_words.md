---
title: "meaning of words"
date: 2016-07-29
forum: Installation &amp; Upgrades
---

### Post by yazdzik-k on 2016-07-29
Dear Friends,
15.10 is dead,  so in order to use the latest flash,  evolution, &c,  which are necessary in the real world, it appears that an upgrade is imminent,  as until the Debian installer is finished,  there are not too many alternatives to use on my relatively new hardware.

Thus the question:  does "not supported" mean:

a:  we keep the repository current, but provide no official help.
b: your current evolution or whatever is the one with which you will go to your grave as we will not update the repos
c: of course we shall keep everything as up to date as possible,  but we feel that the dev team of the particular app is woefully undermanned or whatever,  use at your own risk.

Since this is mission critical machine,  and the only distro which installed at all was Ubuntu 15.10,  one might imagine that,  even as a debian sid user for well over fifteen years,  I experience some trepidation at such a dire warning.

Regards to all,

Martin

---

### Post by howefield on 2016-07-29
> **yazdzik-k said:**
> Thus the question:  does "not supported" mean:

Not supported means that the relevant repositories are moved and archived at old-releases.ubuntu.com. The software they contain will not receive updates of any kind, not security nor versioning updates.

> Since this is mission critical machine,  and the only distro which installed at all was Ubuntu 15.10,  one might imagine that,  even as a debian sid user for well over fifteen years,  I experience some trepidation at such a dire warning.

Running a release that is supported for only 9 months as 15.10 was, is not a normal method of maintaining "*mission critical machine*". Stick to LTS if you want to lessen the trepidation to once every 5 years.

---

### Post by Rex Bouwense on 2016-07-29
> When an Ubuntu release reaches its “end of life” it receives no further maintenance updates, including critical security upgrades. We highly recommend that you upgrade to a recent version of Ubuntu at this point.
[http://www.ubuntu.com/info/release-end-of-life](http://www.ubuntu.com/info/release-end-of-life)

Ninja ed by the master.

---

### Post by vasa1 on 2016-07-29
> **yazdzik-k said:**
> ...
Thus the question:  does "not supported" mean:
...
Could you please provide the entire sentence in which "not supported" appears as well as a relevant link?

---

### Post by yazdzik-k on 2016-07-29
Dear Vasa,

I hope this attachment works.
[ATTACH=CONFIG]270425[/ATTACH]

1.  Mission critical,  in the the arts and academia in the US,  may also be a misnomer,  as the very latest Flash is necessary to work,  as are things like dl-you tube to snatch kids' auditions,  &c, as some colleges and even some gov't websites use flash extensively,  including forms, whatever my or our opinion of that may be.  Same for Java.  This,  a UHD screen might seem overkill for someone in a law chambers or programming,  but when students as for help editing a video which is itself taken in UHD,  or similar other situations arising from the need rather than wish for the latest hardware,  I use mission critical as meaning my livelihood depends upon the latest hardware and absolutely reliable support for it.  I apologise if I used the term incorrectly.


2. I also apologise for my ignorance,  as I have always used rolling distros,  and whilst absolutely impressed with the extremely high quality of the 15.10 version,  as it was the only distro whatsoever that installed where everything worked,  I am used to running things like upgrades -s  and making sure that I know I shan't lose anything I need.

Thus the question,  will evolution,  for a specific example,  still work after the upgrade,  and,  after the upgrade,  whilst unsupported in the sense of technical support,  will it,  as an example and thus relating to all the other listed things,  simply cease to function when a dep will be removed to avoid conflict with a different versioned file of the dep necessary.

To make up a silly example,  guacamole 2.043 depends upon gtk2.  obviously,  hidpi depends upon gtk3.  if I am running Ubuntu 16.x,  which has mostly gtk3 deps,  will I lose guacamole due to a dep conflict resolution issue.

In a more seriously example,  I could probably run Mate, my preferred desktop,  in 16.10 now, but need to manually initiate hidpi support.   One simply needs instructions,  as the ones on the web are mostly for Arch.  Since there is,  for whatever reason,  varying file placement even knowing what would would in one situation may not enable the file change to work in another as the location of the file is variable depending upon distribution.  

Therefore, I am asking the question,  as I must have evolution,  skype,  and a bunch of stuff that might not seem totally to a lot of people, working on recent hardware,  that is nonetheless confined by both budget and availability.   Surely,  as much as the days of building my own kit were lovely,  and coding was fun,  I am not sure I even know anyone,  with one gamer as an exception,  who owns a desktop.  O tempor,  o mores.

So,  will everything work after upgrade,  or am I in for chaos?

Very gratefully,

M

---

### Post by grahammechanical on 2016-07-29
> Thus the question,  will evolution,  for a specific example,  still work  after the upgrade,  and,  after the upgrade,  whilst unsupported in the  sense of technical support,  will it,  as an example and thus relating  to all the other listed things,  simply cease to function when a dep  will be removed to avoid conflict with a different versioned file of the  dep necessary.

You will get an upgraded version of Evolution. I do not have Evolution installed on my 16.04 but the version available in the software store is Evolution version 3.18.5.2. So, your present version of Evolution will be replaced with this newer version but as the user files for Evolution are in the /home directory you will not lose the configuration settings or data associated with Evolution.

The same situation applies to other software such as Libreoffice, Firefox. Synaptic Package Manager shows Skype version 4.3.0.37 available for installing.

Ubuntu 16.10 is still under development. It will not be released until the end of October and it only has 9 months support anyway. This is why you are advised to upgrade to 16.04 until 18.04 comes out or go beyond until its support ends 5 years from April 2016.

The precautionary procedures for upgrading are:

1) Backup.
2) Revert to using an open source video driver.
3) Revert the desktop to a default condition as much as possible.
4) Disable any PPAs.
5) have stable electricity supply.
6) Preferably a wired connection to the internet or a stable WiFi connection.
7) If a laptop do not close the lid.
8) Do not leave the upgrade unattended.
9) Do not start the upgrade just before needing to do something important.
10) Do not power off the machine.

These precautions are based on things that users have actually reported doing when coming on this forum for help on how to fix a broken upgrade.

With a reasonably fast internet connection the downloads do not take hours. It is the installation that takes longer. But I have not found it to be excessively long. And sometimes we do need to give some user interaction.

Regards

---

### Post by yazdzik-k on 2016-07-29
Thank you,  Graham  

Sincerely.

And, especially for the video driver,  as that is something coming from Debian I never would have considered as a possible trouble source.

---

### Post by grahammechanical on 2016-07-29
The latest versions of Ubuntu have the latest proprietary video drivers but the newest proprietary video drivers often drop support for older video adapters. That is the situation I am in. I just think that it is better be on the safe side and upgrade with an open source video driver as that is the default. It avoids the possibility of a conflict. It does not always happen but as with doctors, we only see those people with health problems. And Ubuntu makes it easy to install proprietary video drivers. System Settings>Software & Updates>Additional Drivers.

When installing Ubuntu if we tick the box "install third party software" we get some proprietary audio & video codecs and a proprietary video driver as well. So, we may be using a proprietary video driver without even knowing it.

As I understand Debian philosophy, it is assumed that users want all FOSS. Ubuntu philosophy does not make that assumption but then again it does not assume that the user wants as much non-free software as possible. Ubuntu makes getting non-free software a bit easier with the user taking responsibility.

Regards.

---

### Post by Dennis N on 2016-07-29
If I were in your shoes, I would be reluctant to risk an in-place upgrade of a system critical to my classroom usage. Instead, I would install the 16.04 in a dual boot, and take the time to set it up while still using the existing system for my classes. When you are sure everything works, you can start using the 16.04 instead of the 15.10. Don't burn your bridges until you get safely across to the other side.

During that time, you can get the latest Firefox and flash player from Mozilla and Adobe and install them manually - it is not hard to do.

---

### Post by yazdzik-k on 2016-07-29
Dear D,

Yes,  I am used to getting things manually,  as that's was often necessary in straight debian.   

I shall definitely add a new partition to try 16.04 as when I try the originally install,  I wanted to use it,  but it had a few "issues".  15.10 was easy.

And I am glad you wrote that,  as I was considering the upgrade in situ, and  almost took the risk.

Best,
M

---

