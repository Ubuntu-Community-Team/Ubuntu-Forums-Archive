---
title: "Hugin panotools or any other stitching soft"
date: 2004-11-10
forum: Installation &amp; Upgrades
---

### Post by xutopia on 2004-11-10
has anyone had any success installing and using any software to stitch pictures to make a panoramic view?

I haven't had any luck with Hugin or panotools yet.  I'm wondering if there is anything else that could work.

---

### Post by puzzledm on 2005-01-26
I am about to download them this evening and see if I can get them working... I will let you know how it goes.  

I have downloaded the Panorama Tools but they are really very complicated - there must be an easier way! ([http://www.path.unimelb.edu.au/~dersch/](http://www.path.unimelb.edu.au/~dersch/)) But they are worth a look (you will need java)

---

### Post by puzzledm on 2005-01-27
Hello (if anybody is reading this thread any more) I tried and tried to get it working but can't ... tried loads of different things .... so if anyone has any idea please help.

---

### Post by flaming_monkey on 2005-02-04
I had a quick attempt to install Hugin but ended up in dependency hell.

If anyone has any other tool or managed to get hugin to install please post your information here.

---

### Post by puzzledm on 2005-02-04
I actually managed to get hugin to install but getting it to work is a whole new head ache!  And as far as I can see it is not a very intuitive piece of Kit.  I am used to using Photo-Stitch on windows which is really straight forward ... pick your pictures and press stitch none of these control point thingies!!

---

### Post by piedamaro on 2005-02-04
I've found this guide: it is immensely useful to me. You'll know everything you need to make _great_ panoramas (I've made few of them) :).

The proccess ivolves to use autopano-sift + hugin + enblend, these are amazing apps with powerful algorithms which do the following:
1)autogenerate control-points
2)stich images
3)blend images together

The process is very easy once you have a grasp of it.

The site is here: [One Guy With  A Camera](http://rbpark.ath.cx/) (go under articles)
Hope this helps!

---

### Post by puzzledm on 2005-02-04
I can't get autopanog.exe to work like he says in his instructions.  It keeps complaining about gtk-sharp assembly or something.  Any ideas?

Or basically could you step me through what you had to install and where from to get it working.  It would be most grateful. 8-[

---

### Post by piedamaro on 2005-02-04
[QUOTE=puzzledm]I can't get autopanog.exe to work like he says in his instructions.  It keeps complaining about gtk-sharp assembly or something.  Any ideas?

Or basically could you step me through what you had to install and where from to get it working.  It would be most grateful. 8-[[/QUOTE]
 You need mono. I don't know if it's present in the repositories, sorry. Actually I didn't install those programs on ubuntu, but when I'll do it, I'll post a step by step guide.

---

### Post by puzzledm on 2005-02-05
That would be amazing if you could I have spent about three months trying to make a panorama in Ubuntu - maybe you could out it in the HowTo section for everyone :grin:

---

### Post by piedamaro on 2005-02-14
[QUOTE=puzzledm]That would be amazing if you could I have spent about three months trying to make a panorama in Ubuntu - maybe you could out it in the HowTo section for everyone :grin:[/QUOTE]
Menwhile I'v found debian packages: [http://3demi.net/debian/debs/](http://3demi.net/debian/debs/)

---

### Post by puzzledm on 2005-02-15
Good stuff - They all seem to be the most recent as well, which is the problem I have had with other places.

Keep up the good work.

I actually finally got hugin to work though I don't really know how!!

---

### Post by ericsp on 2005-02-15
I managed to get it to work some time ago. It took me a hell of time finding all the packages. I found it a very intuitive program. Under fedora I could make panorma's but under Ubuntu it crashes.

---

### Post by piedamaro on 2005-02-15
[QUOTE=ericsp]I managed to get it to work some time ago. It took me a hell of time finding all the packages. I found it a very intuitive program. Under fedora I could make panorma's but under Ubuntu it crashes.[/QUOTE]
 Where does it crash? And with what error messages?

---

### Post by ericsp on 2005-02-22
I reinstalled/upgraded from "deb [http://3demi.net/debian](http://3demi.net/debian) debs/./" (apt repository). Now I do get an error message when pressing Stitch:

Error executing PTStitcher.exe
Stitching failed
PTStitcher exited with nonzero error code.
[OK]

Does that help? Seems like it is calling for a windows executable.....

---

### Post by flaming_monkey on 2005-03-03
I'm still lost with all these dependencies.  I'm running warty, and if any kind soul can help me install hugins I would be most greatful.

Thanks.

---

### Post by kswenson on 2005-06-08
I have used hugin on ubuntu...
   you must add the line "deb [http://3demi.net/debian](http://3demi.net/debian) debs/./" to your /etc/apt/sources.list and then do an "update" in synaptic or apt.

I have to specify the control points manually because autopano doesn't work.
Make sure to use "nona" as the the stitching engine in the "Stitcher" tab.

---

### Post by caratcus on 2005-07-22
I think that this is the wrong place for the question I had

---

### Post by kblood on 2005-08-10
I have added:
deb [http://3demi.net/debian](http://3demi.net/debian) debs/./

to my sources.list file, and sure enough, I can find hugin in aptitude now.
But it complains that libpano12 depends on a version of libc6 that it can't find.

I see that I have the Ubuntu libc6 version, which is slightly different than the one libpano12 requires.

Is there any way to get around this? I suspect it might work anyway, but I need to "force" it somehow, to get it installed...

Any ideas?

PS: I just found the package ale, and it seems to be able to stitch images, went through the manual, and I am now trying to do a panorama with it... Couldn't find any gui for it.

PS2: ale didn't do what I expected, I misinterpreted the parameter -follow. It is an interesting program anyway, but for something quite different.

---

### Post by icewt on 2005-08-11
[QUOTE=kblood]I have added:
deb [http://3demi.net/debian](http://3demi.net/debian) debs/./

to my sources.list file, and sure enough, I can find hugin in aptitude now.
But it complains that libpano12 depends on a version of libc6 that it can't find.

I see that I have the Ubuntu libc6 version, which is slightly different than the one libpano12 requires.

Is there any way to get around this? I suspect it might work anyway, but I need to "force" it somehow, to get it installed...[/QUOTE]
I was able to install libpano12 by downloading the latest packaged version from 3demi.net to my computer, and forcing it to be installed even though the dependencies are not met. Here's how it's done:
```
sudo dpkg --force-depends -i libpano12_2.7.0.9.20050610_i386.deb
``` 
I haven't tried to use it yet though, so I don't know whether it works or not.

---

### Post by kblood on 2005-08-11
Mmm... interesting. I will give it a try. Maybe the safest option would be to force the installation of Hugin in this way and give it a go. If it doesn't work, just remove it, and you are back to clean state...

Not at my computer to test, so I don't remember the dependency structure, but I will certainly give this all a go.

---

### Post by icewt on 2005-08-11
[QUOTE=kblood]Mmm... interesting. I will give it a try. Maybe the safest option would be to force the installation of Hugin in this way and give it a go. If it doesn't work, just remove it, and you are back to clean state...[/QUOTE]

And you'd try to use Hugin without libpano12? I think libpano12 is quite important part of Hugin, if you want to do something with it.

---

### Post by kblood on 2005-08-11
Right you are, I wasn't thinking very clearly. Anyway, I will play with it... :)

---

### Post by kblood on 2005-08-13
Ok, I used:
sudo dpkg -i --ignore-depends=libc6 libpano12_2.7.0.9.20050610_i386.deb

and then I ran aptitude, forced it to keep the package, and used it to get hugin and emblend.

Hugin runs, but I get the feeling I am not getting all it's power. The resulting panorama has serious problems with exposure and the seams are really sharply visible.

I am going to give the long way a shot, with compiling and everything, and see what happens. Also a learning process :)

---

### Post by kblood on 2005-08-13
Following the article here:
[http://rbpark.ath.cx/articles/compile-hugin-ubuntu](http://rbpark.ath.cx/articles/compile-hugin-ubuntu)
I managed to get Hugin installed, and it runs.
Going to test a panorama now.
Autopano also is installed and runs, so it's looking good!

UPDATE: Wonderful! My first panorama created with free tools!!! :) It wasn't a difficult one, so the result was quite decent. In any case, the programs work, which is the needed start!

I have to say that what I tried before, forcing the install of libpano12 from the repository mentioned in this thread, also seemed to work. Enblend also got installed from that repository just fine, and Hugin as well once libpano12 was installed.

So installing autopano as mentioned in the article would have been enough afterwards to have a full working set of tools.

The article is fine, and has the advantage of getting the latest versions of Hugin and Panotools, so it's still a better option. But it gave me a couple of small problems, so for the people that want a simpler option, forcing libpano12 would probably be the way to go.

---

