---
title: "Compiling and Installing rTorrent with LibTorrent on Ubuntu / Debian"
date: 2008-11-19
forum: Installation &amp; Upgrades
---

### Post by rglonek on 2008-11-19
Hi,

I have lately been trying to compile the newest rtorrent with libtorrent on a debian system and ubuntu. Reason being is that the repos didn't contain a new version with encryption enabled. It was brought to mee that a huge load of users (google'd for my errors) had a huge number of problems installing rtorrent and getting the dependencies right. I have come up with a quick guide on how to resolve dependencies to compile rtorrent without pain. The error messages during compilation were very ecryptic which has led me to doing so. Here we go (a simple guide to those who just want to get it working):

**_AS ROOT:_**

**--> update apt-list**
```
aptitude update
```

**--> satisfy dependencies (every "aptitude" is one line)**
```
apt-get install linux-kernel-headers build-essential
aptitude install xlibs-static-dev xlibs-data
aptitude install ca-certificates libcurl3 libidn11 openssl
aptitude install automake
aptitude install libtool
aptitude install openssl
aptitude install pkg-config autoconf
aptitude install libssl-dev
aptitude install libsigc++-2.0-dev
aptitude install libncursesw5 libncursesw5-dev
aptitude install libcurl3-dev libcurl3-openssl-dev
aptitude install libncurses5 libncurses5-dev ncurses-base ncurses-bin ncurses-dev ncurses-hexedit ncurses-runtime ncurses-term

```

**--> download and unpack the torrent sources**
```
cd ~
wget http://libtorrent.rakshasa.no/downloads/libtorrent-0.11.9.tar.gz
wget http://libtorrent.rakshasa.no/downloads/rtorrent-0.7.9.tar.gz
mkdir src
cd src
tar -zxvf ../libtorrent-0.11.9.tar.gz
tar -zxvf ../rtorrent-0.7.9.tar.gz

```

**--> compile libtorrent**
```
cd ~/src/libtorrent-0.11.9
./autogen.sh
./configure
make && make install

```

**--> compile rtorrent**
```
cd ~/src/rtorrent-0.7.9
./autogen.sh
./configure
make && make install

```

**--> make a friendly link**
```
ln -s /usr/local/bin/rtorrent /usr/bin/rtorrent
```

**_AS USER THAT WILL USE RTORRENT:_**

**--> create a directory tree for our config**
```
cd ~
mkdir rtorrent
cd rtorrent/
mkdir downloads
mkdir downloads/.session
mkdir torrents
cd ~

```

**--> create config file (vi ~/.rtorrent.rc) with the following (nice, encrypted traffic and folder management config file):**
```
port_range=8500-8600
port_random=yes
download_rate = 0
upload_rate=15
directory= ~/rtorrent/downloads/
session= ~/rtorrent/downloads/.session
encryption = allow_incoming,try_outgoing,enable_retry
safe_sync = yes
schedule = watch_directory,10,10,load_start=~/rtorrent/torrents/*.torrent
schedule = tied_directory,10,10,start_tied=
schedule = untied_directory,10,10,close_untied=

```

That's it. Enjoy :)

In order to start downloading, just wget/copy the .torrent files that you find to ~/rtorrent/torrents. rTorrent will pick them up automatically :)

If you find any more dependency problems, post back and I will update my tutorial on this.

---

### Post by mihalisla on 2009-11-23
Thank you very much!!!!!
Thank you also for providing an .rtorrent.rc  sammple file for ubuntu
I was trying to find one working for a long time!!!!:D

---

