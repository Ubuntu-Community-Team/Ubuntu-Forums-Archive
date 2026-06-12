---
title: "failing to instal w32codec, please help."
date: 2005-08-05
forum: Installation &amp; Upgrades
---

### Post by ekravche on 2005-08-05
I've followed the guide located on this site.

[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

1) I've added the repositories
2) run the following commands
sudo apt-get install gstreamer0.8-plugins
sudo apt-get install gstreamer0.8-lame
sudo apt-get install gstreamer0.8-ffmpeg
sudo apt-get install w32codecs
sudo apt-get install libdivx4linux
sudo apt-get install lame
sudo apt-get install sox
sudo apt-get install ffmpeg
sudo apt-get install mjpegtools
sudo apt-get install vorbis-tools
gst-register-0.8


but w32codecs fail to install. I get the following error

E: Package w32codecs has no installation candidate

I get the same error for 
E: Couldn't find package gstreamer0.8-lame
E: Couldn't find package libdivx4linux

Thank you in advance for the help

---

### Post by coolclassic on 2005-08-05
Change repositories as adviced in the same guide

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by ekravche on 2005-08-05
I've done that. I was able to install some of the files listed in my first post, but not everything. should I target a particular repository for the w32codecs?

---

### Post by coolclassic on 2005-08-05
Did you:

sudo apt-get update

---

### Post by ekravche on 2005-08-05
yes, I've done that. To be more specific here is the detailed message that I'm getting when I run sudo apt-get install w32codecs.

Reading package lists... Done
Building dependency tree... Done
[B]Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
_E: Package w32codecs has no installation candidate_[/B]

---

### Post by Jaymoid on 2005-08-06
[QUOTE=ekravche]yes, I've done that. To be more specific here is the detailed message that I'm getting when I run sudo apt-get install w32codecs.

Reading package lists... Done
Building dependency tree... Done
[B]Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
_E: Package w32codecs has no installation candidate_[/B][/QUOTE]
 For the record, I got the same error today, I did exactly as coolclassic said and now it installed fine.

---

### Post by vimme on 2005-08-06
Same here, can't get those packages installed. And same goes for java (J2RE) for mozilla and Azureus. Can't remember if there was more of problematic installations.

And yes I've done this: [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
and this: sudo apt-get update
and this: sudo apt-get upgrade

And when I checked from Synaptic Package Manager these failed packages weren't there, don't know if they are even supposed to but...

---

### Post by coolclassic on 2005-08-07
Try this link it didn't work for me but it might for yourself.

[http://ubuntuforums.org/showthread.php?t=22646](http://ubuntuforums.org/showthread.php?t=22646)

---

### Post by vimme on 2005-08-07
Actually I did manage to install java and azureus and most of the codecs after doing something, not sure what  :-P 

Need to try that script for w32codecs and so..

---

### Post by coolclassic on 2005-08-07
Try adding this line to your source list:

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main

then do

apt-get update
apt-get install w32codecs

---

### Post by GTvulse on 2005-08-07
[QUOTE=coolclassic]Try adding this line to your source list:

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main

then do

apt-get update
apt-get install w32codecs[/QUOTE]

**No.** Use the [Backports repositories]("http://backports.ubuntuforums.org/"). Using the marillat repositories is the road to hell, if you are not an experienced Debian user.

---

### Post by ekravche on 2005-09-03
[QUOTE=ekravche]I've followed the guide located on this site.

[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

1) I've added the repositories
2) run the following commands
sudo apt-get install gstreamer0.8-plugins
sudo apt-get install gstreamer0.8-lame
sudo apt-get install gstreamer0.8-ffmpeg
sudo apt-get install w32codecs
sudo apt-get install libdivx4linux
sudo apt-get install lame
sudo apt-get install sox
sudo apt-get install ffmpeg
sudo apt-get install mjpegtools
sudo apt-get install vorbis-tools
gst-register-0.8


but w32codecs fail to install. I get the following error

E: Package w32codecs has no installation candidate

I get the same error for 
E: Couldn't find package gstreamer0.8-lame
E: Couldn't find package libdivx4linux

Thank you in advance for the help[/QUOTE]


A workaround to this would be to got to synaptic and then hit reload, but not install anything. Running those commands after seems to work for me

---

### Post by chettyk on 2005-09-25
I am having pretty much the same problem as ekravche. I have added all the repos suggested in the Unofficial Ubuntu 5.04 Starter Guide and carried out an update. But I am not able to install the w32codec; all the other multimedia codecs suggested in the Starter Guide were okay. I am now planning to download and use the Unofficial Ubuntu 5.04 Add-On CD; see:
[http://ubuntuforums.org/showpost.php?p=150088&postcount=1](http://ubuntuforums.org/showpost.php?p=150088&postcount=1)

---

### Post by GTvulse on 2005-09-25
You'll find the information you need in this thread: [http://www.ubuntuforums.org/showthread.php?t=68612](http://www.ubuntuforums.org/showthread.php?t=68612). In particular, in this post: [http://ubuntuforums.org/showpost.php?p=370764&postcount=17](http://ubuntuforums.org/showpost.php?p=370764&postcount=17)

---

### Post by chettyk on 2005-09-27
[QUOTE=dradul]You'll find the information you need in this thread: [http://www.ubuntuforums.org/showthread.php?t=68612](http://www.ubuntuforums.org/showthread.php?t=68612). In particular, in this post: [http://ubuntuforums.org/showpost.php?p=370764&postcount=17](http://ubuntuforums.org/showpost.php?p=370764&postcount=17)[/QUOTE]

Ummm... but from which repository/web site do I download a copy of the w32codec that works with Ubuntu?

---

### Post by phex on 2005-09-27
Do it manually, its far the best. Here is the link from where you can download the codecs: [http://www.mplayerhq.hu/homepage/design7/codecs.html](http://www.mplayerhq.hu/homepage/design7/codecs.html). There is also an installation instruction under [http://mplayerhq.hu/DOCS/HTML/en/install.html](http://mplayerhq.hu/DOCS/HTML/en/install.html).

just download the essential codes package and extract it to: /usr/local/lib/codecs or /usr/lib/codes

if you want to use the codecs with totem download totem-xine and not totem-gstream because the last one will only use the gstream library as far as i know. you can also use mplayer. ;)

---

### Post by chettyk on 2005-09-29
[QUOTE=phex]Do it manually, its far the best. Here is the link from where you can download the codecs: [http://www.mplayerhq.hu/homepage/design7/codecs.html](http://www.mplayerhq.hu/homepage/design7/codecs.html). There is also an installation instruction under [http://mplayerhq.hu/DOCS/HTML/en/install.html](http://mplayerhq.hu/DOCS/HTML/en/install.html).
just download the essential codes package and extract it to: /usr/local/lib/codecs or /usr/lib/codes
if you want to use the codecs with totem download totem-xine and not totem-gstream because the last one will only use the gstream library as far as i know. you can also use mplayer. ;)[/QUOTE]
Thanks for the info. I tested out the Unofficial Add-On CD (which I mentioned in my earlier post) and that did a great job, installing all the necessary software and making configuration changes at one go. All the multimedia stuff on my laptop is working great guns. I strongly recommend use of the CD.

---

### Post by mlomker on 2005-10-08
>  Using the marillat repositories is the road to hell, if you are not an experienced Debian user.

I'd agree if the packages were in the regular repositories anymore.  I just installed libdvdcss and w32codecs from here:

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) sarge main

Remove this entry from your source.list right after installing the packages that you need.

---

### Post by tseliot on 2005-10-08
Why don't you use my guide?

[http://ubuntuforums.org/showthread.php?t=70227]("http://ubuntuforums.org/showthread.php?t=70227")

---

### Post by landotter on 2005-10-08
Download codecs from the mplayer site, put in /usr/lib/win32...

How is this hard? Sheesh people--reconfiguring your apt sources and whatnot just to put some files in a directory is pretty silly.

Or more specifically, grab the essential codecs package from here: [http://www.mplayerhq.hu/homepage/design7/dload.html]("http://www.mplayerhq.hu/homepage/design7/dload.html")

Then right click and choose to uncompress the package. 

Open a terminal and run nautilus as root: $ sudo nautilus

navigate to /usr/lib

file:create folder

Name this folder: win32

put all of the codecs in this folder with no subfolders

Totem and other media players find the codecs automatically.

---

### Post by jixuanliu on 2007-05-07
Please do the following two lines of command to get everything you need to play both rmvb, avi with...

sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse -y --force-yes

sudo apt-get install libxine-extracodecs totem-xine mplayer ffmpeg lame faad sox mjpegtools libxine-main1 win32codecs

---

