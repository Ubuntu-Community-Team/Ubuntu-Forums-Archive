---
title: "Start mpv playlist from specific file and continue playlist"
date: 2016-04-18
forum: MINT
---

### Post by Kevin McCready on 2016-04-18
I start mpv with
```
mpv --load-unsafe-playlists deafvids.pls
```
The playlist file .pls has hundreds of files in it. Sometimes I want to start the playlist from a particular file. How do I do that?

---

### Post by mc4man on 2016-04-18
Read thru the man, if using a ubuntu session &  ppa version it's directly available from mpv unity launcher icon > 1st. quicklist entry > Open Man pages in Evince > search in evince for  playlist, 
(- around page 14 there is this, *may* be applicable to you
> --playlist-pos=<no|index>
Set which file on the internal playlist to start playback with. The index is an integer, with 0 meaning
the first file. The value no means that the selection of the entry to play is left to the playback resume
mechanism (default). If an entry with the given index doesn't exist, the behavior is unspecified and
might change in future mpv versions. The same applies if the playlist contains further playlists (don't
expect any reasonable behavior). Passing a playlist file to mpv should work with this option, though.
E.g. mpv playlist.m3u --playlist-pos=123 will work as expected, as long as
playlist.m3u does not link to further playlists

Otherwise man as pdf is in /usr/share/doc/mpv/mpv.pdf.gz or as normal in terminal or online [https://mpv.io/manual/master/](https://mpv.io/manual/master/)

---

### Post by Kevin McCready on 2016-04-18
```
 mpv --load-unsafe-playlists deafvids.pls --playlist-pos=137 
```

Error parsing commandline option playlist-pos: option not found

Exiting... (Fatal error)

---

### Post by mc4man on 2016-04-18
which version of mpv?
edit: works ok here with a .m3u, mpv 0.17+git

---

### Post by Kevin McCready on 2016-04-18
I can't find version information searching
```
man mpv
```
My system from:
```
cat /etc/*release*
```
DISTRIB_ID=LinuxMint
DISTRIB_RELEASE=17.2
DISTRIB_CODENAME=rafaela
DISTRIB_DESCRIPTION="Linux Mint 17.2 Rafaela"
NAME="Ubuntu"
VERSION="14.04.2 LTS, Trusty Tahr"

---

### Post by howefield on 2016-04-18
Moved to the "*MINT*" forum.

---

### Post by Kevin McCready on 2016-04-19
To check the version of the available package in the Ubuntu repositories
```
apt-cache policy mpv
```
gives:
mpv:
  Installed: 0.3.4-1
  Candidate: 0.3.4-1
  Version table:
 *** 0.3.4-1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/universe i386 Packages
        100 /var/lib/dpkg/status

Wondering why --playlist-pos=137 give an error as above?

---

### Post by mc4man on 2016-04-19
> **Kevin McCready said:**
> To check the version of the available package in the Ubuntu repositories
```
apt-cache policy mpv
```
gives:
mpv:
  Installed: 0.3.4-1
  Candidate: 0.3.4-1
  Version table:
 *** 0.3.4-1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/universe i386 Packages
        100 /var/lib/dpkg/status

Wondering why --playlist-pos=137 give an error as above?
That version of mpv is extremely old & for the most part completely worthless. You should build your own or check here
[https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests](https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests)

---

### Post by Kevin McCready on 2016-04-19
Thanks. Is there any way to ask the keepers of the repository to use an updated version? It works fine for me now with the exception of the original problem.

---

### Post by mc4man on 2016-04-19
> **Kevin McCready said:**
> Thanks. Is there any way to ask the keepers of the repository to use an updated version? It works fine for me now with the exception of the original problem.
keepers of what repository?
I just created a .pls here & it works ok with --playlist-pos=

---

### Post by Kevin McCready on 2016-04-20
I mean the repositories where I download my programs from in Mint17.

---

