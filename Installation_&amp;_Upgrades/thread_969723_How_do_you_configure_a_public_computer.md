---
title: "How do you configure a public computer?"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by brallan on 2008-11-03
I administer the computers in an ecological social center like a cybercafe but free with recycled desktops for public use, and I am curious about others who also administer public computers, what configurations and tricks you all use to set it up for public use, so I have created this thread for us to share our setups.... 

1) No multiuser. I have a single user and I keep the password to myself. 

2) Skip the logon screen in System > Administration > Login window > Security and enable a timed logon so users do not need a password even if someone logs off.

3)  Firefox - inside Preferences > Privacy 
  a) Always clear the private data when i close firefox
  b) Do not ask for confirmation
            - inside Preferences > Security
  c) Do not remember passwords for sites

4) to play dvds and mp3s and youtube videos:
```
sudo apt-get install ubuntu-restricted-extras flashplugin-nonfree
```

5) the quick and dirty way to display almost all unicode characters:
```
sudo apt-get install unifont
```

6) although i use ubuntu, there are some other apps many users prefer:
```
sudo apt-get install k3b kword abiword vlc
```

7) i install skype with the download from the website.

8) kopete for audio and video chat:
```
sudo apt-get install kopete
```

9) right-click on panel, add to panel: 
    a) disk-mounter applet 
    b) force misbehaving application to quit

10) I turn off all desktop effects, since most of my machines have less than half a gig of RAM.

11) I install samba and set up filesharing across the network.

I have yet to figure out a way to download one copy of an update from the repos for all the machines. instead, i just update them one-by-one.

---

### Post by charliebrownau on 2008-11-03
I would like to know the same . Interesting thread .

Ive got a community centre that needs help with a bunch of old free computers and was considering installing Ununtu on them . 
But I would like to lock them down and set them up with a certain amount of applications - eg Firefox with adblock and noscript , OpenOffice and Abiword , aMSN and Skype , DC++ client and an FTP client . Removal of un-wanted/un-needed languages programs/services . Installed multiple times over LAN . Local Based LAN apt-get install server instead of using DVDs or internet.

The same tutorial could be applied for office enviroment and schools

---

### Post by louieb on 2008-11-03
Use to see threads by a guy setting up computers in a public library. 
Don't seem to be any definitive guide. Lots of threads in the security section discuss setting up a public access  computer. Might want to search the security section. 
Believe the KDE desktop has a kiosk mode. There is Kiosk software around like [Open Kiosk  ]("http://openkiosk.sourceforge.net/")

Good Luck.

---

### Post by brallan on 2008-11-04
Its not a big place, and since there are not really a lot of machines (5 desktops, wifi, and a PAP2 voipbox), i've not got round to some kind of kiosk solution. At first, the idea that users don't even see whether its linux or windows seemed odd to me about openkiosk, For the moment, I want people to use the OS, see that its ubuntu and that it works great, so that they will be more courageous about having one less monopolistic corporation in their workspaces.

And then i thought about it. Although the idea of a cross-platform environment thats pretty much the same anywhere which sits on top of a mac a windows or a linux box and gives you a bunch of cross-platform open-source programs which do all of your usual tasks is kind of brilliant. Imagine plugging in a pen to any booted up computer windows, mac or linux even a cybercafe and executing a kiosk program and suddenly being in your own desktop environment anywhere! In any case, I doubt if open kiosk could do that, or else they would have called it cross platform desktop environment or something like that... but Ill check it out.

---

### Post by charliebrownau on 2008-11-12
Its a shame that Linux still to this day does not offer a program extaclty like Nlite for Linux . It would help in these sitations .

---

### Post by timcredible on 2008-11-12
if i were you, i'd look into using pxes to just connect to a central machine via xdmcp, that way you only have 1 machine to maintain instead of 5.

---

### Post by brallan on 2008-11-18
> **timcredible said:**
> if i were you, i'd look into using pxes to just connect to a central machine via xdmcp, that way you only have 1 machine to maintain instead of 5.

Thanks for the advice. If someday we get a box that's permanently up and running, i'll consider it. It might sound kind of  bizarre to most folks, but to us ecologists the idea of a machine on 24-7 is something we've shied away from. With xdmcp, what do you do if the server dies, do you then have some kind of disk image on the harddrives which is still usable?

brian

---

### Post by elianthony on 2008-12-02
Hi,

I have set up a few machines running Ubuntu in the public library. I did a write up of how I configured them, it can be found [**_[SIZE="3"][COLOR="Blue"]here[/COLOR][/SIZE]_**]("http://ubuntuforums.org/showthread.php?t=707688"). These machines have been performing pretty much perfectly ever since. Let me know if you have any questions.

Hope this helps.

---

### Post by brallan on 2009-06-30
now I am using apt-cacher to do updates. I am updating the first post to suit. 

PLEASE HELP ME RELOCATE THIS THREAD INTO THE TUTORIALS SECTION IF YOU ARE A FORUMS ADMIN OR KNOW HOW....

---

### Post by carolineictwiki on 2010-04-11
I've heard apt-cacher-ng to be much faster than apt-cacher (I'm just installing it myself, so I can't say for sure)

---

