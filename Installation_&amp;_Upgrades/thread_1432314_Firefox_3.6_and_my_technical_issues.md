---
title: "Firefox 3.6 and my technical issues"
date: 2010-03-17
forum: Installation &amp; Upgrades
---

### Post by amnite on 2010-03-17
To Wojox:
I did like you told the one kid to do to install FF 3.6, i input all the commands and wound up with neither the new FF or my old one(No such file or directory). Luckily i had the uncompressed archive, i unsuccessfully tried to install earlier, located in my trash and was able to run it from my desktop to write you this message. Sooo ummm.... any help or ideas on how to get it to work again? Thx
---
OK.... Well I followed his code(code follows...) and poof. Bad juju. Well like i said i downloaded the tar.bz2 or wutever and unsuccessfully tried to install it. But i restored it from the trash and have been running it from my desktop, so how do i fix this mistake. But i still have all my add-ons and stuff too btw which i thought was weird..
---
 Re: Installing Firefox 3.6
Okay, you don't want to run Firefox out of your /home/user directory. Anything you download like that should be set up in /opt.

To install from the ppa run this:

Code:

sudo bash -c "echo 'deb [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu) intrepid main' >> /etc/apt/sources.list"

Code:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CE49EC21

Code:

sudo apt-get update && sudo apt-get install firefox-3.6

Code:

sudo apt-get upgrade && sudo apt-get dist-upgrade

__________________
wojox.homelinux.net

---

### Post by quixote on 2010-03-19
I'm not real clear from what you've said, where you are in the process, so my suggestions may or may not be useful.  First, this line: > sudo bash -c "echo 'deb [http://ppa.launchpad.net/mozillateam...-stable/ubuntu](http://ppa.launchpad.net/mozillateam...-stable/ubuntu)  intrepid main' >> /etc/apt/sources.list"Are you actually running Ubuntu Intrepid?  If you're using a more recent version, instead of "intrepid" you want to substitute "jaunty" or "karmic".  Whatever your version is.

I assume you want the experimental, bleeding edge Firefox?  (3.7, which will be 4.0, is also available in that case.)  If not, your simplest solution is just to install firefox from synaptic.  Then all the install troubles will disappear.

The last line: "sudo apt-get upgrade && sudo apt-get dist-upgrade" has nothing to do with installing firefox.  [COLOR="DimGray"][Wrong!  see update below. That upgrades from one version of ubuntu to the next.  Presumably, that did nothing right now, since there's no distribution upgrade released yet.  But unless an upgrade is what you actually want, I wouldn't run that command.][/COLOR]

*Update: Eep.  Brain fart.  Sorry about that.  "sudo apt-get upgrade" is simply the command the install whatever new versions of packages are available in the repositories.  "dist-upgrade" would upgrade to the next distribution version.  So, if a new version of firefox happened to be one of the packages slated for upgrading, it would indeed upgrade it.*

Also, I would disagree that you don't want to run FF from /home/your-user.  It's a bit complicated getting plugins to work and all that good stuff, but it can be useful, especially when trying out new versions if you don't want them stepping on a system-wide version.

---

### Post by Trent T on 2010-03-27
[QUOTE=quixote;8991363]....I assume you want the experimental, bleeding edge Firefox?  (3.7, which will be 4.0, is also available in that case.)  If not, your simplest solution is just to install firefox from synaptic.  Then all the install troubles will disappear.....

Wouldn't it be wonderful to be able to let a working system keep going, without the upgrade?  

Alas!  comcast.net, my internet provider, recently announced that firefox 3.6 will be one of three supported web browsers-- If I don't upgrade soon (from Firefox 3.0.18 ), I will no longer be able to check my email :-(
unless I want to try Internet Explorer or the other one...

I'm watching this discussion with keen interest--best of luck to all.

---

### Post by mkvnmtr on 2010-03-27
The easiest way to get the latest stable Firefox which is now 3.6.2 is to go to the Ubuntuzilla site and follow the instructions. They will add a repository that will keep you updated.

---

### Post by wojox on 2010-03-27
> **amnite said:**
> To Wojox:
I did like you told the one kid to do to install FF 3.6, i input all the commands and wound up with neither the new FF or my old one(No such file or directory). Luckily i had the uncompressed archive, i unsuccessfully tried to install earlier, located in my trash and was able to run it from my desktop to write you this message. Sooo ummm.... any help or ideas on how to get it to work again? Thx
---
OK.... Well I followed his code(code follows...) and poof. Bad juju. Well like i said i downloaded the tar.bz2 or wutever and unsuccessfully tried to install it. But i restored it from the trash and have been running it from my desktop, so how do i fix this mistake. But i still have all my add-ons and stuff too btw which i thought was weird..
---
 Re: Installing Firefox 3.6
Okay, you don't want to run Firefox out of your /home/user directory. Anything you download like that should be set up in /opt.

To install from the ppa run this:

Code:

sudo bash -c "echo 'deb [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu) intrepid main' >> /etc/apt/sources.list"

Code:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CE49EC21

Code:

sudo apt-get update && sudo apt-get install firefox-3.6

Code:

sudo apt-get upgrade && sudo apt-get dist-upgrade

__________________
wojox.homelinux.net


Sorry you had a bad time with it. More than likely the instructions I gave were for 9.10 not 8.10. Do you have the link to the thread  you're talking about?

---

