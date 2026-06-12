---
title: "Trying KDE 4.3 on Karmic- fresh install or kde-desktop install?"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by murderslastcrow on 2009-10-23
So, just wondering how I should go about this. I have about 20 GB of free space on my hard drive to install pretty much anything. Would it be a better experience to install Kubuntu from scratch in 6 days, or should I just install kde-desktop in the Ubuntu Karmic RC I'm currently running?

Are there speed/integration benefits from doing Kubuntu from scratch? Will there be too many new KDE apps flooding my menus (I hate clutter)?

Just wondering which would be suggested from a KDE user, since I'm totally up for either way. Choosing a KDE session or booting into Kubuntu, it's the same for me either way, but I really wanna' see what KDE's all about so I can make suggestions to noobz.

---

### Post by caryb on 2009-10-23
If you want the KDE/Kubuntu experience I would install Kubuntu on a seperate partition for the reason you said clutter, also there could be some idiosincracies with GDM etc conflicting with KDE.


Cary

---

### Post by jbrown96 on 2009-10-23
If you care about clutter at all, then install it cleanly. Here's something that I've been doing recently, and it's really great if you run multiple distros or change distros often. Create one very large partition on your hard drive, and two others that are around 5-6GB. When you install ubuntu use one of the small partitions for / and the large partition for /home. You can do the same for kubuntu. Now all your settings (like Firefox history) will be the same on ubuntu and kubuntu. The only thing to remember is that when you are installing make sure to set the mount point and type for /home, but DON'T format it or else you will lose all your data. 
Really there's no difference between running ubuntu + kde-desktop and kubuntu. The system will run the same, but all the Gnome apps will appear in KDE and vice versa. One of my favorite features in KDE is Krunner. Press Alt+F2 to bring up a command launcher. Krunner is much better than the gnome equivalent because it will search as you type. If you have a ton of gnome apps (there tend to be tons of little apps that you would never use, like the stuff in preferences) it will seriously degrade the user experience with krunner. 

One piece of advice that I do have for KDE users is to ditch KDE's network manager and switch back to gnome's if you use wireless. ```
sudo apt-get install network-manager-gnome
``` ```
sudo apt-get remove network-manager-kde
``` Logout, then back in. You can launch it with alt+f2 then ```
nm-applet
``` You will want this to work automatically in the future, so open system settings (in krunner)-->Advanced tab-->autostart. Add a new program, then next to the black line click the blue icon, then click root on the left, and navigate to /usr/bin and select nm-applet. Wireless will be much more reliable and easier to use.

---

### Post by murderslastcrow on 2009-10-24
Cool. Yes, Plasma and Krunner seem to be to be great additions, and somehow KDE just seem really evolved. So does Gnome, but KDE seems to really include a lot of extra stuff you might love, just in case.

Which at this point seems kinda' fun since I'm not new to Linux by any means. I'll strongly consider using nm-applet instead, since you suggested it. Thanks for the support guys- getting my USB drive ready for this, now. Should be fun (Using the RC, who cares? XD).

Also, I read about having a separate home partition and how it automatically uses your files between distros. I think that's just about the coolest idea ever, and I plan on doing it soon since I have a giant HD anyway.

Again, thanks for the suggestions. This is gonna' be a fun weekend, I can tell.

---

### Post by DodgeV83 on 2009-10-24
Every time I've installed kde-desktop on top of my Ubuntu installation, I've ended up reformatting and installing Ubuntu again from scratch.

Every. Single. Time.

It will mess with your Gnome fonts, seemingly irrevocably.  It will change your mouse pointer and "thinking" animation in Gnome, irrevocably.  It will change something about your program rendering, so even in Gnome some of your programs won't look right, either the fonts will be messed up, or the graphics will be out of place...etc.

I highly recommend installing to a new partition.

---

### Post by murderslastcrow on 2009-10-24
Haha. I'm just glad we can use Gnome apps in KDE and vice versa. I mean, that's a feat that's rarely mentioned by the people in the Linux community, to my notice.

I mean, seriously. People working together to make things awesome. How lucky are we? Then again, I hear some people saying that there's not as much work going into interoperability these days- is that true? I've never noticed any issues with Qt and KDE stuff in Gnome.

---

### Post by Lem on 2009-10-24
Gnome stuff is looking much better in Kubuntu now (yes, even OOffice) with this new release. I've switched over having given KDE a few goes in the past before retreating back to the comfort of stock Ubuntu.
Give it a go.. I'd go with the seperate partition option.

---

### Post by murderslastcrow on 2009-10-24
Well. I'm impressed.

I think I'll probably keep using Gnome, but I can definitely see why people like KDE. I think it's great for people who may be switching over from Vista and wanna' see the same flashy effects. I like that they include lots of cool features by default rather than resorting to compiz to fill in.

I also think it's awesome how snappy it all is. It really is very fast, and my system monitor is extremely happy with it. It may be the lack of compiz enabled so far, but it's very promising!

I think some of my friends who've switched may have liked it better at first if they'd seen all the flash and pizzaz of KDE first. But Gnome is better for beginning PC users, since it's all laid out plain and simple (Applications/Places/System). I like that. Now, I must mention that KDE is a lot less complicated than say, the Windows GUI (WAY less). But still involves a lot more clicking than I do in Gnome.

I think one of the most exciting things is the integration, Konqueror's rendering engine (and layout, for that matter), and Plasma/Krunner. There's just a lot of really cool stuff in here!

And again, it seems so FAST. Could be that the fade-ins are faster than the fade-outs. Not so sure. Great sound effects, and for once I don't feel like changing the default theme (although the new Human theme for Gnome is making some steps in the right direction).

I'm thinking it may be good to keep this around just for the wow factor. XD It's wow in a different way than Gnome, although Gnome seems to fit my work flow better. Definitely a worthwhile adventure, and I plan to play around with it a lot more. It's cool that I don't really need compiz installed to get some sexy stuff goin'.

---

### Post by wxnker on 2009-10-24
I never install kubuntu-desktop on a ubuntu install. I don't like those cluttered menus with kde and gnome apps mixed in together. It's a mess, imo. I know it's possible to prevent this with "hacks", but I think this should be improved by default.

In other distros I use (or have been using) the clutter is easily prevented by putting all kde apps in a subfolder in every category in the gnome menu AND vice versa in kde. E.g. In gnome Konqueror will be found in menu->internet->submenu->konqueror and Amarok in menu->sound & video->submenu->amarok.

I don't understand why ubuntu/kubuntu don't implement this behavior by default.

---

### Post by slakkie on 2009-10-24
I never noticed any clutter :roll:

But whatever you do, give it a try.. 

If you do install it next to eachother, you only need to logout to switch from KDE to Gnome and vice-versa... Otherwise you need to reboot. Great for uptime addicts like me :)

---

### Post by Kokopelli on 2009-10-24
If you just want to experiment with Kubuntu then I would run it in its own partition.  

As a dissenting opinion to those above however, I usually install Ubuntu first then Kubuntu desktop over it.  Other than some initial tests to make sure everything is working I do not use Gnome often however.  Clutter in the menu does not bother me since I rarely use them (krunner and gnome-do are my launchers).

Really the pattern came about due to long term use.  I started with Ubuntu, switched to Kubuntu at Gutsy, then with the debacle that was KDE 4.0 switched back to Ubuntu until Karmic.  By installing Ubuntu then kubuntu-desktop I could switch back and forth and try KDE4 (unusable in Hardy/Ibex, mediocre in Jaunty, I am quite pleased with Karmic) while still having Gnome to fall back on.

---

### Post by murderslastcrow on 2009-10-24
Yeah, I'm a Gnome-DO addict, and krunner seems to be a great alternative to it (a lot of crazy functionality just 'cuz). That's what I like about KDE. It has a lot of experimental stuff hidden away just in case. Sure, a lot of people hate having so much stuff to configure/set, but I think it's a good showcase of what an OS can really pull off.

The only request I would have, for the sake of noobz, is that PackageKit find some way to separate applications from packages (like how we have Add/Remove and the Ubuntu Software Center in Gnome, then Synaptic, but just separate them as menu items). It's a bit cluttered and disorderly when it comes to just installing applications, much more finding them.

But I'm still glad that they're taking on PackageKit at all. Looks like Karmic is a great release for each version so far.

---

### Post by wxnker on 2009-10-25
> **slakkie said:**
> I never noticed any clutter :roll:
Really? What I'm talking about here is Gnome and KDE programs being mixed in the menu. To me that's clutter. I primarily use Gnome and KDE installs so many applications that I never use in Gnome. 

And by all means, I'm not criticizing Ubuntu (or Kubuntu). I merely suggest improvements to basic usability. This is easily taken care of in other distro's I've tried, so I'm just wondering why Ubuntu doesn't.

Regards,
wxnker

---

### Post by murderslastcrow on 2009-10-25
Ah. That is peculiar. However, perhaps they think it adds to functionality since, if QT and GTK can live in perfect harmony, why separate them in the menus?

But you know, I could just edit the menus myself, problem solved. I think it's highly amusing that Linux, something people have chronically associated with difficulty, is actually ridiculously easy to use and set up the way you want it.

No really, it's hilarious. But we keep just making it easier. I'm gonna' go now and contemplate the existence of Windows. XD

---

### Post by wxnker on 2009-10-27
> **murderslastcrow said:**
> Ah. That is peculiar. However, perhaps they think it adds to functionality since, if QT and GTK can live in perfect harmony, why separate them in the menus?
Basically to keep the menus clean and simple. I guess I prefer having the non-native DE apps in a subcategory by default. That way my menus are still easy to browse and non-native DE apps are just a click away.

> But you know, I could just edit the menus myself, problem solved. I think it's highly amusing that Linux, something people have chronically associated with difficulty, is actually ridiculously easy to use and set up the way you want it.
Yes, I know. It's very easy. I would prefer starting out with a more clean menu and then edit from there, though. Less stuff to edit. Also this ensures clean menus in both KDE and Gnome at the same time.

I agree. Linux nowadays is so simple. Much simpler than Windows really, If a user were to start out with both distros from scratch. Not knowing either one in advance.

Cheers,
wxnker

---

### Post by buzzmandt on 2009-10-27
Unlike some of the others that prefer never to install one on top of the other, I ALWAYS install ubuntu, then sudo apt-get install kubuntu-desktop and kde-full.  I then do as another mentioned by removing the kde network manager and go to system settings/advanced/autostart and add nm-applet.  the only way I can connect is wireless and kde wireless is borked. I much prefer running kde but like to play with gnome and gnome-shell at times.  and it just works better for me to just logout select a different session and log back in under a different environement. 

I have always prefered kde but with kde 4.0-3 it was just to unstable and stuck it out with gnome.  Now it's pretty rock solid and snappy so I'm back to being a kde prefered user.  The "clutter" doesn't bother me because I set what I like to use in favorites and have easy access to everything.  The big use apps like terminal, firefox, and pidgeon I just add to panel.  

I especially prefer kdm to gdm2, right now gdm2 is difficult to do anything with, but kdm is still completely configurable from system settings/advanced/login manager in kde.

just my take

---

