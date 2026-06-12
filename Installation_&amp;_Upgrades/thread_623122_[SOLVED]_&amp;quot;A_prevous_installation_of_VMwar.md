---
title: "[SOLVED] &amp;quot;A prevous installation of VMware has been detected&amp;quot; -- FOREVER..."
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by Phrawm48 on 2007-11-25
For 7.04 / Feisty.

I've been trying to correct my problem for three days, including trying most of the strategies described in various forum threads without success.

The more I "clean things up", the worse the problem gets.

I first installed VMware Server from the company's Web site.  I then decided I wanted to uninstall it and install the version from the Feisty / Synaptic repositories.  See this related thread:

[http://ubuntuforums.org/showthread.php?t=620508](http://ubuntuforums.org/showthread.php?t=620508)

The short version is that neither the script based nor Synaptic uninstallers / installers seem to want to do their jobs.[LIST]
[*]The vmware-uninstall.pl script from the old installation package can find nothing that needs to be uninstalled.
[*]The vmware-install.pl script fails because "A previous installation of VMware software has been detected."
[*]Synaptic (Feisty) also reports a previous instance of VMware and won't continue.
[*]If I use apt-get to force the install, Synaptic stays stuck in a "should upgrade / won't upgrade" loop per the forum post cited above.[/LIST]At this point I've tried locating and deleting VMware directories, and tried multiple strategies for "tricking" the installation programs into doing what they're supposed to.

[I][B] I'm hopelessly stuck.
[/B][/I] 
Can someone please tell me -- *HOW* can I get this mess unsnarled and install completely and properly from the repositories for Synaptic?

Cheers & thanks,
Ric
SFO

---

### Post by ruggersway on 2007-11-26
I ran into a similar issue on my system and sadly I went with installing the vmware server version on my system rather than workstation.  I could not find anything that needed removed, performed similar searches as you had.  Some online searches suggest removing /etc/vmware completely, I'd imagine you already tried this...

Server is a free download, they give you a key for it.  If you are using apt-get for the installation you can search the installer script for the exact phrase (error) and try to determine what variables (entries) are tripping the script.  I was too lazy for this, but have had success in the past with similar package installation problems.

-Hope this isn't suggesting what you've already done, but looking through the installer for 'previous install' may point you in the right direction...

If you have the time and patience (I didn't) you can look through the installer script and try to manually remove the corresponding entries by hand.


I didn't have this problem with previous versions of ubuntu or other linux for that matter...



Good luck

-rugger

---

### Post by rosslaird on 2007-12-01
I'm having the same issue. No matter what I do, I can't seem to get rid of it...

Innotek VirtualBox seems to be a decent alternative, by the way.

R.

---

