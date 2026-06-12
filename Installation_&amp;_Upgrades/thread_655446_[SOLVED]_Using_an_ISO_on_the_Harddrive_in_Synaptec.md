---
title: "[SOLVED] Using an ISO on the Harddrive in Synaptec (in lieu of cd-rom)?"
date: 2008-01-01
forum: Installation &amp; Upgrades
---

### Post by Coroney on 2008-01-01
Hi,

I don't have a (functioning) cd-rom drive in my computer that is running xubuntu 7.10 and it is a real problem to install packages whether through Synaptec or apt-get or aptitude since the first thing it always does is ask me to insert a cd-rom.

(I installed from the xubuntu alternate cd .iso file which I had downloaded onto another partition)

Does anyone know how I can set a source /  repository in Synaptec to the iso file.   

I assume I'll first need to first mount the .iso and then...  edit sources.list????   Is that correct?  and how would I go about doing that.

Also it'd be nice if I could make that a permanent situation so that I don't have to remount the iso every time I want to install a new app.


oh, and if this isn't possible, does anybody know a website repository I can go to to get the apps that are on the install cd?  I just want a few basic things like alien.

Thanks

---

### Post by richardjennings on 2008-01-01
if you want to use web based repositories rather than the cd, you can remove your ubuntu cd from the list of repositories in /etc/apt/sources.list

if you type ```
sudo gedit /etc/apt/sources.list
``` in a terminal window, gedit will open the sources.list file that configures apt and synaptics use of repositories. You should find a line that reads something like > deb cdrom:[Ubuntu  ........ near the top. 

Putting a hash symbol infront of this line 'comments' out the repository, effectively making apt and synaptic ignore. Its good practise to comment out lines instead of deleting them in case you want to reverse your actions at some future point.

Should look like this: > #deb cdrom:[Ubuntu  ........

save the file. 
open a terminal. 
type in ```
sudo apt-get update
```

apt should update its list of packages from the repositories in your sources.list file.


If you still want to mount a cd image and add it with apt-cdrom, there is a thread about it here:
[http://www.debianhelp.org/node/10486](http://www.debianhelp.org/node/10486)

---

### Post by forestpixie on 2008-01-01
and check while you're in there that all the repos are not commented out with #

once you've got the repos sorted you won't need the iso

---

### Post by Coroney on 2008-01-01
Thanks, it's workin now.  Actually I had done all that before, but I guess I needed to reboot for it to work for some reason.

---

