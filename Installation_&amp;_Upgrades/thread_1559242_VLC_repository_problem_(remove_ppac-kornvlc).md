---
title: "VLC repository problem (remove ppa:c-korn/vlc)"
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by gencon on 2010-08-23
Using: Ubuntu Lucid

A while ago I installed a ppa repository so I could install VLC 1.1.1 in Lucid, the instructions were on this linked page (but shown below):

[http://www.ubuntugeek.com/install-vlc-1-1-1-in-ubuntu-10-049-10-using-ppa.html](http://www.ubuntugeek.com/install-vlc-1-1-1-in-ubuntu-10-049-10-using-ppa.html)

sudo add-apt-repository ppa:c-korn/vlc
sudo apt-get update
sudo apt-get install vlc mozilla-plugin-vlc

VLC 1.1.1 is working fine and always has.

However the ppa:c-korn/vlc repository no longer exists, the user has shut it down apparently after complaints that "shoddy packaging that caused untold breakage to thousands of systems all over the world."

My problem is with updating Ubuntu I get the 'orange warning triangle' in my notification area:

"Could not download all repository indexes

Failed to fetch [http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead."

Not surprising as the repository has closed.

BUT how do I remove the repository? It is not listed in my /etc/apt/sources.list file.

Thanks all.

PS. How should I update VLC in future?

---

### Post by OliverW on 2010-08-23
If you add repositories, they are added as .list files in /etc/apt/sources.list.d 

For c-korn you can remove it like this:
```
sudo rm /etc/apt/sources.list.d/c-korn-* && sudo apt-get update
```

---

### Post by gencon on 2010-08-23
Thanks Oliver, that worked perfectly. Cheers.

---

### Post by xaliqen on 2010-08-23
I'm sad to hear the repository was shut down because of complaints.

I second gencon's PS question as to whether there are any other repositories with frequently-updated VLC builds.

I'd tap into the VLC git repo and grab the source, but I do have a penchant for apt.

---

### Post by andrew.46 on 2010-08-24
Hi xaligen,

> **xaliqen said:**
> I'd tap into the VLC git repo and grab the source, but I do have a penchant for apt.

Perhaps have a look at the guide I have been running for a while now:

Howto: Build the development version of vlc under Ubuntu
[http://ubuntuforums.org/showthread.php?t=1398119](http://ubuntuforums.org/showthread.php?t=1398119)

There is a small addendum that details how to build 1.1.3 as well..

Andrew

---

### Post by scotty64 on 2010-08-24
There seems to be a new ppa with the latest VLC version. I found it in this post: [http://www.unixmen.com/software/1114-vlc-113-is-released-ppa-for-ubuntu](http://www.unixmen.com/software/1114-vlc-113-is-released-ppa-for-ubuntu)

The ppa is "ppa:n-muench/vlc"

Has anyone tried this build ?

---

### Post by recluce on 2010-08-25
> **scotty64 said:**
> There seems to be a new ppa with the latest VLC version. I found it in this post: [http://www.unixmen.com/software/1114-vlc-113-is-released-ppa-for-ubuntu](http://www.unixmen.com/software/1114-vlc-113-is-released-ppa-for-ubuntu)

The ppa is "ppa:n-muench/vlc"

Has anyone tried this build ?

I really wanted to try this ppa, but I got a laundry list of packages that it would need to uninstall in order to update VLC to 1.1.3, including:

mencoder
mplayer
smplayer
electricsheep
devede

At that point: not worth it, I am OK with 1.1.2 for now. Has anybody else had similar trouble with Nate Muench ppa?

---

### Post by andrew.46 on 2010-08-25
Hi xaliqen,

> **xaliqen said:**
> I'm sad to hear the repository was shut down because of complaints.

Do you have a link to any of the problems / discussions concerning problems with the Korn vlc PPA?

Andrew

---

### Post by slumbergod on 2010-08-25
I am using the new vlc 1.1.3 from the N-Muench ppa and it is working very well for me. This release of vlc seems to have fixed a bug with the space bar (sometimes pause playback, sometimes restart the file at the beginning).

I have found that I am unable to use mencoder to copy audio and video streams from an avi to repair it so possibly you need to make a choice...VLC or everything else relying on ffmpeg.

[EDIT] Forums member inameiname suggests a fix that worked for me... 
([http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=9748067&postcount=3](http://ubuntu-virginia.ubuntuforums.org/showpost.php?p=9748067&postcount=3))
Simply install a couple of small dependencies, then grab three debs for the mencoder, mplayer, and mplayer-gui built for compatibility with the latest ffmpeg from the muench ppa.

---

### Post by roy913 on 2010-08-25
for updating vlc, feel free to try cutting edge multimedia ppa which has vaapi enabled.

---

### Post by cthlhu1987 on 2010-08-26
> **OliverW said:**
> If you add repositories, they are added as .list files in /etc/apt/sources.list.d 
For c-korn you can remove it like this:
```
sudo rm /etc/apt/sources.list.d/c-korn-* && sudo apt-get update
```
Thx, workes... YOU MADE MY DAY :)

---

### Post by recluce on 2010-08-26
> **roy913 said:**
> for updating vlc, feel free to try cutting edge multimedia ppa which has vaapi enabled.

Thank you, that repository works for me. There are still some caveats though, so here is a little "How To" for people that had the ppa:c-korn/vlc installed:

1. Remove the obsolete repository. You can do that with the shell command posted in this thread or in Synaptic Package Manager. In Synaptic, click on "Settings -> Repositories". Now click on the tab "Other Software". Find the c-korn entry, select it and click on the remove button. Close Synaptic for safety.

2. In your command shell, type the following to add Brandon Snyder's "Cutting Edge Multimedia" Repository. Be aware that adding a ppa has certain risks, like breaking your system or the ppa just vanishing into thin air. :rolleyes:

```

sudo apt-add-repository ppa:nvidia-vdpau/cutting-edge-multimedia

```

3. Go back into Synaptic, hit reload to actually load the new repository information.

4. In Synaptic, uninstall your current VLC. (I had trouble in a direct upgrade attempt from the "c-korn" to "cutting edge" VLC, which lead into dependency hell.) Do not purge the configuration information, unless you want to adjust all your VLC settings from scratch.

5. Install the new VLC. You may still run into some dependency issues, I had to remove DeVeDe and Electric Sheep. While you are at it, you may also want to upgrade mplayer, ffmpeg and xine with the more recent, vdpau friendly versions from the ppa.

6. If you want to check if vdpau is working on your machine, install vdpauinfo and run it from the shell without any parameters. It will tell you the vdpau capabilities of you NVidia card or will give you an error if vdpau is not working.

Once again, a big caveat: the above worked for me, which does by no means imply a fix-for-all. If you decide to try this, backup your system with Clonezilla BEFORE you start, to be able to recover from major borkage!

---

### Post by hype on 2010-08-26
Seems like this ppa:nvidia-vdpau/cutting-edge-multimedia is a good alternative to Korn's ppa :)
Thanks !

---

### Post by xaliqen on 2011-06-27
I'm currently getting a 404 for the Nvidia vdpau cutting edge repository in Natty.

Is there a Natty repository with frequent VLC updates similar to c-korn or Nvidia cutting edge?

---

### Post by gencon on 2011-06-27
> **xaliqen said:**
> I'm currently getting a 404 for the Nvidia vdpau cutting edge repository in Natty.

Is there a Natty repository with frequent VLC updates similar to c-korn or Nvidia cutting edge?
[OP Here] I now use lucid-bleed but the same team have natty-bleed too, may be what you're after (it certainly has the most recent VLC release).

See this web page:
[https://launchpad.net/~natty-bleed/+archive/ppa]("https://launchpad.net/%7Enatty-bleed/+archive/ppa")

---

### Post by xaliqen on 2011-06-27
Thanks for the update OP, added and updated.  :)

---

