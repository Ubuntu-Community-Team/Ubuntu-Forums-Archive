---
title: "Any good Ani-Virus software for Breezy ???"
date: 2005-11-10
forum: Installation &amp; Upgrades
---

### Post by jmejedi on 2005-11-10
What would be a good anti-virus software for my Ubuntu Breezy laptop (Dell 700m) ??? One that is feel, preferable.

Thank you for your time,

---

### Post by Sykil on 2005-11-10
The only antivirus that I even know of for Linux is clamav, installable via
```
sudo apt-get install clamav
```

Edit:  I found some more info on the wiki: [https://wiki.ubuntu.com/ClamAV](https://wiki.ubuntu.com/ClamAV)

Also, I found out about another, Panda Antivirus: [https://wiki.ubuntu.com/PandaAntivirus](https://wiki.ubuntu.com/PandaAntivirus) --- but I'm unsure about this one.

---

### Post by LinuxWiz83 on 2005-12-05
Panda Antivirus is the best out of the two. I have tryed both and i can say ClamAV is too bugy and Panda runs flawless.

[http://www.pandasoftware.com/download/linux.htm](http://www.pandasoftware.com/download/linux.htm)

---

### Post by john_c on 2005-12-06
I use f-protect to do a regular scan of my system.  It is available at:

[http://www.f-prot.com/download/home_user/download_fplinux.html](http://www.f-prot.com/download/home_user/download_fplinux.html)

It works well and has never caused any problems with the system.  I have a short bash script that checks for updates, downloads them and then scans the system.

John_c

---

### Post by kosmic on 2005-12-06
Linux does not need antivirus, The antivirus you install in linux is to scan Window$ drives, if you only run a Linux distro (ubuntu etc...) you don't need an antivirus :)

---

### Post by frodon on 2005-12-06
I agree, no need of an anti-virus at all !

If you don't have a local network containing windows PC you won't need an anti-virus. Generally anti-virus are used to scan windows drives or files before sending them to a windows PC.

---

### Post by john_c on 2005-12-06
It is my understanding that there is a potential for an email attachment such as a Word document to contain a virus.  Thus if I was to receive one of these and forward it on it could effect the windows system of the person receiving it from me.  I know that it is extremely unlikely to effect my linux system but am also concerned about someone else receiving an infected file from me (via email or perhaps on a cd or diskette).

The vast majority of the people that I deal with (business and personal) are using a windows operating system and I just can't take a chance of passing something on to them.

Perhaps someone can expand on this.

Thank you,

John_c

---

### Post by mike4ubuntu on 2005-12-08
ClamAV is really basic.  I'm not convinced it really does a very good job of detecting viruses.  I had to download the 0.87.1 source version and compile it since apt-get only had the 0.87 version, and freshclam complained about it being incompatible with virus definition database.  I'm not sure I have clamd configured properly yet, because it complains about "Access denied. ERROR" issues.  However, clamscan was able to scan ok.

I also noticed that an antivirus program called Aegis was available in the "Add Programs" applet.  I thinking about loading this program up and trying it.  Does anybody have experience with this?

I'm also going to take a look at f-prot.  It's free for linux home user.s

---

### Post by ogregore on 2005-12-08
I have had Aegis on my laptop for a few weeks, updated virus definitions a couple of times.  Since I don't really know if the scans are actually looking or finding anything I can't really say  if it is a "good" anti-virus utility or not.

I feel comfortable with it because it has a fairly easy to use interface and allows me to select the directory or directories I want to scan, so I can regularly scan my T-Bird email folders and it doesn't take a lot of time.

Cheers
Ogre

---

### Post by knobcottage on 2005-12-08
I'm new to linux but the folks that I get my free windows av from do a linux version do a free linux version.  You have to ask for a code but they give it free, part of their service to the open source community.  I have never tried the linux version but the windows version is real good.  Linux version was last here

[http://free-av.com/personal/en/unix/antivir-workstation-pers.tar.gz](http://free-av.com/personal/en/unix/antivir-workstation-pers.tar.gz)

try it and see

---

### Post by mike4ubuntu on 2005-12-12
I've had a chance to try Aegis.  The gui is simple, but usable.  However, it appears that it is flagging a lot of false-positives.  I verfied the false-positive files on a ntfs mounted partition with windows os using Norton AV and CA AV.  Has anybody else had the same experience with Aegis?

---

### Post by pizzach on 2005-12-12
Yup.  That is why I don't even touch aegis with a foot long stick now.  I used clamav to check my windows partition after neutering it's internet connection.  I'm gonna be put'r down soon.

---

### Post by LinuxWiz83 on 2005-12-13
[QUOTE=kosmic]Linux does not need antivirus, The antivirus you install in linux is to scan Window$ drives, if you only run a Linux distro (ubuntu etc...) you don't need an antivirus :)[/QUOTE]

Although your pretty much right it is possible to get a virus on linux but only if your login through root and the virus i herd for linux and probably the only one is rootkit or something like that.

---

### Post by beameup on 2006-01-06
[QUOTE=LinuxWiz83]Panda Antivirus is the best out of the two. I have tryed both and i can say ClamAV is too bugy and Panda runs flawless.

[http://www.pandasoftware.com/download/linux.htm](http://www.pandasoftware.com/download/linux.htm)[/QUOTE]

Panda Antivirus for Linux is an antivirus for Linux servers and desktops. It is an antivirus designed to be managed from the command line or console. To do this, an executable called PAVCL will be used.

The aim of Panda Antivirus for Linux is to scan and disinfect Windows and DOS workstations connected to a Linux server, as well as the Linux server itself.

Panda Antivirus for Linux scans files using both string searches and heuristic methods. The target files of the antivirus are Word documents, Java Applets, ActiveX controls and compressed files (ZIP, RAR, etc.). At the moment, it does not scan the boot sector or the partitions table.

Still somewhat limited.

---

### Post by beameup on 2006-01-06
[QUOTE=knobcottage]I'm new to linux but the folks that I get my free windows av from do a linux version do a free linux version.  You have to ask for a code but they give it free, part of their service to the open source community.  I have never tried the linux version but the windows version is real good.  Linux version was last here

[http://free-av.com/personal/en/unix/antivir-workstation-pers.tar.gz](http://free-av.com/personal/en/unix/antivir-workstation-pers.tar.gz)

try it and see[/QUOTE]

Can't find much info onthe website and the linux forum has 0 posts. This just started maybe?

---

### Post by Dr. Blues on 2006-01-07
this seems to be a bit dated, but the openantivirus.org is still functioning:

[http://cvs.sourceforge.net/viewcvs.py/openantivirus/mini-faq/av-unix_e.txt?rev=HEAD](http://cvs.sourceforge.net/viewcvs.py/openantivirus/mini-faq/av-unix_e.txt?rev=HEAD)

most of the products mentioned above seem to be listed.

ciao...dr. blues

---

### Post by Bignut on 2007-07-19
Not sure if this was on Dr Blues' list or not coz I can't seem to get on the page, but Avast also does a linux version. [www.avast.com](www.avast.com)

---

