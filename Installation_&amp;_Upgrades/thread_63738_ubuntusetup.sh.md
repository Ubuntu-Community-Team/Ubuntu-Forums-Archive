---
title: "ubuntusetup.sh"
date: 2005-09-08
forum: Installation &amp; Upgrades
---

### Post by tiwaris on 2005-09-08
Hello all,

I am new to ubuntu and have done a new install of ubuntu today.

I am looking for the script ubuntusetup.sh (the server download.ubuntuforums.org seems to be down).

Are there other similar scripts which I can use to aumatically stuff few more common softwares like gcc, gnuplot, anjuta, mplayer, xmms etc. 

Any links or pointers would be useful.

Thank you all in advance.
Tiwaris

---

### Post by GreyFox503 on 2005-09-08
Here's my copy of it attached.  I downloaded it from the forums about a month or so ago.  I had to rename its extension because you can't upload .sh files.

---

### Post by tiwaris on 2005-09-08
Hi

Thank you very much for posting the file.

I am getting following error on running the script. What could possibly be wrong?

Thank you once again for your help.

tiwaris@tiwaris:~/Desktop$ sudo sh ubuntusetup.sh
mv: cannot stat `sources.list': No such file or directory
gpg: key 1F41B907: duplicated user ID detected - merged
gpg: key 1F41B907: "Christian Marillat <marillat@debian.org>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
OK
E: Opening /etc/apt/sources.list - ifstream::ifstream (2 No such file or directory)
ERROR # 100 : There was an error in apt-get update.

---

### Post by hod139 on 2005-09-08
Might be slightly off topic, but I have sometimes had problems with the `cd` command and sudo.

Back on topic, the problem is line 50, and is probably related to the issue I mentioned above.  Try
```

sudo chmod +x ubuntusetup.sh
sudo ./ubuntusetup.sh

``` 

and also make sure you have sources.list in /etc/apt (Can't imagine why you wouldn't)

---

### Post by GreyFox503 on 2005-09-08
Hehe, whoops.  I just tried to run the script again myself.

Not only could you not download the script, but the first thing the script does it try to download sources.list from http://download.ubuntuforums.org!  grrr.

It also screwed up my /etc/apt/sources.list file.

Here's what I would do if I were you:  go here:

[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

To add the extra repositories.  Since that script isn't much good right now, I would either search in synaptic for what you want or apt-get it myself.

If you just want a general list of useful packages, here are some of the ones I install on Ubuntu.  To install them just run:

```
sudo apt-get install *packagename*
```

Here are some good packages:

```
firestarter - a firewall front-end for iptables
xmms - music player
build-essential - tools to compile programs from source (like gcc)
xine-ui - media player (for more codecs see http://xinehq.de/index.php/faq#QUICKTIME
totem-xine - makes totem front-end use xine
gtkpod-aac - if you have an ipod and want to sync it with Ubuntu
azureus - awesome bittorrent client
linux-k7 - this is the linux kernel optimized for AMD Athlons.  If you want to download a kernel optimized for your proc search synaptic for "linux-" and you will see a whole bunch of them.  If you are not sure what this means then don't do it.
easy-tag - mp3 tag editor
gparted - partition manager (like PartitionMagic)
msttcorefonts - microsoft truetype core fonts (makes text look better)
openoffice.org2 - beta version of the excellent OpenOffice.org suite
sun-j2re1.5 - java runtime environment
smeg - gnome menu editor
bum - boot up manager
flashplayer-mozilla - to see flash animations in firefox
kubuntu-desktop - installs KDE and the whole shebang.  Big download.
sox - cool audio format convertor
k3b - awesome KDE cd and dvd burner
amarok - KDE music player
```

There are other lists on the forum (look at the stickies in the beginners forum) that list lots of other cool programs.

Unfortunately I haven't learned how to script yet, otherwise I would have just given you an uber-script with all this stuff in it.  But all you have to do it copy and paste these into the command line to try them out (shouldn't take too long).

Remember:  If you want to look for a program, check the forums, and use Synaptic.  Synaptic is your friend.  (Try searching Synaptic for "web browser" or "cd burner" or whatever.  Make sure you search by "Name and Description")

Hopefully this helps and is not just information overload!   :smile:

---

### Post by slooksterpsv on 2005-09-09
[QUOTE=GreyFox503]Hehe, whoops.  I just tried to run the script again myself.

Not only could you not download the script, but the first thing the script does it try to download sources.list from http://download.ubuntuforums.org!  grrr.

It also screwed up my /etc/apt/sources.list file.

Here's what I would do if I were you:  go here:

[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

To add the extra repositories.  Since that script isn't much good right now, I would either search in synaptic for what you want or apt-get it myself.

If you just want a general list of useful packages, here are some of the ones I install on Ubuntu.  To install them just run:

```
sudo apt-get install *packagename*
```

Here are some good packages:

```
firestarter - a firewall front-end for iptables
xmms - music player
build-essential - tools to compile programs from source (like gcc)
xine-ui - media player (for more codecs see http://xinehq.de/index.php/faq#QUICKTIME
totem-xine - makes totem front-end use xine
gtkpod-aac - if you have an ipod and want to sync it with Ubuntu
azureus - awesome bittorrent client
linux-k7 - this is the linux kernel optimized for AMD Athlons.  If you want to download a kernel optimized for your proc search synaptic for "linux-" and you will see a whole bunch of them.  If you are not sure what this means then don't do it.
easy-tag - mp3 tag editor
gparted - partition manager (like PartitionMagic)
msttcorefonts - microsoft truetype core fonts (makes text look better)
openoffice.org2 - beta version of the excellent OpenOffice.org suite
sun-j2re1.5 - java runtime environment
smeg - gnome menu editor
bum - boot up manager
flashplayer-mozilla - to see flash animations in firefox
kubuntu-desktop - installs KDE and the whole shebang.  Big download.
sox - cool audio format convertor
k3b - awesome KDE cd and dvd burner
amarok - KDE music player
```

There are other lists on the forum (look at the stickies in the beginners forum) that list lots of other cool programs.

Unfortunately I haven't learned how to script yet, otherwise I would have just given you an uber-script with all this stuff in it.  But all you have to do it copy and paste these into the command line to try them out (shouldn't take too long).

Remember:  If you want to look for a program, check the forums, and use Synaptic.  Synaptic is your friend.  (Try searching Synaptic for "web browser" or "cd burner" or whatever.  Make sure you search by "Name and Description")

Hopefully this helps and is not just information overload!   :smile:[/QUOTE]
 I can't believe just from adding those extra repositories, I'm off the idea of reinstalling OS X. I need to find more repositories to add so I can get whatever I need. Thank you whoever started this topic.

---

### Post by GreyFox503 on 2005-09-09
[QUOTE=slooksterpsv]I can't believe just from adding those extra repositories, I'm off the idea of reinstalling OS X. I need to find more repositories to add so I can get whatever I need. Thank you whoever started this topic.[/QUOTE]

I've seen lots of other people mention other repos here on the forums.  Search the forums for repositories or perhaps google for "ubuntu repositories".  I'm guessing that you could also add debian repositories, but I'm not 100% sure about that, so do so at your own risk.

---

### Post by tiwaris on 2005-09-09
Thanks for the tip. I could get to rectify the error with my package repository

I am planning to write a very simple shell script that should download and install most of the packages I require.

Thank you once again. This is my second day with ubuntu, and I hope to make it useful for me by this weekend.

Cheers
Tiwaris

---

