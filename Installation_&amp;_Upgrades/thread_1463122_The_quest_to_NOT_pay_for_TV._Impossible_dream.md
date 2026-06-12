---
title: "The quest to NOT pay for TV. Impossible dream?"
date: 2010-04-26
forum: Installation &amp; Upgrades
---

### Post by joejoe148 on 2010-04-26
I am trying to setup a linux box that is a combo mythtv frontend/backend and a gnome desktop(for watching video from hulu etc).  I started with an asus-amd 3000 setup but it never worked consistently and it was going to cause a divorce.  So I exchanged the linux box with the household desktop.  an amd64 with 3 gigs of memory and a better graphics card.  this is the setup process so far.  

Install ubuntu 9.10 64 bit
activate nvidia drivers
update everything
install flash
then...and this is where i evidently misremembered something...
sudo aptitude install mythbuntu-desktop

I went though all of that and lost gnome.  What I was had before that wouldnt consistenly run flash and stuttered a lot had the gnome desktop and ran the mythbuntu backend in the background.  When I wanted to watch tv I started the frontend.  If it was in a good mood it worked fine.  most of the time I beat my head on the table and made excuses.

Should I be trying for that or should I learn to love X and figure out how to use it.  even after a few beers.

---

### Post by dannyboy79 on 2010-04-26
not exactly sure what you're asking here but this is what I would do.
you can select which desktop environment gets started at gdm where you enter your username and password. it probably says xfce-session or xfce now, you want it to say gnome? it's there somewhere I know it is. So, change it back to gnome versus xfce-session or xfce or mythbuntu-desktop which runs a hybrid XFCE. that's if you want to run gnome

OR

if you dont see anything liek that because mythbuntu is logging you straight into mythtv then you need to exit mythtv by hitting escape key. once back at the desktop start the Mythbuntu Control Centre. within that you can change which desktop environemnt you use. you can start that with this command
mythbuntu-control-centre
you may need to start it with gksudo prefixed before the command.

good luck

---

### Post by joejoe148 on 2010-04-26
I found that in the control center.  It was set for gnome already.  I reselected it anyway and applied.  It found something to change and gave me smaller fonts and a fuzzy x desktop. 

Its ok though I think I will start over with the ubuntu install.  I have no sound in myth nor do I have a functional remote control.   

There are posts about compiling your own drivers for the hvr 1600 but I thought it was specifically for the 32 bit versions.  

Something for me to do after dinner.

Suggestions for the reinstall?  should I start with Myth or start with ubuntu since I want a functioning desktop with myth in the background?

---

### Post by grege on 2010-04-26
Do you really want or need all of MythTV. If you just want a simple VCR replacement and to watch TV then there are much simpler ways.

I would get the 10.04 RC 32 bit install and do a clean install, add flash and whatever else you need. I use 64 bit on some machines but IMHO 32 bit still has the superior codec support, and as your machine only has 3gb ram there is not much to be gained from going 64 bit. Get w32codecs from Medibuntu.

Then install Me Tv and/or Kaffeine. Kaffeine is a KDE program so it will drag in a lot of extra libraries. Ensure libxine-ffmpeg1 is installed so the sound will work from a KDE program running under Gnome.

Either of these programs provides TV viewing and recording with all the expected timers. They do not have extensive program guides and the other stuff MythTV provides. Depends what you want/need on a machine that you want to use as a normal desktop.

---

### Post by dannyboy79 on 2010-04-27
> **joejoe148 said:**
> I found that in the control center.  It was set for gnome already.  I reselected it anyway and applied.  It found something to change and gave me smaller fonts and a fuzzy x desktop. 

Its ok though I think I will start over with the ubuntu install.  I have no sound in myth nor do I have a functional remote control.   

There are posts about compiling your own drivers for the hvr 1600 but I thought it was specifically for the 32 bit versions.  

Something for me to do after dinner.

Suggestions for the reinstall?  should I start with Myth or start with ubuntu since I want a functioning desktop with myth in the background?
i would start with mythbuntu 9.10 and tell it to install a gnome desktop through control center if you don't want XFCE desktop. 10.04 is pretty stable because I am running it but you may want to start with 9.10 and if everything is ok, upgrade from there once april 29th hits and lucid is released.

---

### Post by joejoe148 on 2010-04-27
Thanks, I will give it a shot...tonight.  I loaded ubuntu 9.10 again last night fresh and thought I would look again at installing myth on top.  I will download the mythtv 64bit edition and see where that takes me

---

