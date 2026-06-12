---
title: "apt update and s/w install problem - pls help"
date: 2008-10-03
forum: Installation &amp; Upgrades
---

### Post by eskay_karthik on 2008-10-03
I installed ubuntu 8.04 a few hours back. I needed to install softwares like vlc and also mp3 plugins like gstreamer. I open the add/remove applications and it asked to reload the list.

But when i reload, I get this:

--------------
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct
--------------

When I try to install gstreamer plugin or vlc player, I get this:

--------------
VLC media player cannot be installed on your computer type (i386)

Either the application requires special hardware features or the vendor decided to not support your computer type.
--------------

I am using the wifi network in my college, and i have added the proxy in System-->Preferences-->Network Proxy. And when I do apt-get update, I get errors similar to:

GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: NODATA 2

W: Failed to fetch [http://archive.canonical.com/ubuntu/...6/Packages.bz2](http://archive.canonical.com/ubuntu/...6/Packages.bz2) Sub-process bzip2 returned an error code (2)

.
.
.

E: Some index files failed to download, they have been ignored, or old ones used instead.

I have used ubuntu before, and I had had no such problems. My apt-get install is working... I am a linux newbie only, since i have not worked much. Please help me...

eskay

---

### Post by Pumalite on 2008-10-03
Post in it's enterity, the output of:
sudo apt-get update

---

