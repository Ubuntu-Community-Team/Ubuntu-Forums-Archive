---
title: "ubuntu 11.10 disaster"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by christosophia on 2011-10-15
greetings!
I updated to UBuntu 11.10 a few hours ago.
It changed everything I Loved about Ubuntu 
/end-exaggeration

But seriously, it changed so many good things.
I can't find the "minimize all windows" button.
The time and date tab up the top doesn't have the Picture of the Earth in Day and in Night, it doesn't have anything it used to have it was cool, and it is just complete failure!
How do I revert back to how it was, to the old GUI?

HALP MEH!

---

### Post by christosophia on 2011-10-15
why did they take away the show-desktop button, and remove the top bar? and make it change into the windows top bar?
why did they change the date and time tab to not include the awesome shadow-light, day-night of the Earth?(which was my favourite thing ever)?

---

### Post by 4thfloorstudios on 2011-10-15
Hi, you could try to get back to classic desktop by doing:

```
sudo apt-get install gnome-session-fallback
```Then logout and login with chosing classic desktop in the settings of the login screen.

This worked for me but left me with my classic desktop settings gone (of course, it has been uninstalled when upgrading, but why? And why are you not informed about it?) and a totally messed up font size, especially in Eclipse.

Then again, how complicated can it be to add a setting for fontsize or even dpi in the systems settings? You have to install an extra software to changes that by GUI..ridiculous.

And those are only the problems I encountered until now...

The new ubuntu really sucks and I think about going to debian.

---

### Post by Hakunka-Matata on 2011-10-15
In general, I agree with everything said so far, we all seem to dislike *change.  *Try the pure Gnome3 shell, I've gotten used to it and it's the best option so far for me in 11.10 Ubuntu Desktop.
```
sudo apt-get install gnome-shell
```

---

### Post by christosophia on 2011-10-15
I Understand the Change part is a shock.
But in reality, the removal of the day-night thing in the tab, it sucks.
and where s the show desktop button lol

---

### Post by 4thfloorstudios on 2011-10-15
@Hakuna-Matata:
Thanks for the tip, I will give it a try.

And it is not about disliking change. I really looked forward to updates in Ubuntu and liked most of the changes but this time it is a *forced* *change*...

Linux always gave the feeling of having things under control (well, kind of ;) and now you have no choices and are left with a messed up system...great...

---

### Post by calande on 2011-10-15
> sudo apt-get install gnome-session-fallback

Thanks. This partly helped but all my customization disappeared, my shortcuts, etc... The menu is broken...Much of the good old desktop doesn't work anymore. But still it's less bad than Unity. Gosh, I'm so mad at this stuff, when they change things that work for something that is not good and when they do it without asking during installation...

---

### Post by meho_r on 2011-10-15
It's not Ubuntu's fault Gnome is changing. I personally find Unity more usable than pure Gnome 3. And going with Debian just because of day-night thingy wouldn't solve anything since next Debian will come with Gnome 3 too.

For minimizing windows use Ctrl+Alt+D shortcut.

---

### Post by 4thfloorstudios on 2011-10-17
@calande:
Yes, I think reason for loosing your settings and menu is that the classic desktop is being uninstalled during update.

---

### Post by calande on 2011-10-17
Not to mention all things that stopped working, when I am idle, I have to type in my password again (I had fixed it), when I start my computer, I'm logged in using the wrong version (Ubuntu 3D instead of 2D), with a cross instead of my mouse pointer, nothing working (have to log out and log back in with 2D only). I'm unable to create application shortcuts (option greyed out). My DVB-T system stopped working with VLC. I'm unable to reorder icons of the Unity bar, I can't move this bar either...Too many problems to name them all :'( 
I just wonder how this release got through with no one to speak out...

---

### Post by 2F4U on 2011-10-17
> I just wonder how this release got through with no one to speak out...

Probably because not enough users did testing and bug reporting during the alpha and beta phase.

---

### Post by X_Splinter on 2011-10-17
Hey I just upgraded my Ubuntu to 11.10 and I gnome 3 sucks so much.

I tried to enable compiz desktop cube and unity crashed immediately. I search the forums and INTERNET and I used the unity --reset and it worked once.

Unity crashed again for no reason and I cant get it to work, I used unity --reset-icons and sidebar comes up and process never end and I if close the terminal the graphical interface totally crash and I need unplug the computer 

I tried Gnome classic but it's not like gnome2 it sucks. I dont mind starting using Unity but first I need it to work.

Is there a way to totally reinstall Unity?

---

### Post by calande on 2011-10-17
I wish Ubuntu (and Gnome didn't try to advance too fast) creating software and testing takes time. If Ubuntu made more time and went not so fast, changes wouldn't be so radical from one release to the other, and if it ain't broke, don't fix it. For me, the previous version was good enough, I didn't ask for better or less good ;)

---

### Post by christosophia on 2011-10-19
I want my old computer back :(
I can't even alt-tab and switch windows with the mouse anymore..
no temperature for my city, no day-might tab, not post-it notes on the top bar
just complete failure!
this sucks!!

---

### Post by kurt18947 on 2011-10-19
Have you considered Xfce desktop?  Quite a few users whose sensibilities were shocked by Unity/Gnome-shell have gone that route, it seems.  You can go to Synaptic (and I assume the software center) and install Xfce-desktop.  I've installed it and it seems to work but I never felt the need for the cube or emerald or other eye candy so don't know if they work or not.  I only know that others have chosen the Xfce route. To select Xfce is just like other desktops -- the gear icon by your user name when logging in.  The nice thing about that vs. installing Xubuntu is the ability to switch between desktops by logging out/logging in vs. rebooting.

---

### Post by superangel on 2011-10-19
I totally agree with the above messages. Did a separate 11.10 install (as my 10.4 update manager crashed in October last year - see my still unanswered query under general help). Now I am glad that I didn't (couldn't) do an upgrade! IMHO, 

**11.10 is Ubuntu VISTA! **:mad:

The fancy, intrusive vertical huge-icon toolbar constantly gets in the way of left-screen access, displays stubbornly defaults to mirroring, printer driver problems all over again and the precious 10.4 cups driver fix does not work. And what happened to Evolution as mail server? It was quite a manual job to migrate mail folders and files from Thunderbird to Evolution - and now 11.10 defaults back to T-bird!
Yes, you can install Evolution, but I can't find any easy way to "restore from files" from my 10.4 - no one-click start, etc...
Ok, maybe it's just me that is adverse to change. But when "change" is going the Windows (de)route, well.....#-oguess I'll stay with my crippled Lucid.

---

### Post by Regele IONESCU on 2011-10-19
I downloaded and installed Ubuntu 11.10. Xfce was default, it nevere asked me if I want it or not. The only problem I have up to now is that network is not working even though during install process it worked like a charm.

---

### Post by calande on 2011-10-19
I don't want an over minimalist desktop either. Balance is good. For me 11.10 is pretty bad, I can't believe it :(

---

### Post by ubu_dynamite on 2011-10-19
> **Regele IONESCU said:**
> I downloaded and installed Ubuntu 11.10. Xfce was default, it nevere asked me if I want it or not. The only problem I have up to now is that network is not working even though during install process it worked like a charm.

You must have downloaded xubuntu then else unity would have been the default.

---

### Post by eklikeroomys on 2011-10-19
I agree, Ubuntu 11.10 sucks. Its not that I dont like change, but the change is incomplete.
Firstly, I like to be in control over personalization. 11.10 requires you to install extra (dodgy IMO) apps like Compiz, which apparently causes numerous problems with Unity.

I think that Unity will be awesome once it is finished. Ubuntu should have postponed the release until it was a complete work, with AT LEAST all of the functionality of 10.10. I think most loyal users will stick with Ubuntu for the time being, but I doubt that new users having to look at 11.10 (or worse, 11.04) for the first time will be impressed. Nobody would be angry if the release was postponed with good reason. 

I use Ubuntu at work as well, and I have to be honest, I am sticking with 10.10 for now. The first app I always install on ubuntu is guake (the drop-down terminal), and this already caused problems in 11.10. For me, Guake is a must for productivity.

However, I think that Unity will be awesome once all of the personalization and functionality is resored. Perhaps even a terminal within one of the tabs of the dash? This would be awesome! :popcorn:

---

### Post by Regele IONESCU on 2011-10-19
> **ubu_dynamite said:**
> You must have downloaded xubuntu then else unity would have been the default.

This is where I downloaded from:

[http://cdimage.ubuntu.com/ubuntustudio/releases/11.10/release/]("http://cdimage.ubuntu.com/ubuntustudio/releases/11.10/release/")

and this is what I effectively downloaded:

[http://cdimage.ubuntu.com/ubuntustudio/releases/11.10/release/ubuntustudio-11.10-alternate-amd64.iso]("http://cdimage.ubuntu.com/ubuntustudio/releases/11.10/release/ubuntustudio-11.10-alternate-amd64.iso")

Nowhere is mentioned Xubuntu and the install screen was clearly saying Ubuntu Studio.

Anyhow, how could I sort out the network problem, could you please tell me???

---

### Post by coldbluesteel on 2011-10-19
I have to go along with the rest here. Ubuntu 11.10 blows.

I thought the move to Unity in 11.04 sucked, but at least you could run Gnome Classic.

Now the whiz kids at Canonical have even taken THAT away without having to futz around.

I tried the "sudo apt-get install gnome-session-fallback " fix and now the stupid thing won't even boot!

Here's a clue for all the Unity/Gnome (and even the Windows 8 folks): If I want something that looks and operates like a tablet, **_I'LL BUY A TABLET_**

This "universal interface" that is being migrated to where your phone, tablet, laptop, desktop all operate the same is just plain asinine. I want my much more powerful machine dumbed down to apps instead of full featured menus. NOT!

Guess it's time to move to KDE, and the Ubuntu developers have pissed me off enough to switch distros. Time to try openSUSE, or Mint. 

I was always a huge fan of Ubuntu, but not anymore.

I agree with the poster who said: Ubuntu 11.10 is the "Windows Vista" of Ubuntu releases.

Too bad really, they were the absolute best for a very long time.

---

### Post by ubu_dynamite on 2011-10-19
> **Regele IONESCU said:**
> This is where I downloaded from:

[http://cdimage.ubuntu.com/ubuntustudio/releases/11.10/release/]("http://cdimage.ubuntu.com/ubuntustudio/releases/11.10/release/")

and this is what I effectively downloaded:

[http://cdimage.ubuntu.com/ubuntustudio/releases/11.10/release/ubuntustudio-11.10-alternate-amd64.iso]("http://cdimage.ubuntu.com/ubuntustudio/releases/11.10/release/ubuntustudio-11.10-alternate-amd64.iso")

Nowhere is mentioned Xubuntu and the install screen was clearly saying Ubuntu Studio.

Anyhow, how could I sort out the network problem, could you please tell me???
Make your own thread describing your problem and maybe someone or i can help you out no idea what your exact problem is ad the moment.

---

### Post by jimbo99 on 2011-10-19
> **4thfloorstudios said:**
> Hi, you could try to get back to classic desktop by doing:

```
sudo apt-get install gnome-session-fallback
```Then logout and login with chosing classic desktop in the settings of the login screen.

This worked for me but left me with my classic desktop settings gone (of course, it has been uninstalled when upgrading, but why? And why are you not informed about it?) and a totally messed up font size, especially in Eclipse.

Then again, how complicated can it be to add a setting for fontsize or even dpi in the systems settings? You have to install an extra software to changes that by GUI..ridiculous.

And those are only the problems I encountered until now...

The new ubuntu really sucks and I think about going to debian.

This is a special fallback edition of gnome 2 that isn't really gnome 2.  It almost looks sabotaged.  You want to **** him off more, make that suggestion again. LOL.

---

### Post by peter3 on 2011-10-19
What I find is that every time I log into 11.10, /etc/resolv.conf is gone.  I have to edit it to put back:
domain <my domain>
search <my domain>
nameserver <my nameserver ip address: 192.168.xx.xx>
And then my networking just works.
I even tried making the file read only:  chmod 444 resolv.conf
and immutable:  chattr -i resolv.conf
Nothing helped.  Rebooting still wipes out everything in the file except the top comment line.  Of course you can't get out of house without the goods.

---

### Post by jimbo99 on 2011-10-19
> **peter3 said:**
> What I find is that every time I log into 11.10, /etc/resolv.conf is gone.  I have to edit it to put back:
domain <my domain>
search <my domain>
nameserver <my nameserver ip address: 192.168.xx.xx>
And then my networking just works.
I even tried making the file read only:  chmod 444 resolv.conf
and immutable:  chattr -i resolv.conf
Nothing helped.  Rebooting still wipes out everything in the file except the top comment line.  Of course you can't get out of house without the goods.

You are using your own DNS server using bind9?  Whatever you choose to modify the resolv.conf file for is your choice, but you might not know that that file is over written upon every reboot.

There is a solution though.  Use chattr.

So, you would sudo chattr +i resolv.conf.

That will make the file so that it can't be updated by anything until you undo it.

Unity and Gnome are horrible programs.  This is not advancement, these are backward steps that promote the stupidification of Linux.  I'm not trying to convince everyone to become programmers.  But to dumb down the interface to a point of being moronic is too much. 

The only real solution right now is KDE and their problem is that they are just as arrogant at times, where they will force change just because they like it instead of looking at it from the perspective of the users.

KDE can be redeemed.  They do reverse course at times so that we can have what we want.  That's the way to produce a distribution--by listening to your users and changing it to what they want.  Go KDE.

---

### Post by coldbluesteel on 2011-10-19
> **jimbo99 said:**
> This is a special fallback edition of gnome 2 that isn't really gnome 2.  It almost looks sabotaged.  You want to **** him off more, make that suggestion again. LOL.

Yup.

I have to say, I have been using Ubuntu since the first release. I have always loved it and recommended it to others.

But the last two releases have been so overwhelmingly disappointing with the change to Unity I'm going to move to either Mint or openSUSE where they still know what people want in a desktop OS which is **_NOT_** to have it look like a tablet or a smartphone.

Just my humble opinion, one of the foundations of Linux in the PC world is being able to almost infinitely customize everything including your desktop. Having everything locked and unable to be customized at all runs counter to everything I've experienced since I started using Linux in the mid-90's.

Unfortunately, it appears Gnome 3 is going in the same direction. I predict KDE will soon be the desktop of choice, followed by LDXE.

Just one users opinion. But WOW they really screwed the pooch with this release.

---

### Post by KBD47 on 2011-10-19
> **kurt18947 said:**
> Have you considered Xfce desktop?  Quite a few users whose sensibilities were shocked by Unity/Gnome-shell have gone that route, it seems.  You can go to Synaptic (and I assume the software center) and install Xfce-desktop.  I've installed it and it seems to work but I never felt the need for the cube or emerald or other eye candy so don't know if they work or not.  I only know that others have chosen the Xfce route. To select Xfce is just like other desktops -- the gear icon by your user name when logging in.  The nice thing about that vs. installing Xubuntu is the ability to switch between desktops by logging out/logging in vs. rebooting.

I tried that Xfce4 desktop session Ubuntu install and it is not as nice as full Xubuntu.
KBD47

---

### Post by mttrn on 2011-10-19
The change to 11.04 was bad enough (due to Unity) but now the upgrade to 11.10 really is a sign that Ubuntu is about to kick the bucket.

Upgrading an existing installation now forces a major UI change down your throat as if it were Windows. At least with Windows 8 they changed the worst part. I wonder what idiot tells the world that everybody has to use tablet-style UI on desktops all of a sudden.

The upgrade from 11.04 to 11.10:
- suddenly, Unity AGAIN!! and NO(!!!!!) way to avoid its installation , which very effectively pisses me off
- no right-click on the gnome panel anymore.. WTF? Why didn't anyone tell us to use Alt-Rightmouse from now on??
- Suddenly, my mouse pointer disappears at monitor edges - handy on my multimonitor setup. But why??
- "No proprietary drivers are in use on this system" Strangely,pcimodules tells me "fglrx_updates" (ATI driver) is running
- Installing the ATI drivers AGAIN fixed the mouse-peekaboo problem. Why??
- Where is synaptic gone? And why??
- I have to enter program names instead of having a nice, categorised drop-down menu where i find everything very quickly. Why???
- The Software Centre offer all available software (try finding a compiler). Why???
- after removing Unity and logging out: Unity is still my default desktop environment. How thoughtful...
- Where is the "System" dropdown gone? Completely lost
- Instead, a "System settings" option can be accessed along with "Online accounts"... How very logical to place it there
- Bad surprise: no admin settings available there?
- The copy dialogue still hasn't got a Pause button - which really just showed me the programmers were busy with useless stuff
- The "System info" tool in system settings provides more than info apparently but also allows you to enable fallback mode. Again, well hidden...
- Also: Ubuntu Software Centre becomes painfully slow - just because I clicked some additional packages offered with a program

All this is a lorry full of moronic decisions, too many to put up with if every future upgrade will annoy the hell out of me like this.

Why didn't they create a Stupuntu for stupid stuff like this and left the good things in Ubuntu intact? How can several people supposedly independent of each other get the same idiotic ideas about UI design?? How can they forget that just because they create a tablet UI, desktop PCs will still be desktop PCs?

Most groups at the informatics department at the university of Duesseldorf are using Ubuntu on their desktop PCs, 10.04 atm, but Unity is sure to be never be used there. Time to check out Xubuntu and Kubuntu again. A Kubuntu install I tried once was so stable, KDevelop crashed faster than I could write a Hello-World program and thus, disqualified itself back then.

Somehow this all reminds me of [http://xkcd.com/927/](http://xkcd.com/927/) - a new desktop environment will NOT replace the old ones :P

OK, thanks for reading up to this part, or not :) Just had to get rid of the burden on my mind. Now if only someone sensible would read this and make it into a decision position on the GNOME and Ubuntu teams...

P.S.: almost forgot: after upgrade, child popup windows opened BEHIND active windows.. and i was waiting for the "administrative privileges required, enter password" window to show up, and waited, and waited...
P.P.S.: switching user just now opened a new xserver on ctrl+alt+f8 but i managed somehow to hide the password input box by just switching through the available users (its that newfangled login screen of 11.10)

---

### Post by 4museman on 2011-10-19
I'm very sad to say that I'm VERY disappointed from Ubuntu 11.10 too.

It screwed up too many things in my so far nearly perfectly working Ubuntu (Gnome classic) installation and brings almost nothing useful but retardation in many ways.
Now I can hardly believe in good future of Ubuntu (and Gnome too) when its development seems to turn really bizarre directions.

For me it's time to check some other GUI or directly other Linux distro... :(

---

### Post by bohemian9485 on 2011-10-19
I totally agree with everyone, Ubuntu 11.10 introduced so many changes and to a new user like me (less than a month) it was quite a shock. I chose Ubuntu because of its easy-to-use features that make transition to Linux system less "painful". But the new release looks so "alien".
I don't want to abandon Ubuntu totally that is why I re-installed Ubuntu 10.04 LTS on my system yesterday, hoping it would introduce less "shocking" changes that would wreck my nerves. When I did an update it trashed desktop effect, but I can live with that.:)

---

### Post by mpiter on 2011-10-19
> **bohemian9485 said:**
> ...I don't want to abandon Ubuntu totally that is why I re-installed Ubuntu 10.04 LTS on my system yesterday, hoping it would introduce less "shocking" changes that would wreck my nerves....

You are waisting your your time and you are going to be very disappointed.  The next LTS version (12.04) is going to the same direction: Unity and Gnome Shell.  Either go to KUbuntu, XUbuntu or another distro.

I am leaving Ubuntu because its upgrade policy has become too unprofessional.  In the past you could upgrade without spending more than an afternoon or two to work around bugs. Now they simply relase an OS which is in beta stage at best.  My computer is my main working tool and I cannot afford to work during two weeks after an upgrade to end up with an untrustworthy though usable computer.

I have just spent several hours reading about Ubuntu future and about other distros.  Obviously, Ubuntu is slipping to a direction I do not like.  I will install Linux Mint tomorrow or Friday.  Linux Mint developers will not use Unity, they will keep Gnome 2.x for their next release and they will switch it for Gnome 3 in about one year, maybe a little bit earlier.  They want Gnome 3 to be more mature than today before releasing it.  The distro is more user oriented and they also have a wiser upgrade policy than Canonical.

I have never tried Mint, but in theory it is a Ubuntu version more user oriented and more careful in its upgrade policy.

---

### Post by mpiter on 2011-10-19
I have spent time testing Unity and Gnome 3.

I think that Unity is full of design mistakes.  I have discussed it with Unity defenders and they could not answer my points.  I therefore think it is a buggy design that will certainly not fit my needs.

Gnome 3 seems more promising to me.  I really like the way they summarize the desktop contents with the overview on the right of the screen and the details of one desktop in the center.  With a dock at the bottom of the screen and a few applets, it can give a good working experience.  Of course, it clearly lacks of customization capabilities, even with tools such as gnome-tweak-tool, and there are things that I prefer in Gnome 2. But overall, it is the first philosophy that I may consider using in replacement of Compiz + Gnome 2 or XFCE.  The facts that many features of gnome-tweak-tool are grey out suggest that future Gnome versions will allow more configuration.  Maybe Gnome 3.2 is still a bit too young to be satisfying right now, but it is clearly something that I will keep in mind.

As I wrote in my previous post, I will install Linux Mint tomorrow or the day after.  According to forums, many Ubuntu users disappointed by Canonical since 11.04 went to Mint.  I will choose Gnome 2.x + Compiz for the beginning.  Then, when Gnome 2 will be replace by Gnome 3 in a little bit less than a year, I will test it again to see how it will have aged.  Maybe it will be mature enough to satisfy both the beginners and the experienced users.  If Gnome 3 will not be good enough, I will go back to XFCE that I had used for years in the past.

According to my recent readings, I think that I will spend less time to set up a good Mint configuration than to try to suit Ubuntu to my needs.  Some complainers of this thread might consider doing the same.  I do not want to end up with an ulcer because Canonical cannot provide anymore a stable and trustworthy OS.  Unix is all about choice, including the distro.

Goodbye Canonical :)

---

### Post by coldbluesteel on 2011-10-19
Downloading Linux Mint now. 

Will test it out. My choices are either Mint, openSUSE, or maybe go old school with good ol' Debian.

---

### Post by eklikeroomys on 2011-10-20
Unfortunately for people with a limited cap hopping between distros isnt that easy. I will go back to using 10.10 for the time being, and start looking for another distro later on. Linux Mint sounds nice I will check that out too.

---

### Post by mpiter on 2011-10-20
> **eklikeroomys said:**
> Unfortunately for people with a limited cap hopping between distros isnt that easy. I will go back to using 10.10 for the time being, and start looking for another distro later on. Linux Mint sounds nice I will check that out too.

According to many users that have recently gave up Ubuntu for Mint, switching from Ubuntu to Mint is not a very difficult task. Many are happy with the change.  Since Mint 11 might be based on Ubuntu 11.04 (something that needs to be verified), it might be easier to hop from Ubuntu 11.04 than from 10.10.  So, if you cannot afford the effort now owing to resource constraints, do not switch now.  Conversely, if you can take time these days, it might be more productive to switch to Mint now instead of changing to Ubuntu 10.10 now and cope with a second change to Mint later.  Furthermore, Ubuntu 11.10 is bringing a new wave of competent dissatisfied users that are installing Mint right now in place of Ubuntu.  So it is a good moment to find help from other users (like myself or coldbluesteel) who are in the process.

> **coldbluesteel said:**
> Downloading Linux Mint now.

eklikeroomys, this is for you too.

I am likely to be a bit late for you coldbluesteel, but in doubt I prefer to give you those hints.  I do not know what you have read, but it seems that switching from Ubuntu to Mint is a bit supported.  The principle would be:
[LIST=1]
[*]Use [COLOR="Green"]etckeeper[/COLOR] to save [COLOR="green"]/etc[/COLOR] in a repository;
[*]Use [COLOR="green"]mintbackup[/COLOR] to save the list of packages that you had installed yourself after the basic Ubuntu installation;
[*]Install Mint;
[*]Restore the supplementary packages using [COLOR="green"]mintbackup[/COLOR] on Mint;
[*]Tune [COLOR="green"]/etc[/COLOR] with the help of your previously saved [COLOR="green"]/etc[/COLOR] repository.
[*]Rebuild [COLOR="Green"]/usr/local[/COLOR].
[/LIST]

Of course, user data need to be backed up and restored too.  I have not done it yet myself, so I cannot share personal experience, but here are the main Web pages I have read:

[[COLOR="Blue"]http://community.linuxmint.com/tutorial/view/2[/COLOR]]("http://community.linuxmint.com/tutorial/view/2") to understand the general Mint upgrade model and to apply it to your Ubuntu-to-Mint switch.  [[COLOR="Blue"]http://aymanh.com/version-control-linux-configuration-files-etc-etckeeper[/COLOR]]("http://aymanh.com/version-control-linux-configuration-files-etc-etckeeper") to manage [COLOR="Green"]/etc[/COLOR] in a repository.  [[COLOR="blue"]http://forums.linuxmint.com/viewtopic.php?f=46&t=83347[/COLOR]]("http://forums.linuxmint.com/viewtopic.php?f=46&t=83347") to upgrade from Ubuntu 11.04 to Mint 11 with not too much effort, including how to install [COLOR="green"]mintbackup[/COLOR] on Ubuntu.

When you have successfully restored user data on your Mint system, it is advised to erase a few hidden directories from the user home directories [COLOR="Red"]BEFORE[/COLOR] they login.  This includes [COLOR="Green"].gconf[/COLOR], [COLOR="green"].gconfd[/COLOR], [COLOR="green"].config[/COLOR], and a few others.  I do not remember where I saw the complete list.  It was in one of the links that I have just provided or in a thread related to Mint upgrade in this forum: [[COLOR="blue"]http://forums.linuxmint.com/viewforum.php?f=46[/COLOR]]("http://forums.linuxmint.com/viewforum.php?f=46").  With a little search, you will find the list.  The reason behind this is that an obsolete [COLOR="green"].gconf[/COLOR] might be more difficult to handle than a new one if you do not have exactly the same versions of the software handled by [COLOR="green"]gconf-editor[/COLOR].  Apparently, there are a little bit more tools to set up your desktop as you want on Mint than on Ubuntu.  So finding back its own old desktop configuration from scratch does not seem a big deal and might be easier than facing incompatibility problems with a previous configuration.  I have never used Mint, so I cannot confirmed this.

I am going to go through the whole process either today or tomorrow.  I will come back here within 48 hours if I find an unforeseen problem.  Good luck to you.

---

### Post by Dale61 on 2011-10-20
So much complaining about something that is FREE!  If you're not happy with the new look, you could always go back to the evil land of W!

The warning has always been to NOT upgrade a machine that is used for important tasks, like a work pc, and it is now common to wait until at least 4 weeks before upgrading said important pc's, so really, those who upgraded to 10.11 WITHOUT doing the research and finding out what changes have been made is no fault of Canonical, or Ubuntu.

There is only one person who decides to upgrade their equipment, and that person should also accept responsibility if such a simple task goes wrong.

I upgraded online, and my laptop is running better now with 11.10 than what it was with 11.04.  I also didn't like Unity at first, but the more I use it, the more it is growing on me.

Adapt to the changes, or just don't change.

---

### Post by coldbluesteel on 2011-10-20
> **Dale61 said:**
> So much complaining about something that is FREE!  If you're not happy with the new look, you could always go back to the evil land of W!

The warning has always been to NOT upgrade a machine that is used for important tasks, like a work pc, and it is now common to wait until at least 4 weeks before upgrading said important pc's, so really, those who upgraded to 10.11 WITHOUT doing the research and finding out what changes have been made is no fault of Canonical, or Ubuntu.

There is only one person who decides to upgrade their equipment, and that person should also accept responsibility if such a simple task goes wrong.

I upgraded online, and my laptop is running better now with 11.10 than what it was with 11.04.  I also didn't like Unity at first, but the more I use it, the more it is growing on me.

Adapt to the changes, or just don't change.

If the changes bring about something better than a previous product there is no problem with adapting. When the changes result in dumbing down a product so it can have more in common with lesser devices, and thereby limits or slows down the way I am able to use it, it becomes counter-productive.

Even the evil Windoze is going to an interface similar to the tablet format.

I say again. If I want to use something that looks and acts like a tablet, **_I'll BUY A TABLET_**.

I don't don't need or want an interface like this on my much more powerful laptop and PC. Especially when I can't even modify the locations of icons, panels, taskbars, etc.

What happened to the idea of "freedom" in Linux?

As you say, it is a free product. So I guess we are free to move on to other products. Products developed by those not interested in capturing the tablet / smartphone marketshare, but keeping desktop and laptop people happy.

In my opinion, Unity blows. It has blown since they first incorporated it in 11.04, and it still blows. But the fact that the developers removed the ability to use Gnome classic without having to screw around to get it back (and it's not even really Gnome classic) was simply idiotic.

---

### Post by Andryg on 2011-10-20
How can I install KDE Desktop on Ubuntu 11.10

---

### Post by nothingspecial on 2011-10-20
This thread no longer has anything to do with the original post.

@ Andryg

Please start your own thread.

Closed.

---

