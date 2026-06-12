---
title: "PLEASE HELP....how to install bittorrent in ubuntu 8.04 LTS AND A FEW QUESTIONS?"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by neerajkumar on 2008-05-25
hello...
i am complete beginner.
i just installed ubuntu 8.04 LTS TODAY MORNING AND LOST all the data in ma hard disk as it got formatted.
i have alot about linux and its broad features.
thats the main reason i switched to linux.
anyway i hav a lott of questions regardin the use of ubuntu.
1st question
i downloaded bittorrent from [http://download.bittorrent.com/dl/Bi...t-5.2.0.tar.gz](http://download.bittorrent.com/dl/Bi...t-5.2.0.tar.gz)

i donno hw to install it?
could u plz help me?

2nd question
can i dual boot to windows vista if i install one and create new partitions as now i hav solely a single drive called file system?

3rd question
could i get a site where i could get the shorcuts and basic commands of ubuntu?

4th question
which are the best and the important softwares to be installed while using ubuntu?

5th question
which are the best media players for ubuntu?

6th question
i have a nvidia 8500 GT graphics card.
after installing the driver am not able to keep a resolution more than 1024x768.
earlier i could keep 1280x1024.

please help me.i am totally stuck up with these questions.

---

### Post by Maz7006 on 2008-05-25
As for the media players use either vlc mediaplayer, amarok or Rhythmbox. Rhythmbox comes installed with ubuntu but in my opinion vlc is the best. As for basic commands use [www.google.com](www.google.com) to find them... there are a ton of things... and if i were you dont use bittorrent use deluge whicg is much more better.

---

### Post by neerajkumar on 2008-05-25
> **Maz7006 said:**
> As for the media players use either vlc mediaplayer, amarok or Rhythmbox. Rhythmbox comes installed with ubuntu but in my opinion vlc is the best. As for basic commands use [www.google.com](www.google.com) to find them... there are a ton of things... and if i were you dont use bittorrent use deluge whicg is much more better.

hey.
thanx a ton.
but could u please tel me the basic softwares that should be installed?
like any necessary antivirus softwares?

---

### Post by phoenix_abhi on 2008-05-25
1. For a torrent client, Transmission is default in Ubuntu 8.04 and better than others. I am terminal user. u can too. type in terminal.
sudo apt-get install bittorrent

2. Yes you can. After installing u have to reload the grub to boot into Ubuntu

3. There are a lot just Google it.here too there is a lot url available

4. There is a beginners thread started my be in this forum. You will get 99 % help and applications from there.

[http://ubuntuforums.org/showthread.php?t=801684](http://ubuntuforums.org/showthread.php?t=801684)

do not forget to leave ur remarks in the thread

5. Amrok. VLC is a good one too. But little bit sound distortion experienced in large speakers

6. I dn not know. I have intel and no problems :)

:lolflag:

---

### Post by FuturePilot on 2008-05-25
No antivirus is needed. For more on security have a look here
[http://www.psychocats.net/ubuntu/security]("http://www.psychocats.net/ubuntu/security")

For Bittorrent, Ubuntu comes with a bittorrent client already installed called Transmission. Have a look under Applications&#8594;Internet

For the resolution issue, install nvidia-settings
```
sudo apt-get install nvidia-settings
```
Then run
```
gksudo nvidia-settings
```
And you can adjust your resolution from there. Don't forget to save it to the X Configuration File so your settings stay.

---

### Post by neerajkumar on 2008-05-25
> **phoenix_abhi said:**
> 1. For a torrent client, Transmission is default in Ubuntu 8.04 and better than others. I am terminal user. u can too. type in terminal.
sudo apt-get install bittorrent

2. Yes you can. After installing u have to reload the grub to boot into Ubuntu

3. There are a lot just Google it.here too there is a lot url available

4. There is a beginners thread started my be in this forum. You will get 99 % help and applications from there.

[http://ubuntuforums.org/showthread.php?t=801684](http://ubuntuforums.org/showthread.php?t=801684)

do not forget to leave ur remarks in the thread

5. Amrok. VLC is a good one too. But little bit sound distortion experienced in large speakers

6. I dn not know. I have intel and no problems :)

:lolflag:

hey thanx a lot buddy..
that was really helpful.
1 more question..hw do i reload the grub to boot?

---

### Post by neerajkumar on 2008-05-25
> **FuturePilot said:**
> No antivirus is needed. For more on security have a look here
[http://www.psychocats.net/ubuntu/security]("http://www.psychocats.net/ubuntu/security")

For Bittorrent, Ubuntu comes with a bittorrent client already installed called Transmission. Have a look under Applications&#8594;Internet

For the resolution issue, install nvidia-settings
```
sudo apt-get install nvidia-settings
```
Then run
```
gksudo nvidia-settings
```
And you can adjust your resolution from there. Don't forget to save it to the X Configuration File so your settings stay.

hi..
thanx buddy...
i have been messing up the resolution stuff from morning..
thanx a lott....
it worked..:)

---

### Post by phoenix_abhi on 2008-05-25
> **neerajkumar said:**
> hey thanx a lot buddy..
that was really helpful.
1 more question..hw do i reload the grub to boot?

Welcome to the Ubuntu world man,

Considering that u have installed both OS
First Ubuntu and then Vista
Now Put ur Ubuntu Live CD in and reboot.
Go to the terminal and type
[COLOR="Blue"]sudo grub
find /boot/grub/stage1[/COLOR]
this will show which is ur Linux partition

[COLOR="Blue"]grub> root (hd0,1)
grub> setup (hd0)
grub> quit
[/COLOR]
reboot ur Grub is reloaded

The hd0 is the number of hardisk u have. If only one it is 0
(hd0,1) the 1 here is ur linux partition

:guitar:

---

### Post by neerajkumar on 2008-05-25
> **phoenix_abhi said:**
> Welcome to the Ubuntu world man,

Considering that u have installed both OS
First Ubuntu and then Vista
Now Put ur Ubuntu Live CD in and reboot.
Go to the terminal and type
[COLOR="Blue"]sudo grub
find /boot/grub/stage1[/COLOR]
this will show which is ur Linux partition

[COLOR="Blue"]grub> root (hd0,1)
grub> setup (hd0)
grub> quit
[/COLOR]
reboot ur Grub is reloaded

The hd0 is the number of hardisk u have. If only one it is 0
(hd0,1) the 1 here is ur linux partition

:guitar:

heyy..than you so much..
yea...am a total beginner...
i have been using windows for so long that i just know the word linux..
nothing more..
i hope to learn linux in depth nw..
its pretyy interesting...:)

---

### Post by neerajkumar on 2008-05-25
can someone tel me a gud audio video converter?
i need to compress ma mp3 songs..
so is der a mp3 compressor?

---

### Post by neerajkumar on 2008-05-26
i hav a new problem.
my screen crashes after using ma pc for awhile.
i use a nvidia 8500GT graphicss card.
is tere any solution to prevent these crashes?

---

### Post by neerajkumar on 2008-05-26
a new problem.

i downloaded a file kylixlibs3-borqt-3.0-2.tar.gz.
in the readme it says "Just run install.sh as root in order to install these Kylix 3
libraries.

Step by step:
1. > su
2. enter root password
3. # ./install.sh
4. # exit


You can find the latest version of this package at [http://kylixlibs.sf.net/](http://kylixlibs.sf.net/)

These libraries are distributed under GPL, you can read license terms at
[http://www.gnu.org/licenses/gpl.html](http://www.gnu.org/licenses/gpl.html)

-- 
Linas Jakucionis Brovienas <brovienas@mailsurf.com>"
i hav no idea what this is,\.
when i tried to run ./install.sh in terminal it said no such file or directory.
i am stuk up here. can someone help me?

---

### Post by neerajkumar on 2008-05-26
after installing ubuntu 8.04 LTS many of ma DVD's r not being read?
can somebody help me?

---

### Post by oldos2er on 2008-05-26
Installing programs: please read [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

 For DVDs: please read [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by neerajkumar on 2008-05-28
> **oldos2er said:**
> Installing programs: please read [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

 For DVDs: please read [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

i did try these..
but still no use.:(

---

