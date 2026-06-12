---
title: "Navit GPS instruction manuals"
date: 2012-02-26
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2012-02-26
Want to use Navit for GPS purposes.

Installed Navit along with a 'World map' as Wiki instructs from Navit:: Planet Extractor. 
[http://maps3.navit-project.org/](http://maps3.navit-project.org/)
Navit looks nice but seems a bit involved in setting up. Are there any good instruction sites that can help you out in configuring Navit to get it to work as a GPS device?

---

### Post by raja.genupula on 2012-02-27
[http://wiki.navit-project.org/index.php/Configuring_Navit](http://wiki.navit-project.org/index.php/Configuring_Navit)

Hi have you gone through that ?

---

### Post by cybrsaylr on 2012-02-27
Yes I read it but to tell you the truth I didn't have a clue it was that difficult to set up. I haven't done that amount of configuring as yet. Was hoping all that was needed was a few lines of code in terminal and it would be good to go.

I checked out YouTube for Navit and it looks nice on a few clips but there was no instructional clips on how to get it running. 

I have used MS Streets & Trips with GPS locater but wanted to try a linux version.

---

### Post by cybrsaylr on 2012-03-03
Navit looks pretty complicated.

Are there any other Linux GPS apps more simple to set up and use?

---

### Post by cybrsaylr on 2012-03-04
Anyone?

---

### Post by ldsnet on 2012-05-09
Depending on your needs - there are few options.  Based on what I have been reading, if you want turn-by-turn street navigation, then working your way through Navit will be your best bet.  
 
If you just want maps and plotting, look at GPS Drive or Marble may contain what you are looking for.  
 
Yes Navit appears to be a pain to configure - read that through a number of forum listings.  Sorry I have not had the pleasure  of attempting it yet (and it will be months before I get the chance).
 
Please post what fixes your problems so we all can learn from the mistakes.

---

### Post by ldsnet on 2012-07-19
> **ldsnet said:**
> Depending on your needs - there are few options. Based on what I have been reading, if you want turn-by-turn street navigation, then working your way through Navit will be your best bet. 
 
If you just want maps and plotting, look at GPS Drive or Marble may contain what you are looking for. 
 
Yes Navit appears to be a pain to configure - read that through a number of forum listings. Sorry I have not had the pleasure of attempting it yet (and it will be months before I get the chance).
 
Please post what fixes your problems so we all can learn from the mistakes.
 
NavIT update.  Spent the last week attempting to get NavIT to work on my older machine running Xbuntu (standard Ubuntu would not build on older machine).
 
First build was successful, but it would NOT find GPSD to update position.  So I started to install extra packages to attempt to get NavIT .configure file locate my GPS correctly.  So far no luck.  The latest build actually crashed with too many not needed packages loaded.  
 
Going to try again on a different machine (virtual machine running on my laptop) and see if I get different results.  There are TONS of configuration possiblilities in NavIT.  The Wiki and help files are not too bad, but certainly not a plug and play apt-get system (or for the feight of heart).  Next attempt will be to see if I can complie GPDS into the kernel instead of running it as a deamon.  
 
Fun times.  
 
If anyone has successfully built Navit and it works WITH a GPS, please chime in; I am interested in your configuration and what worked for you.

---

### Post by cybrsaylr on 2012-09-23
Still can't get Navit to work. I play around with it occasionally trying to configure it but have had no luck so far.

Navit opens, shows all its settings but won't load any maps or show where I am when I plug in the GPS receiver. The various help sites visited don't offer much help.

---

### Post by jonnysat on 2012-12-20
Navit works but it's a PAIN to get set up properly. As of the 19th of December of 2012 I have successfully run navit on a windows xp pro based laptop and a linux debian 6 squeeze laptop! But it took MONTHS of playing around with it on and off to figure out. 

The good news is, once you understand how the settings in navit are correctly manipulated.. it's NOT really that difficult to get it working! The breakthrough for me was once I realized the thing about the "navit.xml" file. That's where the settings are all adjusted. Anything in there regarding a "mapset" must be right or you won't see ANY map show up in navit to be used. The format has to be adhered to so the program can read it and it can't have "yes" enabled to more than one at at time... whether a default map already in there or one you just added. My linux test wouldn't show a map I just added cuz it already had some other one in it enabled! What a NIGHTMARE that was to figure out!!!

Another prob I had with the linux install was with the permissions to modify the "navit.xml" file. I ended up just saving a copy of it and deleting the original through a terminal command override and then relocating the saved copy to somewhere the program could find it and use the modified info... such as MY map and local area. Somehow the linux install had it set to read only. My windows install didn't do that and I was able to modify it directly and show the map for my area.

The gps receiver has to also be set up so the computer and OS and program can use it. I just used gpsd in the debian repository for the linux install and that seems to be working ok... but it doesn't always catch the first time I launch the program? Sometimes I have to pull the usb connection, reinsert and then reload navit. I'm still working on that machine. For the windows I just hunted around for the drivers for my specific gps receiver... a GPS-500 sirf III and that worked.

I ultimately found all this information by just doing very basic google searches like... "navit map windows" and navit map debian" and LOTS of VERY careful reading of each and EVERY line of information on the pages!

 It's amazing how much time can be wasted just because you didn't notice one very important piece of information on one single line on some webpage?!?

---

### Post by cybrsaylr on 2012-12-20
Thanks for the info.
I kinda gave up on Navit after playing around with it. Just couldn't get it to work. Even the Navit site wasn't much help. 

The one thing the does work fairly well is Planet Extractor:
[http://maps3.navit-project.org/](http://maps3.navit-project.org/)

---

