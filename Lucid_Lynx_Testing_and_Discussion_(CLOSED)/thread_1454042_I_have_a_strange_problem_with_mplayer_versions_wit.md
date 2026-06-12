---
title: "I have a strange problem with mplayer versions with lucid"
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-04-14
the version i currently have is 2:1.0~rc3+svn20090426-1ubuntu16 but i can see here:
[https://launchpad.net/~rvm/+archive/mplayer]("https://launchpad.net/%7Ervm/+archive/mplayer")

that there are newer version for karmic and etc                                 2:1.0~rc3+svn20090904 and there is still no ppa for lucid why do we still use 426 and how 
can i get the latest version now?

i downloaded the svn source from here:
[http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)

but i'm not sure how to compile it now.

the same goes for mencoder versoin 426

thanks in advance.

IMPORTANT:
updated version can be found here:
[https://launchpad.net/~rvm/+archive/testing/]("https://launchpad.net/%7Ervm/+archive/testing/")

---

### Post by wilee-nilee on 2010-04-14
smplayer which uses mplayer has a ppa that has lucid, not sure of the versions you will have to check.
[https://launchpad.net/~rvm/+archive/smplayer](https://launchpad.net/~rvm/+archive/smplayer)

---

### Post by aviramof on 2010-04-14
i have a diffrent problem now i manage to compile mplayer or at least i think i do this is what i get when i write mplayer in terminal
MPlayer SVN-r31036-4.4.3 (C) 2000-2010 MPlayer Team

now i'm trying to do this:
Unpack the archive and put the contents in /usr/local/share/mplayer/skins/ or
~/.mplayer/skins/. MPlayer will use the skin in the subdirectory named default
of /usr/local/share/mplayer/skins/ or ~/.mplayer/skins/ unless told otherwise
via the '-skin' switch. You should therefore rename your skin subdirectory or
make a suitable symbolic link.

my problem is putting the contents in /usr/local/share/mplayer/skins/ 

it seem that i don't have permissions despite the fact that i'm the computer administrator
i'v noticed it before every folder there said that i'm not the owner so how can enter as root so i could copy things to there.

thanks in advance.

i don't understand this i managed to copy the files and it said that the files is unredable.

---

### Post by aviramof on 2010-04-14
and by the way why doesn't the main repositories doesn't have smplayer                                               0.6.9-1~lucid1?

it has an older version and the current version wasn't exactly released today.

---

### Post by Stason on 2010-04-23
I have upgraded from beta1 to RC and got mplayer version warning exactly as described in this thread, but synaptic does not have a newer mplayer version - any way to add it to synaptic?

---

### Post by aviramof on 2010-04-23
add rvm ppa and download it from there you can google it or just download the deb file from the same place.
 
but they do need to update the reposetories with it.

---

### Post by cariboo on 2010-04-23
May I ask, what's wrong with the version in the repositories? Is it a matter of a must have feature in the latest version?

I've been using the version in the repository quite extensively for
transcoding avi files, and I haven't run into any problems.

---

### Post by Starks on 2010-04-23
90% of serious mplayer development and packaging is now occurring on the mplayer-build tree, not the mplayer trunk.

Given that the repository versions still use mplayer trunk, there are huge problems.

---

### Post by rvm4000 on 2010-04-23
I uploaded recently a mplayer build for lucid (2:1.0~rc3+svn20100416) to this PPA:

[https://launchpad.net/~rvm/+archive/testing/](https://launchpad.net/~rvm/+archive/testing/)

---

### Post by Starks on 2010-04-23
rvm, are your packages mt and vdpau compatible?

---

### Post by rvm4000 on 2010-04-23
The package 2:1.0~rc3+svn20100416-0lucid3 has support for vdau, but this is the normal version, so it's not multi-threaded.

---

### Post by Starks on 2010-04-23
Not to be rude, but I'd like to put on the table a PPA that has multithreaded, VDPAU, mplayer git current, and CoreAVC-ready builds of mplayer.

[https://launchpad.net/~ripps818/+archive/coreavc]("https://launchpad.net/%7Eripps818/+archive/coreavc")

---

### Post by Luke has no name on 2010-04-23
> **rvm4000 said:**
> I uploaded recently a mplayer build for lucid (2:1.0~rc3+svn20100416) to this PPA:

[https://launchpad.net/~rvm/+archive/testing/](https://launchpad.net/~rvm/+archive/testing/)

I'm trying to use your repo but I still get the CPU crunching my hi-def movies.

I installed your PPA, updated mplayer and smplayer, and set 'vdpau' as the output driver for video. When I try to play a hi-def movie (720p or higher mkv) it doesn't load the movie at all. When the output driver is xv, the CPU decodes it.

I have a 9500GT with nvidia-current drivers enabled. I got VDPAU working on Karmic using the PPA in link [1] below, but I forget exactly what settings were needed, or console switches added to the mplayer command.

Could you tell me exactly what I should have to do and adjust to get VDPAU working?

[1]: [https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

---

### Post by aviramof on 2010-04-24
> **cariboo907 said:**
> May I ask, what's wrong with the version in the repositories? Is it a matter of a must have feature in the latest version?

I've been using the version in the repository quite extensively for
transcoding avi files, and I haven't run into any problems.

i had one major with the repositories version and hebrew translations been reverse you can search for my previous thread on the matter.

---

### Post by Starks on 2010-04-24
> **Luke has no name said:**
> I'm trying to use your repo but I still get the CPU crunching my hi-def movies.

I installed your PPA, updated mplayer and smplayer, and set 'vdpau' as the output driver for video. When I try to play a hi-def movie (720p or higher mkv) it doesn't load the movie at all. When the output driver is xv, the CPU decodes it.

I have a 9500GT with nvidia-current drivers enabled. I got VDPAU working on Karmic using the PPA in link [1] below, but I forget exactly what settings were needed, or console switches added to the mplayer command.

Could you tell me exactly what I should have to do and adjust to get VDPAU working?

[1]: [https://launchpad.net/~nvidia-vdpau/+archive/ppa]("https://launchpad.net/%7Envidia-vdpau/+archive/ppa")
Try the PPA I linked and make sure you have libvdpau installed.

---

### Post by rvm4000 on 2010-04-24
> **Luke has no name said:**
> I'm trying to use your repo but I still get the CPU crunching my hi-def movies.

I installed your PPA, updated mplayer and smplayer, and set 'vdpau' as the output driver for video. When I try to play a hi-def movie (720p or higher mkv) it doesn't load the movie at all. 

Probably the reason why it didn't load the movie will be in the mplayer log (options -> view logs).

---

### Post by Luke has no name on 2010-04-24
> **Starks said:**
> Try the PPA I linked and make sure you have libvdpau installed.

I don't know if the other one would have worked, but yours does just fine. Even after I installed the PPA, I couldn't get anything to work right. I just completely removed all mplayer/smplayer/vdpau stuff, and reinstalled smplayer. That brought everything in, and now it's working well.

---

