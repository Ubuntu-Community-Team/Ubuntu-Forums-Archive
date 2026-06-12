---
title: "Intalled LMMs , where is it ?"
date: 2006-07-07
forum: Installation &amp; Upgrades
---

### Post by nobodysdarling on 2006-07-07
New to Linux/Ubuntu and am a recording engineer exploring new app's.  installed LMMs  through the synaptic manager . But I cannot locate it anywhere on my drive ?

---

### Post by nobodysdarling on 2006-07-08
And to explain what I mean by LMMS , it's a MIDI/Audio sequencer. It said it was installed , but a search of my files reveal's nada. So I suppose I will head over to LMMS's site to find some info . Thanks community for the boards , and all the help . I am excited about Linux once I get the last little tweaks made to my system , and sweet music pumping out my speaker's.

I went to the site's WIKI , and here [http://wiki.mindrules.net/doku.php?id=documentation:installation]("http://wiki.mindrules.net/doku.php?id=documentation:installation") are the install direction's. Looks Greek to me , can someone help me understand this process  , or point me toa  tutorial to get me going ? Thanks in advance

---

### Post by Sandsound on 2006-07-10
You can start it by typing lmms in a terminal, or you can add a desktop icon by rightclickking on your desktop and select "create launcher", in the window that pops up you just fill out
name : LMMS
command : lmms
pick an icon and you should have a nice launcher on your desktop :-)

The one in the repositories should work just fine, just search for lmms and mark the "lmms" and the "lmms-common" for instalation.
I can highly recommend the latest version, it has some wery cool features. I know it looks a bit geeky, but give it a go and write here if you run into problems.

you can try this :

download the 0.1.4 source here :
[http://sourceforge.net/project/showfiles.php?group_id=105168&package_id=113209](http://sourceforge.net/project/showfiles.php?group_id=105168&package_id=113209)

right click the file you downloaded and select "extract here"

open a terminal and cd into the directory

./configure

make

make install

If you run into problems, the error you get will tell you what you nead to do, if you nead some extra things installed it will also tell you this.
just post your errors here and I'll be glad to help you through it.

---

### Post by nobodysdarling on 2006-07-11
Thanks so much , I will give it a go . I am looking for a good midi sequencer , this looks like I can get some work done . I am coming from OSX/Ableton Live , XP/Ableton Live .

---

### Post by Sandsound on 2006-07-11
> **nobodysdarling said:**
> I am looking for a good midi sequencer

Ardour2 looks quite cool but is far from ready, so althou LMMS is missing some things, its the best solution so far (imho).
I have tryed Rosegarden4, Muse and other sequencers, but none of them is as smooth to work with, Rosegarden crashed several times as I tryed to save a song :-( and it acts funny when you try to write songs thats more that 3minutes long, both Rosegarden and Muse are not as intuitive to work with as LMMS.
I have been useing Cubase for about 10 years, and switching to LMMS is wery easy. Now I just nead to get "Rise of nations" to run on Linux (or a mltiplayer option in "Glest"), then I'll be windows-free :-)

---

### Post by nobodysdarling on 2006-07-11
How do install Bristol synth's ?

---

### Post by Sandsound on 2006-07-14
> **nobodysdarling said:**
> How do install Bristol synth's ?

Just download the "bristol-0.9.1-linux-glibc.tar.bz2" file from here :
[http://www.slabexchange.org/index.cgi?DOWNLOAD](http://www.slabexchange.org/index.cgi?DOWNLOAD)

Extract the files and you'll find a "startBristol" in the bin folder, just run that and you should have a Moog synth, no nead to install... ;) 
There are more options, but these you can find in the file "readme.release" file.

It's not as cool as the "real" Moog thou (I miss the arp. and fx's on the back :(  ), But its a lot easyer to use than AMS.

edit : Or... you can install it from Synaptic and run it in a terminal with "bristol"

edit : Or... If you have compiled LMMS with VST-support, why not try Crystal ( [http://www.greenoak.com/crystal/](http://www.greenoak.com/crystal/) ). :D

---

