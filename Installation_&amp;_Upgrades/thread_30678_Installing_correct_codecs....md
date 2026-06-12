---
title: "Installing correct codecs..."
date: 2005-04-29
forum: Installation &amp; Upgrades
---

### Post by YourSurrogateGod on 2005-04-29
Ok, I would love to play my latest avi files, but I can't :( . I double-clicked on of them and got the below error message...
```
There were no decoders found to handle the stream in file 
"file:///media/usbdisk/Videos/my_hime_25.avi", you might need to install the 
corresponding plugins
```
Where do I find the necessary codecs and how do I install them?

/me sorry if this is in the wrong forum.

---

### Post by Professor X on 2005-04-29
[The Ubuntu Guide](http://www.ubuntuguide.org) explains how to install the multimedia codecs.  You will need to install totem-xine if you want to use totem to watch avi files.  You could also install xine-ui or mplayer.

Hope that helps.

---

### Post by YourSurrogateGod on 2005-05-01
Hmm... I got the below.
```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource 
temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is 
another process using it?
```

---

### Post by jodef on 2005-05-01
Did you by chance have Synaptic open while trying to follow the information in the guide? if so close synaptic and try again.

---

### Post by YourSurrogateGod on 2005-05-01
[QUOTE=jodef]Did you by chance have Synaptic open while trying to follow the information in the guide? if so close synaptic and try again.[/QUOTE]
Heh... yeh, I closed that. This is what I tried and got...
```
comp:~$ sudo apt-get install gstreamer0.8-plugins
Password:
Reading package lists... Done
Building dependency tree... Done
Package gstreamer0.8-plugins is not available, but is referred to by another 
package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gstreamer0.8-plugins has no installation candidate
comp:~$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package w32codecs
andrew@andrew-ubuntu-comp:~$

```

---

### Post by YourSurrogateGod on 2005-05-01
I also tried to install xine-ui...
```
comp:~$ sudo apt-get install xine-ui
Reading package lists... Done
Building dependency tree... Done
Package xine-ui is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xine-ui has no installation candidate
```
It says that the packages aren't there. What am I missing?

---

### Post by YourSurrogateGod on 2005-05-01
Ok, after enabling universe and such and executing the below commands again, the avi files are playing, but the only thing that I'm getting is the audio only, no video :( .

---

### Post by YourSurrogateGod on 2005-05-06
I don't know what I did, but I can see the movies fine :) . Now comes another question. Is there a video player that will allow me to do things such as pick out a particular part in the movie that I want to see (such as in the middle, as opposed starting from the very beginning)?

---

