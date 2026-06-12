---
title: "can't install mplayer with apt-get (Hash Sum mismatch)"
date: 2012-04-16
forum: Installation &amp; Upgrades
---

### Post by spotspot on 2012-04-16
on 10.04LTS, this worked fine ysterday, what happened???


$ sudo apt-get install mplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libaudio2 libavcodec52 libavformat52 libavutil49 libdvdnav4 libdvdread4 libenca0 libgsm1 liblzo2-2 libmp3lame0 libmpcdec3
  libopenal1 libpostproc51 libschroedinger-1.0-0 libsvga1 libswscale0 libx264-85 libxvidcore4
Suggested packages:
  nas libdvdcss2 debhelper build-essential mplayer-doc netselect fping
Recommended packages:
  head
The following NEW packages will be installed:
  libaudio2 libavcodec52 libavformat52 libavutil49 libdvdnav4 libdvdread4 libenca0 libgsm1 liblzo2-2 libmp3lame0 libmpcdec3
  libopenal1 libpostproc51 libschroedinger-1.0-0 libsvga1 libswscale0 libx264-85 libxvidcore4 mplayer
0 upgraded, 19 newly installed, 0 to remove and 0 not upgraded.
Need to get 720kB/10.2MB of archives.
After this operation, 25.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main libavformat52 4:0.5.1-1ubuntu1.3 [720kB]
Fetched 720kB in 1s (394kB/s)        
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavformat52_0.5.1-1ubuntu1.3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/ffmpeg/libavformat52_0.5.1-1ubuntu1.3_i386.deb)  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by nmaster on 2012-05-31
This is a little bit late, but I recently had a similar problem and I want to share my solution:

Some people who have this problem blame improper proxy caching by the ISP.  If this is indeed the case, the ISP admins most likely aren't caching traffic using ftp (most likely the bulk of the traffic is http).  To take advantage of the fact that they aren't caching ftp traffic, use ftp mirrors.  

Here's some information on editing your repos: 
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Here's a list of mirrors: 
[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

I would suggest choosing a mirror that is near you (in your country is probably good enough) that uses ftp.

---

