---
title: "POLL: Do you want to have CTRL-ALT-BACKSPACE disabled in Jaunty?"
date: 2009-01-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by eragon100 on 2009-01-16
Hello!

In Jaunty alpha 3, the developers have disabled the shortcut ctrl-alt-backspace to restart the X-server, because some people were complaining that they accidentely restarted X. I don´t like this, and I think most people won´t, so I decided to make a small poll about it. Please post your thoughts about this issue here. Thanx!

---

### Post by SushiR on 2009-01-16
Disabling it will lead to more sorrow than leaving it enabled...

---

### Post by MacUntu on 2009-01-16
I'm sure you can re-enable it whenever you want, so it's no big deal. A common desktop user simply doesn't need to restart X (in fact doing it accidently can cause data loss, which pi**es me more off than having to re-enable it by hand) so I advocate this decision. [OT: Is this what you say when you support sth.?]

---

### Post by agim on 2009-01-16
As long as you can enable, I guess I understand. But I am against this, when you need to restart, you may not be able to enable the option to use it.
I hope it doesn't get changed, how the hell can you accidentally hit all three at once?

---

### Post by Gina on 2009-01-16
Personally, I don't - I have never accidentally typed that key combination.  I'd have thought it would have to be a pretty definite action, requiring two hands and with two keys held down with one hand.  I know a few people have complained that they type it accidentally but I find it hard to believe (unless they're not concentrating on what they're doing).  Better IMO would be to have an option to disable it if needs be but have it enabled by default.  I guess that *[I][I]if everything is working properly*[/I][/I] it shouldn't be necessary to be able to restart X and an option to turn it on would be acceptable.

---

### Post by jrusso2 on 2009-01-16
Leave it do we have to dumb down everything or can't anyone learn how to use the controls?

---

### Post by MacUntu on 2009-01-16
Ctrl+Alt+Enter is sometimes used to switch between fullscreen and window mode. On smaller notebooks it's easy to miss the Enter button and hit Bksp instead.

---

### Post by Dan_Dranath999 on 2009-01-16
Just make it easy to disable, but don't disable it by default...

---

### Post by Peter76 on 2009-01-16
That's my emergency exit for a hanging session.... Leave it where it is!

---

### Post by dgoosens on 2009-01-16
how can one hit three keys "accidentally" ?

however, I guess that if one can reactivate it... it's fine...

---

### Post by cl333r on 2009-01-16
I'm sure Canonical is doing right. It's a strategy that's working good so far by targeting the normal people over geeks for the odds are like 20 to 1, not to mention the huge amount of folks who could come over from windows.
Regardless of whether we like it or not this trend will continue. Expect other options to rise others to fade as Ubuntu makes its way into the mainstream among normal users.

---

### Post by DougieFresh4U on 2009-01-16
As already said, 'How do you hit 3 keys by mistake?'
I have not used Windows for about 3 years now, but isn't the option of 'Control-Alt-Delete' there for the 'End Task' option?(that wasn't really a 'restart x' option, but helped with a locked up screen) Just kind of wondering if that was an issue with users 'hitting by accident'

---

### Post by MacUntu on 2009-01-16
See [https://wiki.ubuntu.com/XorgCtrlAltBackspace](https://wiki.ubuntu.com/XorgCtrlAltBackspace) section "Assumptions". 

As for us, who are posting here in the development forum, this won't hold true but it does for the vast majority of users. It's not "dumbing things down" but reducing the risks of negative experiences. Those who use this function definitely won't have a problem re-enabling it while fiddling around with xorg.conf might not be what a "normal" user wants to do.

Maybe the thing can be turned on during development and turned off for releases?

---

### Post by ssam on 2009-01-16
on the spec page [https://blueprints.launchpad.net/ubuntu/+spec/xorg-ctrl-alt-backspace](https://blueprints.launchpad.net/ubuntu/+spec/xorg-ctrl-alt-backspace) it mentions a 2 second timeout (ie, hold the keys down for 2 sec to restart x).

its been a while since X has locked up for me on a stable version of ubuntu. maybe because i use the opensource drivers. even when it does lock up only sometimes does CTRL-ALT-BACKSPACE help.

I think a lot of the accidental triggering of this is due to people expecting it to do something else ( [http://brainstorm.ubuntu.com/idea/84/](http://brainstorm.ubuntu.com/idea/84/) )

---

### Post by vikigal on 2009-01-16
> **Peter76 said:**
> That's my emergency exit for a hanging session.... Leave it where it is!

Whole heartedly agree. If it is disabled how would one get out of a hanging session???

PLEASE leave it alone. If you must make it so those with chuncky fingers can disable it but leave it on by default.

---

### Post by malspa on 2009-01-16
I would rather not see it disable by default.  I'm glad other distros don't have it disabled.  I don't get it, four years or so of using Linux and I've never hit that keystroke by accident.

---

### Post by sarath_it on 2009-01-16
I woulld like to keep there, but voted Yes. Like people said thats an easy combination to get hit accidentally. The developers should get a more confidente combination, or even a sequence!

---

### Post by DougieFresh4U on 2009-01-16
It was stated that there have been several complaints of hitting by accident. I have been reading the forum here for about 3 years now and I do not recall reading complaints of users hitting the combo by mistake. Where are they complaining to and can some one show me some examples of said complaints?

---

### Post by ronacc on 2009-01-16
to properly describe my outrage at this idea would require words that cannot be used in this forum. and BTW the the workaround posted elsewhere ( add option "DontZap"  "true" to xorg.conf ) dosent work for me and where is the promised gui to re-enable it ???  from the blueprint
> 2008-12-17 Alberto Milone: as Bryce already pointed out, users will be able to switch back to the old behaviour through a GUI (for both GNOME and KDE). Nothing to worry about.

---

### Post by xebian on 2009-01-16
Must be really VIP complaining to have this implemented after all these years.

And what are the chances of accidentally hitting CTL+ALT+DEL since DEL is as close to BACKSPACE?

---

### Post by xzero1 on 2009-01-16
So how will most new Jaunty users know about this new 'feature'?  Most probably will not, unless they stumble upon it in some forum or read the documentation with a fine tooth comb. In effect, you will have broken something that was working for most users. An option to disable would be fine -- just don't disable it by default.

---

### Post by obscur156 on 2009-01-16
Yeah right,hitting 3 keys by accident...
Now i will have to use the restart button on my PC GRRRRR.[-(
regards.

---

### Post by jbernardo on 2009-01-16
<flamebait>Disable it for ubuntu/gnome users, keep it enabled for kde/kubuntu users.</flamebait>

Seriously, isn't this dumbing down too much? It is bad enough that ctrl+alt+del won't reboot a machine any more, unless on a text console - but for ex-windows users that muscular memory was already compromised. But now disable ctrl-alt-backspace? Now what do I do to restart a hung desktop, press the reset button?
At least there still is ctrl-alt-sysreq...

---

### Post by zekopeko on 2009-01-16
> **obscur156 said:**
> Yeah right,hitting 3 keys by accident...
Now i will have to use the restart button on my PC GRRRRR.[-(
regards.

hahaha! you people are amazing. ctrl-alt-backspace shouldn't be enabled by default. and if you need to use a restart button to exit a hanging X then you really don't have a clue.
ctr-alt-f1(2,3...6) brings you to the command line from which you can kill X(and any other app).
enabling it by default camouflages the real problem. X hanging. That should be fixed not beaten down with a stick (or 3 button combo).

---

### Post by lukjad on 2009-01-16
Absolutely not. I have come to rely on it.

---

### Post by lswest on 2009-01-16
I find it's immensely useful, and have never once accidentally restarted the xserver, so I don't see any harm in having it enabled by default.  Or if it is disabled, allow it to be re-enabled easily in a preferences windows.

---

### Post by obscur156 on 2009-01-16
Yeah right zekopeko,sorry for my ignorance but i am not an IT.
I am just an ordinary guy that use ubuntu so it looks like i did not know that one and i am sure a lot of people are like me.
Your just more intelligent than me.
Regards

---

### Post by mrboojive on 2009-01-16
This is the worst idea ever. It's ridiculously unlikely that anyone is going to hit that combination by accident. Furthermore, any new user who does accidentally hit it is only going to do so once. Heaven forbid that they might learn something about Linux in the process.

---

### Post by lavinog on 2009-01-16
I can see it being possible to hit the wrong key, or even have keys stuck so that just pressing backspace will restart X.
I don't see why requiring ctrl-alt-backspace being held for 2 secs would be such a bad alternative.
Sure don't disable it, but make it less accident prone.

---

### Post by ronacc on 2009-01-16
> **zekopeko said:**
> hahaha! you people are amazing. ctrl-alt-backspace shouldn't be enabled by default. and if you need to use a restart button to exit a hanging X then you really don't have a clue.
ctr-alt-f1(2,3...6) brings you to the command line from which you can kill X(and any other app).
enabling it by default camouflages the real problem. X hanging. That should be fixed not beaten down with a stick (or 3 button combo).

ctrl>alt>bkspc is a convient shortcut , yes we can bring up a term and do it from there but that is not the point . by your logic we should disable all shortcuts and mabye gnome/kde/etc too and just do everything from the terminal .

---

### Post by lukjad on 2009-01-16
> **mrboojive said:**
> This is the worst idea ever. It's ridiculously unlikely that anyone is going to hit that combination by accident. Furthermore, any new user who does accidentally hit it is only going to do so once. Heaven forbid that they might learn something about Linux in the process.
Actually, I've done it many, many times. I just accept it. I have another combo that is near it, and sometimes I miss. It's my fault, but I find it to be useful.

---

### Post by zekopeko on 2009-01-16
> **obscur156 said:**
> Yeah right zekopeko,sorry for my ignorance but i am not an IT.
I am just an ordinary guy that use ubuntu so it looks like i did not know that one and i am sure a lot of people are like me.
Your just more intelligent than me.
Regards

this doesn't have to do with intelligence but with knowledge.

> **ronacc said:**
> ctrl>alt>bkspc is a convient shortcut , yes we can bring up a term and do it from there but that is not the point . by your logic we should disable all shortcuts and mabye gnome/kde/etc too and just do everything from the terminal .

most shortcuts don't kill your entire GUI...

---

### Post by ronacc on 2009-01-16
> **zekopeko said:**
> 
most shortcuts don't kill your entire GUI...

and ofcourse there is no reason that you would ever want to kill X .

---

### Post by zekopeko on 2009-01-16
> **ronacc said:**
> and ofcourse there is no reason that you would ever want to kill X .

it should be: "there *shouldn't* be any reason that you would ever want to kill X"

---

### Post by ronacc on 2009-01-16
I'll agree with that ,unfortunately we live in an imperfect world , apps go rouge , x freezes , sometimes you need to hand install a video driver etc and until such time as I don't need it I would prefer to have that shortcut available .

---

### Post by mhh91 on 2009-01-16
i don't think it should be disabled :)

---

### Post by blazemore on 2009-01-16
Make it Opensuse style: You have to do it twice in quick succesion. Then you can still do it, but not accidently!

---

### Post by Miguel on 2009-01-16
I think I've pressed Ctrl+Alt+Backspace accidentally about three times in my linux life. There have been many more times when I wanted it to work, but it didn't (mostly when using fglrx). The thing is, Ctrl+Alt is a pretty common modifier as a shortcut. I use it for the virtual desktops (with the arrows), I fire terminals with T, calculators with C, and so on. 

However, last time I killed my X11 accidentally I was trying to switch to the desktop on the left. I saw a big arrow pointing to the left and, while pressing Ctrl and Alt, my brain pushed me towards backspace instead of left arrow.

---

### Post by aaronb on 2009-01-16
CTRL-ALT-BACKSPACE should be enabled. Its handy when using wine with full screen games that sometimes lock up.

---

### Post by cardinals_fan on 2009-01-16
> **ronacc said:**
> and ofcourse there is no reason that you would ever want to kill X .
> **zekopeko said:**
> it should be: "there *shouldn't* be any reason that you would ever want to kill X"
Both wrong.  I need to kill X every time I log out.

---

### Post by ubername on 2009-01-16
As a relative noobie (certainly uneducated in *nix, finding it out as I go along) I am gutted that this has been removed. I didn't even know it existed until I saw this thread / upgraded to Jaunty. The hours I could have saved when messing with my xorg.conf by being able to just kill then restart X rather than reboot the computer are numerous. But if it is to go I would certainly back the implementation of another short-cut such as the 'hold for two seconds' (that's actually quite  a long time: I can't see anyone accidentally holding a three key combo for more than a fraction of a second) or a different, less easily mistaken combo.

---

### Post by Eclipse. on 2009-01-16
I can understand why its being done but I will re-enable it myself.

You can also use "sudo /etc/init.d/gdm restart" from the terminal although if your desktop has crashed or you got a memory leak and want to fix it quickly then your going to need to enable it.

---

### Post by Slug71 on 2009-01-16
I think this has been influenced from damn Brainstorm. Pretty sure i've seen it on there.

---

### Post by taavikko on 2009-01-16
> **Eclipse. said:**
> I can understand why its being done but I will re-enable it myself.

You can also use "sudo /etc/init.d/gdm restart" from the terminal although if your desktop has crashed or you got a memory leak and want to fix it quickly then your going to need to enable it.

switching to vty... (Ctrl+Alt+"F1-F6")

While were at it, why don't we disable CONFIG_MAGIC_SYSRQ also...

I personally can't remember when was the last time I used C+A+B.
As the development goes onward, few changes requires restart of X.
(Not counting updates of display drivers and of X itself)

Displays can be configured via xrandr (to some extent)
So as a closing note, I'll vote Yes.
Because users are able to enable it if they want to,
thanks for the good documentation.
Sorry for the jibberish..

---

### Post by Wolki on 2009-01-16
Well, I've pressed the key combo by accident while working quickly, and it sucked horribly. I've also used this combo intentionally more that a few times. My opinion: good riddance. It's just too destructive, and there are perfectly good ways to achieve the effect of restarting X. Sure, they may take a few seconds longer, but it's not like this is functionality you need very often (and if you do, there's something else wrong).

Also, Ctrl-Alt-Del is a good shortcut (easy to find with your hands, since all keys are on the edge of the main keyboard), and I look forward to being able to use it for something that will benefit me daily.

[edit] @taaviko, I'd say magic sysrq is more useful to me, since I can often use it to safely reboot a computer that seems to have completely hanged, or at least sync the filesystem.

---

### Post by djbushido on 2009-01-16
I would like to at least have an option to put this in at install: ex. user given a prompt to install the shortcut (with warning that it will restart X and kill all processes) or not install it.

My personal preference is to have it, saved my butt on numerous occasions.

---

### Post by Gourgi on 2009-01-16
just FYK to enable CTRL-ALT-BACKSPACE put this inside your xorg.conf
```
Section "ServerFlags"
	Option 		"DontZap"	"off"	
EndSection
```

---

### Post by ronacc on 2009-01-16
Thanks Gourgi  I had the dontzap option set wrong , it works now :)

---

### Post by taavikko on 2009-01-17
> **Wolki said:**
>  @taaviko, I'd say magic sysrq is more useful to me, since I can often use it to safely reboot a computer that seems to have completely hanged, or at least sync the filesystem.

IMHO is that Ctrl+Alt+Del is far more devious than C+A+B
cause it reboots the system. In windows it open's the prompt to do few things. Both of them should be put away, and be enabled only if user desires it.

and about that comment about SysRq, it was sarcasm :)

---

### Post by caryb on 2009-01-17
Add this to your xorg.conf & then you can!

```
Section "ServerFlags"
        Option "DontZap" "no"
EndSection

```


Cary

---

### Post by raccoonone on 2009-01-17
One thing we need to keep in mind with a poll like this, is that the users who don't want (or use) ctrl-alt-backspace are non-technical users who won't be reading this forum. So it's going to be a rather biased sampling.

---

### Post by caryb on 2009-01-17
I agree with raccoonone it's not hard to add a line to xorg.conf as part of your build! I know myself I make more changes than that when I'm tailoring my system.


Cary

---

### Post by vikigal on 2009-01-17
I am a relative newbie and definitely not a developer or techie or whatever. Just a granny who loves her ubuntu and plays around a lot. I also manage to freeze things occasionally. Ctrl-alt-bksp is an automatic thing when it locks up. I have never heard of the techno phrases that you experts keep saying just use -----. How will others like me know about it? If you really want to spread to the masses stick with what we know. Everyone who knows windows know ctrl-alt-del and it was simple to remember the new. If you make it a command you are adding way too many steps to what should be a simple step. Before I figured out to replace del with backspace I used force quit which I hated to do and have had my mouse freeze in which case the only alternative I could think of was to just use the power button and shut it down.

(I have replaced the old mouse so that hasn't happened in a while.)

---

### Post by cardinals_fan on 2009-01-17
> **raccoonone said:**
> One thing we need to keep in mind with a poll like this, is that the users who don't want (or use) ctrl-alt-backspace are non-technical users who won't be reading this forum. So it's going to be a rather biased sampling.
Yes, and those users are the ones who will have difficulty modifying xorg.conf when they need to kill X.

---

### Post by lukjad on 2009-01-17
Hehe! Good point. I can see the threads now:

**"Help Ctrl+Alt+Del doesn't work, what do I do?"**

And then someone telling them that they need to open up a terminal, install vim or emacs, then cd to...

---

### Post by Slug71 on 2009-01-17
This is a C/P from the poll i made in the 'Ubuntu Idea Pool' about replacing Ubiquity with Anaconda.

> Yeh but you make a good point about Ubiquity's ease of use. What would be very cool is if Ubuntu adopted Anaconda and then worked with RH/Fedora to kinda simplify it for the average/newb by having an 'Advanced' button somewhere in the installer which if you click on it opens up a menu where you can set the drive boot order and change default keyboard shortcuts etc.
Like being able to turn on Ctrl-Alt-Backspace which is going to be disabled by default in Jaunty now.

This way you keep certain things away from people that are new and keep the basic function of the installer simple but have the option there for a more advanced menu for users that know what they are doing.

If that could happen, it would be pretty cool. That way everybody wins.

---

### Post by ozbolt on 2009-01-17
> **Peter76 said:**
> That's my emergency exit for a hanging session.... Leave it where it is!

I am with this one!

---

### Post by zekopeko on 2009-01-17
> **blazemore said:**
> Make it Opensuse style: You have to do it twice in quick succesion. Then you can still do it, but not accidently!

i think that this would be the most sensible option for all. you can still kill X but chances for accidents is diminished.

---

### Post by Slug71 on 2009-01-17
> **blazemore said:**
> Make it Opensuse style: You have to do it twice in quick succesion. Then you can still do it, but not accidently!

Thats a good idea!

---

### Post by lexe-cc on 2009-01-17
I need the key combo because sometimes my ati card fails at boot up, leaving some sort of distorted image. This is where the combo comes in handy. 
Besides I believe the combo proves useful to many people. Also, how could you possibly "accidentally" hit that combination :confused:

Lexe

---

### Post by zekopeko on 2009-01-17
> **lexe-cc said:**
> I need the key combo because sometimes my ati card fails at boot up, leaving some sort of distorted image. This is where the combo comes in handy. 
Besides I believe the combo proves useful to many people. Also, how could you possibly "accidentally" hit that combination :confused:

Lexe

here are a couple of examples on netbooks/notebooks:

[http://farm4.static.flickr.com/3208/2758610258_1f8ffd98b7.jpg](http://farm4.static.flickr.com/3208/2758610258_1f8ffd98b7.jpg)
[http://www.danielmoth.com/Blog/LenovoKeyboardWTF.jpg](http://www.danielmoth.com/Blog/LenovoKeyboardWTF.jpg)

it just takes a slip of a finger...

---

### Post by mrboojive on 2009-01-17
> **zekopeko said:**
> here are a couple of examples on netbooks/notebooks:

[http://farm4.static.flickr.com/3208/2758610258_1f8ffd98b7.jpg](http://farm4.static.flickr.com/3208/2758610258_1f8ffd98b7.jpg)
[http://www.danielmoth.com/Blog/LenovoKeyboardWTF.jpg](http://www.danielmoth.com/Blog/LenovoKeyboardWTF.jpg)

it just takes a slip of a finger...

I have a keyboard almost exactly like that first one and I've never hit ctrl-alt-backspace by accident. 

Just about the only way you could hit it by accident is if you are going for ctrl-alt-del. In a default install of Ubuntu, doesn't ctrl-alt-del just bring up the log out screen? If someone is trying to log out anyways, a finger slip to ctrl-alt-backspace isn't going to be the end of the world. And if someone is sophisticated enough to map ctrl-alt-delete to something besides logging out and a finger slip would be problematic for them, why should we change the behavior of ctrl-alt-backspace for their benefit? If they can change ctrl-alt-del to something else, leave it to them to change ctrl-alt-backspace too.

---

### Post by ac7ss on 2009-01-17
As stated before, the only 'Accidental' keying would be missing a Ctrl-Alt-Del. You should not be using that to log out anyway. ^d works fine.

---

### Post by heatpumpcontrol on 2009-01-17
I've set up Ubuntu on a personal computer at work. I've told everyone that uses it to use the Ctrl+Alt+Bkspc combination whenever the screen locks up or for whatever reason the session locks up. It is easy to instruct Windows users to use this combination as they are familiar with the 'other' famous Windows 3 finger salute combo. This keeps them from forcing a shutdown on the pc.

Leave it as it is and maybe set it up as an option you can disable. 

Please don't mess with it.

---

### Post by Frak on 2009-01-17
1. These three keys are awfully hard to "accidentally" hit in combination.
2. I find this combination beneficial when I am testing and accidentally lock up something.
3. Just do what OpenSUSE did and implement the X-WARNING Beep. The system alarm beeps twice and waits for an intermittent 1-2 seconds for the keys to be unpressed. If the keys remained pressed, it resets the X server.

---

### Post by Joeb454 on 2009-01-17
> **Frak said:**
> 3. Just do what OpenSUSE did and implement the X-WARNING Beep. The system alarm beeps twice and waits for an intermittent 1-2 seconds for the keys to be unpressed. If the keys remained pressed, it resets the X server.

That's not a bad idea :)

Though as others have mentioned, I've never "accidentally" managed to hit that key combo, even on my laptop.

Purposefully on somebody elses laptop...now that's a different question ;)

---

### Post by ShirishAg75 on 2009-01-17
> **Frak said:**
> 1. These three keys are awfully hard to "accidentally" hit in combination.
2. I find this combination beneficial when I am testing and accidentally lock up something.
3. Just do what OpenSUSE did and implement the X-WARNING Beep. The system alarm beeps twice and waits for an intermittent 1-2 seconds for the keys to be unpressed. If the keys remained pressed, it resets the X server.

That's definitely a good idea.

---

### Post by tepsipakki on 2009-01-18
> **Frak said:**
> 1. These three keys are awfully hard to "accidentally" hit in combination.
2. I find this combination beneficial when I am testing and accidentally lock up something.
3. Just do what OpenSUSE did and implement the X-WARNING Beep. The system alarm beeps twice and waits for an intermittent 1-2 seconds for the keys to be unpressed. If the keys remained pressed, it resets the X server.

1. No they're not. There are apps where you are supposed to hit ctrl-alt-delete, but accidentally hit backspace.. all your data is lost, and that's a far more important bug to fix than allowing a convenient way to kill X.
2. Then set 'Option "DontZap" "no"' in your ServerFlags
3. This has been discussed on [email]xorg@lists.freedesktop.org[/email] numerous times, and the default was changed for xserver 1.6 & master on Oct 08 I think. Check the archives if you like... So, every distro that doesn't change the default will have this behaviour. I'm pretty sure that Fedora will not change it, and know for a fact that Debian won't.

And if you need to kill a session that's b0rked, you can just hit the reset/power button..

---

### Post by ShirishAg75 on 2009-01-18
> **tepsipakki said:**
> 

<snipped>

3. This has been discussed on [EMAIL="xorg@lists.freedesktop.org"]xorg@lists.freedesktop.org[/EMAIL] numerous times, and the default was changed for xserver 1.6 & master on Oct 08 I think. Check the archives if you like... So, every distro that doesn't change the default will have this behaviour. I'm pretty sure that Fedora will not change it, and know for a fact that Debian won't.

And if you need to kill a session that's b0rked, you can just hit the reset/power button..

While I can see the xorg archives, its a pain going through the archives. 

[http://lists.freedesktop.org/archives/xorg/](http://lists.freedesktop.org/archives/xorg/)

Can somebody point to the specific discussion regarding X-warning beeps .

---

### Post by plun on 2009-01-18
> **ShirishAg75 said:**
> While I can see the xorg archives, its a pain going through the archives. 

[http://lists.freedesktop.org/archives/xorg/](http://lists.freedesktop.org/archives/xorg/)

Can somebody point to the specific discussion regarding X-warning beeps .

This thread maybe

[http://lists.freedesktop.org/archives/xorg/2008-September/038786.html](http://lists.freedesktop.org/archives/xorg/2008-September/038786.html)

the challenge is also support forums or howtos which doesnt mention that all data will be lost.


Or... introduce a "blue screen"... :P

---

### Post by cmay on 2009-01-18
> **agim said:**
> As long as you can enable, I guess I understand. But I am against this, when you need to restart, you may not be able to enable the option to use it.
I hope it doesn't get changed, how the hell can you accidentally hit all three at once?
this shortcut has saved my life more than once. i voted no. but i can tell you how that it is possible to hit all 3 at once by mistake. i do that sometimes when i play supertux. i have always to fingers on ctr + alt and teh if i reach for my coffecup or drop a lighter i can hit these 3 at once. i could not live wiht out the shortcut since sometimes something is geting so messed up that xkill wont do the trick. if i have too many windows open and all stuff is haning and dragging and its too slow to open a terminal i do a logout by using ctrl+alt+del buttons.sometimes  its one of the most handy and useful features i think.

---

### Post by sdowney717 on 2009-01-18
> 3. Just do what OpenSUSE did and implement the X-WARNING Beep. The system alarm beeps twice and waits for an intermittent 1-2 seconds for the keys to be unpressed. If the keys remained pressed, it resets the X server.

Excellent idea.
Losing data is no fun. But would people be so smart as to let go of the keys?? Likely they would just keep on holding them down. A new key combination might be better such as 'cntrl-alt-end'

---

### Post by ShirishAg75 on 2009-01-18
IMHO, it would be really great if we are able to get that opensuse patch and use it. 

[http://lists.freedesktop.org/archives/xorg/2008-September/038860.html](http://lists.freedesktop.org/archives/xorg/2008-September/038860.html)

Of course after they do implement it so its less annoying to users.

---

### Post by lukjad on 2009-01-18
I have to admit, I have accidentally hit the Ctrl+Alt+Backspace about five times. The reason is because I changed the Ctrl+Alt+Arrow to switch desks to Ctrl+Alt+Plus or Ctrl+Alt+Minus. This is my fault and I own that. Hitting the reset button is the more drastic step. I really hate to do it, and on the odd occasion where my computer has just started to go reeeeeeeeeeeeeeeeeeeeeally slow, I don't want to kill my PC. It's really hard to log out of a computer session when you can't see your mouse for five minutes every time you move it. I really would miss this keyboard shortcut.

---

### Post by supernovus on 2009-01-19
I don't care one way or the other, as long as it's configurable.

So, with that in mind, ship with it off, those who are smart enough to know about it, will be smart enough to re-enable it.

---

### Post by scaine on 2009-01-19
> **supernovus said:**
> I don't care one way or the other, as long as it's configurable.

So, with that in mind, ship with it off, those who are smart enough to know about it, will be smart enough to re-enable it.

Yeah, true.  But it's just one more thing to remember.  It takes me hours to get a system tweaked the way I like it - Medibuntu, Power manager, Compiz, OpenOffice, Terminal, install this/that, everything else.

I don't feel all that strongly about this decision - it was made upstream after all (not that that makes it right of course), but it's just another thing to remember after a new install.

Makes LinuxMint look more and more attractive.  I just tried Felicia and I'm pretty impressed.  It's not perfect, but it cuts down on the post install tweaks/dross by a fair bit.

---

### Post by rubberglove on 2009-01-19
I think they should disable it...

...immediately after they make X so solid that you'll never, ever need to kill it again. ;-)

---

### Post by jrusso2 on 2009-01-19
> **Eclipse. said:**
> I can understand why its being done but I will re-enable it myself.

You can also use "sudo /etc/init.d/gdm restart" from the terminal although if your desktop has crashed or you got a memory leak and want to fix it quickly then your going to need to enable it.

How do you type that when everything is locked up, unless you can ssh in and run it.

---

### Post by zekopeko on 2009-01-19
> **jrusso2 said:**
> How do you type that when everything is locked up, unless you can ssh in and run it.

ctrl+alt+(f1-f6) gives you console mode

ctrl+alt+f7 to return to GUI.

---

### Post by Amaranth on 2009-01-19
You can also press Alt-SysRq-k to kill X which should always work (if it doesn't your only choice would be to hold down the power button anyway).

---

### Post by eragon100 on 2009-01-20
> **Amaranth said:**
> You can also press Alt-SysRq-k to kill X which should always work (if it doesn't your only choice would be to hold down the power button anyway).

For me, that combination only makes a screenshot, and I am default settings.

---

### Post by Zlatan on 2009-01-20
CTRL-ALT-BACKSPACE should be left enabled since it is a very good shorctut. I can not see any reason to disable it.

---

### Post by halovivek on 2009-01-20
Leave as it is.

---

### Post by darkenergy on 2009-01-20
> **Slug71 said:**
> Thats a good idea!

I agree!
think this would be the best solution for both points of view.

I also need this combo since it is the easiest way to kill a hanging X
but i understand that some people tend to press that occasionally.
I think the first time I used this shortcut it was not on purpos lol

---

### Post by urbandryad on 2009-01-20
I just discovered it yesterday and its totally useful! :O I don't want it gone now!

---

### Post by Sprut1 on 2009-01-20
I use it every day. Make an option for disabling - leave it on by default.

---

### Post by MacUntu on 2009-01-20
> **Sprut1 said:**
> I use it every day.
Why?

---

### Post by Sprut1 on 2009-01-20
> **MacUntu said:**
> Why?

Okay not EVERY day :)

---

### Post by kaldor on 2009-01-20
Why disable it? It would be a dumb idea.

This is Linux, not Mac or Windows. People need to understand that.

Personally, after a year using Linux, I never even knew about ctrl-alt-backspace... now it's a lifesaver to me.

Make it so you can disable it in the preferences menu somewhere. Do not disable it by default.

---

### Post by tseliot on 2009-01-21
> **ronacc said:**
> to properly describe my outrage at this idea would require words that cannot be used in this forum. and BTW the the workaround posted elsewhere ( add option "DontZap"  "true" to xorg.conf ) dosent work for me and where is the promised gui to re-enable it ???  from the blueprint

The UI for Kubuntu is ready but won't be available until my "dontzap" package is uploaded. The UI for Ubuntu will be finished soon and you will also be able to enable or disable the option from the command line with something like this:
to enable
```
sudo dontzap -e
```
to disable
```
sudo dontzap -d
```

---

### Post by taavikko on 2009-01-21
> **tseliot said:**
> The UI for Kubuntu is ready but won't be available until my "dontzap" package is uploaded. The UI for Ubuntu will be finished soon and you will also be able to enable or disable the option from the command line

Will this be included in the default installation, or does this pkg have to be installed afterwards via pkg-managers?

---

### Post by marmuta on 2009-01-21
> **tseliot said:**
> 
```
sudo dontzap -e
```
to disable
```
sudo dontzap -d
```
I wish they (Xorg-devs) hadn't used inverted logic for the DontZap option. They could have just as easily named it AllowZap like all the other Allow* options. Always makes me think twice to get what I want.

---

### Post by tseliot on 2009-01-21
> **taavikko said:**
> Will this be included in the default installation, or does this pkg have to be installed afterwards via pkg-managers?

I *think* this will be included by default. I'll ask other developers just to be sure.

---

### Post by tseliot on 2009-01-21
> **marmuta said:**
> I wish they (Xorg-devs) hadn't used inverted logic for the DontZap option. They could have just as easily named it AllowZap like all the other Allow* options. Always makes me think twice to get what I want.

Yes, I know what you mean. In the Kubuntu GUI you won't see the name of the option at all but only something like "Ctrl+Alt+Backspace restarts the xserver"

---

### Post by forcecore on 2009-01-21
i quite often use ctrl+alt+backspace if something happens with 3d game or something eats memory out like faulty screensaver etc...

---

### Post by cariboo on 2009-01-22
I jsut just installed dontzap, and it works as it should.

Jim

---

### Post by jrusso2 on 2009-01-22
> **tseliot said:**
> I *think* this will be included by default. I'll ask other developers just to be sure.

Why are they having us vote if they already decided.  The vote is strongly on the don't change it side.

---

### Post by taavikko on 2009-01-22
> **jrusso2 said:**
> Why are they having us vote if they already decided.  The vote is strongly on the don't change it side.

This vote was put up by an tester just like you and me...
Nothing to do with ubuntu-devs.

As for the dontzap, ubuntu-desktop doesn't include it (yet)?

---

### Post by DougieFresh4U on 2009-01-22
I know, stupid question, but what is the code for me to get in the  'x' file to add that 'Dontzap' option?
Thanks


**EDIT:** I am refering to the actual 'sudo' whatever code, to bring up the file.

---

### Post by marmuta on 2009-01-22
Nothing stupid about it. Here, Gourgi answered it in post [#47]("http://ubuntuforums.org/showpost.php?p=6560895&postcount=47").

---

### Post by quazi on 2009-01-22
How does one reenable this shortcut?  I've just installed Jaunty Alpha 3 and would like it to still be enabled.  I haven't had cause to use it, but I don't expect to hit that key combination by accident.

---

### Post by int on 2009-01-22
> **quazi said:**
> How does one reenable this shortcut?  I've just installed Jaunty Alpha 3 and would like it to still be enabled.  I haven't had cause to use it, but I don't expect to hit that key combination by accident.


Users who do want this function can enable it via the DontZap option in xorg.conf. 

A GUI tool to simplify setting xorg.conf options is under development and will be available in a later Alpha release

---

### Post by mister_pink on 2009-01-22
Wow, classic opensource! Change a small, easy to reverse, default, and everyone is outraged :D

Still, my personal preference is to use Zap warning, like suse. 

Also, something I think we need is a way to kill a misbehaving full screen app easily, without taking down the whole xserver. I know how to go to a terminal and do it, but for new users it would be nice if they could get something like the task manager (which we already have) but so that it is more failsafe like in windows which will come up with a keyboard shortcut as long as the whole thing hasn't locked up.

Edit: It was the use case given on the specification page that made me think this:
> 
Joel's computer interface has frozen due to a graphics driver problem. He still has daemons running which need to remain open, so he cannot reboot. He remembered that Ctrl-Alt-Backspace would restart X, and is surprised that it doesn't restart immediately. Instead, he switches to a terminal console and restarts the gdm process and is back in business. After reading up on the change, he decides to re-enable DontZap in his xorg.conf to make things work the way he's accustomed to in the future

What if Joel hadn't known to go to another terminal? He'd have to use a hard reset. And I'm not suggesting ctrl alt backspace as a good option either - firstly it shouldn't be needed to restart all of X, and also he may not have known about that either. A nice well documented shortcut to get a fail safe task manager would be really great.

---

### Post by tseliot on 2009-01-22
Here's a [blog post]("http://albertomilone.com/wordpress/?p=312") on the UI for Kubuntu.

Posts on the Gnome UI and command line tool will follow.

**EDIT:** in the same blog you can find the instructions on how to use the command line tool

---

### Post by ronacc on 2009-01-22
> **mister_pink said:**
> Wow, classic opensource! Change a small, easy to reverse, default, and everyone is outraged :D 

yes  , because with loads of bugs that need stomping they chose to change a shortcut that has for as long as I can remember been the accepted "quick kill" for X in not only ubuntu but every other distro I can think of . and then having to create gui tools to change it back . now thats great allocation of resources , and this to "protect" a relative few who don't watch what they are typing and who own hardware that makes them vulnerable to hitting an unlikely 3 key combo.

---

### Post by mister_pink on 2009-01-22
> **ronacc said:**
> yes  , because with loads of bugs that need stomping they chose to change a shortcut that has for as long as I can remember been the accepted "quick kill" for X in not only ubuntu but every other distro I can think of . and then having to create gui tools to change it back . now thats great allocation of resources , and this to "protect" a relative few who don't watch what they are typing and who own hardware that makes them vulnerable to hitting an unlikely 3 key combo.
I think people overreact a little here though, I mean come on, does it really matter? I use it probably more often than I should, and I'll re enable it. A task that I suspect will take me all of 20 seconds. 

I think people need to get some perspective on things. This is not going to change your life.

---

### Post by ronacc on 2009-01-22
I think the reaction is as much against the whole Idea of "dumbing things down" as it is against this particular change , you will see much the same kind of posts and much the same range of poll results (heavily against) everytime one of these little "nanny" changes is made . and yes I have already changed it back , atleast until they either completely eliminate xorg.conf or render it un editable .

---

### Post by lykwydchykyn on 2009-01-22
I have spent about 5 1/2 years on various Linux forums helping new users figure out Linux.  I cannot remember a single instance where someone accidentally pressed ctrl-alt-backspace.  I can remember a lot of times where that shortcut helped people get out of a locked-up x session, and where it helped me when things are screwed up.

I read the wiki page, and what irritates me are the case scenarios there and the grand assumptions they make about new users.  Why would a windows user attempt ctrl-alt-backspace?  It does nothing in Windows, I don't see why anyone would attempt that keystroke combination?  Are these scenarios based on actual usability testing, or just pulled out of someone's rear end?

If they're going to do this, why not disable all VT's as well?  After all, our hypothetical dumb-as-a-rock new ubuntu user who justifies these other changes is just as likely to get confused by accidentally switching to a VT and think they've killed X -- then hard restart and lose data.

Well, whatever; just one more tweak I have to do to keep Ubuntu usable.

---

### Post by lykwydchykyn on 2009-01-22
> **mister_pink said:**
> Wow, classic opensource! Change a small, easy to reverse, default, and everyone is outraged :D

Still, my personal preference is to use Zap warning, like suse. 

Also, something I think we need is a way to kill a misbehaving full screen app easily, without taking down the whole xserver. 


You mean like ctrl-alt-esc (which typically is set up to launch xkill)?

---

### Post by mister_pink on 2009-01-22
> **lykwydchykyn said:**
> You mean like ctrl-alt-esc (which typically is set up to launch xkill)?
Really? Doesn't do anything here, could of course been something I did. If its there by default it certainly needs to be better documented - everyone knows ctrl alt delete. 

The other problem is that most keyboard shortcuts won't work when you're running a full screen app. Only ones at a lower level like ctrl+alt+F1/bkspc or whatever, so it would need to be like those.

---

### Post by lykwydchykyn on 2009-01-22
> **mister_pink said:**
> Really? Doesn't do anything here, could of course been something I did. If its there by default it certainly needs to be better documented - everyone knows ctrl alt delete. 

The other problem is that most keyboard shortcuts won't work when you're running a full screen app. Only ones at a lower level like ctrl+alt+F1/bkspc or whatever, so it would need to be like those.

It's been this way on every distro I've used for the last six years.  Except I think compiz messes it up.  Seems like when I ran compiz I had to change it to ctrl-alt-end, but I figured that was because I was using compiz with KDE.  I assumed the default configuration of vanilla Ubuntu would honor the customary keystrokes.

If ctrl-alt-esc isn't working in Ubuntu, it needs to be.  It's one of the more useful shortcuts around.

---

### Post by Gina on 2009-01-22
> **ronacc said:**
> I think the reaction is as much against the whole Idea of "dumbing things down" as it is against this particular change , you will see much the same kind of posts and much the same range of poll results (heavily against) everytime one of these little "nanny" changes is made . and yes I have already changed it back , atleast until they either completely eliminate xorg.conf or render it un editable .I agree entirely with that.  I agree that in an ideal world everything just works!!  But otherwise these "Emergency Exits" can be a "life saver"!  Even "OS for Dummies" has Crtl-Alt-Del to escape from rogue processes that have stopped responding!  I get fed up with all the nannying everywhere in life these days :( :(

---

### Post by chek2fire on 2009-01-22
I think this is very stupid dec&#953;sion. Ctrl+alt+backspace is one of the power thinks in linux

---

### Post by mabovo on 2009-01-22
I prefer not to disable Ctrl+Alt+Bksp by default.
It is very useful even without need of Xorg.conf.

---

### Post by InfinityCircuit on 2009-01-22
Geeks are still the ones who provide the tech support, and the 3-finger salute to kill X is still a common part of such support.

You don't need Ctrl-Alt-Backspace until you NEED it--and you can't predict if you will need it in advance. I think it's ridiculous and asinine to turn it off.

---

### Post by Achetar on 2009-01-22
I love the Ctrl+Alt+Bksp shortcut! it's a lifesaver when trying out buggy game code!

---

### Post by rfruth on 2009-01-22
Are Ubuntu users like the average Windows user ?

---

### Post by ronacc on 2009-01-22
> **rfruth said:**
> Are Ubuntu users like the average Windows user ?

not in this forum !

---

### Post by lykwydchykyn on 2009-01-22
> **InfinityCircuit said:**
> Geeks are still the ones who provide the tech support, and the 3-finger salute to kill X is still a common part of such support.

You don't need Ctrl-Alt-Backspace until you NEED it--and you can't predict if you will need it in advance. I think it's ridiculous and asinine to turn it off.

Exactly.  This isn't just "the geeks crying because Ubuntu is being dumbed down", this is a tool being taken out of the toolbox for helping other people.  Sure, I can enable this on all my ubuntu machines (all umpteen of them... sigh), but it's an extra step when you are helping someone else who needs this feature.

Oh well, what can you do.

---

### Post by whoop on 2009-01-22
> **lykwydchykyn said:**
> 

Oh well, what can you do.

Complain, and hope someone listens :D

I voted "no" btw.

---

### Post by jtsop on 2009-01-23
Instead of Alt+Ctrl+BackSpace use Alt+SysRQ+Backspace. Who presses SysRq in real life??

---

### Post by ronacc on 2009-01-23
changing it to a different key combo would be worse . since unless all distros did so since it would render Ubuntu "non standard ". Ctrl>alt>bkspc has been the standard for many years , why make  us learn a new sequence ?

---

### Post by Gina on 2009-01-23
Absolutely!!!  We had enough of this NON-STANDARD malarky with the legacy OS that's so popular - the last thing we want is the dreaded disease spreading to Linux distros!!

---

### Post by alain57 on 2009-01-24
holly **** !
i hate this new stupid idea ....
because one or two idiots are touching 3 differents keys at the same time the most of us should pay an lost of comfort ?!?

ok we can enabled it back, but what is the case on live CD ?!?
or custom ubuntu based disto ?

because xorg.conf is generated automatically and the enable feature is in this file ....
oh i forgot i accidentally press the off button and my computer stops can they please disable the off button ??? (i joke not that they listen to me)

what next ? remove the control alt F1-F6 shortcut ?

---

### Post by fifth on 2009-01-24
Would it be possible to leave it enabled and implement a system to intercept the key combo and then have a gui window to confirm the action?

Seems like this might keep everyone happy?

---

### Post by chrisccoulson on 2009-01-24
> **fifth said:**
> Would it be possible to leave it enabled and implement a system to intercept the key combo and then have a gui window to confirm the action?

Seems like this might keep everyone happy?

The main reason for needing to use CTRL+ALT+BACKSPACE is when something bad happens to the X server (eg, it freezes). If something bad has happened, you can't trust it to be able to display a window, let alone allowing you to click on it.

---

### Post by Alterax on 2009-01-25
I apologize in advance, but I'm still not certain as to why or how this got to the table to begin with.  The ability to restart X with a key sequence has proven quite useful to me in the past, and it's something that most Linux users are familiar with.

I could understand the need to turn off this feature if it used the same key sequence that users were already accustomed to for a completely different function, or if the keys were positioned in such a way that it is easy to strike that particular combination.  But neither of these are the case; CTRL-ALT-BACKSPACE seems peculiar to X (the closest Windows has is CTRL-ALT-DELETE), and it's not a combination that's easy at all to hit upon.

What I'm saying here is that those who have complained about accidentally restarting X were aware that the key sequence did *something*, albeit were not fully informed about exactly what it does when it's invoked.  I do empathize with them, as I've made mistakes before, but took it as a learning experience.

As most of our new users come from a Windows background, and the closest Windows equivalent is CTRL-ALT-DEL for bringing up the task manager to get rid of runaway programs, locking the screen, or rebooting the computer, it may well be that the users are merely trying to find an equivalent for these functions when they do hit on this particular combination.  Maybe adding the FORCE QUIT button to the panel (perhaps next to the power/switch user button?) would be of more use to the enduser without throwing out a really useful power tool?

---

### Post by Alterax on 2009-01-25
> **chrisccoulson said:**
> The main reason for needing to use CTRL+ALT+BACKSPACE is when something bad happens to the X server (eg, it freezes). If something bad has happened, you can't trust it to be able to display a window, let alone allowing you to click on it.

You do bear a good point here.

---

### Post by hayden92 on 2009-01-25
I like the idea of keeping the short-cut consistent. 

If the dev's disabled it, a lot of users that currently use it would get frustrated at the unannounced change.

---

### Post by mikeize on 2009-01-25
I use it all the time.  Really though, I wish there was the equivalent to "ctrl-alt-del" for when Ubuntu totally hangs up, and the "skinny elephants" doesn't even work.

---

### Post by ronacc on 2009-01-25
if skinny elephants dosen't work your keyboard is lockedup and the reset button is the only option.

---

### Post by hayden92 on 2009-01-26
What on earth is/are 'skinny elephants'?

---

### Post by canesalato on 2009-01-26
Do like opensuse:
they keep the shortcut but to make it work you have to press it TWICE...
I think this is the best solution:
-we keep the traditional shortcut
-it's impossibile for joe users to press the combinations 2 times by mistake
-everyone's happy :popcorn:
IMHO disabling it is just silly...and particolarly now that we are testing jaunty and heavy changes to Xorg are committed...

---

### Post by amano on 2009-01-26
We are talking about a default here:

It will be easy to turn the old combo on (it is just a checkmark in the screen applet away), thus all people who know about, will turn it on.

And all those who don't know about the combo will have it turned off by default. They won't profit from having it enabled anyways (because they don't know about it) and are safe from pressing it by accident and thus be safe from losing important documents/data this way...

I cannot see anybody losing anything, but I see Linux-newbies that will be saved from a possible catastrophy. Thus I cannot understand the upset here since I believe that it was a sensible decision (that sticks to upstream's decision).

Having to press the combo twice or using a different combo would create a new unnecessary delta to upstream which will have it turned off by default now as well. And this change will not be obvious from the GUI and would have to be documented in another way.

Maybe existing installs should keep it enabled and just new installs should turn it off...

---

### Post by Wolki on 2009-01-26
> **hayden92 said:**
> What on earth is/are 'skinny elephants'?

A common mnemonic for sysrequests.

See for example [http://mirzmaster.wordpress.com/2006/12/12/raising-skinny-elephants-is-utterly-boring/](http://mirzmaster.wordpress.com/2006/12/12/raising-skinny-elephants-is-utterly-boring/) and [http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

---

### Post by whoop on 2009-01-26
> **chrisccoulson said:**
> The main reason for needing to use CTRL+ALT+BACKSPACE is when something bad happens to the X server (eg, it freezes). If something bad has happened, you can't trust it to be able to display a window, let alone allowing you to click on it.

However you can display a window for when it was pressed unwanted. You can pop up a window that says: "You hit Ctrl+Alt+Backspace, the window manager will restart in 5 seconds. Are you sure you want to do this." Yes, No. 
So if you hit it by accident you can click No; if you hit it on purpose it will restart after a delay of 5 seconds. Although I still think this would suck.

**I don't want this feature enabled by default.**
I can remember helping 2 people (total noobs) via the telephone that got stuck. With this new feature I would not be able to do that anymore.
I would get the following situation:
*me:*Did you enable Ctrl+Alt+Backspace after you installed Ubuntu
*noob:*Did I what? Euh, yes I did, I think. (but they didn't).
**I don't want a different key combo.**
Please enforce (some kind of) standards
**I don't want popupboxes**
Only bloat where absolutely possible.

The only issue this problem is causing is an occasional user posting on the forums: "My screen went black and threw me to the login screen for no reason"

---

### Post by Tomatz on 2009-01-26
NO NO NO

Bad idea!

---

### Post by mihai.ile on 2009-01-26
The problem here is that if it's not enabled by default will not be available when you need it. Not having this enabled when you try to help someone is bad. You may have it enabled but the one you are trying to help definitely won't.

---

### Post by gspat on 2009-01-26
Maybe a BIG dialog that comes up during install... just before / after you set your time zone? Or maybe really early in the install procedure, so it can be turned on and available from the get-go... before any other action is taken?

Something like...

> Ubuntu now defaults to not allow you to be able to restart the X-Server during a session with the key combination CTRL - ALT - BKSPACE. Do you want to accept this default?

(This option can also be changed after the install by using the "Don't Zap" option in the "System > Preferences" Menu.)

X - Yes, Leave it turned off

0 - No, Please turn it on


This way, everyone knows from the get go, the Ubuntu team fulfils it's obligations to remain "standard", and the Universe can keep turning on it's merry way.

BTW: "Don't Zap" sounds kinda geeky and dumb doesn't it? Isn't there some better wording for it that can be used?

---

### Post by amano on 2009-01-26
> The problem here is that if it's not enabled by default will not be available when you need it. Not having this enabled when you try to help someone is bad. You may have it enabled but the one you are trying to help definitely won't.

How will you help somebody who lost a long document because of accidently hitting the combo. Is there a magic combo that will undo that in your sleeve of helpful tricks?

If X is stuck and the combo is disabled, you can always power down your machine and boot again. Or you could give him the advice to try "Alt+SysRq+R" to shift keyboard focus from X, then change the virtual terminal with "Alt+F2" and then kill X with xkill. But hitting the combo accidently it may cause an irreversible loss of data in all X applications. It's your choice what's the better scenario...

Thus THERE ARE OTHER WAYS TO KILL X already.

---

### Post by gspat on 2009-01-26
> **amano said:**
> How will you help somebody who lost a long document because of accidently hitting the combo. Is there a magic combo that will undo that in your sleeve of helpful tricks?


Nope! But if they have been informed about it from the get-go, AND given a choice... What more can we do?

---

### Post by amano on 2009-01-26
> **gspat said:**
> What more can we do?

Disable all deadly key-combos and kill X in saner ways like I suggested in my last post.

--> Alt+SysRq+R (if the keyboard is not responding)
--> Alt+F2
--> "xkill"

See a more fruitful discussion that covers the possibility that CTRL+ALT+Backspace doesn't work: [http://ubuntuforums.org/showthread.php?p=2670279](http://ubuntuforums.org/showthread.php?p=2670279)

---

### Post by ronacc on 2009-01-26
yes there are other ways to kill x , among them as you pointed out hitting the power button , which of course cannot possibly cause any data loss "sic".

---

### Post by amano on 2009-01-26
That's the way how new users from Windows would do it. They always did so and thus will handle it this way without any better advice

If they look for an advice, we can adivse them to rather use other ways to kill X.

To carry around an all deadly key-combo doesn't sound like a sane idea.

---

### Post by gspat on 2009-01-26
> **amano said:**
> Disable all deadly key-combos and kill X in saner ways like I suggested in my last post.

--> Alt+SysRq+R (if the keyboard is not responding)
--> CTRl+Alt+F2
--> log in and "xkill"

See a more fruitful discussion that covers the possibility that CTRL+ALT+Backspace doesn't work: [http://ubuntuforums.org/showthread.php?p=2670279](http://ubuntuforums.org/showthread.php?p=2670279)

That would be a great idea, but would a new Linux user know to do it? As far as I know there really isn't a way to automate it, so as far as I can tell, only someone that has a reasonably good knowledge of Linux will know to use it. If you really want to make that simple enough for a new Linux user to use you really have to end up making it into - gasp - *another key combo*!.

We all know that when we use CTRl - ALT - BKSPACE we are commiting any unsaved info in our applications to the void, that has never been in dispute... It's just a very fast method of rebooting X to start again. I personally have never viewed it as anything other than a Linux alternative to CTRL - ALT - DEL and always fully expected all data in open programs to be gone. This is why I use the autosave in OpenOffice.

I've put a post-it by my monitor with your suggestion, I never knew that would work, and I've never really tried a sysreq key combo. Thank you for the info!

---

### Post by ronacc on 2009-01-26
I can see that we have different views on this . It is my belief that to try to protect "everyone from everthing " is well meaning but misguided paternalism , and often does more harm than good .

---

### Post by hikaricore on 2009-01-27
So far it's 428 against and 73 for... looks like most of us still have our sanity.

---

### Post by edv on 2009-01-27
Outright disgusting change. Do Ubuntu devs really want to keep dumbing down stuff until they're just as bad as Windows? You won't beat them by repeating their mistakes..

Seriously, if the combination is a problem for someone, then they should be the one disabling it (from a GUI, not xorg.conf *wink*). Not this way around.

/cooloff

---

### Post by chrisccoulson on 2009-01-27
> **edv said:**
> Outright disgusting change. Do Ubuntu devs really want to keep dumbing down stuff until they're just as bad as Windows? You won't beat them by repeating their mistakes..

Seriously, if the combination is a problem for someone, then they should be the one disabling it (from a GUI, not xorg.conf *wink*). Not this way around.

/cooloff

Why? Most people shouldn't need this combination, it can be a nuisance if you hit it accidentally and the response to pressing it accidentally might surprise some users.

On a modern system, this type of keyboard shortcut just should not be needed.

It's not that difficult to re-enable it for people who really want it, is it?

---

### Post by Frak on 2009-01-27
> **chrisccoulson said:**
> Why? Most people shouldn't need this combination

Unless you're me of course.

> **chrisccoulson said:**
> it can be a nuisance if you hit it accidentally and the response to pressing it accidentally might surprise some users.

And that's why the proposed alternate be a warning system with a beep and/or a mandatory two presses. (i.e. Press Ctrl+Alt+Bkspc then wait for a beep, then press Ctrl+Alt+Bkspc again).

---

### Post by mihai.ile on 2009-01-27
> **chrisccoulson said:**
> 
It's not that difficult to re-enable it for people who really want it, is it?

There is the problem, it is difficult to enable it when your X crashed. It's not normal to crash on a modern system as you say so you don't enable it, but when the un-normal happens (usually does) you don't have the shortcut.

And the second point is that the ones that don't know about it would certainly don't enable it, so when they mess things up and X crashes and asks for help I say "did you enable CTRL+ALT+BACKSPACE?" and they say "enable what?".

There you have it. Two real cases where this shortcut is needed. And as far as I know there far are more users that will need it than the other way around.

I don't like having features that I don't use enabled but it's just not the right moment to disable this shortcut, now with all the compatibility problems between intel/nvidia/ati drivers and Xversion/compiz
If you stop seeing threads here on the forum that have problems like "x freeze/crash" in the last months disable the shortcut but not until then.

P.S: as you say it's so simple to enable it I say
> It's not that difficult to **disable** it for people who really **don't** want it, is it?

---

### Post by MacUntu on 2009-01-27
> **mihai007 said:**
> There is the problem, it is difficult to enable it when your X crashed. It's not normal to crash on a modern system as you say so you don't enable it, but when the un-normal happens (usually does) you don't have the shortcut.

And the second point is that the ones that don't know about it would certainly don't enable it, so when they mess things up and X crashes and asks for help I say "did you enable CTRL+ALT+BACKSPACE?" and they say "enable what?".

Doesn't make sense. When X crashes and you don't have the shortcut enabled, you press the restart button, start in single user mode, drop to a root shell and edit the xorg.conf. Same for case two. 

> And as far as I know there far are more users that will need it than the other way around.

No way.

---

### Post by Frak on 2009-01-27
But, say you're in a fullscreen application and *it* crashes and you have no way to return to the desktop. Best way to rid of it is with the good ole' Ctrl+Alt+Bkspc

It's better to have something and not need it than to need something and not have it.

---

### Post by lykwydchykyn on 2009-01-27
We can go round and round with hypothetical scenarios about hypothetical users; as I pointed out before, in years of helping Linux users and being a Linux user, CTRL-ALT-BACKSPACE has been an extremely valuable tool, and I can't recall a single instance where someone hit it "accidentally".  Has someone actually had a different experience, honestly, or are you arguing from a hypothetical standpoint.

IMO this particular issue is a small one, but it's part of a larger problem with the development vector of Ubuntu.  Unless someone can point me to real-world incidents or studies showing this to be a problem, it's just solving a hypothetical problem.  We can sit around all day and come up with a list of features  that could hypothetically be a problem for new users, and remove/disable them from the system.  Seems to me it ultimately causes more problems than it actually solves.

---

### Post by mihai.ile on 2009-01-27
All those hypothetical problems by disabling the shortcut and I forgot to mention the real use that the shortcut does:
When you use an ATI card and connect an external monitor/projector you just have to hit CTRL+ALT+BACKSPACE so that the external display would be enabled. Don't know about NVIDIA or INTEL but with ATI is like this (it shouldn't be, maybe newer versions will fix this) but the shortcut is the simplest way to achieve this...

By the way if 85% out of 500 users says don't disable it why are we repeating ourselvs in the 16 pages thread?

---

### Post by zekopeko on 2009-01-27
> **mihai007 said:**
> All those hypothetical problems by disabling the shortcut and I forgot to mention the real use that the shortcut does:
When you use an ATI card and connect an external monitor/projector you just have to hit CTRL+ALT+BACKSPACE so that the external display would be enabled. Don't know about NVIDIA or INTEL but with ATI is like this (it shouldn't be, maybe newer versions will fix this) but the shortcut is the simplest way to achieve this...

By the way if 85% out of 500 users says don't disable it why are we repeating ourselvs in the 16 pages thread?

probably because 500<8 000 000 of the rest of userbase.

---

### Post by uid313 on 2009-01-27
Maybe change it from Ctrl+Alt+Backspace to Ctrl+Alt+Shift+Backspace? ;)

---

### Post by Frak on 2009-01-27
> **uid313 said:**
> Maybe change it from Ctrl+Alt+Backspace to Ctrl+Alt+Shift+Backspace? ;)
Some keyboards only support a max of 3 keys pressed at once.

---

### Post by lukjad on 2009-01-27
> **hikaricore said:**
> So far it's 428 against and 73 for... looks like most of us still have our sanity.
Hahahahahaha!

---

### Post by tepsipakki on 2009-01-27
Why is it so hard to use the key combo provided by the kernel itself?

alt + sysrq (=printscreen) + k = kill every process on the current VT, including X

problem solved.

(I need to use altgr though, maybe due to the keymap, but anyway..)

---

### Post by lykwydchykyn on 2009-01-27
> **tepsipakki said:**
> Why is it so hard to use the key combo provided by the kernel itself?

alt + sysrq (=printscreen) + k = kill every process on the current VT, including X

problem solved.

(I need to use altgr though, maybe due to the keymap, but anyway..)

Uh-oh, we might better disable that one as well.  Someone might hit it accidentally while trying to print a screenshot of killing a sentence in emacs.

---

### Post by lukjad on 2009-01-27
> **tepsipakki said:**
> Why is it so hard to use the key combo provided by the kernel itself?

alt + sysrq (=printscreen) + k = kill every process on the current VT, including X

problem solved.

(I need to use altgr though, maybe due to the keymap, but anyway..)

Of course it's hard. I mean, it is well known that Ubuntu uses gnomes.... :D

> **lykwydchykyn said:**
> Uh-oh, we might better disable that one as well.  Someone might hit it accidentally while trying to print a screenshot of killing a sentence in emacs.

True!

---

### Post by hikaricore on 2009-01-27
> **tepsipakki said:**
> Why is it so hard to use the key combo provided by the kernel itself?

alt + sysrq (=printscreen) + k = kill every process on the current VT, including X

problem solved.

(I need to use altgr though, maybe due to the keymap, but anyway..)


Because some of us don't want to kill every process, we just want to restart X.

This is a really really lame idea.  Just leave it enabled imho.

---

### Post by Frak on 2009-01-27
> **hikaricore said:**
> because some of us don't want to kill every process, we just want to restart x.

This is a really really lame idea.  Just leave it enabled imho.
+1000000000000000000000000000000000000000000000000000000000000000000000000

---

### Post by chrisccoulson on 2009-01-27
> **hikaricore said:**
> Because some of us don't want to kill every process, we just want to restart X.

This is a really really lame idea.  Just leave it enabled imho.

But if you hit CTRL+ALT+BACKSPACE and restart X, you've just killed everything on the current VT anyway (as you kill everything in your session when you do this, which is everything connected to that VT)

---

### Post by scaine on 2009-01-27
Argh!  I'm sick of reading this thread.  Why am I still reading this thread?  It doesn't HOW many posts or polls you put on here, it won't change the decision to go with upstream on this - face it... it's disabled by default now.  You'll have to remember to edit your xorg.conf if you want this back.

Agree with lykwydchykyn (if that is your real name...) though - it's really poor form to force this change without showing WHY it's being done.  Developers just living in their little bubble again trying to second guess their user base.  Unless there WAS a study and they're just keeping really, really quiet about it - in which case I apologise.

It's gnome-screensaver all over again.  Except that this isn't the gnome devs this time around so I'll have to wait for gnome's next "sane default" before I start spouting off about gnome.  As usual.  Still using it mind you.  One day.  Oh, yes.  One day I'll try KDE...

---

### Post by chrisccoulson on 2009-01-27
I just spoke with Bryce Harrington about this on IRC to clear a few things up. Bryce is the Xorg maintainer for Ubuntu.

Just for some background information, please look at the original specification for this, which can be found here: [https://wiki.ubuntu.com/XorgCtrlAltBackspace/]("https://wiki.ubuntu.com/XorgCtrlAltBackspace/"). Also, the Launchpad blueprint is here: [https://blueprints.edge.launchpad.net/ubuntu/+spec/xorg-ctrl-alt-backspace]("https://blueprints.edge.launchpad.net/ubuntu/+spec/xorg-ctrl-alt-backspace"). The specification explains the rationale for this change. (sorry if this has already been posted in this thread)

The blueprint was opened for this in April 2007. Since then, there has been a general lack of consensus on the issue, so it wasn't implemented right away. However, in the end upstream implemented this anyway, due to lobbying from the community (so this will become the default across all distributions unless they decide to change it). But basically, this is one of those cases where you're never going to be able to please everyone (there will always be some for, and some against, and one of these groups will be more vocal than the other).

You'll note from the specification and blueprint that changing the key combination or having a confirmation dialog were both ideas that were discussed, but these were rejected upstream (see [http://bugs.freedesktop.org/show_bug.cgi?id=10507]("http://bugs.freedesktop.org/show_bug.cgi?id=10507") and [http://bugs.freedesktop.org/show_bug.cgi?id=10510]("http://bugs.freedesktop.org/show_bug.cgi?id=10510"))

Bryce has pointed out that there will be a simple graphical editor for tweaking your xorg.conf, available for both Gnome and KDE before beta. This tool will have support for toggling DontZap. The blueprint for this is here: [https://blueprints.edge.launchpad.net/ubuntu/+spec/xorg-options-editor]("https://blueprints.edge.launchpad.net/ubuntu/+spec/xorg-options-editor")

As already pointed out in this thread - Alt+SysRq+K will kill everything on the current VT, and Bryce confirmed that this can be used as an alternative to CTRL+ALT+BS for killing a frozen X server.

People might argue that someone might not know to disable DontZap until their X server has frozen, but on the flip-side, someone else might not know that they can enable it until after they accidentally hit the combination and lost a lot of work. And for a lot of normal users, CTRL+ALT+BS is not discoverable when Xorg freezes anyway, so it is not a lot of use having the combination available by default.

Bryce also pointed out that he probably doesn't like this change more than anyone, as he is constantly testing Xorg and having to recover from a frozen X server. But (like us), he also knows how to switch the option on if he wants to use it, whereas someone who accidentally pressed CTRL+ALT+BS is not going to know what happened.

---

### Post by cardinals_fan on 2009-01-27
> **chrisccoulson said:**
> 
It's not that difficult to re-enable it for people who really want it, is it?
The people this supposedly protects are the ones who will have trouble reenabling it when they need it.
> **MacUntu said:**
> Doesn't make sense. When X crashes and you don't have the shortcut enabled, you press the restart button, start in single user mode, drop to a root shell and edit the xorg.conf. Same for case two. 

Hard reboots are a bad, bad, bad, bad, bad, ... , bad thing.

---

### Post by doyouhas on 2009-01-28
I use this feature constantly so taking it out wouldn't be good for me. And unlike other people who have expressed frustration with hitting the keys on accident, I haven't had this problem at all. I know if I want to restart my session it's CTRL-ALT-BCKSPCE, taking that out of Ubuntu would be really sad.

---

### Post by ranch hand on 2009-01-28
I can't imagine hitting that combo accidentally.  If I say this it is silly to worry about.  I am a VERY (only had to correct the D for E in that) bad typist.  I can type things I can't figure out. Ctrl+Alt+Backspace is something I don' believe is possible by accident.

---

### Post by chrisccoulson on 2009-01-28
> **doyouhas said:**
> I use this feature constantly so taking it out wouldn't be good for me. And unlike other people who have expressed frustration with hitting the keys on accident, I haven't had this problem at all. I know if I want to restart my session it's CTRL-ALT-BCKSPCE, taking that out of Ubuntu would be really sad.

But the feature hasn't been taken out. You can re-enable it if you use it. And I'd be really worried if you use this feature constantly anyway. It is meant to be an emergengy "get-out" when the server crashes. It is definately not recommended for normally terminating a session, and is very very bad for that

---

### Post by SeanHodges on 2009-01-28
Please disable Ctrl-Alt-Backspace, or at least make it easy to do.

---

### Post by Mr. Picklesworth on 2009-01-28
> **malspa said:**
> I would rather not see it disable by default.  I'm glad other distros don't have it disabled.  I don't get it, four years or so of using Linux and I've never hit that keystroke by accident.

It really comes down to your keyboard. Ubuntu is popular amongst laptop users. On smaller laptop keyboards, all sorts of things are within slipping distance of Backspace. Ctrl + Alt is not unlikely to be absently (or intentionally) pressed, especially if you are coming from Windows :P

This doesn't stop you from switching virtual terminals and killing X that way.

---

### Post by SushiR on 2009-01-28
I didn't read this thread thoroughly but what about putting a file onto the desktop which lists most shortcuts and what they are about? This would be interesting AND helpful to new users...

---

### Post by mrboojive on 2009-01-28
> **Mr. Picklesworth said:**
> On smaller laptop keyboards, all sorts of things are within slipping distance of Backspace.

I do not agree that all sorts of things are within slipping distance. I have a laptop with small keyboard and the keys next to backspace are: delete, insert, +, }, and |. As far as I can tell, none of those do anything with Ctrl+Alt on a default install of Ubuntu except Ctrl+Alt+Delete, which brings up the logout window. If someone is going for the logout window, they want to log out. Or, if someone is a former Windows user going for Ctrl+Alt+Delete, they are having a problem with the OS. Either way, if they accidentally hit Ctrl+Alt+Backspace, it would not cause a serious problem, and might actually help them.

---

### Post by Mr. Picklesworth on 2009-01-28
> **mrboojive said:**
> If someone is going for the logout window, they want to log out.

There is a difference between logging out properly and killing X. Logging out properly saves your session (if you're cool like me :P) and allows other applications to block the action / finish their work if necessary.

---

### Post by jethro10 on 2009-01-28
> **agim said:**
> As long as you can enable, I guess I understand. But I am against this, when you need to restart, you may not be able to enable the option to use it.
I hope it doesn't get changed, how the hell can you accidentally hit all three at once?

My wife has done it, making 2 mistakes as she went along!

1. Looking for CTRL-ALT-DEL for windows forgetting she was on my PC
2. Hitting backspace instead of DEL

it does happen....

---

### Post by issih on 2009-01-28
I voted no, but have no objection to throwing up an "are you sure?" dialog before restarting X. That seems a vaguely sensible compromise imho..

---

### Post by mrboojive on 2009-01-28
> **Mr. Picklesworth said:**
> There is a difference between logging out properly and killing X. Logging out properly saves your session (if you're cool like me :P) and allows other applications to block the action / finish their work if necessary.

That's true. I was just saying if the main concern with Ctrl+Alt+Backspace is the possibility of losing something (unsaved documents, the session, etc.) if it's accidentally pressed, I don't think a lot of people hit Ctrl+Alt+Delete to log out without saving work that is important to them. I'm not sure that saving the session so important that the usefulness of Ctrl+Alt+Backspace should be disabled for everyone because of the possibility that someone attempting to log out using Ctrl+Alt+Delete could accidentally press something else and lose their session.

---

### Post by bruce89 on 2009-01-28
> **issih said:**
> I voted no, but have no objection to throwing up an "are you sure?" dialog before restarting X. That seems a vaguely sensible compromise imho..

How would a dialogue help if X was stuck (don't know the proper term). Surely the dialogue wouldn't appear.

---

### Post by OutOfReach on 2009-01-28
I think there should be a more complicated key group to kill X (like SysRq+REISUB).

I remember how many times I accidentally pressed Ctrl+Alt+Backspace while doing important work.

---

### Post by chrisccoulson on 2009-01-28
> **bruce89 said:**
> How would a dialogue help if X was stuck (don't know the proper term). Surely the dialogue wouldn't appear.

That was exactly the point I was trying to make a few posts ago. The sole reason for this shortcut is as a last-ditch get out when X has frozen. If the X server has frozen, you cannot expect it to be able to paint a dialog, let alone allow you to click on it

---

### Post by Mr. Picklesworth on 2009-01-28
> **OutOfReach said:**
> I think there should be a more complicated key group to kill X (like SysRq+REISUB).

I remember how many times I accidentally pressed Ctrl+Alt+Backspace while doing important work.

I should point out that REISUB is actually a pneumonic, and each key there (R, E, I, S, U and B) does something. If you hit SysRQ+REI, chances are your system will need to be rebooted to work properly again.

---

### Post by jerome1232 on 2009-01-28
I'm pretty sure I used one distro where you had to press ctrl+alt+backspace twice in rapid succession (like as fast as you would double click on the mouse).

Seems like that would be a good option to prevent accidentally hitting the keys.

---

### Post by Starks on 2009-01-29
You guys are all being extremely inconsiderate. Consider laptops for a change.

Fn + Print Screen = SysRq

However, Fn + Print Screen = Print Screen

---

### Post by inportb on 2009-01-29
I am so glad my laptop has a dedicated PrtSc/SysRq key :)

---

### Post by lykwydchykyn on 2009-01-29
> **Starks said:**
> You guys are all being extremely inconsiderate. Consider laptops for a change.

Fn + Print Screen = SysRq

However, Fn + Print Screen = Print Screen

I can honestly say I've never quite worked out how to make magic sysrq key combos work on my laptop.  No combination of Alt, Fn, PrintScrn/SysRq or anything else seems to have any effect.

So alt-sysrq-k doesn't do it for my laptop.  

Otherwise, I would have no problems with that as an alternative.  We'd just need to do global search and replace on all tutorials on the internet and we'd be good.

```

sed -i -e's/CTRL-ALT-Backspace/alt-sysrq-k/g' the_entire_internet

```

---

### Post by cardinals_fan on 2009-01-29
> **jerome1232 said:**
> i'm pretty sure i used one distro where you had to press ctrl+alt+backspace twice in rapid succession (like as fast as you would double click on the mouse).

Seems like that would be a good option to prevent accidentally hitting the keys.
+1

---

### Post by SeanHodges on 2009-01-30
> **lykwydchykyn said:**
> Otherwise, I would have no problems with that as an alternative.  We'd just need to do global search and replace on all tutorials on the internet and we'd be good.

```

sed -i -e's/CTRL-ALT-Backspace/alt-sysrq-k/g' the_entire_internet

```

Doesn't work for me :(

```
sean@SEAN-PC:~$ sed -i -e's/CTRL-ALT-Backspace/alt-sysrq-k/g' the_entire_internet
sed: +++ Out of cheese error. Please re-install universe and reboot +++
sean@SEAN-PC:~$
```

---

### Post by thecityofgold2006 on 2009-01-30
Most users will come to Ubuntu from Windows.

In Windows Ctrl-Alt-Del brings up a task manager and I would often use it when something crashed.

So a lot of new Ubuntu users will use the Ctrl-Alt-Del keypress if anything goes wrong. And as things stand they'll lose anything they're working on and be dumped out the GDM logon (perhaps the first time they'll have seen that screen).

If Ubuntu is serious about being an OS for the masses then Ctrl-Alt-Del must be disabled.

---

### Post by bruce89 on 2009-01-30
> **thecityofgold2006 said:**
> Most users will come to Ubuntu from Windows.

In Windows Ctrl-Alt-Del brings up a task manager and I would often use it when something crashed.

So a lot of new Ubuntu users will use the Ctrl-Alt-Del keypress if anything goes wrong. And as things stand they'll lose anything they're working on and be dumped out the GDM logon (perhaps the first time they'll have seen that screen).

If Ubuntu is serious about being an OS for the masses then Ctrl-Alt-Del must be disabled.

Control+Alt+Backspace is in fact the salute in question.

Also, I really don't like cloning Windows.

---

### Post by thecityofgold2006 on 2009-01-30
> **bruce89 said:**
> Control+Alt+Backspace is in fact the salute in question.

Also, I really don't like cloning Windows.

For most people backspace and del are interchangeable. In windows they operate as one and the same in this regard.

And it's not about cloning Windows, it's about acknowledging that the vast majority of computer users are only familiar with Windows and that a mass market operating system must accommodate this.

---

### Post by mrboojive on 2009-01-30
> **thecityofgold2006 said:**
> For most people backspace and del are interchangeable. In windows they operate as one and the same in this regard.

Control+Alt+Backspace does absolutely nothing in Windows.

---

### Post by bruce89 on 2009-01-30
> **thecityofgold2006 said:**
> For most people backspace and del are interchangeable. In windows they operate as one and the same in this regard.

Actually, backspace removes the character to the left of the caret wheras delete removes the character to the right. I tested this in Windows once too.

---

### Post by inportb on 2009-01-30
> **bruce89 said:**
> Actually, backspace removes the character to the left of the caret wheras delete removes the character to the right. I tested this in Windows once too.

It's quite a useful feature :)

---

### Post by oldsoundguy on 2009-01-30
When Firefox locks up because it interprets a couple of keystrokes from a wireless keyboard as a command macro and does "something". crtrl/alt/backspace is the quick way to restore vs having to reboot entirely!

---

### Post by inportb on 2009-01-30
Hm... I think we need a specific combo just to kill Firefox; it's annoying as hell :p

---

### Post by Mr. Picklesworth on 2009-01-30
Here's a nice blog post on the topic:
[http://www2.bryceharrington.org:8080/drupal/zap](http://www2.bryceharrington.org:8080/drupal/zap)

---

### Post by Npl on 2009-01-30
Seeing at CTRL-ALT-BACKSPACE s a last resort if something goes horribly wrong... why are people missing it so much?
To me killing the X-Server is pretty much equivalent to rebooting anyway, so what if its quicker - every app you had open is gone. Might aswell hit the reboot button on the PC.

Seeing as I already accidently hit the combination by expecting to start the task-manager, I`d be happy to see it gone unless you boot into failsafe mode.

---

### Post by jerome1232 on 2009-01-30
I don't get how people hit ctrl+alt+backspace it's not a key combo on any other os lol! 

At any rate that blog made a good point I suppose, alt+sysRq+k does a better job of restarting x than ctrl+alt+backspace does. 

Also that alt+SysRq+k can work when ctrl+alt+backspace doesn't.

--edit-- excpet it doesn't seem to work on my system :(

---

### Post by Npl on 2009-01-30
CTRL-ALT-DEL brings up the taskmanager in Windows. Backspace is the next thing you try if you dont see something like a taskmanager showing up. The meaning of Del and Backspace is close, and so are the keys.

---

### Post by lykwydchykyn on 2009-01-30
> **Npl said:**
> CTRL-ALT-DEL brings up the taskmanager in Windows. Backspace is the next thing you try if you dont see something like a taskmanager showing up. The meaning of Del and Backspace is close, and so are the keys.

?

Uh... sorry, that's a stretch.  With that kind of logic we should be disabling all kinds of things. 

I suppose the next key they'd try is ESC, which should launch xkill and then they might screw up the session clicking on the desktop and killing whatever is drawing the desktop, or killing whatever app they have up.  So I guess ctrl-alt-esc needs to be disabled.

Next they'll be trying F1, since it's right next to ESC, which would put them in a VT.  They'd of course assume that they killed their GUI and broke their computer in some terrible way and have no idea how to get back to the desktop, and probably hard reset the box.  So we need to ditch VT's and only run X sessions.

Let's see, what's next...  CTRL-ALT-Right?  That'll switch desktops in compiz.  Since our hypothetical user doesn't grok anything but Windows-ese, they've probably never seen multiple desktops before.  Switching like this will confuse them and they'll inadvertently format their hard drive trying to fix it.

This is the exact problem I'm talking about earlier with catering to a hypothetical user -- particularly a hypothetically ignorant user.  You can make them as hypothetically ignorant as they need to be to justify any kind of feature-removal or lockdown.  Whether or not this particular change is a good idea or not on other grounds, that justification has got to go.

---

### Post by s3kt0r on 2009-01-30
> **peter76 said:**
> that's my emergency exit for a hanging session.... Leave it where it is!

+1.

---

### Post by marco123 on 2009-01-30
> **lykwydchykyn said:**
> ?

Uh... sorry, that's a stretch.  With that kind of logic we should be disabling all kinds of things. 

I suppose the next key they'd try is ESC, which should launch xkill and then they might screw up the session clicking on the desktop and killing whatever is drawing the desktop, or killing whatever app they have up.  So I guess ctrl-alt-esc needs to be disabled.

Next they'll be trying F1, since it's right next to ESC, which would put them in a VT.  They'd of course assume that they killed their GUI and broke their computer in some terrible way and have no idea how to get back to the desktop, and probably hard reset the box.  So we need to ditch VT's and only run X sessions.

Let's see, what's next...  CTRL-ALT-Right?  That'll switch desktops in compiz.  Since our hypothetical user doesn't grok anything but Windows-ese, they've probably never seen multiple desktops before.  Switching like this will confuse them and they'll inadvertently format their hard drive trying to fix it.

This is the exact problem I'm talking about earlier with catering to a hypothetical user -- particularly a hypothetically ignorant user.  You can make them as hypothetically ignorant as they need to be to justify any kind of feature-removal or lockdown.  Whether or not this particular change is a good idea or not on other grounds, that justification has got to go.

Put perfectly.:)

Ctrl-Alt-Backspace has saved my behind numerous times.  

Maybe they should do a branch called Stupuntu for stupid users and leave main Ubuntu non-dumbed down?

---

### Post by taavikko on 2009-01-30
Dontzap was to come and bailout inexperienced users to enable the action, but somehow it was removed from ubuntu, at the moment...

```
gnome-control-center
Version: 1:2.25.3-0ubuntu3
Distribution: jaunty
Urgency: low

* debian/control.in, debian/control:
    - revert recommend on dontzap
```

---

### Post by DougieFresh4U on 2009-01-30
> **jerome1232 said:**
> I don't get how people hit ctrl+alt+backspace it's not a key combo on any other os lol!  :(

It's_ NEVER_ (alt-SysRq) worked on my system. :(

---

### Post by bruce89 on 2009-01-30
> **inportb said:**
> Hm... I think we need a specific combo just to kill Firefox; it's annoying as hell :p

Alt-F2, X+K+I+L+L+Enter, LMB.

---

### Post by plun on 2009-01-30
> **taavikko said:**
> Dontzap was to come and bailout inexperienced users to enable the action, but somehow it was removed from ubuntu, at the moment...

```
gnome-control-center
Version: 1:2.25.3-0ubuntu3
Distribution: jaunty
Urgency: low

* debian/control.in, debian/control:
    - revert recommend on dontzap
```

Well....

Ubuntu 2009...:D

Mybe its better to take a look at this "Le grande mess"...

[http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326)

---

### Post by plun on 2009-01-30
> **DougieFresh4U said:**
> It's_ NEVER_ (alt-SysRq) worked on my system. :(

Have you checked your F Lock-key ?

On my keyboard I must disable F-Lock and then SysRq works  ;)

---

### Post by bruce89 on 2009-01-30
I'm surprised this was actually an upstream change, as most dumbing down would be thanks to Ubuntu themselves. I'm sure that upstream have their reasons, but I don't think it's reasonable to change things like this so suddenly.

---

### Post by inportb on 2009-01-30
> **bruce89 said:**
> Alt-F2, X+K+I+L+L+Enter, LMB.

Ah yes. Or CTRL+ALT+ESC, LMB.

---

### Post by bruce89 on 2009-01-30
> **inportb said:**
> Ah yes. Or CTRL+ALT+ESC, LMB.

Ah, but that's not as funny (nor did I know of it).

---

### Post by Gina on 2009-01-30
Display Settings (System > Preferences > Screen Resolution) dialog now has a checkbox to enable Ctrl+Alt+Bksp to kill X session.

---

### Post by plun on 2009-01-30
> **Gina said:**
> Display Settings (System > Preferences > Screen Resolution) dialog now has a checkbox to enable Ctrl+Alt+Bksp to kill X session.

Nope... I believe it was removed earlier today...;)

---

### Post by malspa on 2009-01-30
> **marco123 said:**
> maybe they should do a branch called stupuntu for stupid users and leave main ubuntu non-dumbed down?

+1

---

### Post by inportb on 2009-01-30
> **bruce89 said:**
> Ah, but that's not as funny (nor did I know of it).

I'm not sure if it works on Gnome, but I just remembered that I use this on KDE most often to kill Firefox :p

---

### Post by bruce89 on 2009-01-30
> **inportb said:**
> I'm not sure if it works on Gnome, but I just remembered that I use this on KDE most often to kill Firefox :p

Actually, in GNOME it appears to be a window switcher, but with panels included.

---

### Post by inportb on 2009-01-30
That makes sense... it feels like a Compiz hotkey.

---

### Post by Gina on 2009-01-30
> **plun said:**
> Nope... I believe it was removed earlier today...;)Hmmpff!!!  Is that so?! I give up!  Anyway, I downloaded the daily build of AMD64 Alt CD and installed it - that had it.  I really wonder what they're playing at!!

---

### Post by bug11 on 2009-01-31
What about making the timing to 10sec hold down for restarting X-server? You dont hold Ctrl+Alt+Backspace down for 10sec by accident

---

### Post by techdude3177 on 2009-01-31
I ran updates today to find CTL-ALT-BACKSPACE disabled when i needed to kill the xserver..... (ANNOYED)

What they should do is set it up in keyboard shortcuts and this way it allow people to have an easy way to disable this feature if they get annoyed with it happening, that way the rest of us can keep moving forward because so far ~85% of us agree that CTRL+ALT+BACKSPACE shouldnt be disable at default.

---

### Post by DougieFresh4U on 2009-02-01
I am surprised this thread has gone on this long.
I have been using this forum for almost 4 years and I can not remember any threads starting something like this:
[B]"Help! My fingers were flying around the keyboard so fast that I hit Contr-Alt-Backspace by accident and I lost everything"
[/B]
But I do recall reading many threads titled;
**"My screen/X froze/locked up and I had to do a hard shut down, is there a way I can kill x without having to do HARD SHUTDOWN"**

And as I read replies to the thread most forum members suggested the Contr-Alt-Bacspace combo BUT they also mentioned most times that anything they were doing would be lost  by using the combo.
Yes I know I am being a 'smart a**', but what I have stated here is true :lolflag:

---

### Post by techdude3177 on 2009-02-01
> **DougieFresh4U said:**
> I am surprised this thread has gone on this long.
I have been using this forum for almost 4 years and I can not remember any threads starting something like this:
[B]"Help! My fingers were flying around the keyboard so fast that I hit Contr-Alt-Backspace by accident and I lost everything"
[/B]
But I do recall reading many threads titled;
**"My screen/X froze/locked up and I had to do a hard shut down, is there a way I can kill x without having to do HARD SHUTDOWN"**

And as I read replies to the thread most forum members suggested the Contr-Alt-Bacspace combo BUT they also mentioned most times that anything they were doing would be lost  by using the combo.
Yes I know I am being a 'smart a**', but what I have stated here is true :lolflag:

This may be true that either way everything may be lost, but... at least the kill x is a lot faster then restart.

---

### Post by DougieFresh4U on 2009-02-01
> **techdude3177 said:**
> This may be true that either way everything may be lost, but... at least the kill x is a lot faster then restart.

And I agree. My opinion is that it should have been left the way it was. 
My post (#222) was pointing out that "Where are the complaint threads that they based their decision to change the Contr-Alt-Backspace to disabled"?

---

### Post by MaX on 2009-02-01
Why can't we do like in SUSE?
You have to press CTRL-ALT-BACKSPACE twice for it to kill the X server, it also plays a huge noise on the PC speaker while doing so.
This would keep people away from accidentaly doing C-A-B and for us that want it it will be just a quick extra push on the buttons?

---

### Post by DavidONE on 2009-02-01
> **DougieFresh4U said:**
> "Where are the complaint threads that they based their decision to change the Contr-Alt-Backspace to disabled"?

These forums are not representative of the average turn-computer-on-send-email-do-a-little-surfing user. You won't see lots of threads here that are of concern to 'average' users.

Power users - everyone on this forum - can enable this in a couple of minutes.  It's the right decision to protect everyone else from a key combo (however unlikely some people think it is to accidentally hit it) that kills their PC.

---

### Post by MarblePanther on 2009-02-01
> **MaX said:**
> Why can't we do like in SUSE?
You have to press CTRL-ALT-BACKSPACE twice for it to kill the X server, it also plays a huge noise on the PC speaker while doing so.
This would keep people away from accidentaly doing C-A-B and for us that want it it will be just a quick extra push on the buttons?

I agree completely, I like the twice approach

But disable it completely?

How dumbed down are we gonna get?  (Micro$haft anyone?)

---

### Post by Mr. Picklesworth on 2009-02-01
> **DavidONE said:**
> Power users - everyone on this forum - can enable this in a couple of minutes.

More like a couple of seconds. This is a complete non-issue. Anyone who cares about killing X will know how to do this.

I just want to add that if you are using Ctrl Alt Backspace to log out, it is a good thing this was disabled because it gives you a chance to ponder how absolutely wrong that is. If some process is writing an important file and you choose to reset the X server, that process will not discriminate. It will terminate anything and everything, leaving a SIGNIFICANT mess behind.

**DON'T DO IT.**

Any polls on this topic will be biased since the people currently affected by the change are running an in-development version of Ubuntu and therefore are going to have more lockups than the common user and have an understanding of what Ctrl+Alt+Backspace actually does other than "break the internet".
I've had a LOT of exposure to clueless users - moreso than the typical geek whose parents and relatives own computers - so believe me: this change is a GOOD idea.

Finally, the problem with Windows is not that it is dumbed down. Windows is one of the most complicated operating systems you could force someone to use because it contains billions of layers of brainless abstraction. I encounter people every week who change the input language via their idiotic Ctrl Shift shortcut and have no idea why every time they type ` they see # (and É, etc), then proceed to blame their keyboards because Windows has done such a poor job of explaining concepts like this to its users and of providing relevant visual feedback. (Not that GNOME has any either, but at least we know there's a bug report on the subject).

---

### Post by Gina on 2009-02-01
I can see that a lot of that makes sense - and I agree that Windows is a very complicated OS.  Maybe an install option for Normal or Advanced use which can be changed later.  And this could be applied when adding a new user.  Many applications have this feature when installing and many dialogs an Advanced button.

IMO an operating system for the masses should "just work" with a minimal amount of setting up and have the advanced and trickier features turned off by default  but available by turning on an Advanced mode.

< Shields up Mr Spock >

---

### Post by cariboo on 2009-02-01
THe only problem with having a normal and advanced user setup is, that some new users will choose advanced, because they think the will miss something good.

Jim

---

### Post by ronacc on 2009-02-01
clear simple documentation would go a long way tword preventing problems (if you could get people to actualy READ it) . perhaps a popup the first time you hit ANY shortcut , for instance for ctrl>alt>bkspc    caution this will kill the xserver do you want to do this ? if yes hit return if no hit esc . notice that it calls for a keyboard input not a mouse click , this allows for the desktop being frozen while the keyboard remains active.

---

### Post by malspa on 2009-02-02
> **DavidONE said:**
> Power users - everyone on this forum - can enable this in a couple of minutes.  It's the right decision to protect everyone else from a key combo (however unlikely some people think it is to accidentally hit it) that kills their PC.

Everyone on this forum is not a power user.

It seems ridiculous to disable everything that someone might accidentally hit.  There have been good suggestions presented here that do not include completely disabling this key combo by default.  It seems to me that a simple pop-up window ("You are about to exit the desktop.  You will lose any unsaved data.  Do you wish to continue?  Yes or No.") would be sufficient.  Or having to hold the key combo for two seconds.  Or give us some kind of choice at installation time.  There are probably other solutions that would make everyone happy, but instead, somebody makes the decision to completely disable it, which satisfies only a small percentage of users?  This key combo is one something that's been common to Linux systems for how long?  This decision shows a lack of common sense.

---

### Post by SushiR on 2009-02-02
> **malspa said:**
> Everyone on this forum is not a power user.

It seems ridiculous to disable everything that someone might accidentally hit.  There have been good suggestions presented here that do not include completely disabling this key combo by default.  It seems to me that a simple pop-up window ("You are about to exit the desktop.  You will lose any unsaved data.  Do you wish to continue?  Yes or No.") would be sufficient.  Or having to hold the key combo for two seconds.  Or give us some kind of choice at installation time.  There are probably other solutions that would make everyone happy, but instead, somebody makes the decision to completely disable it, which satisfies only a small percentage of users?  This key combo is one something that's been common to Linux systems for how long?  This decision shows a lack of common sense.I couldn't agree more. While Ubuntu for sure is a very userfriendly distro, it must not be an idiot-proof distro because a) this isn't possible and b) it isn't necessary.

I say it again: Put some README on the desktop, or maybe let it pop in automatically, that explains the most common and most useful keyboard shortcuts. What's the problem in giving users a CHOICE (and let them learn something new)?

---

### Post by scaine on 2009-02-02
Yep.  Still reading this thread.  :o

It's been going for so long, I've gone full circle.  I now agree that this is a good decision if Ubuntu (or, in this case since it's an X decision, Linux) is going to appeal to the masses.  A key combo that can destroy everything?  Too risky.  The various people I've observed who I've given Ubuntu to - they actually look for reasons not to like it.  Finding CTRL-ALT-BS would be too easy for them.

Power users bemoaning the fact it's disabled?  Then turn it on.  They'll even provide a nice GUI for you.  Let's face it, that's far better than the usual "abstract and undocumented gconf key".

As for the "holding for x seconds" or "asking for confirmation" ideas - I doubt they'd work, since the only times I've had to use C-A-BS, the session is usually hard locked and unresponsive.

Big thanks to the poster who mentioned ALT-SYSREQ-K though.  Not much point in moaning about taking CTRL-ALT-BS away when you have an alternative already available...

---

### Post by mavar on 2009-02-03
I would support this. The reason is this - if someone is a power user, it would be a lot simpler for that user to disable this feature than for someone who is a basic user to enable this feature.

Considering that one would want to do a Ctrl+Alt+BkSpc when a session hangs, how would a dialog asking for confirmation work ? (May be I am wrong)

I definitely understand the need for this feature after seeing someone post about keyboards on small laptops and how one might hit Ctrl+Alt+BkSpc instead of Ctrl+Alt+Enter.

I would definitely expect an option to turn back the Ctrl+Alt+BkSpc combo though.

---

### Post by magnus0 on 2009-02-03
> **MacUntu said:**
> I'm sure you can re-enable it whenever you want, so it's no big deal. A common desktop user simply doesn't need to restart X (in fact doing it accidently can cause data loss, which pi**es me more off than having to re-enable it by hand) so I advocate this decision. [OT: Is this what you say when you support sth.?]

But the common desktop user just resets his computer, when he gets into trouble and that can cause more data loss, than a simple X restart.

---

### Post by cardinals_fan on 2009-02-03
> **scaine said:**
> 
It's been going for so long, I've gone full circle.  I now agree that this is a good decision if Ubuntu (or, in this case since it's an X decision, Linux) is going to appeal to the masses.  A key combo that can destroy everything?  Too risky.  The various people I've observed who I've given Ubuntu to - they actually look for reasons not to like it.  Finding CTRL-ALT-BS would be too easy for them.

If they "look for reasons not to like it", that would generally mean that they don't actually want to use it and would have a better experience if allowed to find it of their own accord.  But that's for another thread.

Hard rebooting is a whole lot more destructive than killing X.

---

### Post by danbuter on 2009-02-03
I strongly disagree with turning off CAB. For one thing, if a _standard_ linux technique does not work in Ubuntu, but does in every other distro, guess what people will think of Ubuntu? It won't be anything nice. And I'll agree with them for once.

---

### Post by MacUntu on 2009-02-03
> **malspa said:**
> Everyone on this forum is not a power user.

You don't need to be power user to click on a checkbox. Besides, why would someone incapable of adding an option to xorg.conf read or post in "Jaunty Jackalope Testing and Discussion"?

From those 561 ppl that voted for No, 561 will be able to change the situation in a jiffy. Ppl spent more time complaining than the actual change would take. It is hilarious.

> **danbuter said:**
> if a _standard_ linux technique

Standards change.

---

### Post by ronacc on 2009-02-03
> **MacUntu said:**
> You don't need to be power user to click on a checkbox. Besides, why would someone incapable of adding an option to xorg.conf read or post in "Jaunty Jackalope Testing and Discussion"?

From those 561 ppl that voted for No, 561 will be able to change the situation in a jiffy. Ppl spent more time complaining than the actual change would take. It is hilarious.



Standards change.

I believe you misquoted malspa , he was not implying that only powerusers could undo this change , he was I believe saying that the 86% of us that oppose it are not all powerusers. The outcry against this change is as much against the idea of "protecting us from ourselves" as it is this one specific item ( which is not the first). If I wanted to be "protected" I'd buy an APPLE .  And yes standards change but the changes should be for the better .

---

### Post by MacUntu on 2009-02-03
> **ronacc said:**
> better

Better for whome? Does an average user need this key combo (talking about stable releases)? 

This poll IS biased and for that reason worthless. A better poll would have been: "Does X lock up often enough in stable releases to justify the dangerous key combo being enabled by default?"

---

### Post by jerome1232 on 2009-02-04
I still say having to hit CAB twice in rapid succession (like a double click on the mouse) would make both camps happy. 

No one is going to trigger that on accident.

---

### Post by novafluxx on 2009-02-04
Who hits CTRL+ALT+BACKSPACE on accident? Seriously - I'm not being smart - just REALLY curious as to what you're doing that you accidentally hit that.;)

---

### Post by Mr. Picklesworth on 2009-02-04
> **novafluxx said:**
> Who hits CTRL+ALT+BACKSPACE on accident? Seriously - I'm not being smart - just REALLY curious as to what you're doing that you accidentally hit that.;)

Okay, here's a way I've triggered it. (Disclaimer: I know what Ctrl + Alt + Backspace does).
I know that text can be selected using the arrow keys while holding Shift. I also know that the carot will jump to the next word if I am holding Ctrl. I wanted to erase some blocks of text, so held Shift and Ctrl while backspacing the selected text.
Oh wait a minute. No no no!!!
Session not just logged out, but entirely eradicated. What I had been working on became zilch.

*That* Is Stupid.

It saddens me whenever people go on about "OMG they're dumbing it down!"
That's the whole intent of Ubuntu; to be user friendly. Being user friendly involves rounded corners, friendly explanations and the removal of little red buttons that may eradicate data. (Big ones behind covers are okay). It isn't to limit functionality so much as to enhance it. We want users to be able to pick up Ubuntu and explore it, knowing that if they are putting their data at risk they will know. That they can fiddle, tinker and have fun with the operating systemand experience only positive results. We want it to be a positive and rewarding experience so that people feel empowered to learn, and eventually comfortable to use their own computers instead of needing to enlist the help of expensive computer technicians.

As my above example shows, the presence of the Ctrl Alt Backspace shortcut is completely contrary to that because it can be triggered when a user is exploring keyboard interaction. If that happens to a new user ONCE, he will not feel comfortable tinkering with Ubuntu again.

Further, what is stopping an application from wanting Ctrl Alt Backspace as a shortcut? For example, what about something in Wine, or developed with another distro in mind that has the function disabled already? Great, now we are REALLY screwing people up because xorg zapping itself is implemented at a low enough level that it takes precedence over any child processes.

Finally, I think this should be clarified. It's my understanding that zapping disabled by default was an upstream change in the latest xorg - not in Ubuntu specifically.


It's a good argument that zapping X is a better fix than restarting the computer. Hopefully you guys can figure out the superior kernel-level shortcut with SysRQ (the key designed to go untouched!). I agree it would be cool if xorg could reliably only zap itself if a process in the session doesn't catch the key event. (For example, Ubuntu could have a little daemon that catches the X zapping key combo and gives a popup message when it is pressed).

---

### Post by Circus-Killer on 2009-02-04
you know, there was a day when pressing ctrl-alt-delete just restarted your pc, right there and then, no shutdown no nothing.

now when you in an OS and press ctrl-alt-delete it will in most cases bring up a prompt to the effect of "are you sure you want to shutdown" or it gives the options to reboot,shutdown,etc.

so why not just do something like that. when you push ctrl-alt-backspace it asks "are you sure you want to restart x". just a thought.

---

### Post by OutOfReach on 2009-02-04
> **Circus-Killer said:**
> you know, there was a day when pressing ctrl-alt-delete just restarted your pc, right there and then, no shutdown no nothing.

now when you in an OS and press ctrl-alt-delete it will in most cases bring up a prompt to the effect of "are you sure you want to shutdown" or it gives the options to reboot,shutdown,etc.

so why not just do something like that. when you push ctrl-alt-backspace it asks "are you sure you want to restart x". just a thought.
But what if the X server if frozen and nothing can be displayed? This is what I had thought at first, to bring up a dialog, but then I thought deeper and realized that this would be useless if X was completely unresponsive.

> **novafluxx said:**
> Who hits CTRL+ALT+BACKSPACE on accident? Seriously - I'm not being smart - just REALLY curious as to what you're doing that you accidentally hit that.;)
I've hit it several times, most of the time because I miss a key, such as the del key, and accidentally press Backspace.

> **jerome1232 said:**
> I still say having to hit CAB twice in rapid succession (like a double click on the mouse) would make both camps happy. 

No one is going to trigger that on accident.
I completely am in agreement with that, that will certainly reduce the amount of accidents.

---

### Post by jerome1232 on 2009-02-04
> **Mr. Picklesworth said:**
> Okay, here's a way I've triggered it. (Disclaimer: I know what Ctrl + Alt + Backspace does).
I know that text can be selected using the arrow keys while holding Shift. I also know that the carot will jump to the next word if I am holding Ctrl. I wanted to erase some blocks of text, so held Shift and Ctrl while backspacing the selected text.
Oh wait a minute. No no no!!!
Session not just logged out, but entirely eradicated. What I had been working on became zilch.

*That* Is Stupid.


Except that Shift+Ctrl+Backspace won't restart your X session, Ctrl+Alt+Backspace will. ;)

--edit-- that may have come off as rude so I added a winky face so it didn't sound rude

---

### Post by Mr. Picklesworth on 2009-02-04
Oops, thanks Jerome. I forget what I was doing then :P
It was something along those lines and I definitely did it. Maybe it involved a terminal...

My mash of thoughts about explorability and user friendliness still holds true, I hope!

---

### Post by Starks on 2009-02-04
If you guys can find me a REISUB-esque command that works on Dell Inspirons, I'll be willing to forgive the removal of C-A-B for killing X.

---

### Post by scaine on 2009-02-04
*sob*

Well, it's official.  The thread is now so big, no-one is reading it from the start and are now, instead (quite understandably) posting the same stuff that was posted in the first hundred or so entries.  And then those get replied again.  And again.  And then again.

Trying to remain neutral, the main things to remember seem to be :

1. This is not an Ubuntu decision - it's XORG and will likely be in every distribution in the near future.  OpenSUSE has apparently implemented it as a double-tap of CTRL-ALT-BS, while Ubuntu will provide a GUI mechanism to turn it back on.  Even if they don't, you can STILL turn it back on using an insultingly simple "DONTZAP = NO" type line in your xorg.conf.

2. You can still use ALT-SYSRQ-K to end your X session. (unless you use a specific model of Dell laptop apparently, which has trouble recognising SYSRQ)

3. You can't pop up confirmation dialogs because the only time you should ever use this is when the session is hung and can't be used anyway.

4. There are preferable ways to end your X session anyway, the most cited being to CTRL-ALT-F1 to another terminal, login and issue a "killall xorg" type command.

5. The poll is horribly biased because the people who post in this forum (Jaunty Dev) are the people most likely to want it kept.

6. It is REALLY easy to hit CTRL-ALT-BS by accident.  The most common case is when you use a lot of VMware machines and you toggle full-screen mode with CTRL-ALT-ENTER.  Having used an EEE701 for about a year, I know from experience that's it's possible to hit that combo, although I've never felt strongly enough about doing so to complain to the X developers...

7. Please let this thread die.  Or post a meaningful bug on Xorg and link to it here so that we can complain in an appropriate place.

---

### Post by cardinals_fan on 2009-02-04
> **jerome1232 said:**
> i still say having to hit cab twice in rapid succession (like a double click on the mouse) would make both camps happy. 

No one is going to trigger that on accident.
+1

---

### Post by gspat on 2009-02-04
> No one is going to trigger that on accident.

yes they will... usually either:

1). while banging random keys in frustration at something (anything) not working they way they figure it will.

2). while trying to enter a keyboard shortcut

Murphy's law says it will happen.

I can't believe this thread has gone on this long...

---

### Post by DougieFresh4U on 2009-02-04
> **OutOfReach said:**
> 
[B]I've hit it several times, most of the time because I miss a key, such as the del key, and accidentally press Backspace.
[/B]



Users have got their hands flying over the keyboard so fast. Sorry to be a smart a** but if users are gonna be 'speed' typing, why should others suffer for** their** mistakes made while flying around the keyboard and accidentally hitting the wrong keys

**gspat**[B]
I can't believe this thread has gone on this long...[/B]

Amen, I wish they would close this thread as the end result is gonna be that it stays as it is, disabled

---

### Post by Kow on 2009-02-04
How in the hell do you accidentally hold down ctrl, then alt.. and then backspace?

---

### Post by ronacc on 2009-02-04
heck this thread isn't long . do a search on poll and you will see one that has over 40,000 replies  and many that go over 1,000 .

---

### Post by Starks on 2009-02-04
How would I go about mapping sysrq as being equal to fn+printscr?

---

### Post by jerome1232 on 2009-02-05
> **gspat said:**
> yes they will... usually either:

1). while banging random keys in frustration at something (anything) not working they way they figure it will.

2). while trying to enter a keyboard shortcut

Murphy's law says it will happen.

I can't believe this thread has gone on this long...


I equate your way of thinking to putting the power button behind a closed locking front bezel so somebody doesn't accidentally open the front bezel and accidentally nudge the power button. Then saying power users can remove the front bezel so why shouldn't we like having all these extra safety features.

---

### Post by Mr. Picklesworth on 2009-02-05
> **jerome1232 said:**
> I equate your way of thinking to putting the power button behind a closed locking front bezel so somebody doesn't accidentally open the front bezel and accidentally nudge the power button. Then saying power users can remove the front bezel so why shouldn't we like having all these extra safety features.

Except that modifying an existing configuration file to say False instead of True has absolutely no impact on performance, coolness or even aesthetics?

Besides, having a cover over a power switch is entirely sensible. For example, a big server that absolutely should not be shut down would do well having such a cover so that the pesky cleaning staff doesn't mess with it. It should indeed be attached by default, becuase that way we can be sure there is a cover that fits well. If somebody really cares that much about not having a cover he can buy a different case. However, that case happens to exist for people who benefit from such covers. If a person is really so adamant about it (he is too l337 for safety measures) he should accept that he is in the minority of owners of that case and accept that his weird preference is not the appropriate direction for its target audience of IT firms with lame cleaning staffs.

---

### Post by Gina on 2009-02-06
The answer to cleaning staff switching off servers was found many decades ago when I was in IT.  Use a key switch for the power (and reset is fitted).  All our computer systems had this feature.  There is no reason why a PC case shouldn't be fitted with a key switch for the power where power security is needed.  (Together with an UPS, of course).

---

### Post by plun on 2009-02-06
> **Gina said:**
> The answer to cleaning staff switching off servers was found many decades ago when I was in IT.  Use a key switch for the power (and reset is fitted).  All our computer systems had this feature.  There is no reason why a PC case shouldn't be fitted with a key switch for the power where power security is needed.  (Together with an UPS, of course).

Well... for a modern PC you must hold the power button in x seconds.

All other actions can be defined with software....  Windows and Apple.


Nevertheless.. This thread is now a waste of time and shame for Ubuntu.

The voting result is 100% clear what the community wants and the devs and Ubuntu members must accept this wish.

The same as for throwing out the brownish disaster so called Art-work.

---

### Post by ratmandall on 2009-02-06
HELL NO!
It's very useful, heh it's the only thing that managed to kill a program I wrote, that trapped all keyboard/mouse input to it's own window in an infinite loop. >_<

---

### Post by MacUntu on 2009-02-06
> **plun said:**
> The voting result is 100% clear what the community wants

Members that posted in the last 30 days: 65.328

Members that voted in this poll: 685

A very special 1% of the active ubuntuforums community voted. 

That's not even close to "100% clear what *the community* wants". ;)

---

### Post by taavikko on 2009-02-06
> **MacUntu said:**
> Members that posted in the last 30 days: 65.328

Members that voted in this poll: 685

A very special 1% of the active ubuntuforums community voted. 

That's not even close to "100% clear what *the community* want". ;)

I agree, and for the semantic side, the question is IMHO 
tricky. Correct form would have been something like
"Should C-A-B be disabled by default?"

I for example voted YES, since there's other ways of killing borked
apps and such.
SUSE's implementation of C-A-B-B should be investigated further.

My understanding is that upstream is behind this change, and ubuntu should honor their decision.

---

### Post by z0mbie on 2009-02-06
It's like touching a hot pot of food over the fire. You don't do it again. You don't remove fire as utility in your daily life because of it.

Debian here I come.

---

### Post by ronacc on 2009-02-06
> **MacUntu said:**
> Members that posted in the last 30 days: 65.328

Members that voted in this poll: 685

A very special 1% of the active ubuntuforums community voted. 

That's not even close to "100% clear what *the community* wants". ;)

so post the poll in the general area of the forums and lets see what the other 64,643 think .

---

### Post by dro0g on 2009-02-06
Put me down in the "don't disable unless there's an easy way to turn it back on" column. I use several different docking stations/monitor combinations with my laptop and CTRL-ALT-BACKSPACE is often necessary to get the display up. 

If monitor auto-detection was working a bit better it probably wouldn't be necessary for me (not that I'm going to say anything bad about xrandr since it's light-years better than having to deal with a shellscript to switch out X configs when switching from docked to undocked)

---

### Post by plun on 2009-02-06
> **MacUntu said:**
> Members that posted in the last 30 days: 65.328

Members that voted in this poll: 685

A very special 1% of the active ubuntuforums community voted. 

That's not even close to "100% clear what *the community* wants". ;)


Well....;)

I find it rather clear what the community wants and its a major problem if developers doesn't listen to a community.

But, overall this is a microscopic issue, this can just happen with open source...  "The Debian way" with endless discussions about nothing or even worse flame wars about nothing...

---

### Post by bruce89 on 2009-02-06
> **taavikko said:**
> My understanding is that upstream is behind this change, and ubuntu should honor their decision.

> **z0mbie said:**
> Debian here I come.

Yes, this is upstream. Debian won't be any different (in the future).

---

### Post by nickpick on 2009-02-06
Reassign it to a different combination, but do not disable the function by default. There should be an easy way out.

---

### Post by Ubnuut on 2009-02-06
Would be a pity if it gets disabled. It is very handy to have it ready to restart x if the desktop hangs. Has helped me a lot in the past cause I like test new software which is sometimes unstable. It is one of the nice features of Linux I always show to newbies... I call it the reserve shute of Linux... Now would you like to jump from a plane with your reserve shute disabled ;)

---

### Post by svaens on 2009-02-06
i'm a stupid newbie. 
but hell.... i'm not that stupid that I need to be served a dumbed down linux simply because some people complained about hitting the wrong keys!
I bet they learnt quick smart not to go hitting random keys unless they want random things to happen (if they haven't learnt the system yet). There's no way you can hit ctrl-alt-backspace accidentally.

---

### Post by techdude3177 on 2009-02-06
> **bruce89 said:**
> Yes, this is upstream. Debian won't be any different (in the future).

Guess ill be using my Gentoo distro much more! lol

---

### Post by Playa1313 on 2009-02-06
Abolutely not!  I use ctrl-alt-backspace to get me out of sticky situations.  I would not want to call this Linux without ctrl-alt-backspace.  Wow.

---

### Post by Starks on 2009-02-07
Here's something fascinating.

My hybrid PrntScrn/SysRq acts as a distinct SysRq key, rather than a Fn+PrntScrn key in terminal mode.

---

### Post by Tom Mann on 2009-02-07
It's something that can be enabled for the more experienced user, so I'm going to say yes to this. What concerns me more, is that Gnome disabled CTRL_ALT_ESC as an xkill shortcut.

---

### Post by svaens on 2009-02-07
quick question. 
the ctrl alt esc shortcut you mention. What did that do differently to the ctrl alt backspace?

---

### Post by Tom Mann on 2009-02-07
It fired up xkill, which turns your mouse cursor into an X (or a skull and crossbones), you'd click on an offending hung app and X would terminate it.

I'm aware it still works in KDE, not sure about XFCE or any other Window Managers.

---

### Post by svaens on 2009-02-07
a geez..... that would have come in handy a few times. 
I wonder. That deskpane applet "force a misbehaving application to quit" can't be using xkill. Does it?  Sometimes it just plain doesn't work. Whereas I remember xkill being much more effective than that.

---

### Post by lisati on 2009-02-07
> **agim said:**
> As long as you can enable, I guess I understand. But I am against this, when you need to restart, you may not be able to enable the option to use it.
I hope it doesn't get changed, how the hell can you accidentally hit all three at once?

I agree: although I haven't had that much call to restart anything when things went wrong with Ubuntu, I too don't see how it would be possible to accidentally do the CTRL-ALT-BACKSPACE thing. Bumping the touchpad on a laptop is more likely.

---

### Post by lisati on 2009-02-07
> **Starks said:**
> Here's something fascinating.

My hybrid PrntScrn/SysRq acts as a distinct SysRq key, rather than a Fn+PrntScrn key in terminal mode.

I've always wondered if anything used the SysRq key.....

---

### Post by celafon on 2009-02-08
I've voted to be not disabled, however if there is a an easy way to re-enable it - it could be disabled by default - no problem. I think if 90% of the users do not use it (nor have they an idea about it) - I am OK to do 'open settings / check option / close' in order to restore it.

BTW - most of the time I am not using this at all but when I am starting to tinker with settings it will eventually happen that nothing else would work.

Another thing - if the ctrl-alt-bkspace works, the ctrl-alt-f1 works as well, so what is the big deal - you will just need to kill it manually from console...

---

### Post by Paqman on 2009-02-08
I'm really against this. Ctrl-Alt-Backspace is an incredibly useful thing.

The only real risk of accidentally hitting it comes (presumably) from Compiz's use of Ctrl-Alt. I'd rather they changed the Compiz default hotkeys than disabled a useful feature.

---

### Post by amano on 2009-02-08
If it is useful to you, you can enable it easily. But it isn't useful for those who don't know about it. Those have to be protected from severe data loss.

---

### Post by Frak on 2009-02-08
> **amano said:**
> If it is useful to you, you can enable it easily. But it isn't useful for those who don't know about it. Those have to be protected from severe data loss.
Why disable it when you could just change the combination to make it harder to accidentally trigger. If it's hard to accidentally trigger, yet easy to still work on purpose, then why disable it?

Plus, IIRC, this was already removed from upstream.

---

### Post by ronacc on 2009-02-08
If you disable it at kernel level and then re-enable it externaly (ie. in xorg ) it may not work when you need it . right now that exact situation exists , compiz/nvidia/xorg  are not playing nice right now and even though I have it enabled in xorg it does not work because the xserver is frozen , the key board still works because I can ctrl>alt>F2 ( not F1 thats blackscreen too) . this illustrates why " let them that wants it enable it" is unsatisfactory .Also severe data loss is being a bit extreme , yes you would lose unsaved work but that should be a minor thing if you occasionaly save your work while its in progress , and the odds of hitting crtl>alt>bkspc at the exact instant of a disk write is very small, linux is not windows , it doesnt leave open files all over the place .

---

### Post by ratmandall on 2009-02-09
```
Yes 13.48%
No  86.52%
```
I'm guessing this isn't going ahead, ay?

---

### Post by jrusso2 on 2009-02-09
> **ratmandall said:**
> ```
Yes 13.48%
No  86.52%
```
I'm guessing this isn't going ahead, ay?

Your wrong its already decided it is.  Its not bad enough this encourages bad habits like not saving I still can't figure out how you can hold three keys by accident.

---

### Post by dburnett77 on 2009-02-09
Yeah, my Xserver froze, too.  I didn't realize they disabled it, thought it was a glitch.  Or possible some nose-to-the-window realizing he could hack<<JOKE>>

Seriously, though, You mean if I wait, the new drivers WILL initialize, and I'll have a desktop.  Huh,

Only seems to happen when I try any packaging of Nvidia drivers that replace nvidia-new.  Weird.  Tell them to quit it...

---

### Post by ratmandall on 2009-02-09
> **jrusso2 said:**
> Your wrong its already decided it is.  Its not bad enough this encourages bad habits like not saving I still can't figure out how you can hold three keys by accident.

F*** that I'm not using Jaunty then.

---

### Post by scaine on 2009-02-09
This is UPSTREAM - everyone single distro on the planet will be affected by this unless they decide to alter it in every one of their releases till the end of time.  You can still use the other shortcut (unless you're like ronnac and are having a nightmare getting your sysrq key working).

I'll say it again... THIS IS NOT A BIG DEAL.  First, there's an alternative, second you can easily re-enable it and third, it's not Ubuntu's decision, it's Xorgs.  And it's a good one.

---

### Post by Mr. Picklesworth on 2009-02-09
> **ratmandall said:**
> F*** that I'm not using Jaunty then.

Is that really the difference between a good or a bad operating system? Being able to kill the session with a keypress? Actually using said session, productivity, and usability don't filter in to the equation?

You can crash Windows by inserting a CD, sometimes :P

---

### Post by jrusso2 on 2009-02-09
I like my Linux to work in a standard way even the not enabled root was a problem for me until I got used to working that way.  Why does the experienced long time user have to adjust for the newbie who will be soon gone anyway?

---

### Post by ganoderma on 2009-02-09
I have my ubuntu machine as one of three plugged into a switch that leads to a router.  To access the internet, I have to turn on the power supply to the switch. Very often, when I boot up, I forget to do so.  If I'm in ubuntu, and find I haven't turned the switch on, so I have no internet access, it's much easier to turn on the power to the switch, and then press ctrl-alt-backspace. When I restart the XServer, my machine usually picks up that there is power to the switch, and the internet is accessible.  My other alternative is to turn the power to the switch on and reboot, which is hard on the hard drive, and takes considerably more time.  Please, if you are going to disable CTRL-ALT-BACKSPACE by default (which I think is wrong), DO include some mechanism, possibly on the system preferences bar, that allows me to override that disabling!  Thank You.

ganoderma

---

### Post by DougieFresh4U on 2009-02-09
> **jrusso2 said:**
>   Why does the experienced long time user have to adjust for the newbie who will be soon gone anyway?

?? [-X

Can't wait to see some of the responses to a comment like that.

---

### Post by medeshago on 2009-02-09
I never pressed that combination accidentally when I was just learning how to use Ubuntu, neither my friends. How many complaints have been about accidentally pressing ctrl+alt+backspace? If you have data to back the idea of removing an useful shortcut I would like to see it, but if you don't I don't get the point of removing it. It's useful to many and it goes unnoticed to the ones that are supposedly affected, so why would you remove it?

---

### Post by DougieFresh4U on 2009-02-10
> **medeshago said:**
> I never pressed that combination accidentally when I was just learning how to use Ubuntu, neither my friends. How many complaints have been about accidentally pressing ctrl+alt+backspace? If you have data to back the idea of removing an useful shortcut I would like to see it, but if you don't I don't get the point of removing it. It's useful to many and it goes unnoticed to the ones that are supposedly affected, so why would you remove it?

**The following is from my post (#188)) in this thread.**

> **DougieFresh4U said:**
> It was stated that there have been several complaints of hitting by accident. I have been reading the forum here for about 3 years now and I do not recall reading complaints of users hitting the combo by mistake. **Where are they complaining to and can some one show me some examples of said complaints?**

I am still waiting for some sort of examples of the complaint. Please show me some threads from the last 3 years where they start out some thing like[B]

"Help, I hit Ctr+Alt+Backspace and blah blah blah happened.  What do I do now?[/B]

What ever it may be, it's not coming back, therefore, thread should be closed!

---

### Post by Mr. Picklesworth on 2009-02-10
Err, something else I think people should know is that X already is reset when you log out. For ganoderma, for example, simply loging out would be cleaner and have the same outcome as Ctrl Alt Backspace within a session.

Further, I should point out that the X server has absolutely nothing to do with networking so the belief that resetting it makes Ubuntu talk to the switch is probably based entirely on circumstantial evidence.

Clearly, the presence of this hotkey has done more harm than good if people are developing these bad habits.

---

### Post by ronacc on 2009-02-10
Why is it a "bad habit" if it works ? I assume of course that if you are doing it deliberately you are aware of possible negative effects . I often CAB as a 1st step in troubleshooting some "glitch" and often that by itself puts things right, I supose you believe that we should only set our tables with forks and spoons sice knives are too dangerous ? opps leave out the forks they can deliver a nasty stab .

---

### Post by MacUntu on 2009-02-10
Hell yeah! 666 nos. 

Angels say yes! :D

---

### Post by tigon5 on 2009-02-10
my vote was for no, but on reflection I can see why.  As long as "enable ctrl-alt-backspace ubuntu" throws up the solution on the first link on Google, then I'm all for it.

---

### Post by DougieFresh4U on 2009-02-10
> **tigon5 said:**
> my vote was for no, but on reflection I can see why.  As long as "enable ctrl-alt-backspace ubuntu" throws up the solution on the first link on Google, then I'm all for it.

And when your screen/X is 'locked up because of some game or some thing you were doing, what good is Google to you then?

---

### Post by MacUntu on 2009-02-10
> **DougieFresh4U said:**
> And when your screen/X is 'locked up because of some game or some thing you were doing, what good is Google to you then?

Didn't your computer come with a reset or power button? If you know you'll need the key combo then activate it.

---

### Post by Wolki on 2009-02-10
> **DougieFresh4U said:**
> And when your screen/X is 'locked up because of some game or some thing you were doing, what good is Google to you then?

You learn how to kill a misbehaving process and kill just that one instead of everything you have running. And if you don't know how to do that yet, reset and find out.

This thread makes me think many people just switched from rebooting in windows to restarting X as the main way to solve problems. But it's not a solution, it's a (bad) workaround.

> 
Why does the experienced long time user have to adjust for the newbie who will be soon gone anyway? 

Because it benefits the experienced user, working quickly with complicated shortcuts on a functioning system the most.

---

### Post by Gina on 2009-02-10
I was in Intrepid yesterday and was downloading a PDF file in Firefox when I lost both panels so no way to recover than the keyboard - I was glad of CAB to return me to the login screen rather than using a cold boot - that cured the problem.  Why Firefox had a funny moment I don't know but CAB saved my time and having to get up to operate the power button.

---

### Post by karlmp on 2009-02-10
if jaunty is going to be faster then a cold boot is not going to be a problem

---

### Post by philinux on 2009-02-10
I've had to use reisub to get back to normal where CAB would probably have done the trick. And ctrl alt F1 got me nowhere. How do you enable it in Jaunty.

---

### Post by karlmp on 2009-02-10
re-enable it by setting the DontZap xorg.conf option to False

---

### Post by karlmp on 2009-02-10
[https://wiki.ubuntu.com/XorgCtrlAltBackspace](https://wiki.ubuntu.com/XorgCtrlAltBackspace)

---

### Post by SpenceMakesSense on 2009-02-10
get rid of it? Why?? Whenver I run into a problem where my computer locks up or i hit some strange error that keeps me from doing a current task pressing that saves the day. Its a great alternative to restarting in windows.

And it also helps with my lazyiness when signing out :D

---

### Post by philinux on 2009-02-10
Thanks karlmp. And I'd love to know how many people complained about this.

---

### Post by karlmp on 2009-02-10
9.10 is going to be faster than jaunty so i voted no for "no yet":neutral:

---

### Post by nyarnon on 2009-02-10
[rant]
Was this idea Bill Gates inspired? Microsoft inside. Jeez if there are some people have trouble with it let THEM disable it. There absolutely no logic in disabling it white the MS logic that anyone who doesn't want it disabled can enable it. Propriatory software uses this logic to sell. As Ubuntu isn't soled the isue is obsolete. Keep your F&%$g hand of the CAB.
[/rant]

Pretty please?[-X

---

### Post by wiscalico on 2009-02-10
Thank god it is gone :)

I'm a heavy user of keyboard shortcuts... 
lost work a few times because of it, and thats a few times to many.

I belive people knowing the shortcut and wanting to use it can enable it faster than someone not knowing its there uses to figure out what the hell just happend to his/her system and where did all the work go.

Just a question: The Ctrl+Alt+Backspace is IMO a workaround for X misbehaving... will X ever work good enough for this to be disabled by default?

---

### Post by techdude3177 on 2009-02-10
I use keyboard short cuts a lot and never accidentally hit this combo before.

---

### Post by DougieFresh4U on 2009-02-10
> **MacUntu said:**
> Didn't your computer come with a reset or power button? If you know you'll need the key combo then activate it.

Oh, and hitting the reset button is so 'kind' to your hard drive? I think not!
Actually, I wish this thread would close as it's 'pointless' and gonna go 'no where'

> **Gina said:**
> I was in Intrepid yesterday and was downloading a PDF file in Firefox when I lost both panels so no way to recover than the keyboard - I was glad of CAB to return me to the login screen rather than using a cold boot - that cured the problem.  Why Firefox had a funny moment I don't know but CAB saved my time and having to get up to operate the power button.
 +1

---

### Post by karlmp on 2009-02-10
[quote=DougieFresh4U]Oh, and hitting the reset button is so 'kind' to your hard drive? I think not![/quote]

use REISUB [http://lifehacker.com/software/linux-tip/gently-restart-a-frozen-system-298891.php](http://lifehacker.com/software/linux-tip/gently-restart-a-frozen-system-298891.php)

---

### Post by ronacc on 2009-02-10
as I stated before  re-enableing it via xorg is NOT the same as having it enabled at kernel level , let those who WANT it disabled disable it . the cure for ignorance is not protectionism it is education .

how about a list of default shortcuts to educate newbes (and some "old hands" too .

---

### Post by jrusso2 on 2009-02-10
> **wiscalico said:**
> Thank god it is gone :)

I'm a heavy user of keyboard shortcuts... 
lost work a few times because of it, and thats a few times to many.

I belive people knowing the shortcut and wanting to use it can enable it faster than someone not knowing its there uses to figure out what the hell just happend to his/her system and where did all the work go.

Just a question: The Ctrl+Alt+Backspace is IMO a workaround for X misbehaving... will X ever work good enough for this to be disabled by default?

Have you not heard to save early save often?  You should always save your work.

---

### Post by ratmandall on 2009-02-11
> **Wolki said:**
> You learn how to kill a misbehaving process and kill just that one instead of everything you have running.

How so?

---

### Post by scaine on 2009-02-11
Hey, Ronnac, I read your earlier post about this being disabled at the kernel level and how that's not the same as re-enabling it at the xorg level.

That made little sense to me - not having a go at you, just ignorance on my part - I thought that this was an xorg decision to disable CAB, so why are you talking about kernel level issues?  If you've got a source/link, can you point me in the right direction?

And assuming that there is a realistic difference, can you (or anyone) elaborate on what kind of lock might be so severe that an xorg-only-enabled CAB wouldn't work?

Finally, does any of this have any effect on ALT-SYSRQ-K, which I used yesterday for a hard-locked gnome system on Jaunty when pulseaudio had a hickup?  That worked well, despite CAB being disabled - it looked identical in fact.  So, is ALT-SYSRQ-K also "crippled" the way you say that CAB is when it's disabled at kernel?

---

### Post by ronacc on 2009-02-11
@ scaine sorry it took awhile to get back , I am looking for a reference as to where it is disabled ,I was under the impression that it was a kernel thing but have not yet found the reference , I do know that in the recent problem with xorg/compiz/nvidia ctrl>alt>bkspc did not work even though I had it re-enabled (and tested) in corg.conf . other shortcuts did still work allowing me to get to a term and kill X that way . opps it just got me again , I rebooted my jaunty box after an update and went to low graphics mode , my "normal" procedure in this situation is to kill X at the lowgraphics warning and correct the problem from term , cab did not work in this situation either so again whatever the mechanism , re-enabling it in xorg.conf is not the same as having it not disabled in the first place .

---

### Post by scaine on 2009-02-11
Right, gotcha.  But I wonder if your problems with CAB in these instances are really CAB itself, or whether your xorg.conf has vanished/become corrupt, so you've "reverted" back to DontZap?

I hope you can get your SYSRQ key working, then hopefully you won't feel any pain from this decision at all.

I really believe that once the ALT-SYSRQ-K shortcut becomes a little better known, this will become a 300+ post thread about nothing.

Seeing how vehemently people are defending their "right" to use this shortcut though, I'm pretty sure someone will come up with a reason why ALT-SYSRQ-K isn't as "good" as CAB.  <sigh>

I'm doing a lot of sighing on this thread.  Not a good sign.  :)

---

### Post by ronacc on 2009-02-11
I never had a problem with my sysreq key , that was someone else . It is not that my xorg.conf is reverting ,I checked . apearently when X fails to start completely the settings in xorg,conf don't take effect .

---

### Post by ronacc on 2009-02-11
I finaly found a reference and it is not in the kernel but In X that this is enabled by default . I stand corrected .

---

### Post by scaine on 2009-02-11
Well that's good news, I suppose.  At least you know that technically "DONTZAP FALSE" *should* work...  although you've already found a fringe case where it won't.  I'd be interested to here if the ALT-SYSRQ-K shortcut works in those cases.

Coulda sworn it was you with the Dell who couldn't get his SYSRQ key working.  I'm going senile.  Well, that, or the fact it's nearly 1am here in Scotland!

I'm off to bed...  :)

---

### Post by DougieFresh4U on 2009-02-11
> **scaine said:**
> 
Coulda sworn it was you with the Dell who couldn't get his SYSRQ key working.  I'm going senile.  Well, that, or the fact it's nearly 1am here in Scotland!

I'm off to bed...  :)

I had made a comment in this thread that my 'SYSRQ' has NEVER worked for me. and that was  a DELL with Intel motherboard.
I just had an AMD built yesterday and getting ready to fire up (Jaunty).
 (Got Intrepid going GREAT!!)

---

### Post by ronacc on 2009-02-11
I know that dontzap false or dontzap --disable work in normal circumstances , the first thing I did after addding that to my xorg.conf weeks ago was reboot and try it . the problem is "normal circumstances" , the time you are likely to need it is when circumstances are not normal , after all there are few times that you need to kill an X that is working normaly .

---

### Post by karlmp on 2009-02-11
ctrl-alt-backspace has NEVER worked for me:!:

if i press ctrl-alt-backspace nothing happens

---

### Post by Chrisj303 on 2009-02-12
This is a terrible idea.

ctrl-alt-backspace is a great shortcut, and the fact that it involves hitting THREE KEYS makes it quite idiot prove as it is.

I have a better idea.

You want to make Ubuntu easier for n00bs? 

Get rid of Xorg.
Sort out PulseAudio.

Have the installer explain what a "root partition" actually is, as well as a "mount point" and "bootloader".

---

### Post by scaine on 2009-02-12
> **Chrisj303 said:**
> 
You want to make Ubuntu easier for n00bs? 


I don't think that's the point of this - the main people who have explained on this thread that they've hit CAB by accident are those using VMware and using CA-Enter to move between fullscreen VMs.  They're probably not noobs.  Maybe I'm wrong though - been a while since I tracked down the original announcment on this.

> **Chrisj303 said:**
> 
Sort out PulseAudio.
Have the installer explain what a "root partition" actually is, as well as a "mount point" and "bootloader".

Yep.  PA is causing some pain.  I've been lucky to never have experienced it, but I read about it plenty.

And the installer - totally yep.  But only if you have a noob choosing "manual" partioning.  Most noobs will probably just choose "Guided".  Or hell, install it from Wubi.

---

### Post by Chrisj303 on 2009-02-12
I also think the installer should lose those "Before/After" diagrams.

They even confuse me (I've been using Ubuntu for 3 years)!

*Many* people using Ubuntu for the first time, will be installing as a dualboot with Windows - so "Manual" is needed. 

This really needs to be made easier for the newbie. Otherwise, they may never even get the opportunity of accidently hitting CTRL-ALT-BACKSPACE by accident!

---

### Post by malspa on 2009-02-12
I used ctrl+alt+backspace the other day.  I was trying to log out of E16 in Mepis, but the normal routine wasn't working.  I can't remember at the moment if what I was clicking on said "quit" or "log out."  I know, something that I've got to fix...

This is about the only situation where I normally use ctrl+alt+backspace, and it doesn't happen often.

I'm looking at this article:  [http://www.thegeekstuff.com/2008/12/safe-reboot-of-linux-using-magic-sysrq-key/](http://www.thegeekstuff.com/2008/12/safe-reboot-of-linux-using-magic-sysrq-key/)

I'm not sure by looking at this which alt+SysRq command would be best for simply getting out and getting back to the log-in screen.  Could someone please let me know?  Sorry for the "stupid question," perhaps the answer is obvious and I'm just missing it.

Also, is the SysRq key normally enabled by default, or not?  I see in Mint Elyssa that my /proc/sys/kernel/sysrq is an empty document -- does that mean that SysRq is not enabled?

This thread has helped me because I never knew about those alt+SysRq commands before -- in fact, had never noticed the SysRq key at all.  But you can count me as one of the so-called "whiners" about the ctrl+alt+backspace combo being disabled, because the work-arounds are starting to seem like a hassle, and I'm sorry, I'm having trouble feeling any sympathy towards the folks who hit the wrong key combo, leading to so many of us being inconvenienced by this change.

---

### Post by aldeby on 2009-02-13
It's ridiculous!

Linux is not enough stable to disable those shortcuts and people accidentally pressing 3 keys at the same time (such as CTRL ALT BKSP) are simply nuts and have to think a bit more before acting.

I have had the chance (and the NEED) to use this keyboart shortcut several times during my Ubuntu experience, last but not least with bugs: 

[https://bugs.launchpad.net/bugs/321311](https://bugs.launchpad.net/bugs/321311)

which is probably being resolved and

[https://bugs.launchpad.net/bugs/181065](https://bugs.launchpad.net/bugs/181065)

which is still NOT FIXED.

In these scenarious this shortcut is VERY USEFUL!

---

### Post by MarblePanther on 2009-02-13
I, for one, am not able to use the SysReq shortcut because I'm on a Dell laptop that requires the fn key to be used.  I'll miss you C-A-B...

---

### Post by Sand &amp; Mercury on 2009-02-14
If they want to disable CTRL-ALT-Backspace they should also disable the CTRL-ALT-F1, F2, F3... F12 keys too. I had more trouble with those.

Personally though it's not a problem for me. sudo dontzap --disable fixed all my woes related to this.

---

### Post by scaine on 2009-02-14
[@aldeby]("http://ubuntuforums.org/member.php?u=309734")
Neither of those two bugs warrant the use of CAB, since you'll kill your entire session by doing so.  You should use CTRL-ALT-F1, login, then issue a "killall gnome-screensaver", then use CTRL-ALT-F7 to get back to your X terminal.  If you prefer the quickness of killing X entirely, then just use ALT-SYSRQ-K.

The SYSRQ key issue is an interesting one for Dell users.  I think there's a way to remap that key to another key on the keyboard, but I don't know how off the top of my head.  I suppose the easiest solution for Dell laptop users in the meantime is just to turn CAB back on again, either using the GUI provided, or the dontzap false option in xorg.conf.

---

### Post by yeaitsdark on 2009-02-14
how does one "accidentally" hit 3 buttons...

---

### Post by scaine on 2009-02-14
It's been mentioned about 4 or 5 times before, but I'll say it again - in VMware, the keyboard shortcut to go fullscreen/revert from fullscreen is CTRL-ALT-ENTER.  In just about every keyboard in existence the enter key is just below backspace.

Worse, on most netbooks, the enter key is the same size as the backspace key.

Besides, accidental CAB is only part of this.  The other part was cleaners doing hygeine checks on server keyboards and borking the session.  And of course the casual malicious user, who perhaps can't get past someone's screensaver so just ends the session with CAB.

---

### Post by uh_Iforgot on 2009-02-14
I really don't see how you could "accidentally" press control-alt-back, especially as pretty much everyone in the world knows control-alt-??? is often a hotkey. They're not even close together.

---

### Post by scaine on 2009-02-14
@uh_Iforgot : You're not big on reading the previous posts in a thread, are you?  Even, like, the one before your own...

:)

---

### Post by philinux on 2009-02-14
Hey guys thanks for this. ALT-SYSRQ-K

I've no need to mod my xorg.conf anymore. For me problem solved.

By the way on my desktop I've had hang ups that could not be resolved any other way, except of course reisub or the power button. E.g. When ctrl alt f1 will not allow a log in and fails.

---

### Post by Mr. Picklesworth on 2009-02-14
> **uh_Iforgot said:**
> I really don't see how you could "accidentally" press control-alt-back, especially as pretty much everyone in the world knows control-alt-??? is often a hotkey. They're not even close together.

Yes, everyone knows Control Alt. Exactly! People use it routinely in image editors, desktop window management operations and the like.
Everyone also knows that Control Alt Delete, for example, gives the user an option before borking his session.

This spec on Launchpad has lots of valid rationale:
[https://wiki.ubuntu.com/XorgCtrlAltBackspace](https://wiki.ubuntu.com/XorgCtrlAltBackspace)

Something unmentioned here: If you don't want to edit xorg or use the GUI in KDE, there is a package you can install which does the same thing. (I forget what it's named, though).

You have a lot of choice over what you install since this is built on open standards and you can modify code if you care *that much* (there's even configuration for it), so _stop trying to paint this as a nasty suppressive act_. Everyone knows that Ubuntu is not forced upon people and that it is not suppressing anyone except *maybe* artificially, so that argument will not take your point very far. In my case it causes a little flag to go up in the back of my head that says "disagree with whatever this lunatic says." I know it's not nice, but it is my general knee-jerk reaction to lunacy.

The bottom line is that This is Not Going To Change. What you *can* do is implement a better solution if you find this one inadequate. Please start new threads, new initiatives, etc. as you do so; this particular babble is NOT productive and is exactly why a free software project like Ubuntu ultimately needs a benevolent dictator.

---

### Post by inportb on 2009-02-14
> **scaine said:**
> Worse, on most netbooks, the enter key is the same size as the backspace key.

On most netbooks, there is another key between the enter key and the backspace key.

> **scaine said:**
> Besides, accidental CAB is only part of this.  The other part was cleaners doing hygeine checks on server keyboards and borking the session.  And of course the casual malicious user, who perhaps can't get past someone's screensaver so just ends the session with CAB.

And what about Alt+SysRQ+K in this case? It's as easy to press.

---

### Post by qamelian on 2009-02-14
> **scaine said:**
> It's been mentioned about 4 or 5 times before, but I'll say it again - in VMware, the keyboard shortcut to go fullscreen/revert from fullscreen is CTRL-ALT-ENTER.  In just about every keyboard in existence the enter key is just below backspace.

Nope, I have 7 laptops in my workshop and in excess of 150 keyboards of many different makes and models. Not one of them has the Enter key right below the Backspace key. They are two rows apart in every case. I've been in IT for more than 20 years and have only rarely seen a keyboard where this was not the case.

---

### Post by Gina on 2009-02-14
I have a Logitech wireless kb/mouse and the enter key is immediately below the backspace key and other keyboards I use are the same.  All my five keyboards including my laptop have the enter key  right below the backspace key.  These keyboards span the years, one being over ten years old.  AFAIK this is standard on British QWERTY PC keyboards.

As for SysReq - my Logitech also doesn't have one!

---

### Post by karlmp on 2009-02-14
the enter key of my laptop is right below the backspace key

---

### Post by qamelian on 2009-02-14
Very strange because every single keyboard I have access to has the backslash - pipe symbol key above the enter key, separating it from the backspace.

---

### Post by Gina on 2009-02-14
All the keyboards I have seen have the backslash/pipe key near the LH bottom corner next to the left shift key - i.e. 2nd row up, 2nd key in.  I wonder if this is a country difference.  I live in England and am talking about English/British keyboards.

---

### Post by ronacc on 2009-02-14
the exact layout of the keyboard should not mater that much , if you are a touch typist the enter (carriage return) is ALWAYS a one key reach rt of the home key (semicolon) for the right little finger with a qwerty layout and if you arent a touch typist shouldnt you be looking where your fingers are going ? on the generic keyboard I am typing right now the enter key is large and L shaped so that it extends into the row above and thus the bkspc is just above the extended portion but still no problem since to hit enter I always reach straight rt to hit it and a large odd shaped key is vey easy to distinguish from a normal one. BTW on my logitec wireless keyboard the bkspc is seperated from the enter by a row , must be the difference between US and GB layouts .

---

### Post by malspa on 2009-02-14
???

5 keyboards here.  3 have the backspace key separated from the enter key by the backslash/pipe key; the other two, the enter key is right below the backspace key. All bought in the U.S.

---

### Post by scaine on 2009-02-15
Sounds like the VMware case doesn't hold water unless you live the UK then.  Interesting, but then that theory was only proposed in this thread, not by the xorg developers themselves.

As for the other point about ALT-SYSRQ-K being as easy to hit as CAB - I hope that was a joke, since anyone who's ever tried that combo must be nursing a sprained hand by now.  :)

Generally though, joking aside, there's talk of taking away that shortcut too.  It's a kernel option - from wikipedia, there are security concerns about leaving it on in a server since it grants so much power.  And of course, it's also affected by the "cleaners at the console" and "malicious user" scenarios.  It's an ongoing debate however, and since it's a kernel build option, it should be Ubuntu specific if it happens - unlike this CAB decision.

Anyway, think I've said my piece on this.  Please listen to Mr Picklesworth if you won't listen to me.  This has happened.  It's not going to change by moaning here.

Raise a launchpad bug if you feel that strongly about it.  Or, say, just turn it back on again...

---

### Post by scaine on 2009-02-15
[http://en.wikipedia.org/wiki/British_and_American_keyboards](http://en.wikipedia.org/wiki/British_and_American_keyboards)

Boy, you Americans sure have *wrong* keyboard layouts.  Nothing like a good, big, L-Shaped Enter key in my opinion.

:P

---

### Post by scaine on 2009-02-15
I've asked for this thread to die at least twice and now I keep posting to it.  Irony, eh?

Gina, us Logitech users who don't have a SYSRQ key - use PrintScreen.  The Kernel doens't care what its label is - SYSRQ is PrintScreen.

To that end, if you try to use ALT-PrintScreen-K and find hundreds of gnome-screen-capture dialogs appearing, then you'll have to use ALTGR (or right-ALT for all you Yanks).

So, to summarise, if you only have printscreen and no SYSRQ, then you can kill X (just like CAB) by pressing ALTGR-PrintScreen-K.  I've just tried it - it works.

Oh, and a bug in Intrepid may prevent you from using SYSRQ keys - but that's alright cos you guys still have CAB anyway, right?  ([https://bugs.launchpad.net/ubuntu/+bug/303601](https://bugs.launchpad.net/ubuntu/+bug/303601))

---

### Post by AlexBellisBrown on 2009-02-15
Ctrl-Alt-Backspace has got me out of many many scrapes. I vote STAY!

---

### Post by scaine on 2009-02-15
Too late.

---

### Post by AlexBellisBrown on 2009-02-15
I still needed my voice (or keyboard) to be heard! :)

---

### Post by dentaku65 on 2009-02-15
I voted no
At least in this stage (Alpha 4) this decision is senseless, X can stuck sometimes and ctrl-alt-bkspace is saving odd situations. Beginning users should not install alpha releases or at least not in the production machines.

---

### Post by ameermawia on 2009-02-15
i dont see any nessesity to disable this combination.some time this combination is really very helpul.So i think better would be to give an option to enable and disable this combination at the priority of the user...........

---

### Post by mtopro on 2009-02-15
It may not accomplish anything, and I know I could probably enable it, but I use it and don't really need something else to setup on a new build.  I vote KEEP IT.

For the few that have an issue.. Give them something to disable..

---

### Post by starcannon on 2009-03-02
> **eragon100 said:**
> Hello!

In Jaunty alpha 3, the developers have disabled the shortcut ctrl-alt-backspace to restart the X-server, because some people were complaining that they accidentely restarted X. I don´t like this, and I think most people won´t, so I decided to make a small poll about it. Please post your thoughts about this issue here. Thanx!

I do not have any idea how anyone "accidentally" presses this key combo; for those who are having the issue, and by all accounts they are a very small minority, I believe the best thing to do is have them do their own custom dontzap configuring of the xorg.conf file. I also realize that for some specialty situations, one may not want the user being able to restart X, again, leave it to the special situations to sort out their special set up needs; the mainstream release should leave functionality built in by default, not hidden and obfuscated.

---

### Post by scaine on 2009-03-02
Man, starcannon.  Way to resurrect a thread that had finally died in peace.  Seriously, if you haven't launched a bug about this, there's no point in continually dragging out this thread.  The decision is made, move along, nothing to see here.

Sorry if that's harsh, but this thread is dead, serving no purpose at all.

---

### Post by PythonPower on 2009-03-02
When a session hangs, about half the time Control-Alt-Backspace allows me to restart my session without force rebooting... For that reason, it is valuable to me. I also find it difficult to see how someone could accidentally press those three keys so far apart - quite unlikely at least!

---

### Post by scaine on 2009-03-02
:P  Magic.  Like a phoenix from the flames, the thread rises up again.

To stave off another 400 replies, please recap on the thread first.

Summary of what's going :
[http://ubuntuforums.org/showpost.php?p=6677777&postcount=250](http://ubuntuforums.org/showpost.php?p=6677777&postcount=250)

If you don't have a sysrq key, see this post :
[U][http://ubuntuforums.org/showpost.php?p=6738163&postcount=353](http://ubuntuforums.org/showpost.php?p=6738163&postcount=353)

[/U] Please, please, please - if you feel strongly enough to post on this thread, then go the extra mile and raise a bug about it on launchpad where someone might actually care.
[https://launchpad.net/ubuntu/jaunty](https://launchpad.net/ubuntu/jaunty)

---

### Post by DougieFresh4U on 2009-03-02
omg, here we go again.
Please go back to sleep (thread)

---

### Post by Eruaran on 2009-03-10
rant/

I don't really mind things being changed so you can't accidentally kill X... fair enough. But what infuriates me is the kind of backward thinking that I've only ever seen from GNOME developers for whom the "solution" as always is to remove a feature entirely.

Absolutely infuriating. I cannot stress enough how angry this kind of thinking makes me.

To the person who suggested users reboot because that's what Windows users do: Don't impose that crap on me when its not necessary to reboot ! Its one of the things I love about GNU/Linux and you want to make it more like Windows ?

Please can I NOT have some moronic idealogue imposing his/her ideas on what he/she thinks is best for me ?

/endrant

---

### Post by Amaranth on 2009-03-10
You are looking for Linux From Scratch and (most likely) learning C. This is not the point of Ubuntu.

---

### Post by ronacc on 2009-03-10
> **Amaranth said:**
> You are looking for Linux From Scratch and (most likely) learning C. This is not the point of Ubuntu.

I don't think alienating experienced users is the point of Ubuntu either . We who have come to know and love Ubuntu are the ones who enthusasticly promote Ubuntu , give our time and experience to testing and providing help in the forums . It is not a good idea to tell us to go elsewhere .Your attitude is not the solution, it is a symptom of the problem .

---

### Post by fergalm on 2009-03-15
I would like to keep it, because I use it often enough. I think Ubuntu should keep it because new users migrating from Windows will try to use it when their machine freezes up, and I don't think it makes much sense to remove functionality people expect to be there.

---

### Post by gletob on 2009-03-15
I will miss it because there are situation's where it is very useful.

---

### Post by Darkshade on 2009-03-15
First thing I did when I upgraded to Jaunty was re-enable it. I really don't see how someone can press all 3 keys by accident, and looking at the poll results seems like I'm not the only one missing the shortcut enabled by default.

---

### Post by asimon on 2009-03-15
I don't remember that I ever pressed <alt><control><backspace> by mistake. But I was very upset when I wanted to kill my broken X session and found out that the usability 'experts' from Ubuntu disabled it. Grrrrr.

Reenabling it was the first thing I did afterwards.

BTW, I like what opensuse did. There you have to press <alt><control><backspace> two times to kill the session. A very good compromise.

---

### Post by taavikko on 2009-03-15
> **asimon said:**
> found out that the usability 'experts' from Ubuntu disabled it. Grrrrr.

BTW, I like what opensuse did. There you have to press <alt><control><backspace> two times to kill the session. A very good compromise.

This is upstream's decision, not ubuntu-devs decision.
Just a reminder.

But I agree on Suse's approach, same could have been investigated further by ubuntu-devs

---

### Post by ronacc on 2009-03-15
it sometimes seems that they are determined to make Ubuntu so useable that no one will want to .

---

### Post by asimon on 2009-03-15
> **taavikko said:**
> This is upstream's decision, not ubuntu-devs decision.
Just a reminder.

Really? Thanks, I didn't know.

---

### Post by lachild on 2009-03-16
Well I'm glad I found this post.  I saw that CAB was disabled on default and I was starting to get upset.  I've had a ATI graphics card in the past and CAB was the only thing keeping me out-a jail for throwing the thing through an office window at ATI.  

However thanks to this post I've found that ALT-SYSRQ-K works too.  Even though this is a little more inconvenient then CAB, at least it's there.  

I guess now for me, either way is fine.  As long as we are able to educate the others to use ALT-SYSRQ-K instead of CAB.



BTW, for the record, I really don't care what is going on the Windows world, I use Linux and I have never hit the CAB combo by accident... I hope that as Linux continues to evolve, that we don't make all our decisions based on what Redmond is doing like we did in this case.  Most of the examples I've seen base this decision on windows users not Linux users... That's what's really sad about all this.

---

### Post by mikeize on 2009-03-18
I was pretty annoyed by this, but after reading up on it (and finding how easy it is to re-enable)...  I'm just "meh".  There should definitely be a GUI option to toggle this function though.  Really, a shortcut/hotkey 'wizard' (druid?) would be nice, maybe as part of the installation process.

btw, see here to re-enable, if you don't know how:

[https://wiki.ubuntu.com/X/Config/DontZap?action=show&redirect=DontZap](https://wiki.ubuntu.com/X/Config/DontZap?action=show&redirect=DontZap)

---

### Post by trendyabinash on 2009-03-18
YES leave it as it is.

Don't remove it.

---

### Post by jamaisvu on 2009-03-21
> **taavikko said:**
> This is upstream's decision, not ubuntu-devs decision.
Just a reminder.

Which highlights a more important point: Ubuntu is very bad at rejecting upstream regressions. It's the same problem as when Ubuntu slavishly followed Debian in removing xmms from the repos, despite the fact that people find it useful. The whole point of using Ubuntu is to get the benefits of a Debian system without the silly Debian bureacracy whimsically crippling things with their toy (story) politics. Any upstream change that removes functionality should be rejected from Ubuntu by default, with special pleading needed to get them included.

---

### Post by scaine on 2009-03-22
> **jamaisvu said:**
> Which highlights a more important point: Ubuntu is very bad at rejecting upstream regressions. It's the same problem as when Ubuntu slavishly followed Debian in removing xmms from the repos, despite the fact that people find it useful. The whole point of using Ubuntu is to get the benefits of a Debian system without the silly Debian bureacracy whimsically crippling things with their toy (story) politics. Any upstream change that removes functionality should be rejected from Ubuntu by default, with special pleading needed to get them included.

Last I checked, XMMS was indeed in the repos.  Other than this example, how do you justify your assertion that Ubuntu is bad at rejecting upstream regressions?  Also, how do you define a regression?  My understanding is that a regression is a bug which *was* fixed, and re-introduced in a later version.  That's not the case here.  The removal of CAB is a usability decision, plain and simple.

---

### Post by hyperdude111 on 2009-03-22
I now find when "x" freezes instead of re-starting it I have to manually Re-boot.

Definitely a backwards step. It is similar to now in jaunty the update manager will not notify you about new updates! Crazy.

---

### Post by scaine on 2009-03-22
> **hyperdude111 said:**
> I now find when "x" freezes instead of re-starting it I have to manually Re-boot.

Why?  This thread outlines about 3 different methods to replace CAB.  Take your pick.


> **hyperdude111 said:**
> Definitely a backwards step. It is similar to now in jaunty the update manager will not notify you about new updates! Crazy.

Yep, that's really strange.  It appears to be broken.  Of course, we're not even at Beta yet.

---

### Post by canoemoose on 2009-03-22
I voted for "keep it".
I have 2 machines connected to the same monitor/keyboard/mouse via a KVM switch.  If I boot one machine and X loads whilst I'm looking at the other machine, then X forces the resolution to 800x600 with no way of changing it once logged in.  Oh, and it's a family machine so I can't just start X manually when I'm looking at it.

---

### Post by Reiger on 2009-03-22
I'm probably stupid but if my session hangs (which since recently it often does due to the beta fglrx, my GFX card, kwin & kdm having visually loud disagrements about one another from time to time...) I just hit Ctrl+Alt + F2?

At any rate if you want to re-enable it in Xorg.conf, the thing is an "DontZap false" away? 

Personally, I do think that this is the right decision if you have a laptop like me the difference between a DEL and a Backspace key is (excepting that they delete the opposite character by default) that the Backspace key is only about 6 times larger (and that the traditional Ctrl+Alt+Del combo doesn't kill your session without question and often when you need it, it doesn't do squat at all because all input is blocked anyway). Also, if you come from Windows you are used to assigning hotkeys to the Ctrl + Alt modifier (because both Ctrl and Alt on their own are used rather a lot by default in Windows, due to the fact that the Super/Logo button is already 'conceptually occupied')...

---

### Post by scaine on 2009-03-22
> **canoemoose said:**
> I voted for "keep it".
I have 2 machines connected to the same monitor/keyboard/mouse via a KVM switch.  If I boot one machine and X loads whilst I'm looking at the other machine, then X forces the resolution to 800x600 with no way of changing it once logged in.  Oh, and it's a family machine so I can't just start X manually when I'm looking at it.

Then force the resolution so that you *can *boot the machine while connected to the other box.  Or re-enable CAB.  Or use ALTGR-SYSRQ-K, or restart GDM from a terminal.  This pointless poll should have closed months ago.

---

### Post by yaztromo on 2009-03-22
I dont mind ctrl-alt-backspace being disabled since I always disable it myself on new installs anyway.

But they seem to have disabled ctrl-alt-F1 etc which is rather irksome. How do I drop to a text console if X hangs now?

---

### Post by scaine on 2009-03-22
C-A-F1 (upto 6) still works fine here.  I find that if you've enabled UXA, then you have to use the shortcut twice before it takes you to the terminal.  Perhaps that's the issue?

If you really don't have access to your terminals, you should consider raising this as bug.

---

### Post by yaztromo on 2009-03-22
Scaine, thank you. I have to double tap the key combination to get a terminal. Install is an untweaked fresh 9.04 on an old radeon 7000 card so I don't think UXA is enabled.

---

### Post by hyperdude111 on 2009-03-24
> **scaine said:**
> Why?  This thread outlines about 3 different methods to replace CAB.  Take your pick.




Yep, that's really strange.  It appears to be broken.  Of course, we're not even at Beta yet.

Both of those were done DELIBERATELY by the ubuntu team. Not as you said it is only broken as it is an alpha

---

### Post by inportb on 2009-03-24
Indeed, the functionality is intentionally broken... but *not* by the Ubuntu team.

---

### Post by go7Ul1ai on 2009-03-24
> **inportb said:**
> Indeed, the functionality is intentionally broken... but *not* by the Ubuntu team.

Then the question now is.. who intentionally broke it?

It is a mystery.

---

### Post by inportb on 2009-03-24
I believe it's been broken for a while (in the official X releases), but Ubuntu just recently decided to follow suit.

---

### Post by dirtylobster on 2009-03-25
Haven't read any replies but if they want to disable it to avoid mistakes, why not make a popup saying **"You just pressed Ctrl-Alt-Backspace which will restart GDM. All your open work will be lost. Do you want to continue?"** followed by a checkbox **"Do not show this warning in the future."**?

---

### Post by scaine on 2009-03-25
> **dirtylobster said:**
> Haven't read any replies but if they want to disable it to avoid mistakes, why not make a popup saying **"You just pressed Ctrl-Alt-Backspace which will restart GDM. All your open work will be lost. Do you want to continue?"** followed by a checkbox **"Do not show this warning in the future."**?

It's been suggested many times in this thread.  It's not a feasible suggestion, however, since the time you're most likely to use CAB (or as it is now, ALTGR-SYSRQ-K), is the time that X is incapable of putting anything on the screen.

---

### Post by amano on 2009-03-25
And until the next one steps in having read just the thread title:

[COLOR="DarkOrchid"]1) THIS WAS AN UPSTREAM DECISION. CTRL+ALT+BACKSPACE is destined to die out![/COLOR][COLOR="Purple"]

2) USE ALT**GR** + SYSRQ + K
or ALT**GR** + PRINTSCREEN + K instead.[/COLOR]

:guitar:

---

### Post by Mr. Picklesworth on 2009-03-25
And if your laptop keyboard isn't cooperating, use the Fn key to get to SysRQ. They just don't colour that one since it's such an unusual key to request, but it is *always* there and accessible somehow.

---

### Post by rocknrolf77 on 2009-03-25
I don't know if someone has said it before but for me it's also no. Maybe like openSUSE does it. You have to hit ctrl-alt-bckspace twice. If you just hit them once, you just get a beep.

---

### Post by amano on 2009-03-26
Why is hitting Ctrl-ALT-Backspace twice so much better than hitting  AltGR-SysRq-K once? 

Ubuntu is at least honoring the upstream design decision. OpenSuse will be alone with their "push it twice" combo.

---

### Post by stoffe on 2009-03-26
Just learn ALTGr-SysRq-K. It was always the better option anyway (talks directly to the kernel), and it isn't close to other commands so the finger could slip.

People do hate to learn anything new, even if it is better, but try it. And spread the word, change old tutorials etc. New people really should learn ASK no matter which distro, because it will work everywhere and even when X has gone into a loop CAB can't break.

It's just a question of memorizing one single command that is no harder than the old one you have memorized.

---

### Post by BGFG on 2009-03-26
dontzap worked for me. Mistakenly hitting key combos is not a problem for me.

---

### Post by jacob01 on 2009-03-26
my concern is that some one may forget to enable it then if they need it they are out of luck. but i guess it isn't to much of an inconvenience.

but is this really a common enough issue to change?  i have never hit it.

---

### Post by scaine on 2009-03-26
> **jacob01 said:**
> my concern is that some one may forget to enable it then if they need it they are out of luck. but i guess it isn't to much of an inconvenience.

Then use ALTGR-SYSRQ-K.

> **jacob01 said:**
>  but is this really a common enough issue to change?  i have never hit it.

Nah, the Xorg developers just did it to piss you off personally.  This way, they get you no matter which distro you use...

:)

---

### Post by scaine on 2009-03-26
So, are we all beginning to feel like a broken record yet?  No wait - that was 9 pages ago, wasn't it.

ps.  Use ALTGR-SYSRQ-K now.

---

### Post by mabovo on 2009-03-26
> **scaine said:**
> So, are we all beginning to feel like a broken record yet?  No wait - that was 9 pages ago, wasn't it.

ps.  Use ALTGR-SYSRQ-K now.

Are You out of your mind ?

Kernel Panic - not syncing: attempted to kill init!

---

### Post by tjeremiah on 2009-03-27
what the heck is AltGR-SysRq-K ?

---

### Post by philinux on 2009-03-27
> **tjeremiah said:**
> what the heck is AltGR-SysRq-K ?

Altgr key or plain Alt will do
sysrq >printcscreen key
K from the keyboard.

Result Kill xsession and go to login window.

---

### Post by tjeremiah on 2009-03-27
> **philinux said:**
> Altgr key or plain Alt will do
sysrq >printcscreen key
K from the keyboard.

Result Kill xsession and go to login window.

thanks :)

---

### Post by amano on 2009-03-27
No problem. It was just mentioned 100 times in this thread already ;)

Just use AltGR+SysRq+K to kill your X session.

---

### Post by markbuntu on 2009-03-27
If you are using ubuntustudio strangely enough jackcontrol has an option to enable ctl-alt-backspace for x restart. There is also an option in KDE settings somewhere. I saw it. So that just leaves gnome and xfce....

It seems to me that a lot of devs think ctl-alt-backspace is still a good idea.

---

### Post by scaine on 2009-03-28
> **markbuntu said:**
> 
It seems to me that a lot of devs think ctl-alt-backspace is still a good idea.

Yep, hence the result in this poll.  Of course, those guys will know how easy it is to re-enable it.

If they can be bothered, since ALTGR-SYSRQ-K does exactly the same thing.

---

### Post by phenest on 2009-03-28
I did originally vote no to keep the short-cut, but that was in the early days of this thread. The more I read other users comments, the more I'm leaning towards disabled by default, but that is simply a personal taste.

I do think the solution is simple: To have is enabled by default, but to have the key combination definable like any other. It could be added to the list of shortcuts in Keyboard Shortcuts in Gnome, and you can either redefine it, or disable it.

When I say enabled by default, I mean enabled on a freshly installed system. Once you have disabled it, reinstalling Ubuntu won't re-enable it because the setting is stored in the /home partition, therefore it won't get over-written.

Or is this too easy? Devs, I'm talking to you.

---

### Post by forcecore on 2009-03-28
i like this ALTGR-SYSRQ-K combination too because it is harder to make mistake.

---

### Post by pwk on 2009-03-28
Anyone who can hit ctrl-alt-del by accident is just as likely to hit any other key combination by mistake. And won't this confuse VirtualBox? Please don't disable it.

---

### Post by amano on 2009-03-28
Why is hitting Ctrl+Alt+Backspace so much better than hitting AltGR+SysRQ+K?

Ubuntu just followed the upstream (X.org) design decision. Ctrl+Alt+Backspace is destined to die out within all distros.


Just use the alternative key combo (see above: AltGR ist the key right from the space key and SysRq is commonly known as the Print Screen key). It cannot be that hard to remember it.

AltGR+SysRQ+K
AltGR+SysRQ+K
AltGR+SysRQ+K
AltGR+SysRQ+K
...

---

### Post by DarwinSurvivor on 2009-03-29
I have to say, as annoying as it is to change my habits, at least this combination we can hit with ONE HAND!!!

I've always been opposed to key combos that require 2 hands, and this is actually not bad. (For those having troubles remembering the 'k', think "kill").

---

### Post by other guy on 2009-03-29
The new combo just gives me a screenshot. Even if I remap the 'Take a Screenshot" to another key besides PrntScr. I test the new key toggle, and it works. It gives a screenshot.  I even disabled the screenshot shortcut in the pref settings, to make sure.

When I try out the Right Alt+K+SysRQ, all I get is a screen cap popup. No X-killing, like the old combo gave me.

Any ideas?

---

### Post by scaine on 2009-03-29
> **other guy said:**
> 
When I try out the Right Alt+K+SysRQ, all I get is a screen cap popup. No X-killing, like the old combo gave me.

Any ideas?

I notice from this post that the order is important to ensure that you get the magic sysrq combo to work.  It's ALTGR-SYSRQ-K for a reason, I suppose.  Pressing ALTGR-K-SYSRQ just fills my console up with k's.

Incidentally, the[ magic sysrq key combos]("http://en.wikipedia.org/wiki/Magic_SysRq_key") are kernel-level - unmapping gnome hotkeys won't have any effect here.

---

### Post by Chrisj303 on 2009-03-29
> **amano said:**
> Why is hitting Ctrl+Alt+Backspace so much better than hitting AltGR+SysRQ+K?



Because my laptop doesn't even have AltGR + SysRQ.

What a dumb idea.

This could only happen with Linux.

---

### Post by Crushyerbones on 2009-03-29
I chose "no" because I had no idea it had merely CHANGED to another key combination

---

### Post by phenest on 2009-03-29
> **Chrisj303 said:**
> Because my laptop doesn't even have AltGR + SysRQ.
Why not? I thought all keyboard layouts did?
> **Chrisj303 said:**
> What a dumb idea.
Saying it's dumb, isn't helpful. Tell us why.
> **Chrisj303 said:**
> This could only happen with Linux.
What is that supposed to mean? You don't have to use Linux.

---

### Post by amano on 2009-03-29
> **Chrisj303 said:**
> Because my laptop doesn't even have AltGR + SysRQ

Those are standard keys. SysRQ is another name for the PrintScreen key. I cannot believe that there are crappy laptops without it around.

And then again: For those 0,099 percent of those people who miss even the standard keys on their keypad, you can re-enable the old behaviour with the dontzap command. They left this possibiltiy in for a reason ;)

---

### Post by dundee5 on 2009-03-30
I have never accidentally typed that key combination.

I guess it can be good when you can easily disable it (in keyboard shortcuts dialog), but disabling by default is not a good idea. 

User should be able to enable it in some dialog not in xorg.conf at least.

---

### Post by amano on 2009-03-30
Why don't you just use [COLOR="Red"]AltGR+SysRQ+K[/COLOR]? (AltGR is the RIGHT ALT button and SysRQ is labelled "Print Screen" most of the time, and remeber to press and hold the keys in the in the right sequence, eg. starting with ALtGR, and ending with the K(ill) key).

Upstream (X.org) switched away from using the old key combo and in return all distros will do sooner or later.

What does you prevent from using the now recommended [COLOR="Red"]AltGR+SysRQ+K[/COLOR]?

---

### Post by skotos on 2009-03-30
It is useful to have it enabled by default. When something goes wrong you know you always have an option not to reboot (though ALT+F1 might be good as well..)
BTW, if they disabled it, I would enable it again. It has helped so much in the past, that we are now good friends.

---

### Post by formol on 2009-04-04
the option should be give somewhere to disable it if some want, but it should be keep enable by defaut, it's a great great shortcut, very useful when you need it.

---

### Post by toupeiro on 2009-04-11
Seriously... RE-ENABLE THIS!

Here I thought something was broken until I decided to poke around on the forums.  This is VERY Non-standard behavior for a linux based OS...

---

### Post by Bios Element on 2009-04-11
> **toupeiro said:**
> Seriously... RE-ENABLE THIS!

Here I thought something was broken until I decided to poke around on the forums.  This is VERY Non-standard behavior for a linux based OS...

The change was made upstream, so for just about any updated Linux based OS, this is standard behavior.

---

### Post by Noblacktie on 2009-04-11
Gawd, no wonder I couldn't Ctrl+Alt+Backspace. I was wondering if something was borked.

Disabling it is plain silly. At most, they should just introduce a confirmation prompt, something along the lines of "Are you sure you want to restart your session?"

Making it more difficult for everyone because a few people have poor hand-eye coordination is befuddling, to say the least.

---

### Post by kansasnoob on 2009-04-11
But ............. why listen to the masses?

Does it matter what end users want?

---

### Post by GoldNugget on 2009-04-12
I agree with the poster who suggested a confirmation asking 'Are You Sure..." instead of disabling it. Ubuntu is not just for beginners. Lots of experienced Linux users will miss this shortcut. I can see how it could cause confusion with new users, but they need to learn to use the tools properly and it is a mistake most will only make once.

There is the added benefit of being able to restart a frozen desktop without restarting the computer. This is a major advantage of using Linux. Please don't disable this. Bad idea.

---

### Post by amano on 2009-04-12
The experienced users will have to settle with it. Because it was an upstream decision and will be forgotten soon within all distributions. ):P

And I don't see, why AltGR+SysRQ+K should be any worse. It works and it is the way upstream decided to go half a year ago. Where was the uproar back then?

---

### Post by Noblacktie on 2009-04-12
> **amano said:**
> The experienced users will have to settle with it. Because it was an upstream decision and will be forgotten soon within all distributions. ):P

And I don't see, why AltGR+SysRQ+K should be any worse. It works and it is the way upstream decided to go half a year ago. Where was the uproar back then?

There was no uproar back then (here, at least) because it did not affect the majority of users. We were still all on Intrepid and older.

This feels like change for the sake of change.

Ah, well, profiting of the toil of others, who are we to complain?

---

### Post by oobe-feisty on 2009-04-13
how can anyone accidently do this this was the thing i hated the most when i installed the beta its an inconvenience to people and i think it would be rare for people who are apparently so unsavy as to accidently do this key combination i think if people dont know what there doing its hard enough for them to learn any keyboard shortcut nether lone type the wrong one.

---

### Post by markbuntu on 2009-04-13
It is the people typing LaTex macros on their tiny netbook keyboards with their toes. Apparently there are a lot of them at kernel dev team so their perception is that this is a widespread problem.

---

### Post by amano on 2009-04-13
> **Noblacktie said:**
> There was no uproar back then (here, at least) because it did not affect the majority of users.

But the only way to "affect" users is that they changed a key combo and recommend another one. Maybe I don't get your real problems.

Since this is an upstream change, it will be this way in ALL future distros. Why don't you just spend the 10 seconds to memorize the other now recommended key combo?

For all those new to this thread: It's [COLOR="Red"]AltGR+SysRQ+K[/COLOR]? (AltGR is the RIGHT ALT button and SysRQ is labelled "Print Screen" most of the time, and remeber to press and hold the keys in the in the right sequence, eg. starting with ALtGR, and ending with the K(ill) key).

---

### Post by collinp on 2009-04-13
Does anyone know /why/ they did this, other than to annoy the vast majority of the Linux community? Its pretty idiotic if you "accidentally" kill your X server.

---

### Post by amano on 2009-04-13
Maybe it is more idiotic to get upset rather than just get used to another key combo?

And it's open source. If THAT combo makes you feel that better than any other one, you can just fork and maintain a new X.

---

### Post by collinp on 2009-04-13
> **amano said:**
> Maybe it is more idiotic to get upset rather than just get used to another key combo?

And it's open source. If THAT combo makes you feel that better than any other one, you can just fork and maintain a new X.

No, I have gotten used to using ctrl + alt + backspace in the past 4 years, and its pretty hard to change that :).

---

### Post by oobe-feisty on 2009-04-13
since before ubuntu existed ctl alt backspace was the norm and all people who regularly use linux know this so if you ask me you are alienating people new to ubuntu who already know how to use linux in order to make it more user friendly i have no problem with user friendly concepts but i don't see how this is user friendly at all.

---

### Post by oobe-feisty on 2009-04-13
> **amano said:**
> Maybe it is more idiotic to get upset rather than just get used to another key combo?

And it's open source. If THAT combo makes you feel that better than any other one, you can just fork and maintain a new X.


im confused is this somthing xorg is doing or ubuntu developers

---

### Post by Mr. Picklesworth on 2009-04-13
> **Hellow said:**
> Does anyone know /why/ they did this, other than to annoy the vast majority of the Linux community? Its pretty idiotic if you "accidentally" kill your X server.

It's pretty idiotic that anyone wants to kill their X server on purpose, too. If the issue is rogue applications doing mouse / keyboard grabs and not letting go (which is a woefully frequent thing on my computer), maybe there is a better fix than wiping out the entire X server, hmm?

On that topic, however, I for one have experienced absolutely no problems in Jaunty which have necessitated killing X. I have on a few occasions had processes completely smother the system (which Linux seems to handle less gracefully than Windows), but that issue is better dealt with from another tty anyway. Perhaps the thought is that X is reasonably stable at this point so it doesn't need those old training wheels?

Further, this thread has gone from serving little purpose to serving NO purpose. Jaunty is way past feature freeze now. It's over; this is IN. Now wait and see. If everyone hates it and installs ReactOS or something because they're too lazy to run the dontzap command, you guys can all come back to this thread and say "we told you so." For now, it may as well go quietly. Spend this valuable time, rather than arguing, reporting those bugs which are causing you to want the X server zapping, and while you're at it coming up with the best way the change could possibly be presented in the release notes.


Lastly, things change all the time. That's what happens with Linux, Ubuntu and free software in general. It's not like someone changed the default font to Comic Sans or anything...

---

### Post by hikaricore on 2009-04-16
1,168 to 160 end result.

---

### Post by olskar on 2009-04-16
> **hikaricore said:**
> 1,168 to 160 end result.

If that is not an overwhelming majority, I don't know what is.

---

