---
title: "how to install cinelerra-4.1"
date: 2010-03-04
forum: Installation &amp; Upgrades
---

### Post by tonjaa on 2010-03-04
kamic 9.10 64 bit
i download program [COLOR=RoyalBlue] cinelerra-4.1-src-tar.bz2  [/COLOR]how to install it please tell me by step.;)

---

### Post by 23dornot23d on 2010-03-04
There may be a easier way 

[http://cinelerra.org/getting_cinelerra.php](http://cinelerra.org/getting_cinelerra.php)

from the above link ........

copy this into a terminal window ,,,

echo deb [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-karmic main | sudo tee /etc/apt/sources.list.d/akirad.list && wget -q [http://akirad.cinelerra.org/dists/akirad.key](http://akirad.cinelerra.org/dists/akirad.key) -O- | sudo apt-key add - && sudo apt-get update
______________________________________________________

Then apt-get install cinelerracv

[IMG]http://i47.tinypic.com/os8jcz.jpg[/IMG]

Yours will look slightly different to the above .... as I have some extra packages installed .....
that its asking me to remove .......



Here is the screenshot of the program running after I did the above ,,,, [http://i49.tinypic.com/35a7kgg.jpg](http://i49.tinypic.com/35a7kgg.jpg)

[COLOR=Blue][B]The version is showing as ver 2.1 !!! but its direct from their site .... !!! 

it works though ,,,,,,,[/B][/COLOR]

[COLOR=Red]_______________________________________________________[/COLOR]
[B][COLOR=Red]
Here are my attempts to get it working from the source files .....

Linux Mint
Ubuntu 9.10
Mandriva 2010

Ubuntu 8.10 ....... looked promising .... failed on a plugin .......
[/COLOR][/B][COLOR=Red]_______________________________________________________[/COLOR]

I have also tried to compile this .... but the version is not 4.1 ?

you will need to do the following ..... with your version 
[http://sourceforge.net/projects/heroines/files/cinelerra-4.1-src.tar.bz2/download](http://sourceforge.net/projects/heroines/files/cinelerra-4.1-src.tar.bz2/download)

once you unpack it to the directory you want it in .........

./configure

[IMG]http://i49.tinypic.com/2j47xty.jpg[/IMG]


sudo apt-get install nasm
sudo apt-get install yasm

./configure

[IMG]http://i45.tinypic.com/73mbra.jpg[/IMG]

make


[IMG]http://i50.tinypic.com/2jcikja.jpg[/IMG]



Ok **we hit a problem** ........ ( will swap systems and see if I get the same error ) hang on .....
That was Linux Mint ........

upto ./configure in Karmic now

**make**

Same error ....... same whether root or normal .........

Also same error ,,,,, in Mandriva 2010 ...




[COLOR=Red][B]My final attempt is in Ubuntu 8.10 ..... 
[/B][/COLOR] 
still get an [COLOR=Red]error[/COLOR] .... but it goes a lot further ......

[IMG]http://i45.tinypic.com/15z4002.jpg[/IMG]



once all the errors have gone ...... do .....

**make install**


let me know if this version 4.1 is much better when you or anyone else gets to run it ...... 

please ......

---

### Post by tonjaa on 2010-03-04
i have problem when install like this .
how i can do it?

---

### Post by oldos2er on 2010-03-04
Is there some particular reason you're compiling it? If not, it's much easier to add Cinelerra's repository and install it via Synaptic or apt-get. [http://cinelerra.org/getting_cinelerra.php#ubuntu](http://cinelerra.org/getting_cinelerra.php#ubuntu)

---

### Post by 23dornot23d on 2010-03-04
Seems that the only version is a very old one in the repository ...... 

and the Gdebi did not go too well either when I tried it .......

Thats why .........

I did show a way that I tested and worked at the start of my thread .......

________________________________________________________

This newer version 4.1 does seem to have some problems ........ 

and was hoping somebody could shed some light on why it does not work .....
there are a few clues now ...... I did try it again on my old Elive system ... 
and it still failed but seems to go a lot further using the older libraries/headers for some reason .............

It still fails at the blur plugin .... I wonder if this can be avoided somehow ..........

[IMG]http://i47.tinypic.com/wqo38z.jpg[/IMG]

So I would say **wait** until there is a stable version to download ...... from the Synaptic repository ..........

---

### Post by tonjaa on 2010-03-05
;) ok. now i can install it from[COLOR=DarkOrange] [http://cinelerra.org/getting_cinelerra.php#ubuntu  ]("http://cinelerra.org/getting_cinelerra.php#ubuntu")
i install follow step for karmic koala 9.10[/COLOR] it 's version 2.1

at first time i try install by ./configure but it's have problem .
and i don't know about xcb what is it ?  in menu bar of cinelerra have with and without xcb how is different ? 
and why when i load file .wma to program it's can't play no picture and sound have problem  at setting audio driver set at oss it's correct or not ?
[COLOR=Green]thank you so much .[/COLOR]

---

### Post by 23dornot23d on 2010-03-05
Here is the rest of the information that you requested ...


Here is the link to show XCB .....

XCB ...... [http://en.wikipedia.org/wiki/XCB](http://en.wikipedia.org/wiki/XCB)


WMA ...... Winows Media Audio files ...........

WMV  is supported see links below .......... Windows Media Video ......

Here is another link I found with some more information .......

[http://heroinewarrior.com/cinelerra.php](http://heroinewarrior.com/cinelerra.php)

A manual written for cinelerra ....

[http://cinelerra.org/docs/split_manual_en/cinelerra_cv_manual_en_1.html](http://cinelerra.org/docs/split_manual_en/cinelerra_cv_manual_en_1.html)

________________

Check out Pitivi too

[http://www.pitivi.org/](http://www.pitivi.org/)

Which is available in the Synaptic Package Manager .....

---

### Post by wildhostile on 2010-03-06
Hi 23dornot23d,

There are two version of Cinelerra, originally created by heroine warrior.
- the official one is located at [http://www.heroinewarrior.com/cinelerra.php](http://www.heroinewarrior.com/cinelerra.php) . That the version maintained by the original author. It is at version 4.1 with relatively numerous new features compared to 2.1 version. It has some drawbacks like: the viewer has a bug currently and doesn't work, there is no compatibility with 2.1 version (I don't think).
- the "Community" version, as it's name indicate it, is maintained by a community. It is located at [www.cinelerra.org](www.cinelerra.org) . It's 2.1 version but some works are in progress to port the features in 4.1 version. The community doesn't really work actively on the code because of various reasons. This version is said to be more stable. That's the one I use myself. There is a deb package for this version. But it compile very easily without particular skills.

Other readings:
- About Cinelerra and Cinelerra-CV ==> [http://cinelerra.org/about.php](http://cinelerra.org/about.php)
- Cinelerra 4.0 ==> [http://makefx.wordpress.com/2009/09/02/whats-new-in-cinelerra-4](http://makefx.wordpress.com/2009/09/02/whats-new-in-cinelerra-4)

If you have questions on Cinelerra you can use the community mailling list or the IRC channel. See ==> [http://cinelerra.org/mailinglists.php](http://cinelerra.org/mailinglists.php)

See you.

---

### Post by strumusa on 2010-03-15
> 

once all the errors have gone ...... do .....

**make install**


let me know if this version 4.1 is much better when you or anyone else gets to run it ...... 

please ......Your instructions with screen shots were outstanding..However, now when I open cinelerra and try to record (or just hit r to record), Cinelerra closes completely.  Also, my web cam light is always on when I plug it in to the usb port....Why is that with Linux?  Do I need to umount it or something?  Also, I did have two errors after installing it, so the  -make install- would not work.  Here is my screenshot...Thanks, dude....Finally, some help with video movie making.    

make[2]: *** [install] Error 1
make[2]: Leaving directory `/home/strum/Downloads/cinelerra-4.1/plugins'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/strum/Downloads/cinelerra-4.1'
make: *** [install] Error 2
strumusa@strum-desktop:~/Downloads/cinelerra-4.1$

Aw, hell...forget it...I know you can make youtube videos with unbuntu 9.1.  But the new world OS likes to be discreet about things and make it tough for beginners  (that's OK, I understand.)  I have tried cheese (cheesy, just like it says...But at least Cheese works-- But the video is late sycnhing with the audio,) cinelerra (closes when I hit record,) and now Kino (which suks also -- It won't even let me do anything.)  My USB webcam light is always on all the time, except when I run Cheese, then it acts normal.  I give up...I even tried NixiePixel's codecs at medibuntu.  I'm sorry, but I've been trying for one month to try to get something working, just so I can make real time video and audio, i.e. youtube stuff.  Maybe it's my cheesy computer?  With no extra grafix card (But it worked well with mov1emakr.)   Here are my (cheesy) hardware specs for any of you dev. who might be hopefully watching: 
    description: Desktop Computer
    product: Evo D310v
    vendor: Compaq
    serial: ?????????
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=02604FA0-0D40-11D7-8000-0010DCAD91DC

cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 1.80GHz

*-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:17 ioport:2000(size=256) ioport:2400(size=64) memory:fc480400-fc4805ff memory:fc480600-fc4806ff
 
# (My cheesy webcam on usb 2):
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 093a:2460 Pixart Imaging, Inc. Q-TEC WEBCAM 100
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by OriolCorbella on 2010-08-02
Here is the solution: [https://bbs.archlinux.org/viewtopic.php?id=100668](https://bbs.archlinux.org/viewtopic.php?id=100668)

> Hi:
After struggling a while to make the default cinelerra-cv package work (reported the error as stated in this thread: [http://bbs.archlinux.org/viewtopic.php?id=85542)]("http://bbs.archlinux.org/viewtopic.php?id=85542%29"), I tried with the Heroinwarrior's cinelerra 4.1 version. It just works for my need.
1) I have downloaded the cinelerra 4.1 source from sourceforge.net ([https://sourceforge.net/projects/heroin … 2/download]("https://sourceforge.net/projects/heroines/files/cinelerra-4.1-src.tar.bz2/download"))
2) Uncompressed it using tar -jxvf cinelerra-4.1-src.tar.bz2
3) Changed directory to (cd cinelerra-4.1)
4)  Made some changes to main.c in quicktime/thirdparty/faac-1.24/frontend/  directory. Replaced "include <mp4.h>" with "include  <mp4v2/mp4v2.h>" (without quotes) on line 33
5) Removed a  block in common.h file in quicktime/thirdparty/faad2-2.0/libfaad/  directory. Delete the lines from 310 to 322 and saved file.
6) Then I did ./configure && make && make install"
7) I didn't do 'make install' as I run the cinelerra binary from the /bin folder from the source directory itself.
Hope this helps.
zenny


---

### Post by ahbart on 2010-08-02
I googled around and found this: [link]("https://launchpad.net/~dominik-stadler/+archive/ppa")
They offer a package: cinelerra 4.2git1-1ubuntu8 
Is this something you can use? I'm not sure which 'version' of cinerella this is. (referring to wildhostile message)

---

### Post by Rumpty on 2010-08-17
> **ahbart said:**
> I googled around and found this: [link]("https://launchpad.net/~dominik-stadler/+archive/ppa")
They offer a package: cinelerra 4.2git1-1ubuntu8 
Is this something you can use? I'm not sure which 'version' of cinerella this is. (referring to wildhostile message)

That was a good link to a ppa that you found. I installed Cinelerra from there with no problems on Karmic. I directly downloaded the three lib dependencies first (libguicast, libmpeg3hv and libquicktimehv) and installed them, then d/l Cinelerra and installed that. And it works.

It looks like a serious program to someone like me, used to Ulead Video Studio, and trying Kdenlive!

---

### Post by Rumpty on 2010-08-17
But it says it is version 2.1 CV

---

### Post by OriolCorbella on 2010-09-02
I can't install it because I can't install libquicktimehv because I can't install libfaad0. As you can see, I can't install nothing! xD

What's this of Cinelerra 4.2? I heard about a 4.3 build, and a 5.0 developement...

---

