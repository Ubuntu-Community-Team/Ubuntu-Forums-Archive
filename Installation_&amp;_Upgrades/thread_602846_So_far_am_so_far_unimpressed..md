---
title: "So far am so far unimpressed."
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by Kevsta100 on 2007-11-04
Linux.. yeah so far is been one crappy situation to another.
Problems booting, then problems installing the problems for the fact it can't even handle a partition unless u tell it what to do and mount it etc.

One problem after another...

I'm not geek enough it seems to be able to work this marvellous system.

Seriously tho, am I missing something? 

I can't even play a frigging AVI without first downloading a mass files that  gives me crappy instructions to do... well I dunno... I'm pretty sure its a media player am trying to install.
Least thats what I downloaded via XP even though I think I installed my wifi dongle an ****.

Now all I can do is to boot into what seems Kubuntu, cep't the damn gui seems have went on holiday. Black screen white letter and an unforgiving cursor who dont seem to like me.

I suppose am asking... where is the <end Joke> command,

 I plan to give this nightmare the benefit of the doubt but gonna need to be able least log onto the damn thing.

Send me in the right direction or something please!

In the mean time I'll be adding to my small heap of hair I'm collection on my desk. *stress*

<edit> ok startx  thats a handy command... :p

---

### Post by bethaviv on 2007-11-04
> I can't even play a frigging AVI without first downloading a mass files that gives me crappy instructions to do... well I dunno... I'm pretty sure its a media player am trying to install.

The media player you're looking for is called VLC and you can find that in Add/Remove... Just search for "VLC" and it should pop up.

Another option (also found in Add/Remove...) is to install all the gstreamer apps (Where it says "Show:" you'll have to tell it you want "All available applications").

There really shouldn't be any configuring or messing around with the terminal if you do one of the two above. For me, I installed all the gstreamer apps and installed SMplayer and nothing gives me any issues.

> Least thats what I downloaded via XP even though I think I installed my wifi dongle an ****.

Not sure what you're trying to say here...

> Now all I can do is to boot into what seems Kubuntu, cep't the damn gui seems have went on holiday. Black screen white letter and an unforgiving cursor who dont seem to like me.

I'm not sure what happened, but maybe it had to do with your issues installing this media player, might've broke something if it was done incorrectly. I'm not to knowledgable to help with GUI issues, but I'm sure someone else here can help you with that.

---

### Post by soulmatic09 on 2007-11-04
i'm having the same problems.

this process has wrecked my XP system too, so right now, i've got nothing.

i backed everything up using partimage, a linux based image tool, but that doesn't even work.


at least the livecd works pretty well. if i had known the real thing would have been worse, i never would've installed it.

---

### Post by Kevsta100 on 2007-11-04
Its taken me so long that when I finally did get round to getting the Kubuntu I think I've did a lil too much too quickly.

I remember now installing a NVIDIA driver that came pre packed inside the Kubuntu distro.
I also had to restart X server (the gui from what I have figured out)
I did this to enable dual screen to show an extended desktop.
Upon restarting I can only login via a full screen command prompt.

Whats really stressing me out is the fact I have to keep going back to XP to try find solutions.
What stresses me out more is the fact I don't really know what I'm looking for, and find myself writing down errors on random  bits of paper. (printer is busted)
So far its been an extremely long drawn out process to get Kunbuntu on, then breaks the same day.

I tried StartX command to get this problem.

Fatal Server error requested entity is in use
xIO fatalIO error104

I believe thats saying something about X server being running already but not working.
Gonna try googling a lil, tho unsure as to what am looking for or what applies to me.:mad:

Oh and as far as "installing" the xine media player... the clostest I got to it before putting it on hold was
opening the archive and reading a few read me's.


Oh and @ soulmatic09... I also wreaked my XP, but once Grub was installed it took over as the bootloader and I found my xp again! if the same doesnt work for you, I'm sorry to hear.

---

### Post by Kevsta100 on 2007-11-05
... until Linux winds me up some more, drives me to drink and stresses me out... lol

Aiight I know this much so far, or atleast think I do.

I installed the Kubuntu supplied open source Nvidia 7 series driver, however I am running dual monitors which the open source driver apparently don't get along with.

Now I have downloaded ENVY to correct this problem, but being a linux Newb and unable to actually boot into the KDE GUI, I can do nothing but bash in random commands, jotted down from countless times of hopping back to XP to use the Internet Then back to linux to try a few, to fail and then to repeat.

I am pretty sure there are plenty of guys who can look at my problem and instantly know how to over come the problem and a bad/unsupported driver.

Heck if linux had a safe mode, I'd have fixed this issue ages ago.

Ofcourse what bothers me more is the fact once I finally get back into the gui (if i do for that matter!!) I am then greeted with all the issues before Linux died.

Does it get any easier????
So far I've fixed like 3 major errors or problems and can't really even say what they were or how the fix or solution worked!

Come on! gimme a hand here someone! :p
PLEASE!!

---

### Post by bulldog on 2007-11-05
Well,think back at the days of windows95,was that easy to install and understand? don't think so:)

There are some very good How To's on the forums how to install ubuntu and I'm sure there are some for your problem too.
Just do a search for it,and you'll be rewarded big time.
Remember,ubuntu is NOT windows or a cheap replacement,it's a very nice OS,but you have to digg a little to get used to it.
I use ubuntu from Breezy till Gutsy and I had my share of disappointments,trying Fedora,SuSe and what not,but at the end you have learned a whole lot.

So don't think you understand linux over night,put some efford in it and read,read and read again:)

You can boot into recovery mode and make it to the non graphical login?
If you can login and type envy,this should activate envy in a 'DOS' box.
Uninstall the graphics driver and reinstall if you wish.
I use gnome for DE and don't know to much about the KDE but this should work for a start.
Reboot and see if you can login in the graphical environment.
If not,go into recovery mode once more,run ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` set the right driver if asked to [nvidia] and
select the right resolution.
Reboot and see what gives.

For the two screens look here,```
http://ubuntuforums.org/showthread.php?t=603468
```

---

### Post by Kevsta100 on 2007-11-05
Info looks promising Bulldog TY, I promised myself a night off the linux kernel tonight so will report back tomoz is things worked niice or if things laughed at me or presented me with a new new problem lol.

I am slowly picking things up and realised what Linux has on windows...
from what I can see ya can mod any file ya open as easy as single click, and type the new coding...
Well easy if u know coding lol.

My Goals are for Linux atm

Get back my gui.
Enable my dual monitors in extended desktop mode. (i needs a dual head driver, i know..)
configure my wifi dongle... I think I've installed the driver correct lol.

Oh and as for win95... I only ever upgraded from 95 to 98 never installed 95.
Win98 was easy tho... did it about 10 times. Xp probs... x10 of that. XD

Oh an have a chuckle... My XP is playin up tonite! on my linux night off... Nurech worm fits my symptoms too! SH*T!

<edit> I didnt like SUSE... it may have been the gnome interface i'm not sure... I like Kubuntu...might be the KDE interface... again IDK... where does one part end and another begin... KDE isnt perfect but I'm getting the feel and enjoy using it... when not trying to make it work for me that is. lol

<edit2> ok I should of talked less and answered more... lmao.... Recovery mode dies/appears to crash after loading the following line
IO scheduler cfg registered (default)

as u can see, its NOT an error... it just shows ya where the thing gives up, which i figure might be of use to u.

---

### Post by kkmc92 on 2007-11-05
Believe me I feel your ** pain ** with this os. I can't even install the thing. If anyone can help me check out my post and give me your thoughts. [http://ubuntuforums.org/showthread.php?t=603674](http://ubuntuforums.org/showthread.php?t=603674)

---

### Post by NickDee on 2007-11-05
I'm enough of a geek to have actually gotten ubuntu running for a day . . . and I really want it to work.  I hate MS as mcuh as anyone.  But I have to agree, it's been a huge pain in the butt to get it working.

Nick

---

### Post by Seti on 2007-11-05
Ah the joy and horror of realizing for the first time that YOU are in control of your computer. I would say keep plugging away at it, if you have a willingness to learn you will soon reap the many benefits. As one much wiser than me would say:

"Patience young padiwan"

OK seriously, that was way too geeky.

---

### Post by kkmc92 on 2007-11-05
> **Seti said:**
> Ah the joy and horror of realizing for the first time that YOU are in control of your computer. I would say keep plugging away at it, if you have a willingness to learn you will soon reap the many benefits. As one much wiser than me would say:

"Patience young padiwan"

OK seriously, that was way too geeky.

 question. what should I keep plugging away at if I run into a brick wall O Master of the force.

---

