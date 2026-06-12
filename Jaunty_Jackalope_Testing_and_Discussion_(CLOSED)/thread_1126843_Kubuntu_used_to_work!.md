---
title: "Kubuntu used to work!"
date: 2009-04-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by macroshaft on 2009-04-15
I'm generally a ubuntu user but since my new desktop seems to hate it I thought I'd try kubuntu for a change. Firstly what the hell happened? I used to be able to get around this system, I've got a few questions about Jaunty.

Why can't I find VLC or kubuntu-restricted-extras in the KPackageKit utility? Is there something else I have to use? or some option I need to enable for extra repositories?

How do I do updates?

Why do I now seem to have what looks like a bad parody of vista on my desktop??

I'm beginning to wish I'd taken the time to enjoy kubuntu while it still looked and worked like kubuntu to be honest. I'm sat in front of a fresh install trying to play a video and I'm stumped!

Does anyone know why it displays any web page but ubuntuforums? (connection to server refused)

Also I'm using this on a 50" plasma, every time I reboot it resets the screen size to 1080p, I would like
a) for ubuntu to do as it's told and leave the resolution where I set it and
b) for 1080p to end at the edge of the screen instead of an inch past it on every side (ubuntu and kubuntu, verified with 2 very different machines). I'm loathed to start poking around in xorg without getting an opinion first as I know things have changed since the days of dapper in that area.

Hopefully given a few days the culture shock will wear off and I'll get to like the new go faster stripes!

---

### Post by Zorael on 2009-04-16
Yes, both vlc and kubuntu-restricted-extras are in multiverse, which you'll need to enable. There should be a repositories section in Adept Manager, or you could manually uncomment the lines in **/etc/apt/sources.list**. I'm not sure about KPackageKit.
```
$ kdesudo "adept manager" &      # not sure about this one

$ kdesudo "kate /etc/apt/sources.list" &
```

As for resolutions/picture not centered, you may find some guidelines over at [https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config).

---

### Post by dasme on 2009-04-16
> **macroshaft said:**
> I'm generally a ubuntu user but since my new desktop seems to hate it I thought I'd try kubuntu for a change. Firstly what the hell happened? I used to be able to get around this system, I've got a few questions about Jaunty.

Why can't I find VLC or kubuntu-restricted-extras in the KPackageKit utility? Is there something else I have to use? or some option I need to enable for extra repositories?

How do I do updates?

Why do I now seem to have what looks like a bad parody of vista on my desktop??

I'm beginning to wish I'd taken the time to enjoy kubuntu while it still looked and worked like kubuntu to be honest. I'm sat in front of a fresh install trying to play a video and I'm stumped!

Does anyone know why it displays any web page but ubuntuforums? (connection to server refused)

Also I'm using this on a 50" plasma, every time I reboot it resets the screen size to 1080p, I would like
a) for ubuntu to do as it's told and leave the resolution where I set it and
b) for 1080p to end at the edge of the screen instead of an inch past it on every side (ubuntu and kubuntu, verified with 2 very different machines). I'm loathed to start poking around in xorg without getting an opinion first as I know things have changed since the days of dapper in that area.

Hopefully given a few days the culture shock will wear off and I'll get to like the new go faster stripes!
 
Just do a search in KpackageKit for vlc and kubuntu-restricted-extras u will find both. Thrs no need to use any command. ;)

---

### Post by macroshaft on 2009-04-16
I can assure you neither of those packages were in KPackageKit at first install. I have to admit to being a little rusty on kde but now you've mentioned it I do recall Adept but can't find it in the graphical environment anywhere! Also there does not seem to be an equivalent to update-manager, I had to refresh the sources at command line then whatever handles the upgrades popped up of it's own accord. After this there are many vlc libraries in KPackageKit but the actual package is still absent!

Having had a little time to assimilate what I'm seeing I can confirm that ext4 is lightning fast, the new aesthetics look brilliant however the resemblance to vista is a little unnerving. I'm not so keen on how the K menu etc have been merged into one. However after months of meaning to get around to looking into why ubuntu won't install on this pc the final straw was vista not coping with hd video, I know a certain linux based distro that can!!

---

### Post by macroshaft on 2009-04-16
Adept was not installed!! I have just used KPackageKit to install it now. Surely that isn't right?

---

### Post by dasme on 2009-04-16
> **macroshaft said:**
> Adept was not installed!! I have just used KPackageKit to install it now. Surely that isn't right?

They discontinued adept in 9.04 :)

---

### Post by jbernardo on 2009-04-16
If you don't like the menu, try either enabling the classic menu (right click on the menu icon) or the lancelot applet. I find this last one nicer than the "regular" menu.

---

### Post by Asraniel on 2009-04-16
uh..... comon, take that few minutes to understand the changes in kde4.

So first, if you open kpackagekit, you can go in the options, where you can enable multiverse (there is a button there, click on it, password, popupwindows, great).
then for the updates.. you have two choices, either there is a symbol in your taskbar, or you open kpackagekit, and there is the Software Updates section. There you can click on refresh to get the new package list, and then "Apply all available updates".

Now for the "vista look", i personaly find that it looks not at all like vista, BUT, if you want something more like the old kde look, install kdeartwork. After that, rightclick on you desktop to go in the settings and there you change the plasma theme to Aya, or any other theme you would prefer.


Don't hesitate to ask questions about how kde works and how to use it.

---

### Post by dabl on 2009-04-16
Kubuntu 9.04 works just fine.  Somebody hasn't been following the news, re:KDE 4!

Most all the answers to the questions can be found here:

[http://kubuntuforums.net/forums/index.php?topic=3099811.0](http://kubuntuforums.net/forums/index.php?topic=3099811.0)

For example, #9 covers adding medibuntu repos and all the audio-video stuff.

```
sudo apt-get update && sudo apt-get dist-upgrade
``` still works well for upgrading.

;)

Regarding the demise of Adept package manager:

[http://web.mornfall.net/blog/farewell__44___adept.html](http://web.mornfall.net/blog/farewell__44___adept.html)

---

### Post by macroshaft on 2009-04-16
The first thing I did was enable multiverse but it seemed to do nothing, since updating via terminal the vlc libraries appeared and now after futher use vlc too. No idea why.

With regards to the changes to kde I do recall encountering kubuntu for the first time and loved it wheras I found ubuntu a bit klunky, this time around I was lost and it didn't feel like a plesant experience initially. It's good to know the menu can be changed although I'll stick with the default for a while to see how it grows on me.

I'm starting to play about with the looks now but again, maybe it'll look better in a day or two anyway. Out of the box I can see the new menu etc being more comfortable for windows users.

Thanks

---

### Post by dabl on 2009-04-16
Here's more help with KDE 4:

[http://kde.org/announcements/4.2/guide.php](http://kde.org/announcements/4.2/guide.php)

[http://kde.org/announcements/4.2/desktop.php](http://kde.org/announcements/4.2/desktop.php)

[http://userbase.kde.org/An_introduction_to_KDE](http://userbase.kde.org/An_introduction_to_KDE)

[http://userbase.kde.org/Plasma](http://userbase.kde.org/Plasma)

[http://userbase.kde.org/General_KDE_FAQs](http://userbase.kde.org/General_KDE_FAQs)

:p

---

### Post by macroshaft on 2009-04-16
> **dabl said:**
> Kubuntu 9.04 works just fine.  Somebody hasn't been following the news, re:KDE 4!



To all those who reply to someone having a problem with snidey superior tones, has it never occured to you that a new user shouldn't have to go through a comprehensive history lesson before having to turn the machine on!

Someone trialing the system wants everything to just make sense so when I start a fresh system and can't find packages I know for a fact exist I happen to feel that is a problem for every single one of us.

In ubuntu the update manager can be invoked from the menus, although I don't recall how that used to be done in kubuntu there is no obvious way of updating the system until it decides to offer it to you, not a bug but certainly an area for improvement.

---

### Post by SuperSonic4 on 2009-04-16
If I recall correctly it would scan whenever you told it to and would come up with an update notification in the system try which would be "adept update manager". I've always upgraded from the command line though so I can't be sure about the GUI option

---

### Post by Reiger on 2009-04-16
> **macroshaft said:**
> The first thing I did was enable multiverse but it seemed to do nothing, since updating via terminal the vlc libraries appeared and now after futher use vlc too. No idea why.

Remember on how *every* tutorial out there mentions that after adding a line to your apt repository you should run an update?

The reason is that APT keeps a local copy of the `table of contents' of the repository. (Including version info, so that is how it can detect which packages need upgrading.) So if you just added a new repository (a new line in the source.list or uncommented one) your local `toc' is no longer consistent with your sources list, which requires an update to fix (rebuilding the `toc').

Now, every upgrade command involves an update step in the process somewhere so that is how vlc etc. `suddenly popped up' in the `toc'.

---

### Post by Reiger on 2009-04-16
> **SuperSonic4 said:**
> If I recall correctly it would scan whenever you told it to and would come up with an update notification in the system try which would be "adept update manager".

Yes and since Jaunty it brings up the Upgrade menu of KPackagekit instead. ;)

---

### Post by Reiger on 2009-04-16
> **macroshaft said:**
> In ubuntu the update manager can be invoked from the menus, although I don't recall how that used to be done in kubuntu there is no obvious way of updating the system until it decides to offer it to you, not a bug but certainly an area for improvement.

With Hardy, Intrepid and Jaunty the way to update your system manually (without the shell) is to fire up your package manager of choice, update the cache (check for updates/refresh), and then apply available updates.

---

### Post by meborc on 2009-04-16
> **macroshaft said:**
> I'm generally a ubuntu user but since my new desktop seems to hate it I thought I'd try kubuntu for a change. Firstly what the hell happened? I used to be able to get around this system, I've got a few questions about Jaunty.

Why can't I find VLC or kubuntu-restricted-extras in the KPackageKit utility? Is there something else I have to use? or some option I need to enable for extra repositories?
First change your menu to classic... right click on the big K menu button and choose classic view...

Then go to system -> KPackageKit 

Then go to settings -> edit software sources... it is pretty simple and clear there...
> **macroshaft said:**
> 
How do I do updates?
There is a tab in KPackageKit - Software updates
> **macroshaft said:**
> 
Why do I now seem to have what looks like a bad parody of vista on my desktop??
Well... there are plenty of options in the system -> system settings to change the appearance

remember, the beauty is in the eye of the user... so it can look very nice for some people... (not for me though)

For web, just use firefox... or opera

dont forget to add medibuntu.org repos for some software...

number 1 fault that they made was to let the kicker menu be default... it is very hard to find stuff...

---

### Post by dabl on 2009-04-16
> **macroshaft said:**
> 

has it never occured to you that a new user shouldn't have to go through a comprehensive history lesson 




Nope, because a _new_ user would not write "Kubuntu Used To Work" -- he would write "I don't understand Kubuntu", or something like that.

However, be that as it may, I apologize for any perceived snideness in my reply -- it was not so intended.

---

### Post by Vorian on 2009-04-16
> **dabl said:**
> 

Regarding the demise of Adept package manager:

[http://web.mornfall.net/blog/farewell__44___adept.html](http://web.mornfall.net/blog/farewell__44___adept.html)

Thankfully, since *packagekit sucks so bad, Debian is picking up Adept development.  [http://www.milliways.fr/](http://www.milliways.fr/)

Hopefully we'll see it again soon <3

p.s. Kubuntu still works

---

### Post by Asraniel on 2009-04-16
i prefer kpackagekit over adept. adept was slow buggy and hard to use. kpackagekit is REALLY easy to use, and since it's used now by many distros, it will improve even more

---

### Post by Asraniel on 2009-04-16
wrong post

---

### Post by macroshaft on 2009-04-16
> **Reiger said:**
> Remember on how *every* tutorial out there mentions that after adding a line to your apt repository you should run an update?

The reason is that APT keeps a local copy of the `table of contents' of the repository. (Including version info, so that is how it can detect which packages need upgrading.) So if you just added a new repository (a new line in the source.list or uncommented one) your local `toc' is no longer consistent with your sources list, which requires an update to fix (rebuilding the `toc').

Now, every upgrade command involves an update step in the process somewhere so that is how vlc etc. `suddenly popped up' in the `toc'.

I am aware of how aptitude works, somehow I get the impression a lot of people reading this thread are missing the point. I am STILL totally ignorant of how to update the sources in kde4! This is something I have previously been able to do through common sense without touching the command line. Also why did only the libraries appear after the update and not vlc or restricted extras?

Anyhow, all working now as well as it can without having access to an updater.

---

### Post by macroshaft on 2009-04-16
Glad to hear it, but what does my choice of thread title have to do with how new user friendly/unfriendly kubuntu is? whether you say 'kubuntu used to work well' or 'how do I use kubuntu' it should be an easy process which comes naturally to the user.

Having read all the comments to date I do feel this is beginning to run away with itself. All this whole thing boils down to is I don't like KPackageKit and don't feel it's an improvement. Also it's a well known fact that the look of linux is an aquired taste that most choose to modify, as much as I am not keen on the new style I do feel that it's designed to a high standard and it looks like it could be very versatile too.

---

### Post by meborc on 2009-04-16
> **macroshaft said:**
> I am aware of how aptitude works, somehow I get the impression a lot of people reading this thread are missing the point. I am STILL totally ignorant of how to update the sources in kde4! This is something I have previously been able to do through common sense without touching the command line. Also why did only the libraries appear after the update and not vlc or restricted extras?

Anyhow, all working now as well as it can without having access to an updater.

menu -> system -> kpackagekit -> software updates -> refresh

that is the REFRESH option that you are looking for... did you include third party repos and then refreshed and still did not get vlc?

i don't see your problem, sorry :)

---

### Post by macroshaft on 2009-04-16
My problem was that this did not jump out at me at the particular moment in time I needed it to. As I have already said it's just a personal choice to not prefer this package manager. Now I've got the thing up & running I can get used to it. That is pretty much the end of it.

---

