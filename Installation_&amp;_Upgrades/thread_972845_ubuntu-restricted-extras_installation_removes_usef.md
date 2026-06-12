---
title: "ubuntu-restricted-extras installation removes useful, non-conflicting packages"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by danzvash on 2008-11-06
I want to install ubuntu-restricted-extras.

When I give the install command (below) it says it's going to remove 3 packages - libavcodec, openmovieeditor, and ubuntustudio-video.
The latter is a wrapper package which doesn't bother me that much. 
But Openmovieeditor is a useful app.
And Libavcodec is a useful library.

Why on earth are these going to be removed?

This [*post*]("http://ubuntuforums.org/showthread.php?t=949060") says the issue is resolved, but it is definitely not.

Any ideas anyone?


```
$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgavl0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  ca-certificates-java cabextract gsfonts-x11 gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse
  icedtea6-plugin java-common libaccess-bridge-java libavcodec-unstripped-51 libmjpegtools0c2a msttcorefonts odbcinst1debian1
  openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib rhino sun-java6-bin sun-java6-jre ttf-bengali-fonts
  ttf-kannada-fonts ttf-oriya-fonts ttf-telugu-fonts ttf-wqy-zenhei tzdata-java unixodbc unrar
Suggested packages:
  equivs ttf-liberation sun-java6-fonts rhino-doc sun-java6-plugin ia32-sun-java6-plugin libmyodbc odbc-postgresql libct1
The following packages will be REMOVED:
**  libavcodec51 openmovieeditor ubuntustudio-video**

```

---

### Post by tommcd on 2008-11-06
I personally don't like that ubuntu-restricted-extras package. When it first became available (ubuntu 7.04 I think) it just installed the multimedia codecs (if I remember correctly). Now it wants to install everything but the kitchen sink, including a bunch of fonts and stuff I will likely never use. So I have gone back to apt-getting just the stuff I want, which is how it was done before ubuntu-restricted-extras became available.
Suggestion:
Just enable the medibuntu repository:
[http://medibuntu.org/](http://medibuntu.org/)
Then apt-get (or use synaptic) the w32codecs and the libdvd* stuff as it says here:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
Then just apt-get (or use synaptic) to get java, flash, and what ever gstreamer plugins or other stuff you want. MPlayer is a great multimedia player that will play anything. I also use the mozilla-mplayer plugin in Firefox. 
On Intrepid, if you go to play a media file with Totem, and if you don't have the right codec, a window will pop up and tell you what codecs to install, and you can install them directly from that window (nice!!). Use that as a guide if you find you are missing some codecs.

It may take longer this way, but you will end up with only the stuff you want, and none of the stuff you wan't to keep will be removed.
EDIT: It is possible that those packages that it wants to remove have been renamed as something else, and alternatives are being installed, as in the link you gave

---

### Post by danzvash on 2008-11-06
Thanks for the reply tommcd.

I've worked out the cause of the problem - it's in a conflict between libavcodec51 and libavcodec-unstripped-51, which are different versions of the same library, the difference being tied up in patent issues and Debian packaging, I believe. (Info in /usr/share/doc/libavcodec51/README.Debian.gz)
With these 2 lib versions, it's either/or - you can't have both on the system at the same time.

Basically, openmovieeditor has a hard dependency on libavcodec51, and so gets removed when ubuntu-restricted-extras installs the other lib version  libavcodec-unstripped-51. And since openmovieeditor is removed, which the wrapper package ubuntustudio-video covers, the wrapper is removed as well.

So it's actually the inflexible packaging of openmovieeditor which is broken - I think it should be happy with any version of libavcodec. I might send a bug report to the packager ....


On your broader point of ubuntu-restricted-extras - you're right, it does carry excessive baggage. 
Why two versions of Java Runtime (openjdk-6-jre AND sun-java6-jre) ?
And how many people are really going to use ttf-bengali-fonts, apart from Bengali Ubuntu users?

At the same time it's quite a handy way of pulling in useful extras, like the Java Runtime, unrar, Microsoft fonts and so on. But yes, I think the packagers should discriminate a little more perhaps. And the Medibuntu repo is fantastic.

I agree with your opinion on Totem - it's a really nice front-end to xine-lib, really well integrated, and the auto-installation of codecs is beautiful.
And SMPlayer is I think the best front-end for Mplayer that I have used - no auto-install of codecs, but a very nice and clean interface for the power of Mplayer.

---

