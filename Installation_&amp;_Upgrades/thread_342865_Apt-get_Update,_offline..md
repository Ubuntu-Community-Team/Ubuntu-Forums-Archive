---
title: "Apt-get Update, offline."
date: 2007-01-20
forum: Installation &amp; Upgrades
---

### Post by Tokeli on 2007-01-20
Since my ubuntu-installed computer doesn't have an internet connection, is there a way to manually update the list of available packages, or is the only way with an internet connection through the apt-get update?

It's easier to download a program when one can simply try to get apt-get to install it, then download the packages that come up, than it is downloading every dependency for every dependency on the page.

---

### Post by arqbrulo on 2007-01-25
I agree. I recently freed my self from the chains of M$. I installed Ubuntu on my home PC (with dual boot with WinXP as default for my wife). But I don't have internet at home yet. I'm smart enough to see "http://whatever" on the code and download whatever I want to install, but I'm not smart enough to go home and install what I just downloaded. Most of the programs I download are either tar.gz or deb files, but I have managed to see others. I'm the sort of person who searches first before asking a question (I've been searching for 4 days now, with a bit of luck). So here's my question: Is there a way some of the "learn-ed" ones can post a HowTo to install offline tar.gz or deb or whatever else files for us newcomers? Thanks.

BTW, I've read other forums before (not related to Ubuntu), and I just like the way I see the replies here. Everybody really does treat each other as part of the community, something that I don't see as often as I wish at the other places.

---

### Post by airtonix on 2007-02-08
for a start .deb files cause the application "gdebi" to open when double cliked in gnome.

and usually you can learn how to install the program encased inside a "tar.gz" file by uncompressing as you would a zip file....after that look for the  "README" file....it usually tells you which software it depends on.

---

### Post by arqbrulo on 2007-02-16
That's fine, more than anything I was talking about the dependencies, or other files needed to install that one program that I want.

---

### Post by airtonix on 2007-03-01
ok sorry bout that compadre


yes this is totally do-able.

but the process happens with these progs:
 debmirror
 debpartial
 debcopy
 ruby (for debcopy)

and the concept is outlined step by step here : 
 [http://cargol.net/~ramon/ubuntu-dvd-en]("http://cargol.net/%7Eramon/ubuntu-dvd-en")

---

### Post by StefanoCole on 2007-03-02
Well, since I have the same your problem, I do in this way:
- from work where I have a broadband internet connection on a Windows PC
- I start the Ubuntu live CD on it 
- init connection (i.e. specify IP address of the computer, proxy server, ecc.)
- run Synaptic
- enable all repositories
- search the required package
- mark it for installation (it will prompt for installation of additional required packages)
- select apply button and when it asks me to download and install the packages I check the little box saying "only download packages"
- at the end of the download process the .deb files downloaded are located in the dir:
/var/cache/apt/archives/
- plug in a pen drive and copy those packages
- go home and install them with "dpkg" or GDebi package installer

2nd method (if you are running the Ubuntu live CD on a PC that doesn't have enough RAM memory to store the packages you need (at least 512 MB, 1GB is better) via terminal:
- open the file /etc/apt/sources.list and uncomment repositories (universe, multiverse, ecc.)
- sudo apt get-update
- sudo apt get-install acidrip (for instance)
- apt will tell you which are the additional required packages (copy the list of packages)
- now exit the live CD and, from Windows go to this link [http://packages.ubuntu.com/]("http://packages.ubuntu.com/") and download the packages

Hope this helps, Stefano

---

### Post by arqbrulo on 2007-03-05
Thanks Stefano. I'll be sure to try that.

---

