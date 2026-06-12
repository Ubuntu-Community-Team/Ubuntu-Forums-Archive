---
title: "KDE 4.4 No Login / Black screen"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by Bloemetjesgordijn on 2010-02-11
Hi,

I just upgraded to 4.4 (on Kubuntu 9.10). Install went fine, only after reboot I had an issue=> No login screen (black screen)

I have googled around and found a possible solution: 
delete .kde4 and .config directory [http://forums.opensuse.org/pre-release-](http://forums.opensuse.org/pre-release-) ... creen.html  

I am a bit reluctant to delete folders. 

So the question is....does anybody have a better solution.

Thx

Bloemetjesgordijn

---

### Post by urlacher3292 on 2010-02-11
I'm having the same problem, but if I boot into recovery mode and select resume, I can login and start the kdm from the command line. From here everything seems to work fine but I would like a better fix.

---

### Post by ComputerGeek31618 on 2010-02-11
Don't know if I should post a new thread or not, since I have a slightly related KDE SC 4.4 problem. (...on two computers at once.  Yeah, I was so eager to try 4.4 that I sent two machines into the upgrade without testing on one first; I have my reward.#-o)

My computers have Kubuntu 9.10 with KDE 4.3.5.  I tried to install KDE 4.4 from the ppa backports using KPackageKit.  It seemed to want to upgrade packages in stages, and klipper wouldn't install (some sort of conflict with the old version of another package that was "blocked" from upgrading).  On my desktop, I upgraded everything but klipper.  I was able to finish, but when I logged in, the plasma desktop would die and the screen would go black.  Alt+F2, desktop effects, and applications could still run.  By using apt-get install to install the "held back" upgrades (and satisfy the klipper conflict), everything came undone.  On my laptop, I skipped ahead straight to the undone state somehow.

When I boot up normally, when the progress bar on the Kubuntu splash is 3/4 done, the screen goes into an unusual state.  The resolution is very low.  There is a blinking underscore " _ " in the top left.  White blocks that could be corrupt nonprinting ASCII characters are scattered over the screen.  Blinking on and off are more of these broken blocks in various colors in the spaces not used by the white ones.  There is a KDE pointer arrow that you can move around the screen.

On my laptop, recovery booting into "root prompt with networking" lets me access apt-get, but it says everything's fine and upgraded.  Aptitude (which I just now started to figure out) won't let me downgrade packages because of a tangled web of dependencies.

I tried using a LiveCD to edit /etc/apt/sources.list and remove the kubuntu ppa backports entry.  I'm assuming that that will make apt think that the main packages are the latest and will let me downgrade automatically.  I haven't been able to move my desktop PC downstairs to an ethernet connection (to boot into recovery mode with networking) to to try it yet.  My laptop's sources.list file seems to be hiding the entry from me, and now I've gotten aptitude into some sort of dependency nightmare.

Sorry for the long post, but I couldn't find anyone with this problem in a google or ubuntuforums search.  Does anyone have an idea how I can get back to 4.3?  (Has anyone at all been able to upgrade to 4.4 anyway?):-?

---

### Post by kovi on 2010-02-11
A workaround that works for me is that after a reboot I press ESC couple of times in the moment I see kubuntu sign with a progress bar.

---

### Post by MoeNeigh on 2010-02-11
> **urlacher3292 said:**
> I'm having the same problem, but if I boot into recovery mode and select resume, I can login and start the kdm from the command line. From here everything seems to work fine but I would like a better fix.

Same deal, everything seems to work logging in that way (recovery mode) except the sound. Kde and phonon? say none of my sound drivers work -- but they worked before.

---

### Post by ComputerGeek31618 on 2010-02-11
I can also boot into recovery mode on my desktop and run kdm from the command line.  Although this takes me to the login screen just fine, my desktop after logging on is black.  I can use the Alt+F2 to launch programs, but I have no desktop, no plasma, no taskbar, no anything.  I've googled around, and I think it may have something to do with plasma not being started.  I've also heard stuff about deleting a .kde4 folder to solve upgrade problems.  Any suggestions as to what I need to be doing?

EDIT:

I renamed my .kde folder .kdeOLDVERSION, so it would make a new .kde folder.  This was the solution to other black screen on 4.4 situations in other distros, but it didn't work for me.  I'm still googling for other solutions.

---

### Post by urlacher3292 on 2010-02-11
> **MoeNeigh said:**
> Same deal, everything seems to work logging in that way (recovery mode) except the sound. Kde and phonon? say none of my sound drivers work -- but they worked before.

We're definitly having the same problem. My sound doesn't work any more either, even though they always have before.

---

### Post by MoeNeigh on 2010-02-11
> **urlacher3292 said:**
> We're definitly having the same problem. My sound doesn't work any more either, even though they always have before.

I got my sound working again by adding the audio group to my user privileges in the user manager. I don't think I should have had to do that, but the sound returned after I did that and logged out and back in.

---

### Post by urlacher3292 on 2010-02-11
> **MoeNeigh said:**
> I got my sound working again by adding the audio group to my user privileges in the user manager. I don't think I should have had to do that, but the sound returned after I did that and logged out and back in.

Thanks for the tip.

---

### Post by DeDood on 2010-02-12
I have had tested KDE 4.4 on my laptop first (which has an Intel graphics card) and all seemed to work fine (except for the netbook workspace). On my desktop computer however I have the same probleme as **ComputerGeek31618** with the scrambled screen after the Kubuntu spalsh. My desktop has a NVidia graphics card so maybe that's the problem.

I noticed that switching between Ctrl-Alt-F7 and Ctrl-Alt-F8 a few times made the login screen appear and I coold start working in KDE. However, after a reboot I had to do the Ctrl-Alt-F7 Ctrl-Alt-F8 trick again.
It seems to mee that it are the Console screens that are scrambled and not KDE itself. Maybe KDE changes the resolution setting for the consoles or something.

Anyone an idea how to overcome this problem permanently.

---

### Post by MoeNeigh on 2010-02-12
Woohoo! After the latest round of updates (about 45 or so), I am now able to see the login screen, and am no longer in recovery mode. Thanks, developers!

AFAIK, there is only one small thing remaining (that I've noticed), I still can't access desktop wallpaper folders from the gui. I can, however, modify the kde config file at:

.kde/share/config/plasma-desktop-appletsrc

Since I am using slideshow wallpaper, I search for "slidepaths" in the config file and change the folder(s) there.

---

### Post by ComputerGeek31618 on 2010-02-12
> **DeDood said:**
> On my desktop computer however I have the same probleme as **ComputerGeek31618** with the scrambled screen after the Kubuntu spalsh. My desktop has a NVidia graphics card so maybe that's the problem.

I noticed that switching between Ctrl-Alt-F7 and Ctrl-Alt-F8 a few times made the login screen appear and I coold start working in KDE. However, after a reboot I had to do the Ctrl-Alt-F7 Ctrl-Alt-F8 trick again.
It seems to mee that it are the Console screens that are scrambled and not KDE itself. Maybe KDE changes the resolution setting for the consoles or something.

Anyone an idea how to overcome this problem permanently.

My desktop has an Nvidia GeForce 6200 and my laptop has an old ATI mobility Radeon 7500.  My desktop will log in (although it doesn't boot right on it's own), but the plasma is missing and it's black.  My laptop goes black and nothing works at all.  Possibly because of the package terror I've put it into.  I'm trying to upgrade everything back to 4.4 on my laptop right now.

I think consoles are supposed to be low resolution on purpose as a fallback, but I have no clue why it would drop to a scrambled one during bootup.  I don't necessarily think it's a graphics problem, but I wouldn't know.  Since it happened on my ATI laptop too, I'll bet it isn't Nvidia at fault.

EDIT:
[I]Through apt-get upgrade and apt-get dist-upgrade (a few times), my desktop computer is fixed and works great.  All I can say is this, KDE 4.4 is definitely the best environment ever.  No contest.  (All in my humble opinion, of course.)  It was worth the struggle.

Unfortunately, my laptop isn't any better.  I think it's a graphics problem deeper than KDE because after login, I get a mostly black, unresponsive screen.  When I first installed Kubuntu 9.10 (KDE 4.3.2?), it had some graphics issues that only worked out by fluke, and some of the old symptoms are showing at the new login prompt.  It's my old, unsupported ATI card. :(

Anyway it seems to me like the only way to upgrade successfully from 4.3 to 4.4 is to follow your package upgrade with apt-get dist-upgrade to fix dependency changes in the new packages.  Before you reboot.[/I]

---

### Post by DeDood on 2010-02-13
Yip, the last update seemd to have done the trick!

---

### Post by MoeNeigh on 2010-02-13
One little thing remains. I can't seem to change the wallpaper settings using the gui on the desktop. It brings up a black screen. The latest updates today still haven't fixed that. So looks like changing the wallpaper will have to be done from the config file for a while. Otherwise, I'm enjoying KDE 4.4.0.

---

### Post by zaug on 2010-05-17
After upgrading to Lucid, I had similar issues to what ComputerGeek31618 described in his first post; black screen after login to KDE, alt-F2 would let me start apps, widows worked correctly, etc., just no panels or desktop menus.

For me it turned out simply to be that the plasma desktop package had not been installed during the upgrade.
Simply installing it sorted the problem for me.

---

