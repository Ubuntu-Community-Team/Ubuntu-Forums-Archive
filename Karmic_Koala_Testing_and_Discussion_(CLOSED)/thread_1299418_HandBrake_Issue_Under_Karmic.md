---
title: "HandBrake Issue Under Karmic"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by BAMF1501 on 2009-10-23
OK so i installed handbrake a divx encoder but i get this error /?

[IMG]http://i34.tinypic.com/23ibigh.png[/IMG]

---

### Post by jbrown96 on 2009-10-23
Does this happen when you try to launch handbrake or installing it? If you are installing it, it would help to see the output from the terminal. You should have downloaded a .deb file. Here's how to install it. In a terminal (apps-->accessories), ```
sudo dpkg -i FILE
``` repalce FILE with the handbrake file. It will probably be on your desktop, so Desktop/ at that point you can double tap tab and it will list the available files. Start typing the file name, then you can press tab once to autocomplete. Post the output here if you have errors.

---

### Post by BAMF1501 on 2009-10-24
those codes dont work

---

### Post by tommcd on 2009-10-24
Please post the link from where you got Handbrake. Was it from the Handbrake website:
[http://handbrake.fr/downloads.php](http://handbrake.fr/downloads.php)
or from somewhere else? 
Put the handbrake .deb package in your home directory. Open a terminal and run:
```
sudo dpkg -i Handbrake
``` 
and hit the **Tab** key. It should autocomplete the Handbrake file name. If it doesn't then Handbrake is not in your home directory.

---

### Post by oboedad55 on 2009-10-24
I've got the same deal going on. It installs fine but throws this error trying to start the program.

---

### Post by tommcd on 2009-10-24
> **oboedad55 said:**
> I've got the same deal going on. It installs fine but throws this error trying to start the program.
Some googling suggests this may be a bug in Handbrake. About the only possible fix I could see was this:
[http://forum.handbrake.fr/viewtopic.php?f=13&t=7327](http://forum.handbrake.fr/viewtopic.php?f=13&t=7327)
So you could try finding the ghb.ui file and editing it as per that link. That post is 1 year old though.
The last post in that thread indicates this bug has been fixed in the snapshot version of handbrake and has a link to it. That last post was dated Oct 07, 2009 so it should be current.

---

### Post by oboedad55 on 2009-10-24
Just for laughs I messed around with this issue for a while, including trying to install the snapshot. For some reason it stops with a failed dependency, needing libwebkit 1.0-1 I believe.

---

### Post by tommcd on 2009-10-25
> **oboedad55 said:**
> Just for laughs I messed around with this issue for a while, including trying to install the snapshot. For some reason it stops with a failed dependency, needing libwebkit 1.0-1 I believe.
If there is a missing dependency, then search for it with aptitude. For example:
```
aptitude search libwebkit 
```
will return all packages with libwebkit in their names. A "p" before the package name means it is not installed. An "i" before the package name means it is installed. You can then install the package with apt-get if it is not already installed, and then try installing HandBrake again.
The current version of libwebkit in Jaunty is 1.0-1:
[http://packages.ubuntu.com/search?keywords=libwebkit&searchon=names&suite=jaunty&section=all](http://packages.ubuntu.com/search?keywords=libwebkit&searchon=names&suite=jaunty&section=all)

---

### Post by Mooty on 2009-10-25
Hi, you need to use the SVN version [http://forum.handbrake.fr/viewtopic.php?f=4&t=12464](http://forum.handbrake.fr/viewtopic.php?f=4&t=12464) , as 9.3 doesn't work on Karmic, if I'm remembering correctly.

---

### Post by fenian on 2009-10-25
You need to do 3 things to get it working...

1-Download the SVN snapshot [here]("http://handbrake.fr/snapshot.php")

2-Force the installation to ignore missing webkit dependency,open a termial and enter...

for 64 bit...
> 
for 64 bit...

sudo dpkg -i --force-depends ~/Downloads/HandBrake-svn2845-Ubuntu_GUI_x86_64.deb

for 32 bit...

sudo dpkg -i --force-depends ~/Downloads/HandBrake-svn2845-Ubuntu_GUI_i686.deb

(My downloads go to ~/Downlods change yours appropriately)

3-Create symbolic link for webkit,in the terminal enter...

> [QUOTE]sudo ln -s /usr/lib64/libwebkit-1.0.so.2 /usr/lib64/libwebkit-1.0.so.1[/QUOTE]

For 32 bit the /usr/lib64  bit would be something different but as I am not running 32 bit I cannot give you an exact cut and paste line.

---

### Post by r0ck1t on 2009-10-26
[fenian]("http://ubuntuforums.org/showpost.php?p=8166900&postcount=10") has the answer. Worked for me. Thanks :D

---

### Post by azmo35 on 2009-10-26
Hi, this is what i get,maybe help some one to help us.[IMG][[IMG]http://img44.imageshack.us/img44/8840/screenshotpackageinstal.th.png[/IMG]](http://img44.imageshack.us/i/screenshotpackageinstal.png/)[/IMG]

---

### Post by coffeecat on 2009-10-26
Thanks, **fenian**. It worked for me too in 64-bit Karmic. I made one change though. Seeing that /usr/lib64 is a link to /usr/lib, I changed:

```
sudo ln -s /usr/lib64/libwebkit-1.0.so.2 /usr/lib64/libwebkit-1.0.so.1                      
```... to ...

```
sudo ln -s /usr/lib/libwebkit-1.0.so.2 /usr/lib/libwebkit-1.0.so.1
```Seemed tidier that way. Only one thing though.... It seems they've dropped support for the Xvid codec and AVI container in this latest version. :sigh: Just when I'd settled on that combination for compatibility with my media player :sigh. I suppose I'll have to go with H264/MP4. Looks like there are some more test transcodes coming up. :sigh: 

> **azmo35 said:**
> Hi, this is what i get,maybe help some one to help us.[IMG][[IMG]http://img44.imageshack.us/img44/8840/screenshotpackageinstal.th.png[/IMG]]("http://img44.imageshack.us/i/screenshotpackageinstal.png/")[/IMG]

Did you read **fenian**'s post? All you need to know is there. If you have any specific problems post back and someone will help you, but don't post an issue that's already been debated and resolved.

---

### Post by produnis on 2009-10-26
thx ferian,
Installation worked now...

but unfortunately Handbrake knows nothing about DIVX and MP3 anymore...
does anyone know how to fix that?

---

### Post by coffeecat on 2009-10-26
An update.... If only for myself so that I can remember what I have been up to on this system. :?

First, Synaptic complained about a "Broken Package" (Guess what?) and wouldn't do an update until I'd "fixed broken packages". So it uninstalled the svn version of Handbrake. Thank you, Synaptic! :evil:

Anyway, some good news and some bad news. The good news from [this Handbrake forum thread]("http://forum.handbrake.fr/viewtopic.php?f=13&t=12647"). This after a discussion of the libwebkit dependency problem:

> The official release of karmic is due Oct 29 (next thursday). When that happens, I will be upgrading and future snapshots and releases will be created for karmic.The bad news is in [the Handbrake forum thread]("http://forum.handbrake.fr/viewtopic.php?f=4&t=12464") already posted earlier. Scroll down a bit and see what they say about AVI, ogg and XviD. That's a bummer for me because libavcodec/FFmpeg gives inferior video quality and Avidemux throws a hissy fit about B-frames in H264 video. I like to use Avidemux to edit video files encoded by Handbrake. Ah well. Onward and downward. :(

---

### Post by azmo35 on 2009-10-27
Hello neighbour? Whem i post the screenshot is only to help, some one said [aptitude search libwebkit] the libwebkit is the 1.0.2.,remember meny people come here they are like me not computer savvy,so my self figured out this aswell, like fenian said is
   [] sudo ln -s /usr/lib/libwebkit-1.0.so.2 /usr/lib/libwebkit-1.0.so.1 [] for 32bit,and don't get mad with me, you are very right on your last post.

---

### Post by coffeecat on 2009-10-27
> **azmo35 said:**
> don't get mad with me

I'm not at all mad with you. :wink: Sorry to misunderstand your post. It sounded as though you were asking for help.

Good luck with installing Handbrake and let's hope the future snapshot/release for Karmic will solve these problems for us. Pity about the withdrawn codecs though, although I can respect the developers' decision to do so.

---

### Post by eidoslinux on 2009-10-27
is there any way to get the PS3 preset in the svn listing?

---

### Post by maddojf on 2009-10-27
I stumbled upon this by accident and thought I would share.  After following the directions earlier in this thread I was able to get handbrake running but I couldn't install anything else because of the forced dependency stuff (apt kept telling me that I needed to remove handbrake).

I found out that if you launch hanbrake and then autoremove the package while it is running, you can then install new software (apt will stop complaining) but you can continue to use handbrake as long as you don't close it.  

This what I am planning to do until Thursday.  Hope this helps.

---

