---
title: "Which Ubuntu to install?"
date: 2007-09-09
forum: Installation &amp; Upgrades
---

### Post by Polish Rifle on 2007-09-09
I have a Gateway solo 1450 as my laptop.  Here are the main specs:

[LIST]
[*]1.2 Ghz processor
[*]128 MB of RAM
[*]40 GB Hard Drive
[/LIST]

I just installed Ubuntu 7.04 on the computer but it runs so SLOW, I can't even do anything (I haven't been able to even try out Ubuntu).  I also have XP on this computer and it ran PERFECT but I wanted something even faster and I've heard tons of good things about Linux.  I'm going to use this laptop purely for word processing and browsing.    

I just read about Xubuntu but I'm even hesitant to try that after my recent experience with installing Ubuntu.  Any suggestions?  I want to try Linux out but XP was doing just fine.  Thanks

---

### Post by Amazona aestiva on 2007-09-09
Because of RAM I advise Xubuntu...
It needs less hardware requirements.

Give it a try!;)

---

### Post by Warren Watts on 2007-09-09
Adding an additional 128MB  (or more)  of RAM to that computer will make a HUGE difference in performance.  128MB is a bare minimum.

Xubuntu would definitely run better on 128MB as well as a few other Linux distros designed for older slower hardware, like DSL (Damn Small Linux) or Wolvix Cub

Archlinux is another possibility, but it requires a little more work to get installed.  Arch probably isn't  the best suggestion for someone completely new to Linux.

---

### Post by Polish Rifle on 2007-09-09
What will I miss out on if I go Xubuntu vs. sticking with a slow Ubuntu?

---

### Post by Amazona aestiva on 2007-09-09
Xubuntu is perfect for surfing on the internet or office work with OpenOffice.
I know nothing that You will miss... Try it!

---

### Post by Pharisee on 2007-09-09
An another alternative could perhaps be [Fluxbuntu](http://www.fluxbuntu.org)? It is more lightwieght than Xubuntu. I do not know what they offer in terms of software, but I am sure using apt-get you could install Open Office and Firefox if it is not already available.

Note: This distribution is in its early stages.

---

### Post by ajgreeny on 2007-09-09
Did XP really run properly with that slow a cpu and so little ram?  I'm really surprised if it did.  But perhaps "slow" means different things to different people!

---

### Post by Polish Rifle on 2007-09-09
I had XP down to the bare bones with only running Firefox and Googletalk as applications at the start up.  I also had Word on there but wouldn't use it all the time.  Even now with both OS's installed XP is faster.

---

### Post by Amazona aestiva on 2007-09-09
I can't believe it! But You've found the best for You... How can it be?:confused:

---

### Post by Polish Rifle on 2007-09-09
I'm considering Fluxbuntu, but once again, what is the difference between Flux vs. X?  I can't seem to find the alternate-text install for Flux.  And it also seems like it is hard to get all the essential software for Fluxbuntu.

---

### Post by benhagerty on 2007-09-09
Maybe Slackware?

---

### Post by rsambuca on 2007-09-09
With the system resources you have, I highly recommend that you do a minimal installation and then add specific packages that you require.  Fluxbox should fly on your system compared to XP.  I also recommend something like abiword instead of the rather heavy OpenOffice.

EDIT:  This [website]("http://www.psychocats.net/ubuntu/minimal") has decent info on setting up a lightweight system based on ubuntu.

---

### Post by maybeway36 on 2007-09-09
Don't forget to install xorg!

---

### Post by misfitpierce on 2007-09-09
Wont miss anything you can run same app's if needed. Can also run KDE apps. XFCE in Xubuntu just loads faster and runs lighter and better on lighter hardware... Mainly ram.

---

### Post by ev5unleash1 on 2007-09-09
There are some applications that only really work or work properly on Kubuntu or Ubuntu. You should TRY Ubuntu and see how it runs. IF it runs good for you then keep it. If not then use Xubuntu. I think that Kubuntu uses a bit more resoruces will it's small effects and added services but it's all up to you. Just try to do one or two things at once if your using Ubuntu or Kubuntu.

---

### Post by ryno519 on 2007-09-09
> **ev5unleash1 said:**
> There are some applications that only really work or work properly on Kubuntu or Ubuntu. You should TRY Ubuntu and see how it runs. IF it runs good for you then keep it. If not then use Xubuntu. I think that Kubuntu uses a bit more resoruces will it's small effects and added services but it's all up to you. Just try to do one or two things at once if your using Ubuntu or Kubuntu.

I haven't run into any GNOME or KDE app that wouldn't run on GNOME, KDE, Xfce, what have you for quite a while.

Xfce should be good on there, but your big problem is going to be the applications you're running, not the DE. Firefox for instance can take up quite a bit of RAM using its default settings. Might be wise to buy a 512 meg stick. They're not too pricey and on Xfce I don't think I've ever went over 350 megs doing my normal routine of browsing, chatting, programming, etc. 512 would give you a lot more freedom.

For instance, if you wanted to run a KDE app under Xfce you wouldn't just be loading that application into RAM. You would be loading several KDE libraries into memory as well. With 128 megs of RAM this is a stretch.

---

### Post by rsambuca on 2007-09-09
> **ev5unleash1 said:**
> There are some applications that only really work or work properly on Kubuntu or Ubuntu. Which ones are those?

---

### Post by ev5unleash1 on 2007-09-09
Well some ones that only use the KDE or Gnome envirment and need a bit more resources to run. IF you use the Xubuntu OS to run them you have to load an entire library (aka all the codes from another version of Ubuntu) to run it which we ultimatly suck even more resources. I think that there are more Ubuntu applications than any other taste . But that's from my expierence.

---

### Post by aysiu on 2007-09-09
I know a lot of people recommend Fluxbox, but I find it a bit hard to get used to. From an ex-Windows user perspective, I took more quickly to IceWM. Since you already have Ubuntu installed, [make sure you have extra repositories enabled](http://www.psychocats.net/ubuntu/sources), and then install *icewm*, log out, select *Options*, *Sessions*, and *IceWM*. Log back in again. For more tips and tricks related to IceWM, check out [this thread](http://ubuntuforums.org/showthread.php?t=263710).

And if XP really does run that well, I've heard using [LiteStep](http://www.litestep.net/) can slim it down even more, though I had trouble getting that configured properly. Don't forget that there are lots of [open source programs for Windows](http://www.opensourcewindows.org/), so you can get the benefits of open source without switching to Ubuntu right away.

---

### Post by rsambuca on 2007-09-09
> **ev5unleash1 said:**
> Well some ones that only use the KDE or Gnome envirment and need a bit more resources to run. IF you use the Xubuntu OS to run them you have to load an entire library (aka all the codes from another version of Ubuntu) to run it which we ultimatly suck even more resources. I think that there are more Ubuntu applications than any other taste . But that's from my expierence.

Could you please be more specific.  Especially from your original comment that> There are some applications that only really work or work properly on Kubuntu or Ubuntu.


What specific applications have you found that will not work properly except on Kubuntu or Ubuntu?

---

### Post by Polish Rifle on 2007-09-10
Report:

Well I've installed Xubuntu and it still appears pretty slow compared to my XP set up.  Certain things load fairly quickly on Xubuntu but browsing on Firefox is laggy.  I think it took me 30 seconds after I typed in google.com for it to go to the page.  And whenever I load an application it takes a good 20-25 seconds.

However, some things load quickly.  Like when I switch work spaces, or after I load some applications once they are in the RAM so I can utilize them again.

Haven't used Gaim yet but does it have GoogleTalk?

I'm gonna give it a shot for a week, and if I continue to have to wait for windows to open, websites to load, or applications to load I'm just going to have to go back to XP.  I really like what Linux is all about, but maybe my comp is just more compatible with XP.

---

### Post by ryno519 on 2007-09-10
> **Polish Rifle said:**
> Report:

Well I've installed Xubuntu and it still appears pretty slow compared to my XP set up.  Certain things load fairly quickly on Xubuntu but browsing on Firefox is laggy.  I think it took me 30 seconds after I typed in google.com for it to go to the page.  And whenever I load an application it takes a good 20-25 seconds.

However, some things load quickly.  Like when I switch work spaces, or after I load some applications once they are in the RAM so I can utilize them again.

Haven't used Gaim yet but does it have GoogleTalk?

I'm gonna give it a shot for a week, and if I continue to have to wait for windows to open, websites to load, or applications to load I'm just going to have to go back to XP.  I really like what Linux is all about, but maybe my comp is just more compatible with XP.

I'd check how much RAM you're using and make sure you're not out of RAM and using the swap space a lot. That would explain the slowness. If that's the case, you will either need to download less RAM intensive apps or install more RAM.

And yes, Gaim can connect to Google Talk. Here's a howto.

[http://www.google.com/support/talk/bin/answer.py?hl=en&answer=24073](http://www.google.com/support/talk/bin/answer.py?hl=en&answer=24073)

---

### Post by totalnub on 2007-09-10
hey man, don't give up. i've found that puppy linux works wonders. brought back to life my old optiplex gx220 PIII 900mHz 128Mb _RDRAM_ 10 gig hdd. it completely loads into ram off the cd. i.e. the performance while running it as a live cd is the same as installing it. [http://www.puppylinux.com/download/downpage.htm](http://www.puppylinux.com/download/downpage.htm)

---

