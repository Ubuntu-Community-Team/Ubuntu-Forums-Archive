---
title: "Installing Flash"
date: 2006-11-19
forum: Installation &amp; Upgrades
---

### Post by rigol on 2006-11-19
Hi there,

I simply cannot get Flash to work. I tried Flash 7, Flash 9 beta, installing manually, via Automatix, via Synaptic (flashplugin-nonfree) - but it wouldn't work like it should. 

Whatever I do:
--> Opera 9 recognises the plugin, and the Adobe page tells me the right version, but some Flash sites work, others won't. It's weird.

--> Firefox 2.0 don't even seem to use the plugin, YouTube videos for example don't show, instead I get "Hello, you either have JavaScript turned off or an old version of Macromedia's Flash Player. Get the latest flash player." In Opera, YouTube works fine right now. about: plugins in Firefox is nearly blank, there is just this "default plugin, File name: libnullplugin.so, enabled no". 

It's drivin me nuts. The last time I tried installing flashplugin-nonfree with a friend, it gave me this:

```
rigol@rigol-desktop:~$ sudo apt-get remove flashplugin-nonfree
Password:
Reading package lists... Done
Building dependency tree... Done
Package flashplugin-nonfree is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rigol@rigol-desktop:~$ sudo aptitude install flashplugin-nonfree
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done
The following NEW packages will be installed:
  flashplugin-nonfree
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 15.8kB of archives. After unpacking 168kB will be used.
Writing extended state information... Done
Get:1 http://archive.ubuntu.com dapper-backports/multiverse flashplugin-nonfree 7.0.68~ubuntu2~dapper1 [15.8kB]
Fetched 15.8kB in 3s (4766B/s)
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 106428 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_7.0.68~ubuntu2~dapper1_i386.deb) ...
Setting up flashplugin-nonfree (7.0.68~ubuntu2~dapper1) ...
Downloading...  done.
installation failed
``` 

Someone an idea? I'm using Dapper.

---

### Post by aysiu on 2006-11-19
Have you tried installing it with the first method outlined here?
[http://www.psychocats.net/ubuntu/flashubuntu](http://www.psychocats.net/ubuntu/flashubuntu)

---

### Post by rigol on 2006-11-19
The first version mentioned in the link doesn't work for me, I can't install the plugins like this in Firefox 2, it says at "Completing the Plugin Finder Service" "No plugins were installed." and gives me a link to the manual installation. 

The second version doesn't work for me either, see the code I posted? There I wanted to install flashplugin-nonfree and it just gave me "Downloading...  done. installation failed"

---

### Post by aysiu on 2006-11-19
And when you manually copy the beta 9 plugin to /usr/lib/firefox/plugins ... no go on that either, huh?

What happens when you do that? It just doesn't acknowledge the plugin is there?

Was it this tutorial that you followed?
[http://www.kungfuice.com/index.php/2006/10/18/installing-flash-player-9-beta-on-ubuntu-edgy/](http://www.kungfuice.com/index.php/2006/10/18/installing-flash-player-9-beta-on-ubuntu-edgy/)

---

### Post by rigol on 2006-11-19
I manuelly moved the plugin to /usr/lib/firefox/plugins also, right now it's there, yes. And Firefox seems to not acknowledge it's there whatever I try. Maybe this has something to do with Firefox2? I don't know what's wrong.

And yes, I tried this tutorial also... I spent the last two days following tutorials on how to install flash, it's driving me crazy](*,)

---

### Post by aysiu on 2006-11-19
I think something is seriously wrong, and it doesn't have anything to do with Firefox 2.0. I'm using Firefox 2.0, and I used it with both Flash 7 and Flash 9 beta, using exactly the methods I've linked to in the previous posts.

Are you saying, though, that you had no problems with Firefox 1.5? Are you using Dapper? What version of Firefox (Ubuntu or Mozilla) are you using, and how did you install it?

---

### Post by rigol on 2006-11-19
Yes, something's seriously wrong. I'll try reinstalling Firefox 2, maybe this solves the matter? I installed it using [this](https://help.ubuntu.com/community/FirefoxNewVersion). 

I never used 1.5, I had a fresh install of Ubuntu and switched instantly to 2.0. And it's the mozilla one and yeah, Dapper.

---

### Post by aysiu on 2006-11-19
Ah, that's the problem!

The way that tutorial installs Firefox 2.0, it links your currently installed plugins, but any subsequently installed plugins won't be linked.

*nanotube* created a script that installs the latest Firefox and links your entire plugins folder instead of just the individual plugins.

Please, give this a shot:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by rigol on 2006-11-19
aysiu, you are great, thanks! Installing Firefox with this script worked! I now have all the installed plugins avaible, Flash is working fine. Will Firefox now recognise when I install new plugins?

And what about Opera... like I said, the plugin is installed, but some sites wouldn't work. Do you know anything about that?

---

### Post by aysiu on 2006-11-19
That's great. Firefox should now recognize newly installed plugins.

So basically, the tutorial you followed said "link anything in the /usr/lib/firefox/plugins folder to /opt/firefox/plugins." The script I linked to before says, "link to /usr/lib/firefox/plugins folder /opt/firefox/plugins," so now when you go into /opt/firefox/plugins you'll really be going into /usr/lib/firefox/plugins--it's just a shortcut to that folder, not a real folder any more.

As for Opera... no clue about that...

---

### Post by polt on 2006-11-19
Yep, I'm having the exact same problem.  I tried navigating to the plugins section and telling Mozilla to open swf files with the new *.so file.  Have you tried that too?

---

### Post by rigol on 2006-11-19
polt:

You mean with Firefox? aysiu solved this issue.
And no, I didn't try that. I still have some issues with Opera and Flash though.

---

### Post by polt on 2006-11-19
wow, weird.  I somehow missed about half the posts on this thread...sorry about that.  :)

---

