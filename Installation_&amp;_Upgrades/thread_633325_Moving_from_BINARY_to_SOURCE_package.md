---
title: "Moving from BINARY to SOURCE package"
date: 2007-12-06
forum: Installation &amp; Upgrades
---

### Post by asearles on 2007-12-06
I have been using (Fedora) Linux for several years now, and as of a couple of months ago, switched to using Ubuntu Linux.

Though I will be speaking specifically about the FFMPEG package, I would be very interested in comments about some/most/all Linux packages, and not just FFMPEG.

My current particular task at hand is to enable more video codecs for FFMPEG. The version within the Ubuntu distribution does not have (enabled) all the codecs I am interested in.  I should also state at this point, that I actually downloaded/installed the "Medibuntu" version of FFMPEG... which is almost what I want... I just need to get the VOB file support now.

So my plan of attack is to un-install the current (binary)  FFMPEG, and then install the SOURCE package of FFMPEG. Then... ./configure ... make .... make install.  Simple ! (I think)

Ideally, I would prefer to download a Ubuntu/Debian (.deb) source package, but I am having some problems. Using  "System-Administration-Software Sources" I can't seem to enable (check mark) the "Source code" repository. I could well be doing something wrong.

Since that is not working out for me, I was able to download a tar file containing the FFMPEG source.

Now, I can, and will, configure/compile/install this source-code version of FFMPEG, but I have the following concerns:

1) If I could have received a debian-source package, my HOPE is that I could have been notified when new updates are made to the source
2) when building FFMPEG from the tar source code, should I be dropping the code in /usr/bin or /usr/local/bin

Is there a "standard" (or generally accepted) process/procedure for switching from a BINARY package to a SOURCE package?

Comments on any of this would be appreciated. Thanks/

Alan

---

### Post by zvacet on 2007-12-06
Maybe you will find some answers [here](http://doc.ubuntu.com/ubuntu/packagingguide/C/).

---

