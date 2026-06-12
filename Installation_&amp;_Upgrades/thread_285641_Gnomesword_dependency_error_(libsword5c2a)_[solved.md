---
title: "Gnomesword dependency error (libsword5c2a) [solved, see post #4]"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by UberKnight on 2006-10-27
Hi Guys

Well, I'm busy installing a couple of apps on top of my base ubuntu (edgy) setup.  However, when trying to install Gnomesword, I get the following dependency error:

> gnomesword:
 Depends: libsword5c2a (>=1.5.8-7) but it is not installable

I noticed "libsword6" in synaptic and installed it, thinking that it has perhaps superseded "libsword5c2a" and that once "-6" is installed, Gnomesword will stop wanting "-5c2a".  No go...  I still get the same error and am unable to install Gnomesword using Synaptic.

Any suggestions?

---

### Post by UberKnight on 2006-10-27
Anyone else getting this error?  Or know of a possible workaround?

---

### Post by lgmarshall on 2006-10-27
I got the same error. I could not find any information on how to work around this. Guess I'll wait and see.

---

### Post by matthew on 2006-10-29
[SIZE=2]I found a copy of the updated libsword5c2a (version 1.5.8-8+bg2)[/SIZE][SIZE=2] file in the Debian repos and installed it in Edgy on my computer with no problems. If you are using an i386 then [click this link]("http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fs%2Fsword%2Flibsword5c2a_1.5.8-8%2Bb1_i386.deb&md5sum=f5d3d7aa584860d23ed69055af815236&arch=i386&type=main"), choose a mirror to download from, and let your computer automatically install the lib file for you (using gDebi...if you aren't sure, this is probably the one you want), otherwise [you can find it here for your architecture]("http://packages.debian.org/testing/libs/libsword5c2a"). 

Then using Synaptic or apt-get you will be able to install gnome-sword with no trouble (at least I was...).[/SIZE]

---

### Post by UberKnight on 2006-10-29
Hey, thanks Matthew, I'll try this out :)

---

### Post by leech on 2006-10-29
I noticed this shortly before Edgy was released, but didn't have the time to report it.  I believe Gnome-Sword is in Universe, we'll need to contact the maintainer and have him fix the package so it depends on the new libsword.

Leech

---

### Post by matthew on 2006-10-29
> **leech said:**
> I noticed this shortly before Edgy was released, but didn't have the time to report it.  I believe Gnome-Sword is in Universe, we'll need to contact the maintainer and have him fix the package so it depends on the new libsword.

LeechActually, the problem is that the version of gnomesword that is in the repos depends on a version of libsword5c2a that is newer than the one in the Edgy repos...but the one in the Debian repos that I pointed to earlier is new enough to work. What would need to happen is for the newer version of libsword to be brought into Edgy...

EDIT: Oops! I got that backwards...the one in edgy is *newer* and gnomesword isn't quite ready for it...see below.

---

### Post by chris12349 on 2006-10-29
Matthew,  Thanks your fix using the debian Deb worked perfect!

---

### Post by LaserJock on 2006-10-29
> **matthew said:**
> Actually, the problem is that the version of gnomesword that is in the repos depends on a version of libsword5c2a that is newer than the one in the Edgy repos...but the one in the Debian repos that I pointed to earlier is new enough to work. What would need to happen is for the newer version of libsword to be brought into Edgy...

Actually, the problem is that the libsword in Edgy is *too* new for Gnome Sword. We brought in libsword6 and a new BibleTime shortly before Edgy froze, however gnomesword has an issues with the new clucene libs. The Gnome Sword maintainer in Debian is aware of the issue and hopefully a fixed gnomesword package will be uploaded into edgy-updates before too long.

-LaserJock

---

### Post by matthew on 2006-10-29
> **LaserJock said:**
> Actually, the problem is that the libsword in Edgy is *too* new for Gnome Sword. We brought in libsword6 and a new BibleTime shortly before Edgy froze, however gnomesword has an issues with the new clucene libs. The Gnome Sword maintainer in Debian is aware of the issue and hopefully a fixed gnomesword package will be uploaded into edgy-updates before too long.

-LaserJockDoh! You're right, of course. 6 > 5.8 :oops:

---

### Post by timosa on 2006-12-08
> **matthew said:**
> [SIZE=2]I found a copy of the updated libsword5c2a (version 1.5.8-8+bg2)[/SIZE][SIZE=2] file in the Debian repos and installed it in Edgy on my computer with no problems. If you are using an i386 then [click this link]("http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fs%2Fsword%2Flibsword5c2a_1.5.8-8%2Bb1_i386.deb&md5sum=f5d3d7aa584860d23ed69055af815236&arch=i386&type=main"), choose a mirror to download from, and let your computer automatically install the lib file for you (using gDebi...if you aren't sure, this is probably the one you want), otherwise [you can find it here for your architecture]("http://packages.debian.org/testing/libs/libsword5c2a"). 

It's also possible to install the missing library from Dapper to Edgy. Just download it ([ i386](http://mirrors.kernel.org/ubuntu/pool/universe/s/sword/libsword5c2a_1.5.8-8_i386.deb) |  [amd64](http://mirrors.kernel.org/ubuntu/pool/universe/s/sword/libsword5c2a_1.5.8-8_amd64.deb) | [powerpc](http://mirrors.kernel.org/ubuntu/pool/universe/s/sword/libsword5c2a_1.5.8-8_powerpc.deb)) and the GDebi will take care of rest. I was not able to download the Debian version because libsword5c2a seems not to be available in unstable anymore.

---

### Post by Brookranger on 2006-12-09
Good save. I used your install method and worked just great for me.

---

### Post by jpyanowski on 2007-01-01
It also worked for me. Thanks.

---

### Post by zippytex on 2007-01-21
Well the link reports that it does not know about this file!  It says it cannot find it.  What to do now?:frown:

---

### Post by zippytex on 2007-01-21
[QUOTE=timosa;1860728]It's also possible to install the missing library from Dapper to Edgy. Just download it ([ **i386](http://mirrors.kernel.org/ubuntu/pool/universe/s/sword/libsword5c2a_1.5.8-8_**i386.deb) |  

=D> Yeah!!! Thanks so much for your post.  Finally, I clicked on the i386 link and it downloaded and installed!  Now I can run sword just fine!!   Thanks so much!  I am a 64 year old woman and I learn a little slower, but I do learn!!!  Thanks Again for your time and sharing!!):P

---

### Post by Ptero-4 on 2007-02-03
Another thing. You may need to install libtasn1-2 before libsword5c2a installs. But it works nice.

Thanks and god bless.

---

### Post by everand4ever on 2007-02-08
> **Ptero-4 said:**
> Another thing. You may need to install libtasn1-2 before libsword5c2a installs. But it works nice.

Thanks and god bless.
So now I'm new to linux, but...why in the synaptic package manager for Ubuntu (which I installed only a couple days ago and have been figuring out stuff from installing WINE and setting up video card and everything while giving me minor pains in butt) why does it say that it is: "libsword6 (1.5.9-0ubuntu3)" and yet...when I try to install gnomesword it tells me I have to have a "higher" version? lol It's like when I was having to "install" Nvidia glx yet supposedly there was a graphics driver already? I dunno. I'm trying not to complain, but lots of this stuff seems counter-productive at the moment. Anyways - I'm deciding to see what's up with "BibleTime" - hopefully it will be able to use my .bbl's and other e-sword files I have on Windows (since I am running dual-boot now) because I took the time to use Bible Import and find many helpful books in topical form for E-Sword. I really like Linux so far - it's just too bad the support for games is almost zilch (except a strange WINE program runs it) - else I could see myself switching over completely (oh yeah - forgot about lots of sites preferring Internet Explorer, especially shockwave-wise - doh!).

later friends and God bless,
Richard 8 )

---

### Post by Garyu on 2007-02-25
I am trying to fix my dad's setup with Ubuntu Dapper 6.06, all repos active all updates installed, to work with GnomeSword, but I get this weird error. It installs fine through aptitude but when I run "gnomesword2" in a terminal I get a crash and this message:
```
(gnomesword:7863): GLib-CRITICAL **: g_convert: assertion `from_codeset != NULL' failed
```
I've got BibleTime up and running, but my dad isn't very fond of that program.

---

### Post by everand4ever on 2007-03-03
> **Garyu said:**
> I am trying to fix my dad's setup with Ubuntu Dapper 6.06, all repos active all updates installed, to work with GnomeSword, but I get this weird error. It installs fine through aptitude but when I run "gnomesword2" in a terminal I get a crash and this message:
```
(gnomesword:7863): GLib-CRITICAL **: g_convert: assertion `from_codeset != NULL' failed
```
I've got BibleTime up and running, but my dad isn't very fond of that program.
Can you get e-sword up and running through WINE? I keep switching Linux sys's (finding out what my "taste" is at moment and am now on Kubuntu), but I'm pretty used to installing E-sword, etc. Plus, I can give you extra resource websites for it to download some free Christian books like on apologetics, etc. (they're legal as far as I know). But let me know. I believe you can click my name for the e-mail thingee too (think I enabled it). I'll be out til' Tuesday though if I don't get to it by Sunday morning.

later,
Richard :guitar:
P.S. Added this at last second. In order to get E-Sword to work - you need to make sure it is added as an app by doing :"winecfg" under your terminal. And also, you have to add the rich20.dll replacement (this is in one of the screens in the config). Elsewise - E-Sword will not display properly.

---

### Post by Garyu on 2007-03-03
> **everand4ever said:**
> P.S. Added this at last second. In order to get E-Sword to work - you need to make sure it is added as an app by doing :"winecfg" under your terminal. And also, you have to add the rich20.dll replacement (this is in one of the screens in the config). Elsewise - E-Sword will not display properly.

Thanks for the tip. Maybe I'll give e-sword a try. But I would very much prefer the native app (gnomesword in this case) if it is possible... Since it is in the repo's it should be possible to make it work, right?

---

### Post by mhancoc7 on 2007-03-03
> **everand4ever said:**
> Can you get e-sword up and running through WINE? I keep switching Linux sys's (finding out what my "taste" is at moment and am now on Kubuntu), but I'm pretty used to installing E-sword, etc. Plus, I can give you extra resource websites for it to download some free Christian books like on apologetics, etc. (they're legal as far as I know). But let me know. I believe you can click my name for the e-mail thingee too (think I enabled it). I'll be out til' Tuesday though if I don't get to it by Sunday morning.

later,
Richard :guitar:
P.S. Added this at last second. In order to get E-Sword to work - you need to make sure it is added as an app by doing :"winecfg" under your terminal. And also, you have to add the rich20.dll replacement (this is in one of the screens in the config). Elsewise - E-Sword will not display properly.


You might want to check this out.
[http://www.ubuntuforums.org/showthread.php?t=372359](http://www.ubuntuforums.org/showthread.php?t=372359)
Jereme

---

