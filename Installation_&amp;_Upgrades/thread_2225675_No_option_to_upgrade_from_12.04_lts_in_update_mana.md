---
title: "No option to upgrade from 12.04 lts in update manager"
date: 2014-05-22
forum: Installation &amp; Upgrades
---

### Post by astarmathsandphysics on 2014-05-22
I want to upgrade my ubuntu version. At the moment I am running 12.04 lts server edition and want to upgrade to 14.04, possibly through 13.04
When I change settings in update manager to 'notify me of new software version' to always, I am told I can upgrade to 12.10.
Must I upgrade to 12.10 before I can upgrade to 13.04 or 14.04?#
12.10 is not lts and I am reluctant to upgrade to anything that has not been tried, tested, patched etc

---

### Post by Bashing-om on 2014-05-22
astarmathsandphysics; Hello.

A direct LTS - LTS release is possible, and doable.
Until the 1st point release of 14.04 is released (July 24) 14.04 is a 'development' release and you may release upgrade to 14.04:
```

sudo apt-get update
sudo apt-get upgrade
sudo do-release-upgrade -d

```
Now, when the point release is released, the "sudo do-release-upgrade -d" will no longer point to 14.04, but to that next "development" release 14.10.
Be aware !

[INDENT][INDENT]my little bit to try and help
[/INDENT][/INDENT]

---

### Post by astarmathsandphysics on 2014-05-22
I thought 14.04 was lts. 
Should I upgrade?

When I try to upgrade in termainal I get this message

Your graphics hardware may not be fully supported in Ubuntu 14.04. 

Running the 'Unity' desktop environment is not fully supported by 
your graphics hardware. You will maybe end up in a very slow 
environment after the upgrade. Our advice is to keep the LTS version 
for now. For more information see 
[https://wiki.ubuntu.com/X/Bugs/UpdateManagerWarningForUnity3D](https://wiki.ubuntu.com/X/Bugs/UpdateManagerWarningForUnity3D) Do you 
still want to continue with the upgrade? 

Continue [yN] n

Can I upgrad and keep ubuntu classic environment to keep my system fast?

---

### Post by oldfred on 2014-05-22
They changed from fallback to flashback. Not sure what all the underlying differences are.

       [https://wiki.gnome.org/action/show/Projects/GnomeFlashback?action=show&redirect=GnomeFlashback](https://wiki.gnome.org/action/show/Projects/GnomeFlashback?action=show&redirect=GnomeFlashback)
[http://www.omgubuntu.co.uk/2014/04/ubuntu-14-04-classic-gnome-flashback-session](http://www.omgubuntu.co.uk/2014/04/ubuntu-14-04-classic-gnome-flashback-session)
Flashback/fallback in 14.04 Kansasnoob
Installing the package 'gnome-session-flashback' does exactly the same thing as installing the package 'gnome-panel'.
[http://ubuntuforums.org/showthread.php?t=2220264](http://ubuntuforums.org/showthread.php?t=2220264)
[http://ubuntuforums.org/showthread.php?t=2090021&p=12994477#post12994477](http://ubuntuforums.org/showthread.php?t=2090021&p=12994477#post12994477)
[http://ubuntuforums.org/showthread.php?t=2184682&p=12986002#post12986002](http://ubuntuforums.org/showthread.php?t=2184682&p=12986002#post12986002)
[http://ubuntuforums.org/showthread.php?t=2184682&p=12971487#post12971487](http://ubuntuforums.org/showthread.php?t=2184682&p=12971487#post12971487)
You can reset gnome-panel settings to default:
dconf reset -f /org/gnome/gnome-panel/
[http://askubuntu.com/questions/192130/how-to-change-color-and-width-of-non-overlay-scrollbars-in-ubuntu-12-04](http://askubuntu.com/questions/192130/how-to-change-color-and-width-of-non-overlay-scrollbars-in-ubuntu-12-04)

---

### Post by QIII on 2014-05-22
Hello!  An LTS to LTS upgrade is available when the new LTS has reached its first "point release" -- that is, 14.04.1

With regard to the graphics issue:  what GPU are you using?

---

### Post by Bashing-om on 2014-05-22
astarmathsandphysics; hey,

Release 14.04 is Long-Term-Support and is stable, All I have seen in respect to 14.04 is positive; Smoother than 12.04 and many enhancements.
I know of no reason if you are currently running 12.04 not to upgrade to 14.04.

as always, Murphy's Law applies -> Back up your data (should have backups in any event anyway !) -> and upgrade.

[INDENT][INDENT]just what I think
[/INDENT][/INDENT]

---

### Post by astarmathsandphysics on 2014-05-22
Can I upgrad and keep ubuntu classic environment to keep my system fast?
Am using 2 quad core zeons with 4gb ram.
I will upgrade to 8gb this summer i think

I upgraded and everything seems ok. Thank you and thank god

---

### Post by Bashing-om on 2014-05-22
astarmathsandphysics; Outstanding !

Glad it worked out for you.

As you are now setting pretty ->
Please mark this thread solved; aides others seeking the solution, helps keep the forum clean and precludes others miss-directing efforts to aid.

[INDENT][INDENT]and just keep on keep'n on
[/INDENT][/INDENT]

---

