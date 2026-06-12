---
title: "A Step by Step Guide To making my laptop run linux"
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by Megabreath on 2007-05-18
Hi im new here, and have been considering changing my win 98 to linux, i was advise by a member on a seprate forum to come here for help, basically im looking for a linux alternative for a OS thats similar to win98 and a program that runs old MS office files

My laptops details:

Processor AMD K-6
RAM: 128MB
HDD: 8GB+154MB (not sure on the model)
CD drive(s) TEAC CD-224E
floop drive(s): 1 Standard floppy disk drive
Wireless card:none
Ethernet card:PC line 10/100 32bit cardbus
Model: CTX EzBook 800

hope that enough info, if you could, try to keep it simple in not exactly a wiz kid :(

---

### Post by dannyboy79 on 2007-05-18
well, you should first download the xubuntu fiesty, edgy or dapper Alternate Install CD from here: [http://releases.ubuntu.com/7.04/](http://releases.ubuntu.com/7.04/)

I am suggesting xubuntu because of your limited system specs and also I am suggesting the alternate cd because it's text based and not graphics demanding.  if you know how to use bit torrent than download  it that way otherwise just chose the normal Alternate install iso file and download it to your desktop or whereever. make sure the iso is ok by verifying it's md5sum. there are many free md5sum checkers out there for windows, you'll need to gogle this as it goes beyond my time limit. once you verified the md5sum matches the one on the same website you downloaded the iso from, you'll then need to burn it to a disc using software that can burn images to discs. this is different than just burning a data cd, you need to use a tool that can burn images, like nero, or alcohol120% or similar. then you can simply put the disc in and make sure your bios is booting to cd before hard drive and follwo the installation instructions. 

do you want to keep windows98 or do you want to totally convert? because we can set this up as a dual-boot until you get more comfortable with ubuntu. just chose the option you want and the partitioning stage.

along the way and towards the end it'll ask you for a username and password, make sure you do realize that your entering these and make sure to remember what you're chosing for each!

if you want more detail, there are many guides already written up for installing ubuntu. good luck

---

### Post by aysiu on 2007-05-18
> **dannyboy79 said:**
> well, you should first download the xubuntu fiesty, edgy or dapper Alternate Install CD from here: [http://releases.ubuntu.com/7.04/](http://releases.ubuntu.com/7.04/) I second the motion, but I'd definitely recommend going with 7.04 (Feisty) instead of 6.10 (Edgy) or 6.06 (Dapper).

> if you know how to use bit torrent than download  it that way otherwise just chose the normal Alternate install iso file and download it to your desktop or whereever. make sure the iso is ok by verifying it's md5sum. there are many free md5sum checkers out there for windows, you'll need to gogle this as it goes beyond my time limit. once you verified the md5sum matches the one on the same website you downloaded the iso from, you'll then need to burn it to a disc using software that can burn images to discs. this is different than just burning a data cd, you need to use a tool that can burn images, like nero, or alcohol120% or similar. then you can simply put the disc in and make sure your bios is booting to cd before hard drive and follwo the installation instructions.  More details with screenshots here:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by dannyboy79 on 2007-05-18
aysiu, you're the man! I love your website!!!!!!

---

### Post by stchman on 2007-05-18
> **Megabreath said:**
> Hi im new here, and have been considering changing my win 98 to linux, i was advise by a member on a seprate forum to come here for help, basically im looking for a linux alternative for a OS thats similar to win98 and a program that runs old MS office files

My laptops details:

Processor AMD K-6
RAM: 128MB
HDD: 8GB+154MB (not sure on the model)
CD drive(s) TEAC CD-224E
floop drive(s): 1 Standard floppy disk drive
Wireless card:none
Ethernet card:PC line 10/100 32bit cardbus
Model: CTX EzBook 800

hope that enough info, if you could, try to keep it simple in not exactly a wiz kid :(

I woudl recommend a RAM upgrade as Ubuntu runs better with 256MB.  The hdd will work, but 8GB is a little to small.  40GB 2.5" PATA are under $40 now so for around $60 you could upgrade the RAM and hdd.  Yes use Xubuntu as it is a little more lightweight.

---

### Post by jerrylamos on 2007-05-18
Well, Xubuntu claims to run on 128 MB using the XFCE window manager.  Ubuntu needs at least 192 MB but more like 256 MB MB for the Gnome window manager.  Kubuntu uses more resources yet.

You might have a good shot at Xubuntu Dapper Drake 6.06 or Xubuntu Edgy Eft  6.10.  Xubuntu Feisty Fawn 7.04 has some bugs some of us could help you with, but I'd advise the other releases to start with.

Now the K6 will run, but I don't know how well.  I had a tower with a K6 that was pretty slow.  You can tell pretty much by running CD Live before doing an install; the installed version would run a little faster.

A good way is to get the Xubuntu 6.06 or 6.10 CD and try it CD Live.  Xubuntu has most of the function of Ubuntu or Kubuntu, without as much eye candy, and is a little faster without the eye candy overhead.

Any of them will run Open Office which reads and writes Microsoft Office files as well as its own open standard files, and if course Firefox which looks much like Internet Explorer.

"The Official Ubuntu Book" is a good reference including troubleshooting, from Barnes & Noble or Borders or Amazon or ...  It's got a copy of Ubuntu in it but I don't know about Xubuntu.

Cheers, Jerry

---

### Post by Megabreath on 2007-05-18
thanks :)

well what i really just want is to get rid of the win98 look P.S its a 32bit pc

---

### Post by aysiu on 2007-05-18
> **jerrylamos said:**
> Well, Xubuntu claims to run on 128 MB using the XFCE window manager.  Ubuntu needs at least 192 MB but more like 256 MB MB for the Gnome window manager.  Kubuntu uses more resources yet. Xubuntu *does* run on 128 MB of RAM. It runs. It's not snappy, but it's usable.

> You might have a good shot at Xubuntu Dapper Drake 6.06 or Xubuntu Edgy Eft  6.10.  Xubuntu Feisty Fawn 7.04 has some bugs some of us could help you with, but I'd advise the other releases to start with. I haven't seen convincing evidence (either through forum polls or my own experience) that Feisty is any buggier than previous releases.

> Now the K6 will run, but I don't know how well.  I had a tower with a K6 that was pretty slow.  You can tell pretty much by running CD Live before doing an install; the installed version would run a little faster.

A good way is to get the Xubuntu 6.06 or 6.10 CD and try it CD Live.  Xubuntu has most of the function of Ubuntu or Kubuntu, without as much eye candy, and is a little faster without the eye candy overhead. The live CD won't run on 128 MB of RAM without freezing up.

While Xubuntu may be a friendlier approach, it won't fly on 128 MB of RAM. This will require a little more setup and a lot more questions from you, but your best bet is probably IceWM:
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

You can also look into Fluxbuntu:
[http://fluxbuntu.org/](http://fluxbuntu.org/)

IceWM and Fluxbox are much better for systems with less RAM.

---

### Post by dannyboy79 on 2007-05-18
I happily use Xubuntu Feisty on my ancient Hitachi 266mhz Pentium MMX 128mb ram laptop, 10gb hard driver, 24x cdrom, 4mb video ram using the NeoMagic graphics card. Live cd was a no-go so I had to just dive right in. I did however try out Puppy and DSL on it but still wanted to use Ubuntu but coiuldn't get that on it so I went with the Xst best thing, Xubuntu. (Xst best thing, Xubuntu, gety it, ha ha) I know, horrible joke. Anyway, you'll be fine with Xubuntu on your machine, it will be slower but it will work. You can always try out what Aysiu stated, you can at any point ditch XFCE and do with a lighter windows manager like IceWM or FLuxbox but they do take more effort to learn and configure than Xfce I think. A better option might just be to install the server version , than install your window manager after the fact, then install your file manager like Thunar or ...... damn, I forget the file manager Fluxbox uses at the moment. That way you won't have all the dependencies that you'll get when installing xubuntu. this is just a suggestion i'd like to point out before others tell me that I may scare away potential newbies by telling them to install the server verison and then install a window manager. it will just create a much leaner linux install but again it will take more effort and understanding of things.

---

### Post by RedSquirrel on 2007-05-18
> **jerrylamos said:**
> Now the K6 will run, but I don't know how well.  I had a tower with a K6 that was pretty slow.  You can tell pretty much by running CD Live before doing an install; the installed version would run a little faster.

In my experience, the installed version runs *much *faster than running the LiveCD.




> **dannyboy79 said:**
> I happily use Xubuntu Feisty on my ancient Hitachi 266mhz Pentium MMX 128mb ram laptop, 10gb hard driver, 24x cdrom, 4mb video ram using the NeoMagic graphics card. Live cd was a no-go so I had to just dive right in. I did however try out Puppy and DSL on it but still wanted to use Ubuntu but coiuldn't get that on it so I went with the Xst best thing, Xubuntu. (Xst best thing, Xubuntu, gety it, ha ha) I know, horrible joke. Anyway, you'll be fine with Xubuntu on your machine, it will be slower but it will work. You can always try out what Aysiu stated, you can at any point ditch XFCE and do with a lighter windows manager like IceWM or FLuxbox but they do take more effort to learn and configure than Xfce I think. A better option might just be to install the server version , than install your window manager after the fact, then install your file manager like Thunar or ...... damn, I forget the file manager Fluxbox uses at the moment.

Fluxbox doesn't come with a file manager; you have to install one separately. Some possibilities are rox filer, pcmanfm, and emelfm. Thunar is a nice one, but it has more dependencies.

I agree with the idea of a server plus window manager (Fluxbox or IceWM). It's fast and you don't end up with a bunch of apps you'll probably never use.

---

