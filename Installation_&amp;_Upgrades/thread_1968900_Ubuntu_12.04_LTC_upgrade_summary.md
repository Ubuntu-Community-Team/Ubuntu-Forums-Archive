---
title: "Ubuntu 12.04 LTC upgrade summary"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by linuxrev on 2012-04-29
My server at home runs Ubuntu 10.04 LTS. Learning that Ubuntu  12.04 LTS has been released, I tried to upgrade using the  'do-release-upgrade' command, over an ssh connection, but whatever I  tried, the steadfast response was 'No new release found'. Puzzling! So I started  to search the forum. Because I noticed, many others are puzzled, let me  summarise what I have found.

NOTE: this is about upgrading a server *without a GUI* -- so no Upgrade Manager, no Unity, no GNOME, just the goold old shell!

1. First of all: **it is yet too early to upgrade a server to Ubuntu 12.04 LTS**. The current release, although official, is still treated as a development version. If you really want, you *can* upgrade using the command 'sudo do-release-upgrade -d', but that is NOT advised. See Precise Pangolin [Release Notes]("https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop")  for more information. Once the first point release will be out in July,  i.e. version 12.04.1, the recommended procedure will work (see 4. below.)

2. Once that marvelous day has come when you can actually upgrade to 12.04 LTS, **first** make sure you have your Ubuntu 10.04 LTS distro updated to the max:
[INDENT]$ sudo apt-get update
$ sudo apt-get upgrade
[/INDENT] That will effectively take your version to level 10.04.4.

3. Needless to say -- one would assume, but reality proves the need for repetition -- you need to make a **backup** of any files you might regret to lose if something goes wrong (documents, pictures, spreadsheets, config files, etc.). Of course, on your machine nothing ever goes wrong, but why not be better safe than sorry?

4. Then run the magic command...
[INDENT]$ sudo do-release-upgrade
[/INDENT] ...and follow the instructions. See [Documentation]("https://help.ubuntu.com/12.04/serverguide/installing-upgrading.html") for details.
 
5. In case you would not have a working internet connection, you could  upgrade using the Alternate CD/DVD, either from disk or by mounting the  ISO image. Of course you would need to download the 12.04.1 version of  Ubuntu LTS. More information can be found [here]("https://help.ubuntu.com/community/PreciseUpgrades").

Well, happy updating in July!

---

