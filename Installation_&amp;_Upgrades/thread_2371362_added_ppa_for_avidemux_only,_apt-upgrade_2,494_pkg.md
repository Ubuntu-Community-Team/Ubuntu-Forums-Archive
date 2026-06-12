---
title: "added ppa for avidemux only, apt-upgrade 2,494 pkgs??"
date: 2017-09-13
forum: Installation &amp; Upgrades
---

### Post by ubuntubrian on 2017-09-13
I know PPAs can be dicey but I want to run avidemux in 16.04, for which it does not exist. I had avidemux from earlier versions but they didn't function so I removed everything avidemux then added this PPA: ```
sudo add-apt-repository ppa:mc3man/avidemux1
```
PPA was added, apt-update all good then on ```
sudo apt-get upgrade
``` I got about 1500 pkgs to be held back and 2,494 to upgrade or 1.17 Gigs! I run the software updater every time it requests an upgrade and did this morning. The PPA is pkg specific. I guess I could remove the PPA and try an upgrade command and see if I get the same result........

Yep! So sorry about the length of this but perhaps there's something in the re that will help figure this out. I do know that there are some backports from Zenity but their in the software sources choices, not me adding them separately:

Many advance thanks!  

[https://paste.ubuntu.com/25531000/](https://paste.ubuntu.com/25531000/)

---

### Post by vasa1 on 2017-09-14
Your pastebin indicates that you have a pretty vast system with a mix of gnome and unity! I hope you don't do anything before mc4man comes around to guide you.

---

### Post by ajgreeny on 2017-09-14
Let's see your sources.list file ```
cat /etc/apt/sources.list
``` and the content of /etc/apt/sources.list.d ```
ls -l /etc/apt/sources.list.d
```

---

### Post by vasa1 on 2017-09-14
howefield posted a nice one-liner which I modified a bit:```
grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

I would be interested in seeing the output of```
ls /usr/share/xsessions
```as well.

---

### Post by ubuntubrian on 2017-09-14
I am bad, bad. I know that my sources have been a mess for quite a while and ignored it as upgrades seemed to work fine. Now I am paying the price of poor maintenance. Please be gentle....

As pre ajgreeny:
[https://paste.ubuntu.com/25534199/](https://paste.ubuntu.com/25534199/)

[https://paste.ubuntu.com/25534261/](https://paste.ubuntu.com/25534261/)

And vasa1:

```
~$ ls /usr/share/xsessions
cairo-dock.desktop                LXDE.desktop
gnome-classic.desktop             openbox.desktop
gnome.desktop                     ubuntu.desktop
gnome-flashback-compiz.desktop    xfce.desktop
gnome-flashback-metacity.desktop  xubuntu.desktop
```

Sorry about the double output for you both but seemed easier. Gotta run for a while but I'm very thankful!!

---

### Post by ubuntubrian on 2017-09-14
I should go into my sources and do some serious housecleaning but as I wrote, I have done many update/upgrades and never had this happen. I just removed all avidemux pkgs. with synaptic, added the ppa, updated and installed avidemux. Anyway......

And to vasa1 nice little ditty:

[https://paste.ubuntu.com/25535810/](https://paste.ubuntu.com/25535810/)

---

### Post by ubuntubrian on 2017-09-14
really sorry about the double post! I was checking /etc/apt/sources and see that I have zesty repos in there. I didn't add anything zesty nor backports. Obviously I did something, or there is a ghost in the machine, but that could explain a lot of this issue. I now it's bad to mix versions unless it's specifically a backport. Yes?

---

### Post by ubuntubrian on 2017-09-14
and that's what it was. I commented out zesty and an upgrade returns just 2 pkgs. Sorry for all the kerfuffle!

---

### Post by ajgreeny on 2017-09-15
You do have a problem with line 37 of sources.list which still has a repo for maverick enabled; I am very surprised that you do not see an error every time you update the packages list, or perhaps you do?
**deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner**

Delete this line if you see problems related to that; in fact, delete it even if you don't have any errors showing.

And Oh Boy!! That list you show of files in /etc/apt/sources.list.d is the biggest and messiest I have ever seen in my 12 years of using Ubuntu, and definitely needs cleaning up; again you have several lines relating to karmic, maverick, oneric, precise, utopic, vivid and wily repos there, none of which are of any use to you and should be removed by whatever means you prefer, cli or GUI.

---

### Post by ubuntubrian on 2017-09-15
Thanks for the reply. Yeah, I knew it was a mess but I just let things be as they mostly worked OK. My bad and I own it. But at least I gave you something that you haven't seen in 12 years so no boredom, I guess! Just a joke but the truth-yikes.

I looked at the list with gedit and it's not a text file but a list of separate files as text documents. what's the easiest way? 
Really appreciate the help-really

---

### Post by ubuntubrian on 2017-09-15
After a big clean-up. I never meant for all those repos to be there. I guess it's just years of upgrades? See how this looks now. And many thanks!
```
~$ grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/*
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial universe
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates restricted multiverse main universe
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial-backports restricted multiverse main universe
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu/ xenial-security universe main restricted multiverse
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial-proposed universe main restricted multiverse
/etc/apt/sources.list.d/cairo-dock-team-ubuntu-ppa-xenial.list:deb http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu xenial main
/etc/apt/sources.list.d/cairo-dock-team-ubuntu-ppa-xenial.list.save:deb http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu xenial main
/etc/apt/sources.list.d/canonical_partner.list:deb http://archive.canonical.com/ xenial partner
/etc/apt/sources.list.d/canonical_partner.list.save:deb http://archive.canonical.com/ xenial partner
/etc/apt/sources.list.d/dhor-ubuntu-myway-xenial.list:deb http://ppa.launchpad.net/dhor/myway/ubuntu xenial main
/etc/apt/sources.list.d/dhor-ubuntu-myway-xenial.list.save:deb http://ppa.launchpad.net/dhor/myway/ubuntu xenial main
/etc/apt/sources.list.d/getdeb.list:deb http://archive.getdeb.net/ubuntu xenial-getdeb apps
/etc/apt/sources.list.d/getdeb.list.save:deb http://archive.getdeb.net/ubuntu xenial-getdeb apps
/etc/apt/sources.list.d/google-chrome.list:deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/google-chrome.list.distUpgrade:deb http://dl.google.com/linux/chrome/deb/ stable main # disabled on upgrade to vivid
/etc/apt/sources.list.d/google-chrome.list.save:deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/google-earth.list:deb http://dl.google.com/linux/earth/deb/ stable main
/etc/apt/sources.list.d/google-earth.list.distUpgrade:deb http://dl.google.com/linux/earth/deb/ stable main
/etc/apt/sources.list.d/google-earth.list.save:deb http://dl.google.com/linux/earth/deb/ stable main
/etc/apt/sources.list.d/google-talkplugin.list:deb http://dl.google.com/linux/talkplugin/deb/ stable main # disabled on upgrade to xenial
/etc/apt/sources.list.d/google-talkplugin.list.distUpgrade:deb http://dl.google.com/linux/talkplugin/deb/ stable main
/etc/apt/sources.list.d/google-talkplugin.list.save:deb http://dl.google.com/linux/talkplugin/deb/ stable main # disabled on upgrade to xenial
/etc/apt/sources.list.d/playonlinux.list:deb http://deb.playonlinux.com/ utopic main # disabled on upgrade to natty disabled on upgrade to oneiric disabled on upgrade to precise disabled on upgrade to quantal disabled on upgrade to saucy disabled on upgrade to trusty disabled on upgrade to utopic disabled on upgrade to wily disabled on upgrade to xenial
/etc/apt/sources.list.d/playonlinux.list.save:deb http://deb.playonlinux.com/ utopic main # disabled on upgrade to natty disabled on upgrade to oneiric disabled on upgrade to precise disabled on upgrade to quantal disabled on upgrade to saucy disabled on upgrade to trusty disabled on upgrade to utopic disabled on upgrade to wily disabled on upgrade to xenial
/etc/apt/sources.list.d/skype-stable.list:deb [arch=amd64] https://repo.skype.com/deb stable main
/etc/apt/sources.list.d/skype-stable.list.save:deb [arch=amd64] https://repo.skype.com/deb stable main
/etc/apt/sources.list.d/stebbins-ubuntu-handbrake-releases-xenial.list:deb http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu xenial main
/etc/apt/sources.list.d/stebbins-ubuntu-handbrake-releases-xenial.list.save:deb http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu xenial main
/etc/apt/sources.list.d/vivaldi.list.distUpgrade:deb http://repo.vivaldi.com/stable/deb/ stable main
/etc/apt/sources.list.d/wine-ubuntu-wine-builds-xenial.list:deb http://ppa.launchpad.net/wine/wine-builds/ubuntu xenial main
/etc/apt/sources.list.d/wine-ubuntu-wine-builds-xenial.list.save:deb http://ppa.launchpad.net/wine/wine-builds/ubuntu xenial main
/etc/apt/sources.list.d/xenial-partner.list:deb http://archive.canonical.com/ubuntu xenial partner
/etc/apt/sources.list.d/xenial-partner.list.save:deb http://archive.canonical.com/ubuntu xenial partner
/etc/apt/sources.list.d/yorba-ubuntu-ppa-xenial.list.save:deb http://ppa.launchpad.net/yorba/ppa/ubuntu xenial main
```

---

### Post by ajgreeny on 2017-09-16
That looks a lot better now as at least everything is for xenial.

There are a lot of repos there that I do not use nor know about but if you can run ***sudo apt update*** with no errors or warnings all must be OK with the sources.

---

### Post by ubuntubrian on 2017-09-16
Thanks again! I have really diminished the issue but have some remaining loose ends. I can run an update but I do get an errors. Nothing seems effected operating-wise though. It seems that sources are in at least 4 locations and I've looked for the offending ones
```
W: The repository 'http://deb.playonlinux.com utopic Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://deb.playonlinux.com/dists/utopic/main/binary-amd64/Packages  404  Not Found [IP: 51.254.83.230 80]
E: Failed to fetch http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu/dists/xenial/main/binary-amd64/Packages  404  Not Found
E: Failed to fetch http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/dists/xenial/main/source/Sources  404  Not Found
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/xenial-proposed/restricted/dep11/Components-amd64.yml  Could not open file /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_xenial-proposed_restricted_dep11_Components-amd64.yml.gz - open (13: Permission denied) [IP: 91.189.91.26 80]
E: Some index files failed to download. They have been ignored, or old ones used instead.
```
I have searched for those that  ```
.....does not have a Release file
```
to no avail.
I don't know why this happens but the file is self generating as I renamed it and another one was created on an update:
```
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/xenial-proposed/restricted/dep11/Components-amd64.yml  Could not open file /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_xenial-proposed_restricted_dep11_Components-amd64.yml.gz - open (13: Permission denied) [IP: 91.189.91.26 80]
```
I removed many pkgs and archives not xenial from and /var/lib/apt/lists.partial and here is the contents of var/lib/lists lots of zesty but why? Got me!
[https://paste.ubuntu.com/25549465/](https://paste.ubuntu.com/25549465/)

---

### Post by oldos2er on 2017-09-17
I'd remove all the PPAs that show a 404, since they likely don't exist anymore. Once you've done that please post the output from *sudo apt update* again.

---

### Post by ubuntubrian on 2017-09-17
That's the problem, I can't find them to delete them. I've searched in software sources GUI, sources.list, sources.list.d, var/lib/apt/lists and list/partial. I've deleted everything not xenial but cant' find the 404 offending sources. any ideas of how to search for them? Whereis returns nothing nor does searching with nautilus.

thanks again for all of the help. We've managed to whittle this monster down to size!

---

### Post by ubuntubrian on 2017-09-17
I found the ppas and commented them out. Still these pop up and as I wrote earlier in the thread they seem to be self-generating as deleting them doesn't work. they keep showing up:

```
Reading package lists... Done
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/xenial-proposed/restricted/dep11/Components-amd64.yml  Could not open file /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_xenial-proposed_restricted_dep11_Components-amd64.yml.gz - open (13: Permission denied) [IP: 91.189.91.26 80]
E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by oldos2er on 2017-09-17
Try ```
sudo rm /var/lib/apt/lists/partial/*

sudo apt update
```

---

### Post by ubuntubrian on 2017-09-17
There are many items in there:
[https://paste.ubuntu.com/25559679/](https://paste.ubuntu.com/25559679/)

Is it good to rm all of them as the command would do?

---

### Post by oldos2er on 2017-09-17
Normally there's nothing in partial. And running sudo apt update refreshes your sources list at any rate. 

Just out of curiosity, what are the dates on those files? Run ll (two letter "ells") rather than ls.

---

### Post by ubuntubrian on 2017-09-17
thanks for putting in the effort. running ll returns "command not found" but "ls -l" returns the dates. Looks like 3 "events". so does this mean that there were partial pkgs. downloaded? If they are completely unnecessary I can run your previous command and delete the contents, if that is your advice.
the output: [https://paste.ubuntu.com/25560812/](https://paste.ubuntu.com/25560812/)

---

### Post by oldos2er on 2017-09-17
Yes, that's my advice. Let us know how it goes.

---

### Post by ubuntubrian on 2017-09-17
Clean as a whistle now! Had to mod the command a titch but partial is now empty and here's the out put from an update:

```
Fetched 2,171 kB in 30s (72.3 kB/s)                                            
Reading package lists... Done
```

Now that's gotta help my poor little ubuntu box!

Thanks again and long live OS2!    :D

---

### Post by oldos2er on 2017-09-17
OS/2 is dead, long live OS/2. 

Glad you're good to go now.

---

