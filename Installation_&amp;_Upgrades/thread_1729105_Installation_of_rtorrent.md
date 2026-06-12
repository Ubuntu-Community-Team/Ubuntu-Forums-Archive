---
title: "Installation of rtorrent"
date: 2011-04-14
forum: Installation &amp; Upgrades
---

### Post by sandy0594 on 2011-04-14
I installed rtorrent..but,when i try to connect to it i am getting an error..Could someone explain the cause for this error

> 
sandy@ubuntu:~$ sudo apt-get install rtorrent
[sudo] password for sandy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libswt-cairo-gtk-3.5-jni libswt-gtk-3.5-jni liblog4j1.2-java
  libswt-mozilla-gtk-3.5-jni libcommons-cli-java libcommons-lang-java
  libswt-gnome-gtk-3.5-jni libswt-gtk-3.5-java java-wrappers
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  rtorrent
0 upgraded, 1 newly installed, 0 to remove and 8 not upgraded.
Need to get 0B/407kB of archives.
After this operation, 1,339kB of additional disk space will be used.
Selecting previously deselected package rtorrent.
(Reading database ... 157168 files and directories currently installed.)
Unpacking rtorrent (from .../rtorrent_0.8.6-1_i386.deb) ...
Processing triggers for man-db ...
Setting up rtorrent (0.8.6-1) ...
sandy@ubuntu:~$ rtorrent
rtorrent: Error in option file: ~/.rtorrent.rc:110: Could not prepare socket for listening: Address already in use



---

### Post by pyroscope on 2011-04-15
I guess it'd be a horrible idea to show us line 110 of ~/.rtorrent.rc...

---

### Post by sandy0594 on 2011-04-15
What should i do to get rid of that?

---

### Post by Enigmapond on 2011-04-15
Have you tried just opening it from the application/internet menu? Have you tried to download a torrent? If so, what happens?

---

### Post by sandy0594 on 2011-04-15
Just now somehow managed to get rid of the error message..But,when i navigate a file it's not downloading what could be the cause

```


                  *** rTorrent 0.8.6/0.12.6 - ubuntu:2477 ***
[View: main]




















(19:52:23) Tracker group list not a list
[Throttle off/off KB] [Rate   0.0/  0.0 KB] [Port: 6974] [U 0/0] [D 0/0] [H 0/3




```My file was **/media/18D80590D8056CF6/Documents and Settings/Sandy/My Documents/Downloads/[isoHunt] The.Curious.Case.Of.Benjamin.Button.2008.DvDRip-FxM.torrent**

---

### Post by sandy0594 on 2011-04-15
Why can't i see anything in the terminal even after i upload a file

In the first attachment as u see i am uploading a torrent file
In the second attachment as u see there is nothing going on and worst part is that i can't even see the file name

---

