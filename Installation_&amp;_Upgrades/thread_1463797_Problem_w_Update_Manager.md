---
title: "Problem w/ Update Manager"
date: 2010-04-27
forum: Installation &amp; Upgrades
---

### Post by max-power2717 on 2010-04-27
Hi People,

This has poped up and I have no idea how to go about resolving it:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=154473&stc=1&d=1272385821[/IMG]

That appears whenever Update Manager starts. When I press partial upgrade I get the following message:

```
**Error authenticating some packages**

It was not possible to authenticate some packages. 
This may be a transient network problem. You may 
want to try again later. See below for a list of unauthenticated 
packages.
```And a long list of packages follows:

[LIST]
[*]ffmpeg
[*]libamrnb3
[*]libamrwb3
[*]libavcodec51
[*]libavdevice52
[*]libavfilter0
[*]libavformat52
[*]libavutil49
[*]libdirac0
[*]libmjpegtools0
[*]libswscale0
[*]libx264-60
[/LIST]
When I try apt-get upgrade, I get:
```
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  ffmpeg libavdevice52 libavfilter0 libavformat52 libavutil49 libpostproc51 libquicktime1
  libswscale0 transcode
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.

```Other important information:

[LIST]
[*]Ubuntu 9.04
[*]Recently removed the latest version of wine, and built version 1.1.17. Installed with make. Attempted installation of Adobe CS4 (failed). Put the attempt on hold. (Could this be the problem? So far I've seen no mention of wine at all!?)
[*]I've been messing about with my disk boot sectors and experimenting with different bootloader configurations in the last few hours. It was soon after one of the many reboots I noticed the problem, and it's been persistent since that first time it appeared.
[/LIST]
I can't think of anything else I need to mention. Please, let me know if you want to know something else about my configuration.

Normally I'd have a good crack at trying to resolve a problem like this before running to support, but one of the updates is a security update, and the error is something about package authentication. I don't understand the problem, but I want to get it resolved quickly for my peace of mind. 

Thanks in advance,
Max.

---

### Post by max-power2717 on 2010-04-28
Hi again, 

I haven't solved my problem, but I've found out a thing or two more about it.

First of all I am certain that there are a couple of repositories in my sources.list file which I don't have an authentication key for:

> max@thorbuntu:~$ sudo apt-get update
[sudo] password for max: 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty Release.gpg
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) jaunty/main 

---
                                                                                                                         
Reading package lists... Done
W: GPG error: [http://www.debian-multimedia.org](http://www.debian-multimedia.org) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY XXXXXXXXXXXXXXXX
W: GPG error: [http://deb.torproject.org](http://deb.torproject.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY XXXXXXXXXXXXXXXX
W: You may want to run apt-get update to correct these problemsThis is the truncated (and slightly doctored) output from the apt-get update command. Warnings of two unverified repositories are shown at the bottom. 

The reason I'm having the problems is because there is a later version of ffmpeg on the [www.debian-multimedia.org]("http://www.debian-multimedia.org") repository. And since that package, (and the associated libraries which I listed in the above post,) are configured on my system to automatically update, but the repository that the new software is on cannot be authenticated by my system, the update fails.

The solution seems easy enough, simply get the key file (or what ever I need) for my system to authenticate from the repository. 

I wonder, is it wise to simply update this software from this repository? Does anyone know about this repository? Is software from here likely to interfere with the normal operation of Ubuntu?

Anyway, I've relaxed now, I understand the problem and I don't believe my system is facing impending attack.

---

### Post by max-power2717 on 2010-04-28
[Here]("http://debian-multimedia.org/faq.php#q1"), in the FAQ of debian-multimedia, I found the precise instructions to get the appropriate key installed and that I believe will eradicate the error reported by Update Manager (for now).

However, I haven't installed the keyring just yet, I'm hoping someone in the know will give me their opinion of my query above: is it wise to update this software from this repository? Does anyone know what this repository is all about? Should I simply turn away from it perhaps?

Cheers.

---

