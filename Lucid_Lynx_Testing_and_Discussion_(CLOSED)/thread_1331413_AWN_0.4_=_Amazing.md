---
title: "AWN 0.4 = Amazing"
date: 2009-11-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Toadinator on 2009-11-19
I just decided to try out AWN again because Docky (Gnome-Do) seemed rather slow to me, and I found this: [http://www.webupd8.org/2009/10/avant-window-navigator-awn-04-available.html]("http://www.webupd8.org/2009/10/avant-window-navigator-awn-04-available.html")

It's just amazing! So, I decided to try it out, and it not only does everything Docky could do (as a dock; I have Gnome-Do running separately now), but it's very very stable and all of my problems with the old versions of AWN (like slow unhiding or no intellihide feature) are gone! You can even make the dock behave like a panel! If GNOME 3 ever wanted a dock, they should look no farther than this. It's the most perfect dock I've ever seen in my entire life!

The reason I'm posting this here is because I figured that AWN might be a good idea for a future version of Ubuntu (maybe 10.10, since GNOME 3 looks like it needs a dock) and to see what you all think about how it would look replacing the bottom (and maybe even) top panels in a regular Ubuntu release (such as 10.04 LTS). Of course, it's not 100% stable yet, so it's not an immediate option, but it's an interesting idea.

Any opinions?

EDIT: Also, I find it very similar to the new Windows 7 taskbar in expanded mode with the right configuration of applets. It'd make users feel right at home after installing it.

ANOTHER EDIT: Run this command after installing to get a bunch of extra applets:
```
sudo apt-get install python-awn-trunk python-awn-extras-trunk awn-applets-python-extras-trunk awn-applets-c-extras-trunk
```

---

### Post by Regenweald on 2009-11-19
Could you post a shot of it on your desktop ? I'd like a look ;)

---

### Post by darco on 2009-11-19
I have been an AWN fan for awhile...Ill test it out...
One thing though, after adding the ppa, I get this error

```
Failed to fetch http://ppa.launchpad.net/awn-testing/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```

Matter of fact I gotten that error before w/another PPA. I am running x64 but is there something I need to change or update in my Update Manager to d/l x32 apps or ignore amd64?

thxs

darco

---

### Post by Vanishing on 2009-11-19
> **Toadinator said:**
> I just decided to try out AWN again because Docky (Gnome-Do) seemed rather slow to me, and I found this: [http://www.webupd8.org/2009/10/avant-window-navigator-awn-04-available.html]("http://www.webupd8.org/2009/10/avant-window-navigator-awn-04-available.html")

It's just amazing! So, I decided to try it out, and it not only does everything Docky could do (as a dock; I have Gnome-Do running separately now), but it's very very stable and all of my problems with the old versions of AWN (like slow unhiding or no intellihide feature) are gone! You can even make the dock behave like a panel! If GNOME 3 ever wanted a dock, they should look no farther than this. It's the most perfect dock I've ever seen in my entire life!

The reason I'm posting this here is because I figured that AWN might be a good idea for a future version of Ubuntu (maybe 10.10, since GNOME 3 looks like it needs a dock) and to see what you all think about how it would look replacing the bottom (and maybe even) top panels in a regular Ubuntu release (such as 10.04 LTS). Of course, it's not 100% stable yet, so it's not an immediate option, but it's an interesting idea.

Any opinions?

EDIT: Also, I find it very similar to the new Windows 7 taskbar in expanded mode with the right configuration of applets. It'd make users feel right at home after installing it.

Got it running for about 2+ weeks now..
the best function i enjoyed from this is the "group" one.
it is simply amazing..

the next thing i want from awn for my christmas gift is the movie preview as icon like the "mac dock", but i see only few ppl mentioned it..~.~

Anyways, it is nice, try it guys.

edit: as a matter of fact, in "awn about", awn is not 0.4, it shows 0.39 for me...o.o

---

### Post by Vanishing on 2009-11-19
> **darco said:**
> I have been an AWN fan for awhile...Ill test it out...
One thing though, after adding the ppa, I get this error

```
Failed to fetch http://ppa.launchpad.net/awn-testing/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```

Matter of fact I gotten that error before w/another PPA. I am running x64 but is there something I need to change or update in my Update Manager to d/l x32 apps or ignore amd64?

thxs

darco

FYI: awn-testing ppa for lucid is not set up right now, you have to edit the /etc/apt/source.list file and change it to karmic.

---

### Post by darco on 2009-11-19
> **Vanishing said:**
> FYI: awn-testing ppa for lucid is not set up right now, you have to edit the /etc/apt/source.list file and change it to karmic.

Thxs!


darco

---

### Post by Toadinator on 2009-11-19
> **Regenweald said:**
> Could you post a shot of it on your desktop ? I'd like a look ;)

Gladly. 

EDIT: My new desktop looks like this: [http://farm3.static.flickr.com/2740/4156341369_8216df3cae_b.jpg]("http://farm3.static.flickr.com/2740/4156341369_8216df3cae_b.jpg")
[IMG]http://farm3.static.flickr.com/2750/4117423753_a864a0178c_b.jpg[/IMG]

TIP: to get your dock like mine, set it to Edgy mode and slide its position all the way to the left or the right; you can do that in AWN Settings by right-clicking your dock.

Another thing I found about this dock: even with my tricked-out configuration, the dock only uses about 3MB! Python was using about 10, however. That's not bloated at all; not as much as Compiz is at least. And yes, that's a notification area at the bottom right :D.

---

### Post by baizon on 2009-11-19
Very impressive, will test soon.

---

### Post by jfernyhough on 2009-11-19
/me wonders what DVD you were watching in order to blank out the name...

;)

---

### Post by Toadinator on 2009-11-19
> **Vanishing said:**
> the next thing i want from awn for my christmas gift is the movie preview as icon like the "mac dock", but i see only few ppl mentioned it..~.~

I just tried out the Media Player Applet and it's really neat! Gloobus Previews might be a better idea for previewing movie files, though.

---

### Post by Toadinator on 2009-11-19
> **jfernyhough said:**
> /me wonders what DVD you were watching in order to blank out the name...

;)

XD nothing. It's a DVD for school. I'm home-schooled (9th grade and sneaking online during class ;)).

---

### Post by Neon Lights on 2009-11-19
Whoa, that's pretty spiffy. Maybe I'll try out AWN again. I wonder though, can it go on the sides of the screen? Docky2 does this, and I love it. x: haha.

And go homeschooled kids, lol. :p 11th grade here.

---

### Post by zekopeko on 2009-11-19
> **Neon Lights said:**
> I wonder though, can it go on the sides of the screen? Docky2 does this, and I love it.

Yes it can.

---

### Post by LKjell on 2009-11-19
> **Toadinator said:**
> 
...Also, I find it very similar to the new Windows 7 taskbar in expanded mode with the right configuration of applets. It'd make users feel right at home after installing it.

Does it differ from Dockbarx?

---

### Post by andrewabc on 2009-11-19
> **zekopeko said:**
> Yes it can.

Sweet, it didn't last time I tried it and I had to use cairo dock.

EDIT:
No mention of 0.4 at their website.
EDIT:
info at forum thread, which leads to PPA. Currently numbered 0.3.9
[https://launchpad.net/~awn-testing/+archive/ppa](https://launchpad.net/~awn-testing/+archive/ppa)

---

### Post by Roasted on 2009-11-19
So uh, I'm reading that this is multiple monitor friendly, but it's hating my primary monitor. Where do I go to kick it to my primary monitor?

---

### Post by Vanishing on 2009-11-19
> **Toadinator said:**
> I just tried out the Media Player Applet and it's really neat! Gloobus Previews might be a better idea for previewing movie files, though.

hmm..tried gloobus couple weeks ago,,its not as good as i imagined...maybe its better now?
well check it out..
thanks

---

### Post by nanog on 2009-11-19
Brilliant!

Amazing customizability, light weight, snappy responsiveness, stability (YMMV), nice looking applets (the new task manager is beautiful), and it perfectly matches gnome themes. 

I sincerely hope that Ubuntu is considering this for a default install.

---

### Post by Roasted on 2009-11-19
VERY nice. I like this a lot. The only thing I can't figure out is how do I make this thing auto hide? I can't figure it out, even set on intellihide.

Also - I did fix the dual monitor issue. I just adjusted the horizontal axis until it was centered on my main screen. I also had to put the horizontal pixel count of both monitors, which since they're 1440 and 1920, I had to add them = 3360. Then just offset the axis to where it was centered and bingo - I was done.

Anybody know about the auto hide gizmo?

---

### Post by Toadinator on 2009-11-19
> **Roasted said:**
> VERY nice. I like this a lot. The only thing I can't figure out is how do I make this thing auto hide? I can't figure it out, even set on intellihide.

Anybody know about the auto hide gizmo?

You can configure AWN by right-clicking your dock and selecting Dock Preferences, which takes you to AWN Settings. In AWN Settings, you can change Autohide as follows:

Under Preferences, go to Behavior. 
1)"Autohide Keep Below" means it'll stay below windows unless you move your mouse to the bottom of the screen.
2)"Autohide Fade Out" means that the whole bar will fade out of view until you move your mouse to the bottom of the screen.
3)"Transparency" means that the bar will still be visible, but it will be highly transparent and only usable when you move your mouse once again to the very bottom.
4)I have no idea about "Custom".

"Intellihide" means that it'll only hide when a window is over it. This is only noticeable with "Autohide Fade Out" and "Transparency" I believe; still very useful. To set it, go to "Task Manager" on AWN Settings. I hope I helped! :)

---

### Post by TerminX on 2009-11-20
I've been using this for a while myself; it is indeed great.  In fact, I think my only problem with is it that there's no clock app you can configure in the same way as the GNOME panel clock applet.  I have a separate machine with Win7 on it right next to my Linux box, so it's not like I'm without a decent text based clock completely (though even then I have to use third party software because the Windows clock sucks too), but it has been a little weird only having the analog cairo clock.

It doesn't look like the "digital clock" applet has been updated in a couple of years, and it lacks basic configuration options like display of seconds, etc.  The lack of a decent basic clock applet is kind of a weird thing to encounter in what is otherwise such a badass application.

---

### Post by Roasted on 2009-11-20
> **Toadinator said:**
> You can configure AWN by right-clicking your dock and selecting Dock Preferences, which takes you to AWN Settings. In AWN Settings, you can change Autohide as follows:

Under Preferences, go to Behavior. 
1)"Autohide Keep Below" means it'll stay below windows unless you move your mouse to the bottom of the screen.
2)"Autohide Fade Out" means that the whole bar will fade out of view until you move your mouse to the bottom of the screen.
3)"Transparency" means that the bar will still be visible, but it will be highly transparent and only usable when you move your mouse once again to the very bottom.
4)I have no idea about "Custom".

"Intellihide" means that it'll only hide when a window is over it. This is only noticeable with "Autohide Fade Out" and "Transparency" I believe; still very useful. To set it, go to "Task Manager" on AWN Settings. I hope I helped! :)

Ah hah! It did. Thanks much!

General question - how do you feel AWN beta is compared to the original? I feel as though Docky might have some serious competition here... but I have a hard time deciding which to use because they both are really solid.

---

### Post by Toadinator on 2009-11-20
> **Roasted said:**
> Ah hah! It did. Thanks much!

General question - how do you feel AWN beta is compared to the original? I feel as though Docky might have some serious competition here... but I have a hard time deciding which to use because they both are really solid.

Docky, compared to AWN, isn't nearly as good. I used to use it, but it has a few problems:

1) SLOW
2) Mono (which means it's not only slow but a resource hog AND from Microsoft/Novell, two companies I will never trust no matter what they do).
3) Lack of applets/docklets/whatever. There are some out there, but there isn't many of them. Also, AWN is more developer-friendly since it has lots of different ways to develop extensions/applets/whatever.

For the time being, AWN is the best alternative.

---

### Post by plun on 2009-11-20
Docky up and running

[[img]http://ubuntu-pics.de/thumb/31591/snapshot24_J227bR.png[/img]](http://ubuntu-pics.de/bild/31591/snapshot24_J227bR.png)

AWN is better....

---

### Post by Roasted on 2009-11-20
> **Toadinator said:**
> Docky, compared to AWN, isn't nearly as good. I used to use it, but it has a few problems:

1) SLOW
2) Mono (which means it's not only slow but a resource hog AND from Microsoft/Novell, two companies I will never trust no matter what they do).
3) Lack of applets/docklets/whatever. There are some out there, but there isn't many of them. Also, AWN is more developer-friendly since it has lots of different ways to develop extensions/applets/whatever.

For the time being, AWN is the best alternative.

Where did you get your information about Docky being from Microsoft/Novell? I happened to have spoken to the developers of Docky and that's the exact opposite of what I heard.

The auto hide feature with Docky is significantly snappier than AWN. With AWN I feel like I gotta sit for a second or two till it realizes I'm trying to wake the dock up.

I really like AWN, and I'm happy to see they *FINALLY* have multiple screen support, but I'm just not too sure yet.

Another thing about Docky I prefer is say you have Pidgin open with 5 ims. You can right click to select an individual IM, or you can just simply click the Pidgin icon and BAM - all of them pop up. With AWN you can't launch all of the boxes associated with that program. 

HOWEVER - you can hover over the icon and scroll, and it'll selectively pop up each window associated with that program. But Docky already does that. :P

Still playing with each one, glad to see AWN is making improvements, but I'm just not sure if it'll be a full time dock for me.. yet.

---

### Post by VMC on 2009-11-20
> **Vanishing said:**
> FYI: awn-testing ppa for lucid is not set up right now, you have to edit the /etc/apt/source.list file and change it to karmic.

I tried this and still nothing:

```
/etc/apt/sources.list.d/awn-testing-ppa-karmic.list:
deb http://ppa.launchpad.net/awn-testing/ppa/ubuntu karmic main

```
sudo aptitude update && sudo aptitude safe-upgrade

Nothing to upgrade.

---

### Post by afv on 2009-11-20
> **VMC said:**
> I tried this and still nothing:

```
/etc/apt/sources.list.d/awn-testing-ppa-karmic.list:
deb http://ppa.launchpad.net/awn-testing/ppa/ubuntu karmic main

```
sudo aptitude update && sudo aptitude safe-upgrade

Nothing to upgrade.

You do have to install avant-window-navigator-trunk.

---

### Post by Taiebot65 on 2009-11-20
I still prefer cairo-dock... And i encourage testers to play with it because we had such issue with video graphic cards not supporting openGL that we had quite few issues 

They have know a ppa and a launchpad account and a tester branch :p
[https://launchpad.net/cairo-dock](https://launchpad.net/cairo-dock)

 .... i think gnome-shell should really look into this project because the dbus interface make it really easy to create an applet ..

---

### Post by Roasted on 2009-11-20
> **Taiebot65 said:**
> I still prefer cairo-dock... And i encourage testers to play with it because we had such issue with video graphic cards not supporting openGL that we had quite few issues 

They have know a ppa and a launchpad account and a tester branch :p
[https://launchpad.net/cairo-dock](https://launchpad.net/cairo-dock)

 .... i think gnome-shell should really look into this project because the dbus interface make it really easy to create an applet ..

Cairo Dock is a solid application, but they really, really need to clean up that control panel.

---

### Post by Toadinator on 2009-11-20
> **Roasted said:**
> Where did you get your information about Docky being from Microsoft/Novell? I happened to have spoken to the developers of Docky and that's the exact opposite of what I heard.
I meant C#/Mono, not the whole dock. I respect the developers of Gnome Do/Docky, I just don't like Mono/the people behind it.

> **Roasted said:**
> The auto hide feature with Docky is significantly snappier than AWN. With AWN I feel like I gotta sit for a second or two till it realizes I'm trying to wake the dock up.
Did you try the new version I suggested? I find that it's actually much snappier than Docky.

> **Roasted said:**
> Another thing about Docky I prefer is say you have Pidgin open with 5 ims. You can right click to select an individual IM, or you can just simply click the Pidgin icon and BAM - all of them pop up. With AWN you can't launch all of the boxes associated with that program.

HOWEVER - you can hover over the icon and scroll, and it'll selectively pop up each window associated with that program. But Docky already does that. :P
...what? On AWN 0.4 Beta (the version I suggested trying), you can have grouped windows like on Docky. By default if you click it, a small AWN dialog pops up asking you which window you'd like to select. This feature's configurable as well. Could you explain a little better what you mean please?

---

### Post by Roasted on 2009-11-20
I'm basing my opinion off of the current AWN Beta that's being talked about in this thread. I'm currently running it at the moment. I have Docky running on my work laptop and my spare rig...

---

### Post by ronacc on 2009-11-21
I like it , I only have one problem , when I add apps with dock-preferences>task manager  they all use the same icon , if I select one and then customise icon they all change to that icon . this does not happen with the applets .Is this  intentional , a bug ,or am I doing something wrong ?

---

### Post by Schendje on 2009-11-21
Wow, this really is amazing! Never liked the old AWN that much, but this is smooooooooth with lots of cool features and applets.

I still won't use it, not my thing. But massive props to the AWN developers! :KS

---

### Post by darco on 2009-11-21
It also wont let me install previous themes....so stuck w/just the one.



darco

---

### Post by Toadinator on 2009-11-21
> **ronacc said:**
> I like it , I only have one problem , when I add apps with dock-preferences>task manager  they all use the same icon , if I select one and then customise icon they all change to that icon . this does not happen with the applets .Is this  intentional , a bug ,or am I doing something wrong ?

Probably a bug; might be good if you reported it on Launchpad. A workaround I know of is opening an application and right-clicking its icon on the dock and selecting "Add to launcher list". I haven't tried changing the icon, but this is a good way to add apps from my own experience.

---

### Post by Toadinator on 2009-11-21
Another good reason for Ubuntu to maybe adopt this: it can run without compiz! I don't think the older version had this feature (I could be wrong) but if you're trying AWN right now, try switching compiz off and see how it still works just about as well as the regular mode! There's no transparency yet, but it works like a charm.

---

### Post by Gina on 2009-11-21
When I tried to run AWN a few days ago it wanted me to install compiz-fusion and run it.  At that point I ran out of time and haven't tried since.  AWN looks good and I don't really want compiz.

---

### Post by ronacc on 2009-11-21
@ Toadinator   your workaround does the trick , I couldn't report it as a bug , ubuntu-bug says it is not a genuine ubuntu package  , I guess ubuntu-bug is no good for PPA's .

---

### Post by ninjapirate89 on 2009-11-21
Thanks OP. This is amazing. :guitar:

---

### Post by Josh04 on 2009-11-21
New AWN is so much better than old AWN, thanks OP!

Got it going as part of my current desktop: [http://i100.photobucket.com/albums/m8/Josh0-4/Screenshot-18.png](http://i100.photobucket.com/albums/m8/Josh0-4/Screenshot-18.png)

---

### Post by nanog on 2009-11-21
Awn 0.4 does run without compiz but its still a little buggy. Just try metacity --replace. Awn also works flawlessly without compiz if you tick the "compositing manager" on in gconf-->apps-->metacity. 

You can report bugs at the awn testing ppa.

---

### Post by thefunnyman on 2009-11-22
So, maybe I'm half asleep or something, but, I cannot seem to figure out how to delete an applet that I've added.  Anyone else having this problem?  I'm sure it's something stupid I'm not getting.  The button to delete seems to be permanently grayed out.

Thanks..

The funnyman

---

### Post by the8thstar on 2009-11-22
For those of you having too many problems installing AWN 0.4 Beta with the command line, you can try the GUI route through [Ubuntu Tweak]("http://http://ubuntu-tweak.com/"). 

From there just go to the Applications panel, enable Third-Party sources and finally select Add/Remove. AWN-trunk will be there. ;)

---

### Post by McDuff on 2009-11-22
> **thefunnyman said:**
> So, maybe I'm half asleep or something, but, I cannot seem to figure out how to delete an applet that I've added.  Anyone else having this problem?  I'm sure it's something stupid I'm not getting.  The button to delete seems to be permanently grayed out.



me too, i was wondering how to do that. you have to drag&drop the applet from “active applets” back to “available applets”

---

### Post by scouser73 on 2009-11-22
I've just updated AWN and am finally able to move it about the screen now, which is something that I have been wanting to do for a while with this fantastic dock.  Thank you for the tip, I appreciate it.

---

### Post by 23dornot23d on 2009-11-22
I like it ..... cheers .... neat and fast .... :D

---

### Post by thefunnyman on 2009-11-22
> **McDuff said:**
> me too, i was wondering how to do that. you have to drag&drop the applet from “active applets” back to “available applets”

Thanks a lot!  That was driving me crazy.

---

### Post by Toadinator on 2009-11-22
Also, if you want more applets then try running this command:

```
sudo apt-get install python-awn-trunk python-awn-extras-trunk awn-applets-python-extras-trunk awn-applets-c-extras-trunk
```

Or just install the packages specified manually however you please. This will get you a load of extra applets for your dock (my favorite of which is Yet Another Menu Applet), but apparently a few of the ones mentioned aren't compatible with version 0.4 so they don't show up. Pitty, the meebo applet looks rad. Try it out! :)

---

### Post by HalfEmptyHero on 2009-11-22
How did you put applets on the right side of awn?

---

### Post by ZeroSpawn on 2009-11-22
Pretty good of a up date, **EDIT** Autohide is working now!

I wish they changed the FireFox Task manager to a applet so you can open new windows just by clicking on the icon.

---

### Post by Flywaver on 2009-11-22
> **Toadinator said:**
> Gladly. 

[IMG]http://farm3.static.flickr.com/2750/4117423753_a864a0178c_b.jpg[/IMG]

TIP: to get your dock like mine, set it to Edgy mode and slide its position all the way to the left or the right; you can do that in AWN Settings by right-clicking your dock.

Another thing I found about this dock: even with my tricked-out configuration, the dock only uses about 3MB! Python was using about 10, however. That's not bloated at all; not as much as Compiz is at least. And yes, that's a notification area at the bottom right :D.

Thanks a LOT Toadinator! AWN looks great!!! 
Although I see that AWN uses 60mb of RAM while docky would use 30+30 for compiz

---

### Post by ronacc on 2009-11-22
60 mb ? I am only showing it using 9.2 mb  with compiz and set to edgy and expand . 64 bit lucid and nvidia 7600gs and 185.18.36 driver

---

### Post by VMC on 2009-11-22
> **nanog said:**
> ...Awn also works flawlessly without compiz if you tick the "compositing manager" on in gconf-->apps-->metacity. 
Sorry this doesn't make any sense to me. Is "gconf-->apps-->metacity" a directory. I do have that in my home directory but no "compositing manager" any where, whatever that is. AWN does work without compiz very well right now but if I can improve it I will do so.

---

### Post by Toadinator on 2009-11-22
> **HalfEmptyHero said:**
> How did you put applets on the right side of awn?

Enable the setting "Expand the panel" in AWN Settings. Then, add the Expander applet in between the two you want there to be a space for. Hope it works for you :)!

---

### Post by Toadinator on 2009-11-22
> **VMC said:**
> Sorry this doesn't make any sense to me. Is "gconf-->apps-->metacity" a directory. I do have that in my home directory but no "compositing manager" any where, whatever that is. AWN does work without compiz very well right now but if I can improve it I will do so.

I think he means to open that setting in the Configuration Editor (you'll see what he means when you do; it's hidden in the menu structure somewhere, you have to toggle it as visible to use it without using the terminal). Another easy way to change your window manager/etc. is to install compiz-fusion-icon.

```
sudo apt-get install fusion-icon
```

You can then run it from the System Tools menu. I set it to start automatically when I boot, but that's just me :p. Works very well if disabling compiz is something you do frequently for things like games or video editing.

---

### Post by VMC on 2009-11-22
> **Toadinator said:**
> I think he means to open that setting in the Configuration EditorThanks, I was looking in the Configuration Editor. The gconf threw me. That's why. gconf=Configuration Editor. Now I see, also AWN now it looks great! Thanks.

---

### Post by phenest on 2009-11-23
> **Toadinator said:**
> Another good reason for Ubuntu to maybe adopt this: it can run without compiz! I don't think the older version had this feature (I could be wrong) but if you're trying AWN right now, try switching compiz off and see how it still works just about as well as the regular mode! There's no transparency yet, but it works like a charm.

+1 on Ubuntu having this as default with maybe a gnome panel too.

I've been using AWN for ages without compiz. I use metacity as compositing manager since gnome introduced it. Someone correct me if I'm wrong, but I think AWN doesn't require either now (or since a few versions ago), and uses it's own software rendering instead, but you lose out on transparency.

---

### Post by phenest on 2009-11-23
> **Flywaver said:**
> Thanks a LOT Toadinator! AWN looks great!!! 
Although I see that AWN uses 60mb of RAM while docky would use 30+30 for compiz

6.1MB here and 42MB including applets.

---

### Post by McDuff on 2009-11-23
> **phenest said:**
> 6.1MB here and 42MB including applets.

here:
- cairo dock (no opengl): 95,4mb
- gnome-do with docky: 40mb
- awn: 3,8mb + 12,5mb (applets) -> 16,3mb

---

### Post by Toadinator on 2009-11-23
Everyone, I have just posted a blueprint for ubuntu on launchpad to include this! Check it out here: [https://blueprints.launchpad.net/ubuntu/+spec/adopt-awn-dock]("https://blueprints.launchpad.net/ubuntu/+spec/adopt-awn-dock")

---

### Post by Toadinator on 2009-11-23
I've now added a public poll for those of you wanting to voice your opinion :).

---

### Post by Merk42 on 2009-11-23
> **Toadinator said:**
> I've now added a public poll for those of you wanting to voice your opinion :).

I think this would get better adoption once GNOME Shell becomes default since they (as of right now) don't feel window management sans-overlay is neccesary.

---

### Post by blur xc on 2009-11-23
I think I'm missing something.  I use awn, and I added the rep and installed awn trunk like you all said.  But, now what?  All I can see that's different is when I right-click my dock and select doc preferences, nothing happens.  So, all I managed to do is break my otherwise sound AWN.

Any help?

BM

---

### Post by Toadinator on 2009-11-23
> **blur xc said:**
> I think I'm missing something.  I use awn, and I added the rep and installed awn trunk like you all said.  But, now what?  All I can see that's different is when I right-click my dock and select doc preferences, nothing happens.  So, all I managed to do is break my otherwise sound AWN.

Any help?

BM

try re-starting your dock. that might help.

---

### Post by Toadinator on 2009-11-23
> **Merk42 said:**
> I think this would get better adoption once GNOME Shell becomes default since they (as of right now) don't feel window management sans-overlay is neccesary.

That's what I was thinking, actually. Gnome-Shell is much more enjoyable for me with AWN, but I can't live without glipper so I'll have to pass on it for now :\.

---

### Post by nanog on 2009-11-23
> **VMC said:**
> Sorry this doesn't make any sense to me. Is "gconf-->apps-->metacity" a directory. I do have that in my home directory but no "compositing manager" any where, whatever that is. AWN does work without compiz very well right now but if I can improve it I will do so.

I have gconf installed as a menu item. The command is gconf-editor (e.g. alt F2 gconf-editor) followed by selection of apps and metacity tabs.

---

### Post by blur xc on 2009-11-23
> **Toadinator said:**
> try re-starting your dock. that might help.

That worked- but now it wiped out my pervious AWN configuration...  Any way to get it back?  Or do I have to try to fix it back to the way it was from memory?  

Thanks,
BM

---

### Post by Toadinator on 2009-11-23
> **blur xc said:**
> That worked- but now it wiped out my pervious AWN configuration...  Any way to get it back?  Or do I have to try to fix it back to the way it was from memory?  

Thanks,
BM

From memory. Awn 0.4 Beta's a complete re-write and it uses a new settings manager so old configurations shouldn't work any longer.

---

### Post by ninjapirate89 on 2009-11-23
> **Toadinator said:**
> Also, if you want more applets then try running this command:

```
sudo apt-get install python-awn-trunk python-awn-extras-trunk awn-applets-python-extras-trunk awn-applets-c-extras-trunk
```

Or just install the packages specified manually however you please. This will get you a load of extra applets for your dock (my favorite of which is Yet Another Menu Applet), but apparently a few of the ones mentioned aren't compatible with version 0.4 so they don't show up. Pitty, the meebo applet looks rad. Try it out! :)

Thanks for this! Your right about Yet Another Menu Applet. It's much better.

---

### Post by blur xc on 2009-11-24
> **Toadinator said:**
> From memory. Awn 0.4 Beta's a complete re-write and it uses a new settings manager so old configurations shouldn't work any longer.

Bummer...  So, I guess I'm back to square one...

Thanks,
BM

---

### Post by DynastyX on 2009-11-24
After using it for a while I do like it, I just wish I could mix launchers and applets together. I would also like the ability to place separators anywhere I want (why can they only go between applets?) While it may look good and work well (besides that stupid theme-manager that doesn't hold a list of themes as it should) I just don't like it better than my current Cairo-dock set up, which is why I voted to keep it out of the stock package. Here's a comparison of my two docks,
[IMG]http://steven-de.smugmug.com/photos/723096570_uircK-L.png[/IMG]

---

### Post by PuddingKnife on 2009-11-24
I love it, thank you!

I only have one problem, and its that I cant delete my top panel. I reduced it to only the date and time, unchecked the expand option, and set it to auto hide in the mean time.

Check me out!

[ATTACH]137512[/ATTACH]

---

### Post by moonbeam on 2009-11-24
> **PuddingKnife said:**
> I love it, thank you!

I only have one problem, and its that I cant delete my top panel. I reduced it to only the date and time, unchecked the expand option, and set it to auto hide in the mean time.

Check me out!

[ATTACH]137512[/ATTACH]

There info on removing all panels from Gnome at:

[http://wiki.awn-project.org/FAQ#How_do_I_permanently_remove_GNOME_Panel_from_my_GNOME_session.3F](http://wiki.awn-project.org/FAQ#How_do_I_permanently_remove_GNOME_Panel_from_my_GNOME_session.3F)

---

### Post by moonbeam on 2009-11-24
> **Toadinator said:**
> 

It's just amazing! So, I decided to try it out, and it not only does everything Docky could do (as a dock; I have Gnome-Do running separately now), but it's very very stable and all of my problems with the old versions of AWN (like slow unhiding or no intellihide feature) are gone! You can even make the dock behave like a panel! If GNOME 3 ever wanted a dock, they should look no farther than this. It's the most perfect dock I've ever seen in my entire life!


Just a quick note.  This thread was a uplifting read for all the devs on #awn on freenode.  

We welcome everyone to drop by #awn on freenode.org at any time, someone will respond to comments/inquiries eventually though _sometimes_ it may take a couple hours.

General discussions/comments can be made on our forum: [http://awn.planetblur.org/index.php?shard=forum&action=g_default](http://awn.planetblur.org/index.php?shard=forum&action=g_default)

Bugs or small feature requests:
Core:  [https://bugs.launchpad.net/awn](https://bugs.launchpad.net/awn)
Applets:  [https://bugs.launchpad.net/awn-extras](https://bugs.launchpad.net/awn-extras)

Larger Feature Requests:
Core:  [https://blueprints.launchpad.net/awn](https://blueprints.launchpad.net/awn)
Applets: [https://blueprints.launchpad.net/awn-extras](https://blueprints.launchpad.net/awn-extras)

And the wiki is at:  [http://wiki.awn-project.org](http://wiki.awn-project.org)  (A fair amount of updates are needed for rewrite)

And if you're really interested:-)  then:  [http://planet.awn-project.org/](http://planet.awn-project.org/)

Once again, it was very nice to hear all of the kind words and the constructive comments.

Thanks.

---

### Post by moonbeam on 2009-11-24
> **ronacc said:**
> I like it , I only have one problem , when I add apps with dock-preferences>task manager  they all use the same icon , if I select one and then customise icon they all change to that icon . this does not happen with the applets .Is this  intentional , a bug ,or am I doing something wrong ?

It is not a bug.  When you customize an icon the task manager it will substitute the new icon for every instance that uses the themed icon.

For example if you customize the icon of a launcher for gnome-terminal the associated desktop file probably has the line Icon=utilities-terminal.  This will cause the taskmanager to use that customized icon for all launchers that uses Icon=utilities-terminal.

If you want to really use different icons... what you're going to need to do is create a customized desktop file with an unique Icon= line.

It's understandable that you might want the behaviour you're expecting but in most cases we would expect the current behaviour to be less surprising.  I'll give some thought about how to accommodate the behaviour you've described after the 0.4 release (it might be an idea to file a bug requesting it).

---

### Post by moonbeam on 2009-11-24
> **ZeroSpawn said:**
> Pretty good of a up date, **EDIT** Autohide is working now!

I wish they changed the FireFox Task manager to a applet so you can open new windows just by clicking on the icon.

Middle click should always (attempt) to open a new instance of an app.

---

### Post by moonbeam on 2009-11-24
> **phenest said:**
> Someone correct me if I'm wrong, but I think AWN doesn't require either now (or since a few versions ago), and uses it's own software rendering instead, but you lose out on transparency.

It's required a compositor up until the rewrite (Metacity and Xfwm4 have had decent compositors available for a while, compiz has _never_ been a requirement as such, even xcompmgr is good enough).  With rewrite a compositor is not required but it will revert to basic effects and some applets may not behave as expected.

---

### Post by ronacc on 2009-11-24
@ moonbeam Thank you for taking the time to answer some of our questions . Toadinators suggestion of right click and add to launcher list works for me , anything I would bother to change the icon on I would want a permanent part of my dock ayway .

---

### Post by solwic on 2009-11-24
> **moonbeam said:**
> There info on removing all panels from Gnome at:

[http://wiki.awn-project.org/FAQ#How_do_I_permanently_remove_GNOME_Panel_from_my_GNOME_session.3F](http://wiki.awn-project.org/FAQ#How_do_I_permanently_remove_GNOME_Panel_from_my_GNOME_session.3F)

Problem is, when I do that, and log back in the awn panel is gone along with the top panel....

Am I doing something wrong?  I followed the directions in that link....

EDIT:  Besides, when you turn off the panel, certain functions go away (like Alt + F2).  Right now, I've hidden mine, unexpanded it, shrunk it to 12px, removed everything but the menu, and changed the unhide time to 2 seconds, so it doesn't pop out if I run the mouse across the top of the screen.  Seems to be working so far....

---

### Post by moonbeam on 2009-11-24
> **solwic said:**
> Problem is, when I do that, and log back in the awn panel is gone along with the top panel....

Am I doing something wrong?  I followed the directions in that link....

Yeah, the directions there were for removing the panel, not autostarting awn :-)

To start awn on login either go to the dock preferences and look at the bottom left of the front tab and you should see "Start Awn automatically"
with a checkbox.

Or you can add it to your session manually, see:  [http://wiki.awn-project.org/FAQ#How_can_I_make_AWN_run_when_my_desktop_starts_up.3F](http://wiki.awn-project.org/FAQ#How_can_I_make_AWN_run_when_my_desktop_starts_up.3F)

---

### Post by solwic on 2009-11-25
> **moonbeam said:**
> Yeah, the directions there were for removing the panel, not autostarting awn :-)

To start awn on login either go to the dock preferences and look at the bottom left of the front tab and you should see "Start Awn automatically"
with a checkbox.

Or you can add it to your session manually, see:  [http://wiki.awn-project.org/FAQ#How_can_I_make_AWN_run_when_my_desktop_starts_up.3F](http://wiki.awn-project.org/FAQ#How_can_I_make_AWN_run_when_my_desktop_starts_up.3F)

Yeah I know that.  And AWN starts fine; it's just not visible.  If I hover the mouse in that general area, the tooltips will pop up, and I can even click on stuff...it's just that the bar is invisible...

---

### Post by Viva on 2009-11-25
I've tried it and its very good. There is a slight delay between clicking on a minimized icon before the window starts maximizing. I experienced a similar delay in cairo-dock, but never in AWN before. It is pretty annoying, but other than that the testing version is ace.

---

### Post by moonbeam on 2009-11-25
> **solwic said:**
> Yeah I know that.  And AWN starts fine; it's just not visible.  If I hover the mouse in that general area, the tooltips will pop up, and I can even click on stuff...it's just that the bar is invisible...

Interesting.  If you could file a bug at [https://bugs.launchpad.net/awn](https://bugs.launchpad.net/awn) including relevant system specs it would be greatly appreciated.

---

### Post by Darkshade on 2009-11-25
The new version looks cool, has some useful applets and all that stuff, it's definitely a big improvement over the previous one but it's painfully slow for me.
I'm going to stick with Cairo-Dock-OpenGL which I recently rediscovered after long time using Docky. It's fast as hell and does the job for what I need. I'll keep checking AWN's performance after updates though.

---

### Post by ElSlunko on 2009-11-25
Is there any way to customize the notification pop ups?

---

### Post by moonbeam on 2009-11-25
> **ElSlunko said:**
> Is there any way to customize the notification pop ups?

Yes.  That being said, the configuration location has recently changed in trunk and will be reflected in the next ppa update, at which time you should see the default appearance of the notifications follows that of your awn theme.

If you do want to change the appearance after that time it's necessary to start gconf-editor and look in /apps/awn-applet-notification-daemon/  (It will not show up until after the next ppa update).

---

### Post by solwic on 2009-11-25
> **moonbeam said:**
> Interesting.  If you could file a bug at [https://bugs.launchpad.net/awn](https://bugs.launchpad.net/awn) including relevant system specs it would be greatly appreciated.

I will.  Don't get me wrong; this AWN is still, far and away, the best version so far, and the Ubuntu devs would be remiss in the extreme if they don't include this in the next release in lieu of the bottom panel.  

Now if I could find a way to put a "power off" button on the far right side of the bar, I'd be flippin' wonderful.  :)

---

### Post by PuddingKnife on 2009-11-25
> **solwic said:**
> I will.  Don't get me wrong; this AWN is still, far and away, the best version so far, and the Ubuntu devs would be remiss in the extreme if they don't include this in the next release in lieu of the bottom panel.  

Now if I could find a way to put a "power off" button on the far right side of the bar, I'd be flippin' wonderful.  :)

If you use the "Yet Another Menu" applet, theres a shutdown option in there.


BTW, thanks Moonbeam! You guys are doing a bang up job. I'd love to see this as default in Ubuntu.

---

### Post by benjamimgois on 2009-11-25
I still prefer DOCKY, that now is separated from GnomeDO. It's simple to use, very small, doesn't take to much resources and looks good.

---

### Post by Toadinator on 2009-11-25
Wow, this thread sure is getting a lot of publicity (compared to what I'm used to anyways). I'll be sure to join #awn on freenode (my nick's "Sloshy", as in the HSR band) as soon as I get on next! I love AWN and it makes using my desktop a hundred times more intuitive :D.

---

### Post by moonbeam on 2009-11-25
> **solwic said:**
> 

Now if I could find a way to put a "power off" button on the far right side of the bar, I'd be flippin' wonderful.  :)

Quit applet, Cairo Menu (Session submenu), and YAMA all have shutdown.  I expect you probably want quit the quite applet (I'd suggest going into its preferences and setting it to docklet mode).

---

### Post by Toadinator on 2009-11-26
New AWN update today. Looks like there's a new applet or two (dialect applet is all I notice different) and a new theme, "Dark Theme". The Theme customization menu is cleaned up as well. TIP: If you want to try out a new theme and don't want to lose your current settings just in case, go to the theme customization screen and export you current theme to a file and add it back to the list.

Also, this seemed to fix a bug where I couldn't drag-and-drop applications from the applications menu to AWN (not sure if it was just me who had this issue). Hope you all enjoy!

---

### Post by caryb on 2009-11-26
Was going to install it on my Kubuntu machine as when I googled AWN it had KDE as a option, when I went to install it it wanted to install a petabyte of Gnome stuff[-(

Cary

---

### Post by meborc on 2009-11-27
using the ppa version on xubuntu... now 100% xfce-panel free :)

---

### Post by McDuff on 2009-11-27
> **Toadinator said:**
> New AWN update today. Looks like there's a new applet or two (dialect applet is all I notice different)

dialect applet is not functional for me, it's crashing all the time. is there anybody else who has this problem?

---

### Post by moonbeam on 2009-11-27
> **McDuff said:**
> dialect applet is not functional for me, it's crashing all the time. is there anybody else who has this problem?

Might just be a matter of restarting gconfd.  I don't think know if it's done with the package installation or not.  Anyway, try opening a terminal and run.

killall gconfd-2

If that doesn't resolve the issue, it would be appreciated if you could file a bug at [https://bugs.launchpad.net/awn-extras](https://bugs.launchpad.net/awn-extras) .

---

### Post by McDuff on 2009-11-27
killall gconfd-2 didn't help.
bug filed: [https://bugs.launchpad.net/awn-extras/+bug/489205](https://bugs.launchpad.net/awn-extras/+bug/489205)

---

### Post by vexorian on 2009-11-27
> **Toadinator said:**
> Gladly. 



TIP: to get your dock like mine, set it to Edgy mode and slide its position all the way to the left or the right; you can do that in AWN Settings by right-clicking your dock.

Another thing I found about this dock: even with my tricked-out configuration, the dock only uses about 3MB! Python was using about 10, however. That's not bloated at all; not as much as Compiz is at least. And yes, that's a notification area at the bottom right :D.
I instantly voted no after reading the question. But after seeing this screenshot, I have my doubts.

---

### Post by Toadinator on 2009-11-27
> **vexorian said:**
> I instantly voted no after reading the question. But after seeing this screenshot, I have my doubts.

Yeah, it's a great dock and improving all the time. I should upload an updated screenshot later today if anyone wants to see.

---

### Post by tacantara on 2009-11-27
I'm glad that I found this thread, because I used to use AWN but found it to be slow and resource intensive.  This new AWN is much more responsive.  I installed it to replace Cairo-Dock this morning.  One of the things I've always liked about AWN is the ease of customization - AWN's GUI is much easier to navigate.

That being said, I don't think replacing the lower taskbar is necessarily in the best interests of Ubuntu.  Having choices is one of the great things that makes Ubuntu (and Linux distros in general) more appealing than other OSes.  I don't mind taking the few seconds to right-click the lower taskbar and selecting "remove."

---

### Post by PuddingKnife on 2009-11-27
I used one of the commands earlier in the thread to get rid of my top panel, but not my workspace switcher doesn't work and alt+F2 doesnt work either. 

Any ideas on how to fix this?

---

### Post by PuddingKnife on 2009-11-27
Ok, so I followed the instructions here:

[http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

I restarted the computer and it was like I had just installed a fresh Ubuntu! All my personal data is gone except for software I had installed before like Blender and PiTiVi and compiz button. How would it have deleted all my data but left programs Ive installed??

Help, Im freaking out! Is there a way to restore my computer to yesterday so that I can leave all this nasty business behind me??

---

### Post by meborc on 2009-11-27
> **PuddingKnife said:**
> Ok, so I followed the instructions here:

[http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

I restarted the computer and it was like I had just installed a fresh Ubuntu! All my personal data is gone except for software I had installed before like Blender and PiTiVi and compiz button. How would it have deleted all my data but left programs Ive installed??

Help, Im freaking out! Is there a way to restore my computer to yesterday so that I can leave all this nasty business behind me??

what do you mean your data is gone?

in terminal issue: ```
df -h
```
to see how much data is on the drives

and may i remind you, you are reading this on a DEVELOPMENT forum... about latest and bleeding edge software... you probably should not be playing with stuff you can't fix ;)

---

### Post by PuddingKnife on 2009-11-27
Yea I know .. somehow one of those commands deleted all my personal data. Im on vacation right now and have a back up on an external back at my home. Just kind of miffed that I somehow deleted all of my data  :(

---

### Post by meborc on 2009-11-27
> **PuddingKnife said:**
> Yea I know .. somehow one of those commands deleted all my personal data. Im on vacation right now and have a back up on an external back at my home. Just kind of miffed that I somehow deleted all of my data  :(

well... spelling mistakes can be fatal when in linux command line :)

sorry for your loss

---

### Post by thecityofgold2006 on 2009-11-27
Stunning piece of software. Lightning fast and simple to use. 

This in combination with the top panel must be the way forward.

---

### Post by moonbeam on 2009-11-27
I'd like to make one quick observation regarding replacing the standard UI with Awn, and I am making this as a Awn dev...  One word "accessibility".

Therefore, though I encourage one and all to install and configure our software, I don't honestly think that it should be the default.  This is not to say that we have no thoughts about solving these issues... but they're no where close to being implemented.

Once again, our thanks for the support.

---

### Post by Toadinator on 2009-11-27
> **moonbeam said:**
> I'd like to make one quick observation regarding replacing the standard UI with Awn, and I am making this as a Awn dev...  One word "accessibility".

Therefore, though I encourage one and all to install and configure our software, I don't honestly think that it should be the default.  This is not to say that we have no thoughts about solving these issues... but they're no where close to being implemented.

Once again, our thanks for the support.

You're welcome, but if it's ready for what's after Lucid then it might make the cut, since Gnome-Shell really needs a dock.

---

### Post by Rob2687 on 2009-11-28
Fantastic stuff.

---

### Post by phenest on 2009-11-28
Has any one noticed the applet mess in the Configuration Editor? Before, they were in a sub directory of AWN, where as now they are separate.

---

### Post by moonbeam on 2009-11-28
> **phenest said:**
> Has any one noticed the applet mess in the Configuration Editor? Before, they were in a sub directory of AWN, where as now they are separate.

Yes, we are aware.

It's a tradeoff associated with using libdesktopagnostic.  The (not unanimous) opinion, is that, while a bit messy, it's not intrinsically an issue, given the nature of direct editing of gconf.  But, it can be acknowledged that it is not as tidy.

And, to quote malept (libdesktopagnostic and awn dev): "It won't matter much soon, as everything will magically be fixed when dconf/gsettings is unleashed upon the world"

---

### Post by phenest on 2009-11-30
There was some updates today for the PPA, and I ended up with 2, yes two, bars: the one I'd configured down the left edge and a new one at the bottom (albeit only with the taskmanager applet).

Has anyone else noticed (via the Configuration Editor), there is a new key titled 'panels' (plural). If you add a second panel to the panel_list, you end up with more than one bar.

Now, my question is this: is this a new feature? I can't find any info on it (not that I've looked too hard as I'm tired).

---

### Post by nanog on 2009-11-30
Moonbeam, is parabolic zoom feasible for 0.4?  Google reveals an incomplete blueprint. 

Thanks for your work on this project!

---

### Post by moonbeam on 2009-11-30
> **nanog said:**
> Moonbeam, is parabolic zoom feasible for 0.4?  Google reveals an incomplete blueprint. 

Thanks for your work on this project!

Feasible?   Not really at this time.  The architecture for it isn't there, and quite frankly most of the core devs are, at best, indifferent to parabolic zoom.  This is not say that if someone came up with a patch that it would/wouldn't be accepted :-)

[http://wiki.awn-project.org/FAQ#Why_doesn.27t_Awn_have_the_parabolic_zoom_effect_that_other_docks_have.3F](http://wiki.awn-project.org/FAQ#Why_doesn.27t_Awn_have_the_parabolic_zoom_effect_that_other_docks_have.3F)

It also seems that some distributions (*cough* Fedora) are doing some hack-and-slash on docks with parabolic zoom enabled, but this has never really been the principle reason for not implementing.

---

### Post by moonbeam on 2009-11-30
> **phenest said:**
> There was some updates today for the PPA, and I ended up with 2, yes two, bars: the one I'd configured down the left edge and a new one at the bottom (albeit only with the taskmanager applet).

Has anyone else noticed (via the Configuration Editor), there is a new key titled 'panels' (plural). If you add a second panel to the panel_list, you end up with more than one bar.

Now, my question is this: is this a new feature? I can't find any info on it (not that I've looked too hard as I'm tired).

Let's just say it's a bug for now :-)

---

### Post by Reiger on 2009-11-30
> **PuddingKnife said:**
> Ok, so I followed the instructions here:

[http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

I restarted the computer and it was like I had just installed a fresh Ubuntu! All my personal data is gone except for software I had installed before like Blender and PiTiVi and compiz button. How would it have deleted all my data but left programs Ive installed??

Help, Im freaking out! Is there a way to restore my computer to yesterday so that I can leave all this nasty business behind me??

From that guide:
> 
rm -rf ~/.gconf/apps/panel

This looks like a culprit command. If misspelled as rm -rf ~/ .gconf/apps/panel (with a stray space) you will likely end up wiping your home directory. I do not actually know (having had no incentive to wipe my home directory like that) whether or not this would yield an error due to rm -rf ~/ wiping .gconf/apps/panel before rm -rf tries to wipe .gconf/apps/panel (e.g. a file not found type of error). But it may not if rm only checks in advance whether or not the file is available and suppresses all further errors when files are no longer found because rm just deleted them; or employs some kind of intelligent queuing mechanism (in which case it might intelligently decide to wipe .gconf/apps/panel before ~/ as it is more specific)...

---

### Post by nanog on 2009-12-01
Anyone know if there is a way to close all grouped applications in the task manager (e.g. kill firefox processes simultaneously after update).

---

### Post by moonbeam on 2009-12-01
> **nanog said:**
> Anyone know if there is a way to close all grouped applications in the task manager (e.g. kill firefox processes simultaneously after update).

Not yet.  Some work on taskmanager context menus is underway (involving defining them using xml).  I'm planning on including a close all menu item in the the default menu.

---

### Post by nanog on 2009-12-01
> I'm planning on including a close all menu item in the the default menu.

Thanks!

---

### Post by darco on 2009-12-05
The Cairo Menu applet crashed on me. Its still on my toolbar but it says "click to restart" but that does not help. I have removed/reinstalled AWN but the problem remains. I removed AWN thru synaptic, is the purge command more thorough?

thxs

darco

---

### Post by moonbeam on 2009-12-05
> **darco said:**
> The Cairo Menu applet crashed on me. Its still on my toolbar but it says "click to restart" but that does not help. I have removed/reinstalled AWN but the problem remains. I removed AWN thru synaptic, is the purge command more thorough?

thxs

darco

Could you please file a bug at [https://bugs.launchpad.net/awn-extras](https://bugs.launchpad.net/awn-extras)

I'd like to get some info on this crash before you reset your settings.

Thanks,

---

### Post by darco on 2009-12-05
> **moonbeam said:**
> could you please file a bug at [https://bugs.launchpad.net/awn-extras](https://bugs.launchpad.net/awn-extras)

i'd like to get some info on this crash before you reset your settings.

Thanks,

done!

*edit* Also I re-enabled the Gnome panels and they are going bonkers. Flashing panel, had to run a killall. I see some other threads on this but no fix. I wonder if they are related?

---

### Post by vgrisham on 2009-12-05
How do you get the corner thing? I chose edgy, but I don't see a way to activate a corner applet.

EDIT: Got it. Never mind. You have to pull the position on the screen slider all the way over to the left. If you put the notification area on the right and then slide the dock to the right, the notification area becomes curved, which is an interesting effect. 

By the way, thanks for this thread. I have been using AWN for years. The new version is great, but I never would have explored all of the new features if it hadn't have been for this thread.

---

### Post by donniezazen on 2009-12-06
Hi All,

I would really like to have a Dock but the thing is it makes my system slow and its not as fast and stable as in Mac OS. Its not at all convenient when you want to fastly switch between windows. It hides it comes and then takes few more seconds to load up the applet. Does anyone else shares my frustration?

Regards,
SK.

---

### Post by vgrisham on 2009-12-06
> **solwic said:**
> 
EDIT:  Besides, when you turn off the panel, certain functions go away (like Alt + F2).  Right now, I've hidden mine, unexpanded it, shrunk it to 12px, removed everything but the menu, and changed the unhide time to 2 seconds, so it doesn't pop out if I run the mouse across the top of the screen.  Seems to be working so far....

Where can you change the unhide time for the top panel?

Never mind. The setting is in gconf-editor.

---

### Post by vexorian on 2009-12-06
> **soham_1207 said:**
> Hi All,

I would really like to have a Dock but the thing is it makes my system slow and its not as fast and stable as in Mac OS. Its not at all convenient when you want to fastly switch between windows. It hides it comes and then takes few more seconds to load up the applet. Does anyone else shares my frustration?

Regards,
SK.
Could it be you have GPU driver issues?

---

### Post by COden6484 on 2009-12-06
I'm trying to install the latest version on my AMD64 Karmic computer.  I've added the repository to the list, but whenever I try to use Synaptic to install it I get the following error:
> avant-window-navigator-trunk:
 Depends: avant-window-navigator-data-trunk but it is not going to be installed
 Recommends: awn-settings-trunk but it is not going to be installed
 Recommends: awn-applets-c-core-trunk but it is not going to be installed
 Recommends: awn-applets-python-core-trunk but it is not going to be installed


If I try to install it using apt-get I get the following message:
> The following packages have unmet dependencies:
  avant-window-navigator-trunk: Depends: avant-window-navigator-data-trunk (>= 0.3.9.1~bzr1796-1.9.10) but it is not going to be installed


In Synaptic I see that avant-window-navigator-trunk is version 0.3.9.1~bzr1796-1.9.10 and avant-window-navigator-data-trunk is version 0.3.9.1~bzr1789-1.9.10.  Could this be the problem?  Will it not install because the versions don't match up?  Thanks for any help.

---

### Post by gilir on 2009-12-06
Please wait a bit more, some packages are not build yet, so there is depends problem. It should be fixed shortly.
You can also monitor the progress here : [https://edge.launchpad.net/~awn-testing/+archive/ppa/+packages](https://edge.launchpad.net/~awn-testing/+archive/ppa/+packages)
If i386 are not build (even if you are under amd64), be prepare for some depends problem (like now).

---

### Post by donniezazen on 2009-12-06
> **vexorian said:**
> Could it be you have GPU driver issues?

If so. How to find out that?

Thanks.

---

### Post by COden6484 on 2009-12-06
> **gilir said:**
> Please wait a bit more, some packages are not build yet, so there is depends problem. It should be fixed shortly.
You can also monitor the progress here : [https://edge.launchpad.net/~awn-testing/+archive/ppa/+packages]("https://edge.launchpad.net/%7Eawn-testing/+archive/ppa/+packages")
If i386 are not build (even if you are under amd64), be prepare for some depends problem (like now).

Ok, sounds good.  Thanks!

---

### Post by Toadinator on 2009-12-06
> **soham_1207 said:**
> Hi All,

I would really like to have a Dock but the thing is it makes my system slow and its not as fast and stable as in Mac OS. Its not at all convenient when you want to fastly switch between windows. It hides it comes and then takes few more seconds to load up the applet. Does anyone else shares my frustration?

Regards,
SK.

1) Try turning Compiz off. AWN can work without it.

2) You can use "panel mode", which makes the dock act just like a regular gnome panel.

---

### Post by donniezazen on 2009-12-06
> **Toadinator said:**
> 1) Try turning Compiz off. AWN can work without it.

2) You can use "panel mode", which makes the dock act just like a regular gnome panel.

Thanks it did work.

With "you can use panel mode" do you mean style=none.

Thanks.

---

### Post by McDuff on 2009-12-07
> **soham_1207 said:**
> 
With "you can use panel mode" do you mean style=none.


panel mode is “behaviour=panel mode”

---

### Post by donniezazen on 2009-12-07
> **McDuff said:**
> panel mode is “behaviour=panel mode”

Thanks.

---

### Post by PuddingKnife on 2009-12-07
> **Reiger said:**
> From that guide:


This looks like a culprit command. If misspelled as rm -rf ~/ .gconf/apps/panel (with a stray space) you will likely end up wiping your home directory. I do not actually know (having had no incentive to wipe my home directory like that) whether or not this would yield an error due to rm -rf ~/ wiping .gconf/apps/panel before rm -rf tries to wipe .gconf/apps/panel (e.g. a file not found type of error). But it may not if rm only checks in advance whether or not the file is available and suppresses all further errors when files are no longer found because rm just deleted them; or employs some kind of intelligent queuing mechanism (in which case it might intelligently decide to wipe .gconf/apps/panel before ~/ as it is more specific)...


It was crazy. All apps were present but Gnome's branding replaced Ubuntu, and all personal data was gone.

I've since recovered everything off of my back up and did a complete install of Ubuntu -- before I was running a dual boot. Now Im getting quite good at setting up AWN how I like it. :)

---

### Post by AllRadioisDead on 2009-12-07
I never thought I'd see myself using a dock, ever. 
To be honest I pretty much hate them, but with the implementation of panel mode and all these nice applets, AWN has made a believer out of me.

---

### Post by blur xc on 2009-12-07
So, I've been using this version for a bit now, and I'm not that impressed.  Other than being able to extend it to the edges of the screen (which I don't do), I don't see it doing anything particularly special over the old version.  The control panel is maybe a bit more streamlined, but as it stands I can't change the color of the background of my dock.  Those options are greyed out in the them editor, and I don't know how to create a new them, in case the default one is uneditable?

BM

---

### Post by Dysphoria on 2009-12-07
Hmmm, I'm not that impressed. I'll stick to Docky.

But as a side note: did anyone notice the ridiculous amount of entries in the Gnome configuration? (run gconf-editor and see for yourself). It's starting to look like the Windows registry with each awn applet having its own registry settings (even the ones you have never used).

---

### Post by moonbeam on 2009-12-07
> **blur xc said:**
> So, I've been using this version for a bit now, and I'm not that impressed.  Other than being able to extend it to the edges of the screen (which I don't do), I don't see it doing anything particularly special over the old version.  The control panel is maybe a bit more streamlined, but as it stands I can't change the color of the background of my dock.  Those options are greyed out in the them editor, and I don't know how to create a new them, in case the default one is uneditable?

BM

When editing a theme just uncheck "use gtk theme" and you'll be able to modify the items that are greyed out.  Yes, the theme editor still needs a bit of work.

---

### Post by phenest on 2009-12-08
> **Dysphoria said:**
> Hmmm, I'm not that impressed. I'll stick to Docky.

But as a side note: did anyone notice the ridiculous amount of entries in the Gnome configuration? (run gconf-editor and see for yourself). It's starting to look like the Windows registry with each awn applet having its own registry settings (even the ones you have never used).

See post #111.

---

### Post by jmcgovern on 2009-12-08
I love it!  I do have one issue though.  the clock applet font is painfully small, and I can't seem to be able to change it.  I can see where it can be changed in teh settings for the applet, but the changes never take effect,  Not even a reset helps.

---

### Post by Greenwidth on 2009-12-08
I've tried using a dock before but wasn't overly impressed, I am converted.

---

### Post by hanlin on 2009-12-08
How did you get the weather to show up like that? I checked Use transparent/curved forecast dialog, and it doesn't do anything.

---

### Post by Toadinator on 2009-12-08
> **jmcgovern said:**
> I love it!  I do have one issue though.  the clock applet font is painfully small, and I can't seem to be able to change it.  I can see where it can be changed in teh settings for the applet, but the changes never take effect,  Not even a reset helps.

If you follow my instructions on the front page, you can add a lot of extra applets; one of which is a great clock applet. Here's a picture of it: [http://farm3.static.flickr.com/2740/4156341369_8216df3cae_b.jpg]("http://farm3.static.flickr.com/2740/4156341369_8216df3cae_b.jpg")

As you can see, my desktop looks quite a bit nicer now! :D

---

### Post by Greenwidth on 2009-12-08
I don't remember doing anything other than using the transparent/curved forecast dialog..
What do you get?

---

### Post by hanlin on 2009-12-08
It looks the same as when it's unchecked: grayish background and black blocks for the 5 days.

---

### Post by jmcgovern on 2009-12-08
> **Toadinator said:**
> If you follow my instructions on the front page, you can add a lot of extra applets; one of which is a great clock applet. Here's a picture of it: [http://farm3.static.flickr.com/2740/4156341369_8216df3cae_b.jpg]("http://farm3.static.flickr.com/2740/4156341369_8216df3cae_b.jpg")

As you can see, my desktop looks quite a bit nicer now! :D


That's the same applet in my dock...the font is TINY and I can't change it.  I even get no preview in the properties dialog.  see SS.

---

### Post by Greenwidth on 2009-12-09
@hanlin
Are you running Compiz? Mine looks like that when using Metacity.

---

### Post by Greenwidth on 2009-12-09
oops double post!

---

### Post by hanlin on 2009-12-09
Yes, I'm using compiz. That's very interesting that it doesn't work with compiz but it does with metacity.

---

### Post by Greenwidth on 2009-12-09
Other way round, works with Compiz not Metacity. Well it does 'work' the transparency bit doesn't.
Works OK in gnome-shell too:

---

### Post by moonbeam on 2009-12-09
> **Greenwidth said:**
> Other way round, works with Compiz not Metacity. Well it does 'work' the transparency bit doesn't.
Works OK in gnome-shell too:

You need to activate the compositor in Metacity if you want transparency.

---

### Post by kevpan815 on 2009-12-09
I think that it would be better if we don't rock the boat as this is a Long Term Support Release.

---

### Post by woodbj on 2009-12-09
> **Greenwidth said:**
> Other way round, works with Compiz not Metacity. Well it does 'work' the transparency bit doesn't.
Works OK in gnome-shell too:

OMG where did you get your background

---

### Post by Greenwidth on 2009-12-09
> **woodbj said:**
> OMG where did you get your background

[http://izach7.deviantart.com/gallery/](http://izach7.deviantart.com/gallery/)

---

### Post by moonbeam on 2009-12-10
Just want to mention that we've opened up a rewrite themes thread on awn forums.

[http://awn.planetblur.org/index.php?shard=forum&action=g_reply&ID=2330&page=1&isLive=true](http://awn.planetblur.org/index.php?shard=forum&action=g_reply&ID=2330&page=1&isLive=true)

Please post, we've been seeing some beautiful themes showing up and would like to encourage their sharing.

(I do apologize for our very ajaxy forum software, its use is a bit of a painful legacy issue)

---

### Post by 6205 on 2009-12-11
IHMO Docky is better dock and it will be in the near future. AWN has only one advantage, currently has more applets, but it does mean anything, because Docky much more polished, pretier, easier to use and optimized for GNOME.

---

### Post by moonbeam on 2009-12-11
> **6205 said:**
> IHMO Docky is better dock and it will be in the near future. AWN has only one advantage, currently has more applets, but it does mean anything, because Docky much more polished, pretier, easier to use and optimized for GNOME.

We chat with DBO quite often.  In many aspects Docky and Awn are converging to the same spot from different directions though there are, and will remain, differences in emphasis.

Anyway, one can more or less count on popular/good features in awn showing up in Docky and vice versa (in some form or other) :-)

---

### Post by bluebyt on 2009-12-11
> **6205 said:**
> IHMO Docky is better dock and it will be in the near future. AWN has only one advantage, currently has more applets, but it does mean anything, because Docky much more polished, pretier, easier to use and optimized for GNOME.

I disagree with you, AWN 0.4 has become my main Dock. 

Docky is not bad but lacking features. You cannot change the icons on the dock, that mean you have all this ugly icons!

---

### Post by 6205 on 2009-12-13
> **bluebyt said:**
> I disagree with you, AWN 0.4 has become my main Dock. 

Docky is not bad but lacking features. You cannot change the icons on the dock, that mean you have all this ugly icons!

Yes you cannot, if you're desperate mac os x fetishist you're out of luck. Humanity icon theme is amazing and looks great and will be even more enhanced in comming months so those "ugly" comments are nonsense.

---

### Post by Gina on 2009-12-13
Ugly is like beauty - in the eye of the beholder.

That's why there's always arguments about themes and styles!

---

### Post by ranch hand on 2009-12-13
> **Gina said:**
> Ugly is like beauty - in the eye of the beholder.

That's why there's always arguments about themes and styles!
+1

And, they get old in a hurry, particularly if, like me, you don't really care as long as the stuff WORKS.

---

### Post by VMC on 2009-12-13
> **Gina said:**
> Ugly is like beauty - in the eye of the beholder.

That's why there's always arguments about themes and styles!

> **ranch hand said:**
> +1

And, they get old in a hurry, particularly if, like me, you don't really care as long as the stuff WORKS.

I mostly agree with these statements. I tried AWN, and it messed up gconf to the point I had to delete and start over - without AWN!

I removed AWN, but I notice gconf-editor had tons of AWN items listed that I couldn't remove or edit out.

AWN probably looks and works great for the correct hardware, but on my limited i865 video, it didn't work well.

---

### Post by gregbzh on 2009-12-13
I've just installed 0.4 and really like it, but can anyone tell me if it's possible to remove ALL of the gnome panels and if so how?  Cheers.

ps.  I'm already autohiding the last panel.

---

### Post by phenest on 2009-12-13
> **gregbzh said:**
> I've just installed 0.4 and really like it, but can anyone tell me if it's possible to remove ALL of the gnome panels and if so how?  Cheers.

ps.  I'm already autohiding the last panel.

See post #73.

---

### Post by gregbzh on 2009-12-13
> **phenest said:**
> See post #73.

Thanks mate.  Funny how page 8 was the only one I didn't read.  I'll check it out.  Cheers.

---

### Post by darco on 2009-12-13
Does anyone know how to change the icon of an "active applet"? I know its simple to change a "task manager" icon but an active applet isnt so easy.
I tried via gconf-editor, changed the App/awn-applet-cairo-menu/applet_icon to mintmenu but was a no-go. I was able to add a task manager icon of the mint menu to the panel, which would have worked fine but now I am unable to "move" the mintmenu  icon to the far left of my panel using the Edgy style. Task manager icons seem to be limited in their range.

thxs

darco

---

### Post by moonbeam on 2009-12-13
> **darco said:**
> Does anyone know how to change the icon of an "active applet"? I know its simple to change a "task manager" icon but an active applet isnt so easy.
I tried via gconf-editor, changed the App/awn-applet-cairo-menu/applet_icon to mintmenu but was a no-go. I was able to add a task manager icon of the mint menu to the panel, which would have worked fine but now I am unable to "move" the mintmenu  icon to the far left of my panel using the Edgy style. Task manager icons seem to be limited in their range.

thxs

darco

You can change _most_ applet icons by dragging and dropping the desired icon onto the applet.

---

### Post by darco on 2009-12-13
thank you!


darco

---

### Post by gregbzh on 2009-12-14
>  Originally Posted by phenest
See post #73.

I have already tried this and it doesn't work (at least it hasn't yet).  Any other ideas would be much appreciated.

---

### Post by meborc on 2009-12-14
> **gregbzh said:**
> I have already tried this and it doesn't work (at least it hasn't yet).  Any other ideas would be much appreciated.

i got rid of xfce panels by deleting them and logging out with save session ticked... i guess there should be something similar in gnome

there is also a thread about removing panels in gnome (there is a thread on anything in ubuntuforums) - [http://ubuntuforums.org/showthread.php?t=405721](http://ubuntuforums.org/showthread.php?t=405721)

---

### Post by quazi on 2009-12-26
So, is anyone else having trouble with the fonts in AWN when you click on a launcher with multiple windows open?  For me, I keep ending up with a darkish font on a black background regardless of theme.  It's a pain in the ***.

---

### Post by AndyP79 on 2009-12-30
Hi Moombeam, if your still checking this thread out. Do you have any info for AWN .4 in Lucid? I have been using it in Karmic, but really want it in my Lucid Alpha that I am testing(which is great so far in case anyone was wondering). I have tried to add the PPA for both Lucid of which there appears to actually be none right now, and the Karmic one. Nothing. With Karmic, it just showed up in synap, I uninstalled the regular AWN, then added the trunk and it worked fine, but that was karmic.

Thanks for all the work you and your team have put into this. Even if this does not end up in any release anytime soon, it won't matter, cause I will end up installing it anyway. I have been enjoyin gthe constant flow of update I see coming through on Karmic, so i know ya'll are working up. Keep up the great work. 
Happy New Years

---

### Post by moonbeam on 2009-12-30
> **AndyP79 said:**
> Hi Moombeam, if your still checking this thread out. Do you have any info for AWN .4 in Lucid? I have been using it in Karmic, but really want it in my Lucid Alpha that I am testing(which is great so far in case anyone was wondering). I have tried to add the PPA for both Lucid of which there appears to actually be none right now, and the Karmic one. Nothing. With Karmic, it just showed up in synap, I uninstalled the regular AWN, then added the trunk and it worked fine, but that was karmic.

Thanks for all the work you and your team have put into this. Even if this does not end up in any release anytime soon, it won't matter, cause I will end up installing it anyway. I have been enjoyin gthe constant flow of update I see coming through on Karmic, so i know ya'll are working up. Keep up the great work. 
Happy New Years

To quote someone who is working on the Lucid packages it's a "work in progress".  My understanding is that there are issues with Python on Lucid which are blocking the build.

---

### Post by AndyP79 on 2009-12-30
> **moonbeam said:**
> To quote someone who is working on the Lucid packages it's a "work in progress".  My understanding is that there are issues with Python on Lucid which are blocking the build.

Ahh... I see said the blind man. Well, I have my PPA in, and I will just wait to see when the updates show up. I have been using it in Karmic and I love it. 
Thanks for all the hard work again

---

### Post by Jordanwb on 2009-12-30
I added the repo using "add-apt-repo...", changed "lucid" to "karmic" and "apt-get update"'d but the latest version of avant-window-navigator-trunk is 0.3.9.1 and it wants to install HAL. I suppose that the Python issue has a hand in it?

Great, something in my computer is making a buzzing noise which keeps coming and going.

---

### Post by iggykoopa on 2009-12-30
not sure what the issue is jordanwb, I did the same thing as you yesterday and it installed fine.... running it now. Maybe try completely uninstalling the old version first? It was on a fresh install.

---

### Post by Jordanwb on 2009-12-30
> **iggykoopa said:**
> not sure what the issue is jordanwb, I did the same thing as you yesterday and it installed fine.... running it now. Maybe try completely uninstalling the old version first? It was on a fresh install.

I don't have AWN installed. Plus I was sortof questioning the HAL dependency since it is deprecated.

---

### Post by gilir on 2010-01-02
Lucid packages are now available on the awn-testing PPA. Please remove any karmic packages you have on your lucid system :-)

---

### Post by Jordanwb on 2010-01-02
I'm not sure the Ubuntu guys are going to include AWN, since HAL is a dependency.

I'll take a look at it.

*Edit*

Is there a network manager applet?

---

### Post by moonbeam on 2010-01-02
> **Jordanwb said:**
> I'm not sure the Ubuntu guys are going to include AWN, since HAL is a dependency.

I'll take a look at it.

*Edit*

Is there a network manager applet?

The HAL dep is probably just for the battery applet in extras.  No core dependency on it.

No packaged network manager applet.  Some (alpha) code is available at [https://launchpad.net/awn-nm-applet](https://launchpad.net/awn-nm-applet) . I will get around to doing some more work on it when I have an opportunity.

---

### Post by gilir on 2010-01-03
> **Jordanwb said:**
> I'm not sure the Ubuntu guys are going to include AWN, since HAL is a dependency.

It's not. Just remove it and you will see that Awn works fine without it. Just the battery applet may have some problem to work.

---

### Post by dyltman on 2010-01-03
How stable is this?

edit: I hated the previous AWN because of the way it closed apps else it was pretty fancy, this thing looks even more awesome

---

### Post by nanog on 2010-01-03
Its quite stable in my experience (testing on 3 laptops and 2 desktops). 

Moonbeam, thanks for the close all function!

---

### Post by AndersAA on 2010-01-03
Seriously doubt it'll make it in as default, but maybe it could be as an unsupported option in apperance -> visual effects or something, it's quite impressive.

---

### Post by pritamps on 2010-01-04
> **quazi said:**
> So, is anyone else having trouble with the fonts in AWN when you click on a launcher with multiple windows open?  For me, I keep ending up with a darkish font on a black background regardless of theme.  It's a pain in the ***.

Yes...I changed the colours in Dock Preferences -> Themes -> Customize :)

---

### Post by LKjell on 2010-01-04
AWN is nice is you could align applets and replace dockbarx with the default launcher/taskmanager. Then I would happily replace the gnome-panel.

---

### Post by Zoot7 on 2010-01-05
I think the Gnome panels are fine. I was never a fan of docks.

---

### Post by gabo.cr on 2010-01-05
I've being using AWN for a long time and I love it.
That's one of the first things I get after a new installation.

---

### Post by dyltman on 2010-01-05
Wow, AWN 0.4 certainly is amazing, just tried it out.

---

### Post by nanog on 2010-01-05
moonbeam and gilir,

As far as I can tell the only way to shutdown awn 4.0 is to "killall avant-windows-navigator". I think a right click option that kills the program should be available (I believe it was there earlier). Should I open a bug?

---

### Post by moonbeam on 2010-01-05
> **nanog said:**
> moonbeam and gilir,

As far as I can tell the only way to shutdown awn 4.0 is to "killall avant-windows-navigator". I think a right click option that kills the program should be available (I believe it was there earlier). Should I open a bug?

It's available in the right click at the ends of the dock, and in the case of expanded mode/separators/expanders in the places where there are no applets.

The Preferences applet also provides a Quit option in its context menu.  New installs will provide this as one of the default applets in the applet list, existing configurations would need start Awn Settings up and add it to the applet list.

There, have been recurring discussions in #awn about this and we still feel it's best to not have it available in the applet context menus, yet we do recognize that the current situation isn't quite right either.

---

### Post by donniezazen on 2010-01-05
I like AWN but i think Docky is faster when it comes to opening the applications.

---

### Post by nanog on 2010-01-05
> It's available in the right click at the ends of the dock, and in the case of expanded mode/separators/expanders in the places where there are no applets.

moonbeam,
actually when I select "style = none" this is not the case. its also very hard to find the end with some of the other styles.

```
ii  avant-window-navigator-trunk               0.3.9.1~bzr1859-1.9.10                                   A MacOS X like panel for GNOME

```

---

### Post by moonbeam on 2010-01-05
> **nanog said:**
> moonbeam,
actually when I select "style = none" this is not the case. its also very hard to find the end with some of the other styles.

```
ii  avant-window-navigator-trunk               0.3.9.1~bzr1859-1.9.10                                   A MacOS X like panel for GNOME

```

ah yes... style = none might be an issue.  If you feel like opening a bug for that one it would be appreciated.

---

### Post by mhr3 on 2010-01-06
> **nanog said:**
> moonbeam,
actually when I select "style = none" this is not the case. its also very hard to find the end with some of the other styles.

For style=none you can use the preferences applet to get the menu with Quit option.

---

### Post by nanog on 2010-01-06
**I don't see this option on my preferences menu:**

[IMG]http://137.53.250.24/preferences.png[/IMG].
[B]
Am I looking in the right spot?[/B]

---

### Post by moonbeam on 2010-01-06
> **nanog said:**
> **I don't see this option on my preferences menu:**

[IMG]http://137.53.250.24/preferences.png[/IMG].
[B]
Am I looking in the right spot?[/B]

Go the Applets tab.  And look for the applet called "Preferences" and add it to the applet list.

---

### Post by EJM3377 on 2010-01-08
I really like this AWN, but I have ran across two apps so far that don't work me. The Battery and Hardware Sensor, there might be more that don't but those are the two I've tried so far. The error I get is, "Settings instance has no attribute 'load_preferences.'" Is this because this is still in the testing phase or is it me? If it's me how do I correct it?

---

### Post by moonbeam on 2010-01-08
> **EJM3377 said:**
> I really like this AWN, but I have ran across two apps so far that don't work me. The Battery and Hardware Sensor, there might be more that don't but those are the two I've tried so far. The error I get is, "Settings instance has no attribute 'load_preferences.'" Is this because this is still in the testing phase or is it me? If it's me how do I correct it?

Yes.  They are broken at the moment.  We hope they will be fixed soon.  Sorry for the inconvenience everyone.

---

### Post by ptviperz on 2010-01-09
Everytime I try to install any of the applets, it opens up a window to browse for the applet. I've tried installing all the extras via apt-get but it tells me they are already installed. 

Am I missing something obvious?

---

### Post by quazi on 2010-01-09
So, I'm still having issues with font colors:

[[img]http://www.ubuntu-pics.de/thumb/37330/screenshot_001_OSTa63.png[/img]](http://www.ubuntu-pics.de/bild/37330/screenshot_001_OSTa63.png)

Anyone know why this is happening?

---

### Post by moonbeam on 2010-01-09
> **quazi said:**
> So, I'm still having issues with font colors:

[[img]http://www.ubuntu-pics.de/thumb/37330/screenshot_001_OSTa63.png[/img]](http://www.ubuntu-pics.de/bild/37330/screenshot_001_OSTa63.png)

Anyone know why this is happening?

Looks to me like your theme info has disabled the use of gtk for your dialog background colour.  Have you installed an awn-theme or edited theme info using gconf-editor?

---

### Post by quazi on 2010-01-09
I've installed awn themes through awn itself trying to fix the problem but it has no effect.  I haven't mucked around with themes in gconf-editor.

It's using the gnome theme font color for Windows, but not the Background.

---

### Post by moonbeam on 2010-01-09
> **quazi said:**
> I've installed awn themes through awn itself trying to fix the problem but it has no effect.  I haven't mucked around with themes in gconf-editor.

What GTK/Gnome theme do you use

---

### Post by quazi on 2010-01-09
> **moonbeam said:**
> What GTK/Gnome theme do you use

New Wave.

EDIT: While this isn't really a solution, I changed my theme to Dark Room and everything works fine, so I'm going to stick with it.

---

### Post by moonbeam on 2010-01-09
> **quazi said:**
> New Wave.

Try a different theme and see if the problem is still present.

If it is still happening then 

1) start gconf-editor and navigate to /apps/avant-window-navigator/theme/

2) Look for dialog_gtk_mode and make sure it is checked.

---

### Post by moonbeam on 2010-01-09
> **quazi said:**
> New Wave.

EDIT: While this isn't really a solution, I changed my theme to Dark Room and everything works fine, so I'm going to stick with it.

If a gtk theme is providing poor results you can always 

1) start gconf-editor and navigate to /apps/avant-window-navigator/theme/

2) Look for dialog_gtk_mode and uncheck it.  Then set the rest of dialog_* as you like.

Keep in mind if you change your theme and would like awn to start using the theme colours for the dialog again then re-enable dialog_gtk_mode.

---

### Post by quazi on 2010-01-09
Thanks for the tip.  Interestingly enough my problem was that it was unchecked, no idea how that could have happened.

---

### Post by ptviperz on 2010-01-10
> **ptviperz said:**
> Everytime I try to install any of the applets, it opens up a window to browse for the applet. I've tried installing all the extras via apt-get but it tells me they are already installed. 

Am I missing something obvious?

Ok, haha, double click to start applet instead of selecting and using the 'Install Applet' radio button. Not readily apparent IMO

---

### Post by lucazade on 2010-01-10
> **moonbeam said:**
> Try a different theme and see if the problem is still present.

If it is still happening then 

1) start gconf-editor and navigate to /apps/avant-window-navigator/theme/

2) Look for dialog_gtk_mode and make sure it is checked.

Same problem here.. using murrine engine and turrican theme


I think the issue is related to gtkrc panel color:

style "panel" {
	fg[NORMAL]        = "#FFFFFF"
	fg[PRELIGHT]      = "#FFFFFF"
	fg[ACTIVE]        = "#FFFFFF"
	bg[NORMAL]        = shade (0.2, "#D9D9D9")
	bg[PRELIGHT]      = shade (0.30, "#D9D9D9")
	bg[ACTIVE]        = shade (0.26, "#D9D9D9")
}
# Panel
class "*Panel*" style "panel"
class "*Notif*" style "panel"
class "*Tray*" style "panel"
widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"
class "PanelAppletFrame" style "handle"

Awn inherits panel's bg_color but not fg_color (1st screenshot)

Disabling compiz Awn can't get at all panel bg_color. (2nd screenshot)

---

### Post by mhr3 on 2010-01-10
> **lucazade said:**
> Same problem here.. using murrine engine and turrican theme


I think the issue is related to gtkrc panel color:

style "panel" {
    fg[NORMAL]        = "#FFFFFF"
    fg[PRELIGHT]      = "#FFFFFF"
    fg[ACTIVE]        = "#FFFFFF"
    bg[NORMAL]        = shade (0.2, "#D9D9D9")
    bg[PRELIGHT]      = shade (0.30, "#D9D9D9")
    bg[ACTIVE]        = shade (0.26, "#D9D9D9")
}
# Panel
class "*Panel*" style "panel"
class "*Notif*" style "panel"
class "*Tray*" style "panel"
widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"
class "PanelAppletFrame" style "handle"

Awn inherits panel's bg_color but not fg_color (1st screenshot)

Disabling compiz Awn can't get at all panel bg_color. (2nd screenshot)

Yea, we don't expect the theme to be so generic, the class "*Panel*" rule screws things up, try to use "Panel*" instead.

---

### Post by lucazade on 2010-01-10
> **mhr3 said:**
> Yea, we don't expect the theme to be so generic, the class "*Panel*" rule screws things up, try to use "Panel*" instead.

Why you say "so generic"?
Attached the gtkrc theme.. please explain! :)
(It needs latest rev from murrine git)

---

### Post by Eestlane on 2010-01-11
AWN 0.4 seems to rule. I've currently set the behaviour to "Transparency", which means I can see half-transparent fullwidth-dock in the bottom, but can click on stuff behind it.
Moving mouse to the bottom of the screen fades the dock in and it's fade out again when the mouse cursor is out of dock area for 1,5 seconds or so.
I might go back to the panel mode, though in case I find I don't need that extra 40px vertical space for apps.

Also replaces the normal panels for me. Though I've let one panel survive to test Lucid's Indicator-applet and session-indicator-applet (probably written a bit differently, I've got localized version). Made it non-expanded and auto-hideable, to avoid disturbance.

Applets themselves should be taken care of now, as the dock seems to be almost perfect (though maybe multiple docks would be a good feature for some users).

It might be good idea to allow use of gnome-panel applets, but anything essential probably gets replaced by it's own anyway.

Absolutely well done!

---

### Post by lucazade on 2010-01-11
> **mhr3 said:**
> Yea, we don't expect the theme to be so generic, the class "*Panel*" rule screws things up, try to use "Panel*" instead.

I've modified gtkrc using "Panel*" as you suggested.
Now menu are gray with black text.. i'll see if i get white text on black bg.

---

### Post by shafin on 2010-01-11
Just replaced my panel with AWN. It works great. Just two inquiries..
1. I need an applet which works like ubuntu menu, with separate Applications and System menus.
2. Is there any equivalent of [namebar]("http://www.gnome-look.org/content/show.php/NameBar?content=101643") in AWN?

BTW,Is there any plan to get some sort of Gnome-shell overview like menu into AWN? Then we could still enjoy compiz hotness once gnome-shell arrives.
Oh, and any possible AWN-Zeitgeist integration, like Docky2?

Big thumbs up to the developers. You've done a great job.

---

### Post by mhr3 on 2010-01-11
> **lucazade said:**
> I've modified gtkrc using "Panel*" as you suggested.
Now menu are gray with black text.. i'll see if i get white text on black bg.
That's right, dialogs are meant to look like standard windows. Though you should be able to theme the dialog using gtkrc with class "AwnDialog" (though I have a suspicion I need to fix something for that to work).

---

### Post by moonbeam on 2010-01-11
> **shafin said:**
> Just replaced my panel with AWN. It works great. Just two inquiries..
1. I need an applet which works like ubuntu menu, with separate Applications and System menus.
2. Is there any equivalent of [namebar]("http://www.gnome-look.org/content/show.php/NameBar?content=101643") in AWN?

BTW,Is there any plan to get some sort of Gnome-shell overview like menu into AWN? Then we could still enjoy compiz hotness once gnome-shell arrives.
Oh, and any possible AWN-Zeitgeist integration, like Docky2?

Big thumbs up to the developers. You've done a great job.

Cairo Menu allows you to setup separate icons on the Dock for any submenu (you will need to right click a couple times to get the option to "Create icon".  At the moment you would need to do this for Preferences and Administration separately (grouping them under System is on one of my many todo lists).

Regarding namebar, I'll look into what it does and see if it fits in anywhere.

Gnome-shell integration will also happen in some form or other (remembering we are _not_ an Gnome app as such, many of use use XFCE or other environments).  Some Zeitgeist integration is also going to happen, it'll probably happen either this month or in February.  It's not that we don't plan on supporting many of the cool things that are happening but they're also not at the very top of the list, since those technologies are still very much in development.  But, I'm comfortable that the Zeitgeist API has settled down enough at this point that it is something that can be pursued.

---

### Post by Menti on 2010-01-12
> **moonbeam said:**
>  Some Zeitgeist integration is also going to happen, it'll probably happen either this month or in February.

This would be incredible.

I have been using AWN exclusively (no panel) for almost a couple of years now and I must say that 0.4 is wonderful. It feels a lot faster and lighter on my system, and applets like Cairo Menu, that crawled in the previous version, are really snappy now. I have also used AWN only as a window list, in combination with Gnome Shell, and it works nicely. Thank you very much.

Knowing that developers read this forum, I have a feature suggestion. Would it be possible that new windows of a running application would spawn dock icons next to the first icon of that application? I mean, after opening a second Firefox window, the new icon appears next to the first Firefox icon, instead of being in the right end of the task manager. This way, I would have all the icons of different Firefox windows together, followed by all icons of Thunderbird, whatever. It would be like automatic drag & drop using the grouping logic. Maybe some people would prefer that to grouping.

Thank you again, this is a great work.

---

### Post by moonbeam on 2010-01-12
> **Menti said:**
> 

Knowing that developers read this forum, I have a feature suggestion. Would it be possible that new windows of a running application would spawn dock icons next to the first icon of that application? I mean, after opening a second Firefox window, the new icon appears next to the first Firefox icon, instead of being in the right end of the task manager. This way, I would have all the icons of different Firefox windows together, followed by all icons of Thunderbird, whatever. It would be like automatic drag & drop using the grouping logic. Maybe some people would prefer that to grouping.


That's a very good idea.  And probably quite easy to do.  I will implement it soon.

Thanks,

---

### Post by estyles on 2010-01-12
> **Toadinator said:**
> You're welcome, but if it's ready for what's after Lucid then it might make the cut, since Gnome-Shell really needs a dock.

People keep saying this, but I fail to see why it's desirable, much less necessary.  Is there any reason that a dock isn't just an ugly (to me) and intrusive version of a panel?  I know some people like them and don't find them ugly, and I encourage those people to download AWN or docky or whatever.  But does a dock offer anything *useful* that gnome-panel doesn't?

It seems like when we're talking about an addition that is nothing more than eyecandy and is very taste-specific, the default should be to leave things as is...

---

### Post by nanog on 2010-01-12
uhpinyan:

*docks facilitate the efficient grouping  of multiple application instances.

*docks facilitate the communication of information as visual cues. 

**docks allow faster identification of application due to their pretty icons. 

*a panel is a subset of the larger dock universe.

*docks can take up less screen space than a panel.  

*a properly implemented dock will make windows users green with envy.

---

### Post by Spaced on 2010-01-22
> **pritamps said:**
> Yes...I changed the colours in Dock Preferences -> Themes -> Customize :)

If I do like you suggest I can change only the tooltips font, not the font of the windows that pop up when you have multiple open windows of the same software. Or is there a way of changing it that I haven't seen?

---

### Post by Triscuit713 on 2010-01-23
I am trying to compile awn 0.3.9 from bzr trunk for Fedora 12. I have all the dependencies, and ./autogen.sh completes. However, make yields the following errors:

# error parsing GIDL file: Error on line 1 char 1: Document was empty or contained only whitespace
# awn-custom.vala:30.122-30.142: error: The type name `Awn.CairoRoundCorners' could not be found
# awn-custom.vala:31.131-31.151: error: The type name `Awn.CairoRoundCorners' could not be found
# awn-custom.vala:42.81-42.90: error: The type name `Awn.Applet' could not be found
# awn-custom.vala:50.59-50.70: error: The type name `Awn.PathType' could not be found
# Generation failed: 4 error(s), 0 warning(s)
# make[2]: *** [awn.vapi] Error 1

---

### Post by phenest on 2010-01-26
How does the Shiny Switcher applet work? It only ever shows the current workspace.

---

### Post by Roasted on 2010-01-26
Can I organize things in the dock in a manner I want to? I always like to organize things in the gnome panel... pidgin first, firefox, thunderbird, media player, then all others, etc. Can I do that in awn?

---

### Post by phenest on 2010-01-26
> **Roasted said:**
> Can I organize things in the dock in a manner I want to? I always like to organize things in the gnome panel... pidgin first, firefox, thunderbird, media player, then all others, etc. Can I do that in awn?

In a word: Yes.

Open AWN Settings, and under Task Manager, check 'Drag and drop reordering'.

---

### Post by Roasted on 2010-01-26
> **phenest said:**
> In a word: Yes.

Open AWN Settings, and under Task Manager, check 'Drag and drop reordering'.

Is this under dock preferences, or something else?

---

### Post by phenest on 2010-01-26
> **Roasted said:**
> Is this under dock preferences, or something else?

Yes, Dock Preferences.

---

### Post by Roasted on 2010-01-26
Does AWN act somewhat less responsive to anybody else in regard to its auto hide? It seems to forget that it should hide... forcing me to hover over it, hover away, and THEN it finally leave.

Granted I just grabbed the repo version. It's probably old...

EDIT - got the updated PPA. Seems much nicer. But even though reorder grouping is enabled, I can drag the icons off now, but I cant seem to put them in different orders. For example, I have Firefox, Pidgin, Exaile, and an icon to browse my files in my home directory. I want that file browser icon to be on the far left, not the far right, yet I can't drag it there... :(

---

### Post by moonbeam on 2010-01-27
> **phenest said:**
> How does the Shiny Switcher applet work? It only ever shows the current workspace.

Could you file a bug with Window Manager info etc at [https://bugs.launchpad.net/awn-extras](https://bugs.launchpad.net/awn-extras)

A screenshot would also be useful in the bug.

---

### Post by uBeer on 2010-01-27
> **phenest said:**
> How does the Shiny Switcher applet work? It only ever shows the current workspace.

By scrolling over the icon you can switch workspaces (last time I looked).

---

### Post by Roasted on 2010-01-27
Uh, question. My AWN dock I have checked to auto start. Yet... it never auto starts. I always have to open it up on my own under Apps - Accessories each time I boot up.

Why is this?

---

### Post by moonbeam on 2010-01-28
> **Roasted said:**
> Uh, question. My AWN dock I have checked to auto start. Yet... it never auto starts. I always have to open it up on my own under Apps - Accessories each time I boot up.

Why is this?

I see you dropped by #awn with this issue also, it's a bit odd. If you haven't already done so could you please file a bug at [https://bugs.launchpad.net/awn](https://bugs.launchpad.net/awn)

---

### Post by phenest on 2010-01-28
Auto start works with me.

---

### Post by moviemaniac on 2010-01-29
I too have a problem with awn autostarting. Well, it autostarts, but it doesn't show. I have to kill the process and start it again after almost every login but it isn't reproducable every time. Right now I can't get AWN to show at all :(

//edit: now I know why:
> (avant-window-navigator:15467): GConf-CRITICAL **: gconf_value_get_list: assertion `value != NULL' failed



---

### Post by Jenkins1 on 2010-01-29
> **moviemaniac said:**
> I too have a problem with awn autostarting. Well, it autostarts, but it doesn't show. I have to kill the process and start it again after almost every login but it isn't reproducable every time. Right now I can't get AWN to show at all :(

//edit: now I know why:

I get the same error as well have you filled a bug? If not let me know and I will file one.

---

### Post by kaitwospirit on 2010-01-29
Just so you guys know, this doesn't seem to be just an AWN 0.4 thing. I'm still running 0.3 and I have the same problem - it won't show up. 

(avant-window-navigator:10599): GConf-CRITICAL **: gconf_value_get_list: assertion `value != NULL' failed

Wonder if it's gconf rather than AWN?

---

### Post by gilir on 2010-01-29
Seems to be a bug in gconf : [https://bugs.launchpad.net/bugs/514134](https://bugs.launchpad.net/bugs/514134)

---

### Post by phenest on 2010-01-30
I'v stopped using AWN for a bit as I'm now testing Gnome Shell. But I have a question regarding the removal of AWN. AWN has been purged but I cannot remove the gconf keys. If I unset them from the Configuration Editor, they seem to delete. Close the editor, and reopen, and they're back! Even using the command line, the will not delete. I can unset keys for other things like gnome panels (I don't have any keys left to test with now), but not AWN.

EDIT: Ignore this post. I think I've found a possible bug in gconf-editor.

---

### Post by philhughes on 2010-01-31
I've avoided Docks until now, but I really like this. A couple of questions:

1. There appears to be a very small amount of transparency in Panel mode - is there any way to change the degree of transparency?

2. Is there any way to change the icon spacing?

---

### Post by Roasted on 2010-01-31
So the other night I was in the AWN IRC and somebody there was very helpful in helping me troubleshoot, however we never got anywhere constructive because out of no where it started to auto launch again on my laptop. 

We edited the awn.desktop autostart file and edited the entry for AWN to calculator, and sure enough calculator auto started. Okay, fine. So I changed it back to AWN, and blam. AWN auto started.

Well my desktop had issues auto starting too, so I took Docky off of auto start to give it a shot and AWN was now auto starting. Were there any updates that fixed this?

---

### Post by TerminX on 2010-01-31
Yes, the gconf bug was fixed and a new package was uploaded.

---

### Post by Roasted on 2010-01-31
> **TerminX said:**
> Yes, the gconf bug was fixed and a new package was uploaded.

No kidding? What luck... Good to hear it's patched! Was that just today? (1/31)?

---

### Post by FrancoNero on 2010-01-31
looks nice, but will turn gnome into a windows/kde clone :) where are "new" ideas? ;)

---

### Post by Simian Man on 2010-01-31
> **FrancoNero said:**
> looks nice, but will turn gnome into a windows/kde clone :) where are "new" ideas? ;)

Umm, have you ever used Winodws or KDE?  If *anything* a Mac clone, but this AWN can do things even the OSX dock can't.

---

### Post by mhr3 on 2010-01-31
> **Roasted said:**
> So the other night I was in the AWN IRC and somebody there was very helpful in helping me troubleshoot, however we never got anywhere constructive because out of no where it started to auto launch again on my laptop. 

We edited the awn.desktop autostart file and edited the entry for AWN to calculator, and sure enough calculator auto started. Okay, fine. So I changed it back to AWN, and blam. AWN auto started.

Well my desktop had issues auto starting too, so I took Docky off of auto start to give it a shot and AWN was now auto starting. Were there any updates that fixed this?

No, we didn't change anything in core for the past ~3 weeks. And the gconf bug affected only Lucid...

---

### Post by Roasted on 2010-01-31
> **mhr3 said:**
> No, we didn't change anything in core for the past ~3 weeks. And the gconf bug affected only Lucid...

My desktop and laptop are both fine now... and I have no idea why...

Is anybody else who previously had the autostart bug experiencing the awn dock starting automatically now?

---

### Post by Roasted on 2010-01-31
> **FrancoNero said:**
> looks nice, but will turn gnome into a windows/kde clone :) where are "new" ideas? ;)

Um. What? KDE? Windows? Holy backwards.

---

### Post by OlyPerson on 2010-01-31
> **FrancoNero said:**
> looks nice, but will turn gnome into a windows/kde clone :) where are "new" ideas? ;)

Look at gnome-shell.

---

### Post by Roasted on 2010-01-31
Okay, so on my spare desktop I fired up AWN. Rebooted. Didn't auto start. Blam. That was my time to figure out what it was I did that fixed it.

I went into startup applications, and completely removed "Avant Window Manager" from the auto start menu. Then I opened AWN and went into the preferences and checked "Start AWN Automatically" again. 

Logged out.
Logged in.
AWN loaded.

Rebooted.
Powered up.
Logged in.
AWN loaded.

Not sure what it is about removing it from auto start in the system preferences, then in AWN preferences re-enabling it to auto start, but it seemed to work for me. *Shrug*

---

### Post by darco on 2010-02-01
I am really glad to see the gconf update...awn back up and working

---

### Post by Roasted on 2010-02-01
> **darco said:**
> I am really glad to see the gconf update...awn back up and working

So.. wait.

There was a gconf bug that directly effected AWN. So despite the AWN developers saying they didn't update anything in the last month, there was still a gconf update pushed down that subsequently patched the AWN problem (autostart) we were seeing earlier?

---

### Post by TerminX on 2010-02-02
A gconf change broke AWN, then another gconf update fixed whatever the regression was.

---

### Post by Roasted on 2010-02-02
Does anybody have any differences with AWN in terms of how fast it reacts?

It seems like there's times where it'll take a full 2-3 seconds to wake up from its hiding state and present itself to me, and other times it's a nanosecond to respond and blam - it's there.

I fired up AWN and Docky in the same side of my screen and tested it, and it's pretty obvious Docky is always an instant nanosecond wakeup time, whereas AWN varies. I can't seem to find a pattern with it either. Anybody else notice this?

---

### Post by nikef on 2010-02-02
Awn website is not working 

I registered today and i am still waiting for an email confirmation 

Does any1 know if the site is being moderated ?

---

### Post by moted on 2010-02-02
Has anyone successfully used AWN 4 with TwinView and 2 monitors?  Are you able to change the default screen and change which monitor the bar is on?

As far as I know there is still a looming bug around that.

---

### Post by Roasted on 2010-02-02
> **moted said:**
> Has anyone successfully used AWN 4 with TwinView and 2 monitors?  Are you able to change the default screen and change which monitor the bar is on?

As far as I know there is still a looming bug around that.

Try:

Open dock preferences.
Applets.
Drag "Preferences Applet" to "Active Applets"
Then click and drag on the blue folder dock icon to the edge of the screen you want.

---

### Post by mhr3 on 2010-02-03
> **Roasted said:**
> Does anybody have any differences with AWN in terms of how fast it reacts?

It seems like there's times where it'll take a full 2-3 seconds to wake up from its hiding state and present itself to me, and other times it's a nanosecond to respond and blam - it's there.

I fired up AWN and Docky in the same side of my screen and tested it, and it's pretty obvious Docky is always an instant nanosecond wakeup time, whereas AWN varies. I can't seem to find a pattern with it either. Anybody else notice this?

By default it actually takes anything up to 1 second. To change this, open `gconf-editor`, navigate to /apps/avanti-window-navigator/panels and set mouse_poll_delay to ie 200.

> **nikef said:**
> Awn website is not working 

I registered today and i am still waiting for an email confirmation 

Does any1 know if the site is being moderated ?

Probably some problems with the forums. Feel free to ask here, obviously the devs read it.

> **moted said:**
> Has anyone successfully used AWN 4 with TwinView and 2 monitors?  Are you able to change the default screen and change which monitor the bar is on?

As far as I know there is still a looming bug around that.

We aren't aware of any bugs with multiple monitors, please do what Roasted suggested.

---

### Post by Roasted on 2010-02-03
> **mhr3 said:**
> By default it actually takes anything up to 1 second. To change this, open `gconf-editor`, navigate to /apps/avanti-window-navigator/panels and set mouse_poll_delay to ie 200.


You, my friend, are the man. That did exactly what I wanted it to. 

Although I can understand how a tad slower response time is nicer (I often accidently hit the bottom and the panel appeared, sometimes can be annoying) but I prefer it to pop up almost instantly as opposed to having a delay, so that setting @ 200 did the trick perfectly.

---

### Post by mhr3 on 2010-02-03
It has also the added bonus of saving your laptop battery little bit.

---

### Post by northwestuntu on 2010-02-03
i still like dockys mac style bar.  awns effect functions are not very good.

---

### Post by PuddingKnife on 2010-02-03
> **northwestuntu said:**
> i still like dockys mac style bar.  awns effect functions are not very good.


Are they not very good because theyre not emulating what Apple is doing?

I for one am a big fan of "squish"

---

### Post by northwestuntu on 2010-02-03
> **PuddingKnife said:**
> Are they not very good because theyre not emulating what Apple is doing?

I for one am a big fan of "squish"


the mac effects are better then awns imo

---

### Post by sudoer541 on 2010-02-03
how can I get awn on ubuntu 9.04?
any .debs available?

---

### Post by Funnnny on 2010-02-03
> the mac effects are better then awns imo
Yeah, so just use a MAC

---

### Post by Enigmapond on 2010-02-03
Here..read this guys thread and add the repos he has listed...works super!!

[http://ubuntuforums.org/showthread.php?t=1393141](http://ubuntuforums.org/showthread.php?t=1393141)

---

### Post by Roasted on 2010-02-04
> **funnnny said:**
> yeah, so just use a mac

lol

---

### Post by Jordanwb on 2010-02-05
```
root@lubuntu-desktop:/home/jordanwb# apt-get install avant-window-navigator
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libevent-1.4-2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  alacarte app-install-data avant-window-navigator-data awn-applets-c-core awn-applets-python-core awn-settings bzr bzrtools capplets-data cpp-4.4 evolution-data-server
  evolution-data-server-common fortune-mod fortunes-min gcc-4.4-base ghostscript gnome-about gnome-applets gnome-applets-data gnome-control-center gnome-doc-utils gnome-media
  gnome-media-common gnome-menus gnome-panel gnome-panel-data gnome-session gnome-session-bin gnome-settings-daemon gnome-system-monitor gnome-user-guide
  gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gvfs gvfs-backends indicator-applet indicator-application indicator-messages libappindicator0
  libarchive1 libasound2-plugins libatspi1.0-0 libawn1 libcairomm-1.0-1 libcamel1.2-14 libcupsimage2 libdbusmenu-glib1 libdbusmenu-gtk1 libdesktop-agnostic-cfg-gconf
  libdesktop-agnostic-fdo-glib libdesktop-agnostic-vfs-gio libdesktop-agnostic0 libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6
  libedataserver1.2-11 libedataserverui1.2-8 libegroupwise1.2-13 libexempi3 libgcc1 libgdata-google1.2-1 libgdata1.2-1 libglib2.0-0 libglibmm-2.4-1c2a libgnome-media0
  libgnome-menu2 libgnome-window-settings1 libgnomekbd-common libgnomekbd4 libgomp1 libgphoto2-2 libgphoto2-port0 libgs8 libgstreamer-plugins-base0.10-0 libgstreamer0.10-0
  libgtkmm-2.4-1c2a libgucharmap7 libgweather-common libgweather1 libicu42 libindicate4 libindicator0 libjson-glib-1.0-0 libmagickcore2 libmagickwand2 libmetacity-private0
  libnautilus-extension1 libpangomm-1.4-1 libpaper-utils libpaper1 libpulse-browse0 libpulse-mainloop-glib0 libpulse0 librecode0 libspeexdsp1 libstdc++6 libtidy-0.99-0
  libwebkit-1.0-2 libwebkit-1.0-common libwnck-common libwnck22 libxklavier16 libxml2-utils libxres1 metacity metacity-common mousetweaks nautilus nautilus-data
  obex-data-server patch psfontmgr pulseaudio pulseaudio-esound-compat pulseaudio-module-x11 pulseaudio-utils python-awn python-awn-extras python-chardet python-crypto
  python-dateutil python-desktop-agnostic python-feedparser python-gmenu python-gnomeapplet python-gnomedesktop python-gst0.10 python-gweather python-paramiko python-rsvg
  python-utidylib python-vobject python-xkit rtkit screen-resolution-extra ubuntu-system-service xsltproc yelp zenity
Suggested packages:
  awn-applets-c-extras gconf-editor awn-applets-python-extras bzr-gtk bzr-svn python-pycurl python-kerberos bzr-doc librsvg2-bin graphviz gcc-4.4-locales evolution
  evolution-data-server-dbg ghostscript-cups ghostscript-x hpijs acpid tomboy gnome-netstatus-applet deskbar-applet cpufrequtils libcanberra-gtk-module gnome2-user-guide
  epiphany-browser menu-xdg desktop-base gnome-screensaver libdesktop-agnostic-vfs libdesktop-agnostic-cfg libdesktop-agnostic-fdo gphoto2 gtkam libvisual-0.4-plugins
  gstreamer-codec-install gnome-codec-install gstreamer0.10-tools gstreamer0.10-plugins libmagickcore2-extra gnome-themes eog gnome-app-install totem mp3-decoder brasero
  nautilus-cd-burner diffutils-doc pavumeter paman paprefs avahi-daemon python-gnomekeyring python-gnome2-desktop python-crypto-dbg python-gst0.10-dev python-gst0.10-dbg
  ttf-dejavu
Recommended packages:
  fortune
The following NEW packages will be installed:
  alacarte app-install-data avant-window-navigator avant-window-navigator-data awn-applets-c-core awn-applets-python-core awn-settings bzr bzrtools capplets-data
  evolution-data-server evolution-data-server-common fortune-mod fortunes-min ghostscript gnome-about gnome-applets gnome-applets-data gnome-control-center gnome-doc-utils
  gnome-media gnome-media-common gnome-menus gnome-panel gnome-panel-data gnome-session gnome-session-bin gnome-settings-daemon gnome-system-monitor gnome-user-guide
  gstreamer0.10-pulseaudio gvfs-backends indicator-applet indicator-application indicator-messages libappindicator0 libarchive1 libasound2-plugins libatspi1.0-0 libawn1
  libcairomm-1.0-1 libcamel1.2-14 libcupsimage2 libdbusmenu-glib1 libdbusmenu-gtk1 libdesktop-agnostic-cfg-gconf libdesktop-agnostic-fdo-glib libdesktop-agnostic-vfs-gio
  libdesktop-agnostic0 libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-11 libedataserverui1.2-8 libegroupwise1.2-13
  libexempi3 libgdata-google1.2-1 libgdata1.2-1 libglibmm-2.4-1c2a libgnome-media0 libgnome-menu2 libgnome-window-settings1 libgnomekbd-common libgnomekbd4 libgomp1
  libgphoto2-2 libgphoto2-port0 libgs8 libgtkmm-2.4-1c2a libgucharmap7 libgweather-common libgweather1 libicu42 libindicate4 libindicator0 libjson-glib-1.0-0 libmagickcore2
  libmagickwand2 libmetacity-private0 libnautilus-extension1 libpangomm-1.4-1 libpaper-utils libpaper1 libpulse-browse0 libpulse-mainloop-glib0 librecode0 libspeexdsp1
  libtidy-0.99-0 libwebkit-1.0-2 libwebkit-1.0-common libwnck-common libwnck22 libxklavier16 libxml2-utils libxres1 metacity metacity-common mousetweaks nautilus nautilus-data
  obex-data-server patch psfontmgr pulseaudio pulseaudio-esound-compat pulseaudio-module-x11 pulseaudio-utils python-awn python-awn-extras python-chardet python-crypto
  python-dateutil python-desktop-agnostic python-feedparser python-gmenu python-gnomeapplet python-gnomedesktop python-gst0.10 python-gweather python-paramiko python-rsvg
  python-utidylib python-vobject python-xkit rtkit screen-resolution-extra ubuntu-system-service xsltproc yelp zenity
The following packages will be upgraded:
  cpp-4.4 gcc-4.4-base gstreamer0.10-plugins-base gstreamer0.10-plugins-good gvfs libgcc1 libglib2.0-0 libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libpulse0 libstdc++6
11 upgraded, 132 newly installed, 0 to remove and 140 not upgraded.
Need to get 61.6MB of archives.
After this operation, 324MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
root@lubuntu-desktop:/home/jordanwb#
```

[img]http://img196.imageshack.us/img196/3799/1243154594896.jpg[/img]

"Do you want to continue?" Uh no.

---

### Post by ptviperz on 2010-02-05
Don't you want avant-window-navigator-trunk?

---

### Post by Jordanwb on 2010-02-05
Yes but if I want gnome-panel and all that other stuff I would've installed Ubuntu and not Lubuntu. Is there an option for apt-get that displays a dependency tree?

---

### Post by seeker5528 on 2010-02-05
> **Jordanwb said:**
> Yes but if I want gnome-panel and all that other stuff I would've installed Ubuntu and not Lubuntu. Is there an option for apt-get that displays a dependency tree?

First install apt-rdepends then do:

```
apt-rdepends -s Depends,Recommends  avant-window-navigator | less
```

```
apt-rdepends -rs Depends,Recommends  avant-window-navigator | less
```

If you wanted to get fancy and have a graph you could install graphviz then do:

```
apt-rdepends -s Depends,Recommends --dotty avant-window-navigator > awn.dot && dotty awn.dot
```

EDIT:
Oh, yeah.....

If you want to install without pulling in the recommended packages......

```
apt-get --no-install-recommends avant-window-navigator
```

EDIT2:
Somebody really needs to give dotty and her friends some luvin'

Later, Seeker

---

### Post by Jordanwb on 2010-02-05
> **seeker5528 said:**
> ```
apt-get --no-install-recommends avant-window-navigator
```

This alone reduced dependencies from around 40 down to 12.

---

### Post by Robertjm on 2010-02-06
I just installed AWN after reading this thread. Have to say I'm really liking it. 

One problem I had is with installing new themes. Downloaded a couple from their forums, however, when I tried to install them the AWN settings applet wouldn't see the them file. W

After playing around with it I found my problem was that I had extracted the files included in the theme .tgz when I should have simply told selected the compressed file to install the theme. Once I made the change it installed just fine!!

---

### Post by phenest on 2010-02-06
A thought occurred to me regarding Gnome Shell. If the Gnome devs drop metacity, and Gnome users want to use AWN instead of GS, what will be used for a compositing manager? In fact, metacity is also a window manager, so what are the alternatives?

I know GS isn't due out until late this year, but I was just thinking ahead. Better to be prepared.

---

### Post by seeker5528 on 2010-02-06
> **phenest said:**
> If the Gnome devs drop metacity, and Gnome users want to use AWN instead of GS, what will be used for a compositing manager?

The 'AWN instead of GS' doesn't really compute for me?

But the other part of the question, [Mutter](http://packages.ubuntu.com/lucid/mutter) does compositing, and is basically Metacity with clutter support. Metacity may die in name at some point, but if so only because the fork took over for the original.

I don't know how GS uses Mutter, but just did:

```
mutter --replace
```

in a terminal window and the desktop looks exactly the same as with Metacity, which is the expected result, being a fork of Metacity.

[http://blogs.gnome.org/metacity/category/compositing/mutter/](http://blogs.gnome.org/metacity/category/compositing/mutter/)

Later, Seeker

---

### Post by phenest on 2010-02-06
[QUOTE=seeker5528;8785429]The 'AWN instead of GS' doesn't really compute for me?/QUOTE]

Me neither, but I could just foresee this possible issue.

---

### Post by Menti on 2010-02-06
> **moonbeam said:**
> That's a very good idea.  And probably quite easy to do.  I will implement it soon.

Sorry, I missed this. Thank you very much.

---

### Post by seeker5528 on 2010-02-06
One difference I do see with Mutter right off the bat, aside from the window animations when you open or close a window, real transparency in Gnome-terminal as opposed to the fake transparency with Gnome-terminal in Metacity that always shows a cutout of the wallpaper no mater what windows might be open behind Gnome-terminal.

[Screenshot](http://home.comcast.net/~seeker5528/Screenshot-Mutter.png)

Later, Seeker

---

### Post by moted on 2010-02-07
> **Roasted said:**
> Try:

Open dock preferences.
Applets.
Drag "Preferences Applet" to "Active Applets"
Then click and drag on the blue folder dock icon to the edge of the screen you want.

Thanks!  That worked out for me!

---

### Post by uBeer on 2010-02-07
> **seeker5528 said:**
> One difference I do see with Mutter right off the bat, aside from the window animations when you open or close a window, real transparency in Gnome-terminal as opposed to the fake transparency with Gnome-terminal in Metacity that always shows a cutout of the wallpaper no mater what windows might be open behind Gnome-terminal.

[Screenshot](http://home.comcast.net/~seeker5528/Screenshot-Mutter.png)

Later, Seeker

If your terminal had fake transparency before, then you were not using the compositing feature of metacity. If you turn on /apps/metacity/general/compositing_manager in gconf you actually turn on mutter, that's what seeker5528 was saying (at least I think so).

---

### Post by seeker5528 on 2010-02-08
> **uBeer said:**
> If your terminal had fake transparency before, then you were not using the compositing feature of Metacity. If you turn on /apps/metacity/general/compositing_manager in gconf you actually turn on mutter, that's what seeker5528 was saying (at least I think so).

I didn't see that Metacity had compositing until I started exploring the gconf settings to switch my window manager to Mutter. Which, on a side note, appears not to work in Debian unstable, the gconf keys are still there for it, but when you look at them it is indicated that method of setting the window manager is deprecated. So I ended up creating a .xsession file with the lines:

```
export WINDOW_MANAGER=/usr/bin/mutter
gnome-session


``` 

Back to Metacity, it looks like you get real transparency if you edit the gconf setting to enable compositing in Metacity, I'm pretty sure it doesn't use Mutter for it, but I expect they probably share the same compositing code.

Later, Seeker

---

### Post by uBeer on 2010-02-08
Thanks for the insight! I'm gonna try the Mutter thing. It could be that it's not the same as Mutter uses OpenGL, right? While Metacity compositing uses Xrender I believe.

I'll try the mutter thing, see how that works now that OpenGL works kinda ok on my ati radeon mobile 3650 :D

Edit: Hmm, apparently Mutter (the version from Gnome Shell ppa) is really slow and cpu intensive, so that is a no go for me yet.

---

### Post by phenest on 2010-02-08
> **uBeer said:**
> Thanks for the insight! I'm gonna try the Mutter thing. It could be that it's not the same as Mutter uses OpenGL, right? While Metacity compositing uses Xrender I believe.

I'll try the mutter thing, see how that works now that OpenGL works kinda ok on my ati radeon mobile 3650 :D

Edit: Hmm, apparently Mutter (the version from Gnome Shell ppa) is really slow and cpu intensive, so that is a no go for me yet.

Mutter uses about 45MB RAM, and sometimes the CPU usage goes up to 1%.

---

### Post by seeker5528 on 2010-02-08
On my system at work I don't have the PPA added.

I don't often look at the memory and CPU usage. 

CPU is Athlon 2200+, memory is 512 MB, video is Radeon 9600 (R300 chipset).

Generally speaking on my system Mutter seems as fast as Metacity, a little faster than GS, don't do a lot of stuff on the web that uses flash video players or do games that use flash at work.

My home specs are 64 bit AMD don't remember the MHz off the top of my head, 1.5 GB RAM, Radeon with an R500 chipset, 64 bit Debian installation.

Same as above, generally speaking Mutter seems as fast a Metacity, a little faster than GS. I think the version of GS in Debian is the same or close to the same as the one from the Lucid repositories, I do more stuff were flash might be an issue and it seems like there are more performance issues than with GS than without. Haven't been to the gaming/video sites enough to say how the experience is affected with Mutter. 

Haven't tried Mutter on my home install Ubuntu yet where I do have the PPA added, but it is very close to the specs of my other home system, most significant differences being Radeon card with an RV450 chipset,  but I expect the same results. Flash seems to be a little more of an issue on Ubuntu than on Debian, but I did watch 3 episodes of Full Metal Alchemist: Brotherhood on Hulu without any issues so it may be a good time to switch to Muter and try some of these sites. It's Ubuntu 64 bit.

Later, Seeker

---

### Post by donniezazen on 2010-02-16
Hi All,

I have problem with notification area applet of AWN. Its not showing volume icon and sometimes multiple icons.

Thanks,
SK.

---

### Post by seeker5528 on 2010-02-17
> **soham_1207 said:**
> I have problem with notification area applet of AWN. Its not showing volume icon and sometimes multiple icons.


If you have something else running that provides a tray/notification area they may be intercepted by that instead of the AWN applet.

Later, Seeker

---

### Post by donniezazen on 2010-02-17
> **seeker5528 said:**
> If you have something else running that provides a tray/notification area they may be intercepted by that instead of the AWN applet.

Later, Seeker

No i dont have any other notification area or tray enabled. It has gone permanently.

---

### Post by seeker5528 on 2010-02-17
> **soham_1207 said:**
> No i dont have any other notification area or tray enabled. It has gone permanently.

I don't know what else to look for.

Later, Seeker

---

### Post by mhr3 on 2010-02-17
> **soham_1207 said:**
> Hi All,

I have problem with notification area applet of AWN. Its not showing volume icon and sometimes multiple icons.

Thanks,
SK.

Are you using Lucid? What happens when you use gnome-panel's notification area applet?

---

### Post by donniezazen on 2010-02-17
> **mhr3 said:**
> Are you using Lucid? What happens when you use gnome-panel's notification area applet?

The gnome panel notification area applet is working fine.

Thanks guys.

---

### Post by dccrens on 2010-02-23
Anyone know how to get AWN to run on two monitors? I want a bar on each monitor. 

I used to be able to start two instances using a shell script below but that doesn't seem to be working now. 

```
#!/bin/bash


killall avant-window-navigator
sleep 4

DISPLAY=:0.0 avant-window-navigator &
sleep 4

DISPLAY=:0.1 avant-window-navigator &
```

---

### Post by dccrens on 2010-02-23
Playing around more with this and it looks like avant no checks to see if there is another instance running and will not start if there is. That is a bummer. Any way to change this? 

dccrens@cavermax-ubuntu:~$ DISPLAY=:0.0 avant-window-navigator &
[1] 15569
dccrens@cavermax-ubuntu:~$ 
** (avant-window-navigator:15569): WARNING **: Another instance of Awn is running


[1]+  Done                    DISPLAY=:0.0 avant-window-navigator

---

### Post by Docaltmed on 2010-02-23
Is AWN still supported? I've posted a couple of questions on the AWN forum, and marked up a bug, but there don't seem to be any responses.

It would be a shame if it tanked, it's a nice little app. In the meantime, I've switched to Docky which has fewer docklets, but at least works on my system.

---

### Post by tekstr1der on 2010-02-23
> **Docaltmed said:**
> Is AWN still supported?

It's regularly updated in the trunk ppa. Speaking of which, I've seen a bug in the last couple builds since the "window dodge" hide mode was added.

Filed this bug today:

[https://bugs.launchpad.net/awn/+bug/526476](https://bugs.launchpad.net/awn/+bug/526476)

Excerpt:
> STR:

1) Freshly booted desktop with AWN dock displayed, set in intellihide or window dodge mode
2) Open a full-screen maximized application window.
3) Observe AWN dock hide properly
4) Close full-screen maximized window
5) AWN dock is not restored, stays hidden

Expected Result: Upon closing window, the AWN dock should be displayed.

Anyone else seeing this behavior? I've seen is on a couple different installs. Both Intel graphics though. Please chime in on the bug or at least add yourself as affected if you are, indeed, affected by this.

---

### Post by donniezazen on 2010-02-24
> **Docaltmed said:**
> Is AWN still supported? I've posted a couple of questions on the AWN forum, and marked up a bug, but there don't seem to be any responses.

It would be a shame if it tanked, it's a nice little app. In the meantime, I've switched to Docky which has fewer docklets, but at least works on my system.

This thread has gone too long. I think its better idea to start a new thread if you have some specific problem.

SK.

---

### Post by softwarejonas on 2010-04-01
Awn needs compositing, which doesn't work on my laptop (too well). I like the panels just like they are right now.

---

### Post by donniezazen on 2010-04-01
> **softwarejonas said:**
> Awn needs compositing, which doesn't work on my laptop (too well). I like the panels just like they are right now.

+1. I am using Lucid which uses nouveau that doesn't support compositing and without compositing AWN looks ugly.

---

### Post by arnab_das on 2010-04-01
i think ubuntu is heading towards a stage where it might want to do that. although i would love to have awn installed as a default package, its unlikely to happen simply because of the incompatibility of a large no of hardware.

---

### Post by Rob2687 on 2010-04-01
It works fine without compositing.

---

