---
title: "Sound &amp; apt-get problem in Gutsy"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by spyderbilt on 2007-11-14
Hi all. 

I am having problem with sound running Gutsy on Dell D830. Prior to this I've had little (near zero) experience with non-windows environment so pardon me if any of my questions is absurdly trivial. 

sudo lshw -C sound gives me : 
>   *-multimedia UNCLAIMED  
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0


I'm not sure what is the problem exactly but after searching I decided to try my luck and try to follow the steps described in [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

After running the first command (apt-get install build-essential ncurses-dev gettext) this is what I get : 
> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
Note, selecting libncurses5-dev instead of ncurses-dev
The following packages were automatically installed and are no longer required:
  libdc1394-13-dev libdc1394-13 libtheora-dev mesa-common-dev libogg-dev
  libglu1-mesa-dev libraw1394-dev libgsm1 libgl1-mesa-dev libgsm1-dev
  libvorbis-dev
Use 'apt-get autoremove' to remove them.
Suggested packages:
  gettext-doc
The following NEW packages will be installed:
  gettext libncurses5-dev
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 3009kB of archives.
After unpacking 12.9MB of additional disk space will be used.
Get:1 [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) gutsy/main gettext 0.16.1-2ubuntu3 [1552kB]
Get:2 [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) gutsy/main gettext 0.16.1-2ubuntu3 [1552kB] 
Get:3 [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) gutsy/main gettext 0.16.1-2ubuntu3 [1552kB] 
Get:4 [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) gutsy/main gettext 0.16.1-2ubuntu3 [1552kB] 
Get:5 [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) gutsy/main gettext 0.16.1-2ubuntu3 [1552kB] 
Get:6 [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) gutsy/main gettext 0.16.1-2ubuntu3 [1552kB] 
Get:7 [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) gutsy/main gettext 0.16.1-2ubuntu3 [1552kB] 
Get:8 [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) gutsy/main gettext 0.16.1-2ubuntu3 [1552kB] 
Get:9 [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) gutsy/main gettext 0.16.1-2ubuntu3 [1552kB] 
Get:10 [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) gutsy/main gettext 0.16.1-2ubuntu3 [1552kB]
Get:11 [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) gutsy/main gettext 0.16.1-2ubuntu3 [1552kB]
Get:12 [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) gutsy/main gettext 0.16.1-2ubuntu3 [1552kB]
Get:13 [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) gutsy/main gettext 0.16.1-2ubuntu3 [1552kB]
Get:14 [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) gutsy/main gettext 0.16.1-2ubuntu3 [1552kB]
Get:15 [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) gutsy/main gettext 0.16.1-2ubuntu3 [1552kB]
Get:16 [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) gutsy/main gettext 0.16.1-2ubuntu3 [1552kB]
Get:17 [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) gutsy/main gettext 0.16.1-2ubuntu3 [1552kB]
Get:18 [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) gutsy/main gettext 0.16.1-2ubuntu3 [1552kB]
Get:19 [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) gutsy/main gettext 0.16.1-2ubuntu3 [1552kB]
Get:20 [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) gutsy/main gettext 0.16.1-2ubuntu3 [1552kB]
Get:21 [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) gutsy/main gettext 0.16.1-2ubuntu3 [1552kB]
Get:22 [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) gutsy/main gettext 0.16.1-2ubuntu3 [1552kB]
Get:23 [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) gutsy/main gettext 0.16.1-2ubuntu3 [1552kB]


It seems to me that downloading of the file never gets completed and it repeatedly try download the same file (the download indicator at the bottom never goes beyond 24% and it moves on to the next line. Is there another repository I can point to ? I am pretty sure my internet connection is alright because other downloads do not have the same problem. 

Can anyone tell me whether I'm going in the right direction and how do I resolve the apt-get download issue (I noticed that the problem happens when use the UI for add/remove as well)? Any help would be greatly appreciated.

---

### Post by anjoze on 2007-11-26
I just instaled Ubuntu 7.10 on my Dell Latitude D830 and then:
sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

Reboot computer and it's perfect

---

### Post by dustman on 2007-11-27
> **anjoze said:**
> I just instaled Ubuntu 7.10 on my Dell Latitude D830 and then:
sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

Reboot computer and it's perfect

this didn't work for me :(

---

