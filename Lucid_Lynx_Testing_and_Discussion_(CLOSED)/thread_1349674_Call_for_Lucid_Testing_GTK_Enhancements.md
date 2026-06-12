---
title: "Call for Lucid Testing: GTK Enhancements"
date: 2009-12-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by castrojo on 2009-12-08
Please see here: [https://lists.ubuntu.com/archives/ubuntu-desktop/2009-December/002337.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2009-December/002337.html)

---

### Post by Regenweald on 2009-12-08
I use the gnome-core desktop, but added the ppa and getting the following updates:
```

The following packages will be upgraded:
  gtk2-engines-pixbuf libgail-common libgail18 libgtk2.0-0 libgtk2.0-bin 
  libgtk2.0-common libnautilus-extension1 nautilus nautilus-data 
9 packages upgraded, 0 newly installed, 0 to remove and 23 not upgraded.
Need to get 16.9MB of archives. After unpacking 20.5kB will be used.
Do you want to continue? [Y/n/?] y

```

will test.

---

### Post by Regenweald on 2009-12-08
Nautilus has been bricked ;) launching it gives an unresponsive window with the inability to successfully navigate.

---

### Post by nperry on 2009-12-08
Upgraded, rebooted. Can't seem to see any regression issues.

---

### Post by Regenweald on 2009-12-08
> **nperry said:**
> Upgraded, rebooted. Can't seem to see any regression issues.

Then i'll try again with ubuntu-desktop

---

### Post by gnomeuser on 2009-12-08
> **Regenweald said:**
> Nautilus has been bricked ;) launching it gives an unresponsive window with the inability to successfully navigate.

Works for me but as is noted in the announcement mail it does have some rather worrisome redraw issues now.

---

### Post by Regenweald on 2009-12-08
Seems like it's just me then. Will dig around.

---

### Post by Neon Lights on 2009-12-08
> **Regenweald said:**
> Seems like it's just me then. Will dig around.

hmm, nope, nautilus is pretty unresponsive for me as well.

---

### Post by Regenweald on 2009-12-08
> **Neon Lights said:**
> hmm, nope, nautilus is pretty unresponsive for me as well.

Please comment on your experience [here](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/491521). Thanks for the feedback.

---

### Post by Neon Lights on 2009-12-08
> **Regenweald said:**
> Please comment on your experience [here](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/491521). Thanks for the feedback.
already did, thanks :D
Opening it as root seems to fix everything but the redraw problems.

---

### Post by Regenweald on 2009-12-08
> **Neon Lights said:**
> already did, thanks :D
Opening it as root seems to fix everything but the redraw problems.
Cool :)
you know, I tried to gksudo nautilus but got an error that i did not take note of. Kind of borked my install with another issue and waiting for some dependencies to fix that. When i get back into Lucid, I'll report more.

---

### Post by RAOF on 2009-12-09
Whoops!  This kills Banshee stone-dead.

EDIT: And emacs!

---

### Post by jfernyhough on 2009-12-09
For me it kills any gksudo'd app! I think it's also killed totem...

Fun fun. :)

---

### Post by BwackNinja on 2009-12-09
There are still problems with some programs that use tray icons

Empathy works
Gnome-Mplayer works
nm-applet works
gnome-power-manager works
gnome-volume-control-applet works
Rhythmbox works
Padevchooser works
Gmpc works
Pragha works
Tomboy works
Nautilus works (the tray icon comes up during large file transfers, deletions, etc)

Pidgin fails
Transmission fails
Sonata fails
Ario fails
Banshee fails
Deluge fails (though shows its tray icon properly)
Liferea fails

Abiword and gnumeric and denemo still have general rgba drawing issues (drawing transparent some places instead of black)

---

### Post by jfernyhough on 2009-12-09
Oh sweet, sweet [ppa-purge](https://edge.launchpad.net/~xorg-edgers/+archive/ppa/+sourcepub/893290/+listing-archive-extra).

What would I do without you?

---

### Post by shakaran on 2009-12-10
How to revert to the old version? I cant use my laptop because the gnome-panel freeze.

---

### Post by MadMan2k on 2009-12-10
are there any screenshot-worth changes with the decorations already?

---

### Post by godhika on 2009-12-10
No, nothing to see. This is strictly about the new patches which make client side window decorations possible, not the upcoming (hopefully) new window borders. There is still a long way to go

---

### Post by gnomeuser on 2009-12-10
> **jfernyhough said:**
> Oh sweet, sweet [ppa-purge](https://edge.launchpad.net/~xorg-edgers/+archive/ppa/+sourcepub/893290/+listing-archive-extra).

What would I do without you?

wow, that is a lifesaver. Thank you

---

### Post by MacUntu on 2009-12-10
> **BwackNinja said:**
> Banshee fails

IIRC Banshee uses a TrayIcon instead of a GtkStatusIcon. Maybe that's the problem (unless they changed that in the meantime, can't check right now).

---

### Post by tretle on 2009-12-10
> **godhika said:**
> No, nothing to see. This is strictly about the new patches which make client side window decorations possible, not the upcoming (hopefully) new window borders. There is still a long way to go

Actually your very very very wrong with that statement. What this also does is enable rgba support by default with gtk which is a very big deal on the theming point of view. 
It will enable theme creators to work with transparency on gtk themes now and if the patch gets sorted it will have an impact on the look of lucid.
The problem with cimi's work with transparency and gtk was he used an approach which required the widgets to be rendered in the rgba color map. 
GTK used rgb and in order to have transparency work you needed to patch each application to use rgba one by one.
What this patch does on top of client side window decorations is render using rgba globally meaning in order to have transparency in gtk themes you no longer have to patch each app one by one.

Take a look at cimi's old posts on the subject of rgba gtk transparent themes to get an idea of what this patch actually enables - 

[http://www.cimitan.com/blog/2007/12/12/gtk-rgba-transparent-widgets-with-the-murrine-engine/](http://www.cimitan.com/blog/2007/12/12/gtk-rgba-transparent-widgets-with-the-murrine-engine/)

Thanks canonical for progressing the situation, without you we would still be stuck in rgb stagnation.

---

### Post by godhika on 2009-12-10
I am aware of that. I was referring to the previous poster which asked (or at least that is what I understood) if there is already something to see regarding the new window decorations which this changes to gtk are supposed to enable.

---

### Post by shakaran on 2009-12-12
I get a temporaly workaround for fix gnome-panel freeze:
Download and install the last stable package for gtk+2.0:
wget [http://archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.19.1-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.19.1-1_i386.deb)
sudo dpkg -i libgtk2.0-0_2.19.1-1_i386.deb
Reboot or start a new gnome session. For me works now.

---

### Post by phillw on 2009-12-12
> **jfernyhough said:**
> Oh sweet, sweet [ppa-purge]("https://edge.launchpad.net/%7Exorg-edgers/+archive/ppa/+sourcepub/893290/+listing-archive-extra").

What would I do without you?


ppa-purge: command not found

My desktop background, all my icons etc. have gone :-(

I've tried selecting a new background in preferences - any ideas ?

32Bit, Alpha1 up dated today. Restricted libraries enabled and 10.1 flash installed (All runnijg fine before i booted after the installation of this ppa.

Phill.

---

### Post by phillw on 2009-12-12
> **shakaran said:**
> I get a temporaly workaround for fix gnome-panel freeze:
Download and install the last stable package for gtk+2.0:
wget [http://archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.19.1-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.19.1-1_i386.deb)
sudo dpkg -i libgtk2.0-0_2.19.1-1_i386.deb
Reboot or start a new gnome session. For me works now.

Thanks, I've done that. BUT !! - if i repair broken packages - it borks, again. I'm just hoping it will not totally kill updating my system - else, as I can't purge the ppa - It's a re-install.

Phill.

---

### Post by BwackNinja on 2009-12-12
also breaks flash for me in epiphany, chromium, and midori but not firefox

---

### Post by shakaran on 2009-12-12
> **phillw said:**
> Thanks, I've done that. BUT !! - if i repair broken packages - it borks, again. I'm just hoping it will not totally kill updating my system - else, as I can't purge the ppa - It's a re-install.

Phill.

Remove the ppa ubuntu-desktop with:
$ gksudo software-properties-gtk
Go to other software tab and uncheck the ppa for ubuntu-desktop, then do:
sudo apt-get update
And you can upgrade your packages normally again (I hope)

---

### Post by phillw on 2009-12-12
```
$ gksudo software-properties-gtk
```

Gives 
```
Gtk-Message: Failed to load module "atk-bridge": libatk-bridge.so: cannot open shared object file: No such file or directory

```

The library window opens & I can uncheck the desktop ppa - It then updates package list. Closing the window gives me 

```
(gksudo:7506): GLib-CRITICAL **: g_str_has_prefix: assertion `str != NULL' failed

```

I hope that means something to you !!

Bear in mind, that I am runnning the 'fix' from above.

I'll wait doing the update until I hear back ;-)

---

### Post by Starks on 2009-12-12
I'm normally the first person to hop on PPA testing, but this is breaking far too many things from a usability standpoint right now.

---

### Post by shakaran on 2009-12-12
> **phillw said:**
> ```
$ gksudo software-properties-gtk
```

Gives 
```
Gtk-Message: Failed to load module "atk-bridge": libatk-bridge.so: cannot open shared object file: No such file or directory

```

The library window opens & I can uncheck the desktop ppa - It then updates package list. Closing the window gives me 

```
(gksudo:7506): GLib-CRITICAL **: g_str_has_prefix: assertion `str != NULL' failed

```

I hope that means something to you !!

Bear in mind, that I am runnning the 'fix' from above.

I'll wait doing the update until I hear back ;-)

Have you init with gnome-session xterm?
You need a gnome enviroment up.
On splash login choose xterm on combobox session. Then enter your user and password and a terminal show. Then write just there the commands that I said.

---

### Post by BwackNinja on 2009-12-12
I guess its not so much that this patch is broken, but rather that everything else isn't prepared for this. Embedding things with a different colormap doesn't work, so gstreamer video apps fail, gnome-mplayer fails, and things that use TrayIcon instead of gtkStatusIcon fail. The only further problem is clearing things to 0 (which in rgb is black, but is transparent in rgba) rather than specifically saying rgb black.

---

### Post by phillw on 2009-12-12
From my running of the 'work-around' here's how i got back to full updating, with a desk-top

Carried out the temp-fix, as above

>                                   **Re: Call for Lucid Testing: GTK Enhancements**             
                                                                I get a temporaly workaround for fix gnome-panel freeze:
Download and install the last stable package for gtk+2.0:
wget [http://archive.ubuntu.com/ubuntu/poo...9.1-1_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.19.1-1_i386.deb")
sudo dpkg -i libgtk2.0-0_2.19.1-1_i386.deb
Reboot or start a new gnome session. For me works now.
                                                                                               Followed by

> Remove the ppa ubuntu-desktop with:
$ gksudo software-properties-gtk
Go to other software tab and uncheck the ppa for ubuntu-desktop, 
allowed the update of the package list & accepted the errors.
Did NOT allow it to update
Followed by 

```

cd /var/lib/dpkg
sudo mv status status.bak
sudo mv status-old status
sudo apt-get update

```Reboot

:popcorn:

Thanks to Sazaam who posted a method to fix a messup up dpkg/status file 

I'm bookmarking in case I ever need it again --> [http://ubuntuforums.org/showthread.php?t=1352725](http://ubuntuforums.org/showthread.php?t=1352725)

I'll be happy to 'a playing' again when some of the dust settles :P

Regards,

Phill.

---

### Post by plun on 2009-12-25
> **whiprush said:**
> Please see here: [https://lists.ubuntu.com/archives/ubuntu-desktop/2009-December/002337.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2009-December/002337.html)

Well.... this call was strange, "empty rooms"....:)

---

### Post by durand on 2009-12-25
> **phillw said:**
> From my running of the 'work-around' here's how i got back to full updating, with a desk-top

...

Thanks a LOT!

---

### Post by BwackNinja on 2009-12-25
Any real news on this? I've been hoping for applications to be rgba capable for a long time now.

---

### Post by gnomeuser on 2009-12-25
> **BwackNinja said:**
> Any real news on this? I've been hoping for applications to be rgba capable for a long time now.

Right now it's both vacation time and there are other fires to put out, but the work is slated for inclusion in alpha 2. Given that it would be unwise to throw in shortly before the Alpha 2 release I would expect the code to enter the repo and cause some degree of pain short after the New Year. The alternative to such a schedule would be to push inclusion back to post Alpha 3 and then we are starting to be close to the feature freeze with also isn't desirable.

Logic says that if this goes in it will happen soon, right now though I think the relevant developers are happily enjoying their families and vast amounts of food. Historically the time around Christmas and New Years aren't expected to be that productive at least.

---

### Post by plun on 2009-12-26
> **gnomeuser said:**
> 
Logic says that if this goes in it will happen soon, right now though I think the relevant developers are happily enjoying their families and vast amounts of food. Historically the time around Christmas and New Years aren't expected to be that productive at least.

Well, it was posted 2 weeks ago and now its vacation time.

If a developer makes a "Call for testing" he/she must follow his "call" !

I dont think its a good idea to run tests within a "closed" mailing list.

Move the test to a forum !  (but then we have the "noob challenge"....)

It must be better routines for testing software anyway !!!

---

### Post by 23meg on 2009-12-26
ubuntu-desktop isn't a closed mailing list by any means, the announcement has been mirrored on the forums too in this very thread, and in any case, the desired feedback mechanism wasn't the mailing list but [a (meta)bug]("https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/491521"); you're supposed to post your feedback there.

The bug has seen plently of activity (updates to the patch, discussion, new affected components) since the announcement was made.

---

### Post by gnomeuser on 2009-12-26
I have to say that this feature renders the desktop entirely unusable. My panels disappeared, nothing starts, there's no flash, chromium renders strangely. I am feeling less and less confident that this can be brought to work in just 2 small weeks as is supposedly the plan.

It's very hard to test and report problems when the damage is so extensive, my fear is that when we solve the problems reported now there will be a whole slew of issues underneath which we can't see on account of the desktop being so broken now.

There also hasn't been an update to the ppa since the 9th, I was assuming that all fixes would go through there rather than the main repo for testing purposes.

In other words, for all practical purposes, this is untestable and the developer requesting the testing to be done appears to have some what lost interest in the feedback (it's also been 10 days since any developer reported checking in a fix to any problem reported in the metabug).

I wish Cody would have displayed a bit more responsibility for his call for testing, now those of us who really want to help are left with unusable desktops and a feeling that nothing is being done about it.

---

### Post by plun on 2009-12-26
> **23meg said:**
>  the desired feedback mechanism wasn't the mailing list but [a (meta)bug]("https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/491521"); you're supposed to post your feedback there.

The bug has seen plently of activity (updates to the patch, discussion, new affected components) since the announcement was made.

OK I missed that.... strange way to perform software testing anyway.

I then just followed MacUntus excellent advice earlier in the thread and performed a ppa-purge. Problem solved !

---

### Post by Regenweald on 2009-12-26
I actually had to re-install due to this and a xorg problem and have since avoided this particular 'test'. It's just too broken for me to make a productive contribution at my level.

---

### Post by BwackNinja on 2009-12-26
The discussion on the gnome bug for client side window decorations is more interesting, but it doesn't really address what is there in the call for testing and the launchpad bug. RGBA by default does not trigger RGBA in the murrine engine for me (despite that I think that it should to be able to see problems in the drawing of custom widgets such as the ones in gnome-system-monitor, which is ironically a program with RGBA by default). I think it should because any program that would work with RGBA there should also work with RGBA in the murrine engine.

Theres also how terribly this breaks the desktop, how gnomeuser has said, but the client side window decorations, the point of this change, is still in heavy development, and I don't think this will make it for Alpha 2, and maybe not even for lucid.

The lack of changes in the PPA is understandable, because I doubt that its packages there that are broken, but instead apps that are not ready for RGBA are the ones that need to be changed, and these changes should be going upstream anyway and fit well in the packages in the repos. It is disappointing though how few applications are mentioned in the bug report, especially considering how many I found broken. The xembed problems are probably the worst to get through though.

I'm also disappointed I haven't seen the tooltips that are talked about being in fedora. [http://blogs.gnome.org/mccann/2009/11/01/just-leave-it-on-the-counter/](http://blogs.gnome.org/mccann/2009/11/01/just-leave-it-on-the-counter/)

---

### Post by phillw on 2009-12-26
As a tester, I cannot speak for all. But, we don't mind testing stuff out, even if it breaks our system & we have to scurry around, do some patches - or even a new install. We accept that is the way it is.

**But** when there have been so many reporting back problems, it'd be nice if those in charge of the package could come along and let us know if the problems we've faced have been resolved, if necessary - take the request down for a while - or, at least update the 1st posting to let us know what is going on. Doing the 'chat' about progress in other places is, quite frankly, not good enough. If you post on here for volunteers - you keep the volunteers appraised of the development and where you are with 'bug-fixing'. That, to me, is only polite.

And, yes, when the developers post back with an update - I will quite be more than happy to give it another run on my system - But **not** untill they do so.

Just my $0.02
Phill.

---

### Post by gnomeuser on 2009-12-27
> **phillw said:**
> As a tester, I cannot speak for all. But, we don't mind testing stuff out, even if it breaks our system & we have to scurry around, do some patches - or even a new install. We accept that is the way it is.

Absolutely one of the mental boxes you tick off when agreeing to run the development version of Ubuntu is "I understand this might break and make me a sad panda". 

Personally I got fed up with the lack of incoming fixes, the fact that every day something new seemed to stop working that for the time being I backed out of testing (all the way down to Karmic in fact but that is just a personal choice and shouldn't reflect poorly on Lucid as a whole which has been very stable for me). Sadly nobody wins in that scenario, but for now, this remains untestable.

---

### Post by 23meg on 2009-12-27
I just do a [PPA purge]("https://launchpad.net/ppa-purge") in this kind of scenario. Or at worst, a reinstall takes twenty minutes. Not a big deal.

---

### Post by gnomeuser on 2009-12-27
> **23meg said:**
> I just do a [PPA purge]("https://launchpad.net/ppa-purge") in this kind of scenario. Or at worst, a reinstall takes twenty minutes. Not a big deal.

ppa-purge is indeed a wonderful tool, however when I did that in this specific case the machine hit another error and being halfway done or something first left the machine in a state where X didn't come up - trying to fix that by reinstalling and reconfiguring the driver (thank you nvidia, your driver is ever so wonderful) caused a dkms error that took my boot away. 

ppa-purge in some cases will not allow graceful recovery: 

time invested in fixing error and the errors of errors > time spend reinstalling. It might not be pretty but it gets the job done. 

As an added bonus I got to clean out a lot of crust this way and I got to go back and this time remember to turn on home directory encryption.

---

### Post by Regenweald on 2010-01-01
Will we see more progress in alpha 2 ?

[ Edit, milestones already up. Hope they make it :D](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/491521)

---

### Post by gnomeuser on 2010-01-02
> **Regenweald said:**
> Will we see more progress in alpha 2 ?

[ Edit, milestones already up. Hope they make it :D](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/491521)

12 days till release (meaning freeze is likely to happen in about 10 days).

10 days to fix all the issues seems unlikely, getting enough of them to have a working release (with post alpha 2 updates to fix lesser used applications) seems unlikely depending on how you define essential. 

However the pace at which issues are reported compared to how quickly they have been fixed so far, unless a major effort is undertaken I remain ununconvinced this will happen for Alpha 2.

That is not a bad thing as such, this has not just the potential but the assurance to break a lot of things and alpha 2 has enough other issues to deal with as it is. The time is probably better spent fixing those and doing work on this feature post alpha 2. That would still give a lot of time to update the PPA with fixes to a point where this could be merged before the feature freeze on Feb 25th.

---

### Post by rednus on 2010-01-02
[ATTACH]142110[/ATTACH]My first issue after installing ppa is that i dont have background..

---

### Post by gnomeuser on 2010-01-02
> **rednus said:**
> [ATTACH]142110[/ATTACH]My first issue after installing ppa is that i dont have background..

Thank you for reporting a problem, however it is prefered that you do so to the bug report. 

Additionally this issue has already been reported, please check the bug report for a full list of known problems.

---

### Post by Bratwurstler on 2010-01-02
Hey,

sorry, if this was already discussed, but what can we expect from RGBA in GTK? Are there already themes made (the murrine-ones I already know, but as far as I know murrine patches the application itself to get rgba working).

Will there be an updated/nicer gnome panel? :)


Someone got resources for me? Thanks :)

---

### Post by BwackNinja on 2010-01-02
> **Bratwurstler said:**
> Hey,

sorry, if this was already discussed, but what can we expect from RGBA in GTK? Are there already themes made (the murrine-ones I already know, but as far as I know murrine patches the application itself to get rgba working).

Will there be an updated/nicer gnome panel? :)


Someone got resources for me? Thanks :)

This (should at least) remove the need to patch applications individually because they should all end up working with it. Other engines would need to be patched to be able to take advantage of RGBA. Applications like gnome-panel should also be patched to be able to use real transparency rather than just the fake parent-relative transparency that they are using right now. There are no options and will not be any options for changing the transparency of any individual widgets in Murrine though, unless the author changes his mind.

---

### Post by phillw on 2010-01-02
> 
Thanks to Sazaam who posted a method to fix a messup up dpkg/status file 

I'm bookmarking in case I ever need it again --> [http://ubuntuforums.org/showthread.php?t=1352725](http://ubuntuforums.org/showthread.php?t=1352725)

I'll be happy to 'a playing' again when some of the dust settles :razz:


Has the, ermm, dust settled ?

I don't believe this !!! - I am spending about 95% of my time on 10.04 now.... Me thinks me had better start backing up more than just /home !!!!!

(Yes, I know we aren't supposed to - When I'm doing web-site stuff, I do reboot into 9.10 - not been that brave, yet ;-) )

This was the *only* thing that had a real go at borking it. - But, a promise is a promise ....

Phill.

---

### Post by godhika on 2010-01-05
Todays update fixed all the issues (as far as I can tell for now):guitar:

---

### Post by Starks on 2010-01-05
What updates?

---

### Post by godhika on 2010-01-05
To the ubuntu-desktop ppa. cody russel released 2 patches some hours ago. It seems now after the last 2 quiet weeks that the development is once again full steam ahead.

---

### Post by Regenweald on 2010-01-05
Added the ppa and did an upgrade, machine still functional. Tired and sleepy, will test give it a proper run through tomorrow :)

---

### Post by BwackNinja on 2010-01-05
I think you guys have the wrong idea. There have been no new changes to that ppa, but there is a new version of gtk+ in the repos, and upgrading (even when using the ppa) will give you the new version, not the version in the ppa.

False alarm, business as usual.

EDIT: Although, yes, once the changes are actually in the ppa it seems that more stuff will actually work

---

### Post by Starks on 2010-01-05
> **godhika said:**
> To the ubuntu-desktop ppa. cody russel released 2 patches some hours ago. It seems now after the last 2 quiet weeks that the development is once again full steam ahead.
He did no such thing and there have been no new builds/uploads to the PPA. What are you talking about?

There was an update for the main repo's gtk+2.0 today though: [https://launchpad.net/ubuntu/lucid/+source/gtk+2.0/2.19.2-1](https://launchpad.net/ubuntu/lucid/+source/gtk+2.0/2.19.2-1)

The diff does suggest RGBA code starting to land: [https://launchpadlibrarian.net/37457509/gtk%2B2.0_2.19.2-1.diff.gz](https://launchpadlibrarian.net/37457509/gtk%2B2.0_2.19.2-1.diff.gz)

---

### Post by godhika on 2010-01-05
you are right - mea culpa #-o. too much coffee and not enough sleep.

---

### Post by Starks on 2010-01-05
It's fine.

Besides, nothing seems broken.

How do I force themes to use RGBA?

---

### Post by BwackNinja on 2010-01-05
> **Starks said:**
> It's fine.

Besides, nothing seems broken.

How do I force themes to use RGBA?

RGBA works only in murrine, and only in apps patched for it already. If you are using a murrine theme, just change RGBA=FALSE to RGBA=TRUE in the gtkrc. You'll see the difference in gnome-system-monitor at least.

---

### Post by Starks on 2010-01-05
Well, it works, but the window border is still opaque.

---

### Post by tgpraveen on 2010-01-06
can somebody tell me if enabling this causes a jump in used system resources RAM or CPU? if so how much?
my computer is old and i want to know how much performance is being sacrificed for this.

---

### Post by tgpraveen on 2010-01-06
can somebody tell me if enabling this causes a jump in used system resources RAM or CPU? if so how much?
my computer is old and i want to know how much performance is being sacrificed for this.

---

### Post by Regenweald on 2010-01-13
I think some updates came through from the ppa that have borked panel applets  and make my screen look like the shot attached. Desktop is still usable though, this time it's mostly looks that have been affected.

---

### Post by LiquidMeson on 2010-01-13
Lookin awesome on my end! Larger Icons, half transparent frame. Cool stuff bro. Maybe little more transparency and blurring? Can also still see those black tipped edges. Awesome tho! Great to have a distro with a sense of style. :biggrin:

[http://imgurl.filetac.com/img/34374890.png]("http://imgurl.filetac.com/img/34374890.png") apparently I wasn't feeling so lucky and when to the wrong site, but whatever.

edit:lol, logout, login :p Now i'm in a similar situation as Regenweald

[http://i.imgur.com/gqyIz.png]("http://i.imgur.com/gqyIz.png")

---

### Post by maKA28 on 2010-01-13
> **LiquidMeson said:**
> Lookin awesome on my end! Larger Icons, half transparent frame. Cool stuff bro. Maybe little more transparency and blurring? Can also still see those black tipped edges. Awesome tho! Great to have a distro with a sense of style. :biggrin:

[http://imgurl.filetac.com/img/34374890.png]("http://imgurl.filetac.com/img/34374890.png")

Its cool to see how everyone's shots are different.. 

[http://img138.imageshack.us/img138/1592/myub.png](http://img138.imageshack.us/img138/1592/myub.png)

I get the borders to show up in almost everything except nautilus

---

### Post by Regenweald on 2010-01-13
> **LiquidMeson said:**
> 

edit:lol, logout, login :p Now i'm in a similar situation as Regenweald

[http://i.imgur.com/gqyIz.png]("http://i.imgur.com/gqyIz.png")

Glad to see the crazy nautilus desktop window on your screen also :D

---

### Post by ikt on 2010-01-14
> **Regenweald said:**
> I think some updates came through from the ppa that have borked panel applets  and make my screen look like the shot attached. Desktop is still usable though, this time it's mostly looks that have been affected.

I have a similar situation to report, borked applets, window manager.

---

### Post by Tompalaz on 2010-01-14
Is it worth trying or will it eat up my cat?

---

### Post by LiquidMeson on 2010-01-14
Everything is back to normal :frown:

---

### Post by Regenweald on 2010-01-15
So is transparency in the terminal still the hack, or using RGBA ?:P

---

### Post by godhika on 2010-01-15
According to the blueprints still the hack [https://blueprints.launchpad.net/ubuntu/+spec/dx-lucid-gtk-improvements]("https://blueprints.launchpad.net/ubuntu/+spec/dx-lucid-gtk-improvements")

---

### Post by Regenweald on 2010-01-15
> **godhika said:**
> According to the blueprints still the hack [https://blueprints.launchpad.net/ubuntu/+spec/dx-lucid-gtk-improvements]("https://blueprints.launchpad.net/ubuntu/+spec/dx-lucid-gtk-improvements")

Thanks, thought so :D. The desktop now has a very smooth look, I look forward to alpha 3

---

### Post by Regenweald on 2010-01-15
Question though, are these cool rgba improvements going upstream ? would be nice to see all Gnome desktops benefit from ubuntu-desktop's great work.

Edit: It also seems that some of the unnecessary padding has been done away with. More real estate for UI design, I'm glad.

---

### Post by seeker5528 on 2010-01-15
I didn't see any transparency, different combinations of controls and window borders all produced results similar to....

[Screenshot](http://home.comcast.net/~seeker5528/Screenshot-Ubuntu-rgba.png)

My trash applet on the right of the lower panel and accessibility applet on the upper panel next to the clock were borked.

Later, Seeker

---

### Post by Merk42 on 2010-01-26
Wondered why I hadn't gotten any updates since it reverted back, seems since it didn't make Alpha 2, I guess it won't be in Lucid **[at all](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/491521/comments/100)**

---

### Post by Regenweald on 2010-01-26
> **Merk42 said:**
> Wondered why I hadn't gotten any updates since it reverted back, seems since it didn't make Alpha 2, I guess it won't be in Lucid **[at all](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/491521/comments/100)**
Can't say I disagree, this needs heavy testing and support from themers. Not for a LTS. So on we go, we test in Lucid+1 then :)

---

### Post by Merk42 on 2010-01-26
> **Regenweald said:**
> Can't say I disagree, this needs heavy testing and support from themers. Not for a LTS. So on we go, we test in Lucid+1 then :)

It just feels like they 'gave up' too soon. Like if it was in the betas and not ready sure, but we're not even at Alpha 3.

---

### Post by godhika on 2010-01-26
I don't think they gave up. There where two things on the table and both needed some major modification to the gtk engine. One thing are the client side window decoration (which is still worked on) Mark announced, and the other is full rgba-support. CSS window decoration is still worked on (the single post referred to above is taken out of context, it is only about rgba), but both changes turned out to be more problematic as the desktop-team initially thought (the changes to gtk were originally scheduled for alpha 1). So we will see the new window decoration probably some time around the artwork drop.

---

### Post by Merk42 on 2010-01-26
> **godhika said:**
> I don't think they gave up. There where two things on the table and both needed some major modification to the gtk engine. One thing are the client side window decoration (which is still worked on) Mark announced, and the other is full rgba-support. CSS window decoration is still worked on (the single post referred to above is taken out of context, it is only about rgba), but both changes turned out to be more problematic as the desktop-team initially thought (the changes to gtk were originally scheduled for alpha 1). So we will see the new window decoration probably some time around the artwork drop.

I hope you're right, but what are you basing it on?
Everything [here has a milestone of Alpha 2](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/491521) and all comments seem to have stopped around Alpha 2's release.

---

### Post by godhika on 2010-01-26
I am basing my assumptions on the blueprint here: [https://blueprints.launchpad.net/ubuntu/+spec/dx-lucid-gtk-improvements]("https://blueprints.launchpad.net/ubuntu/+spec/dx-lucid-gtk-improvements") Quote : [ken-vandine] integrate patches in the gtk package: INPROGRESS . But on the other side. the work on the theme engine has the status POSTPONED. I thought work on client side window decoration was still in progress. Now I am officially confused myself. The reason why the bug report you gave seems dead, is simply because the current packages are more up to date then those in the testing ppa. Maybe they thoight they have tested enough?

---

### Post by k64 on 2010-01-26
We can only really see if this will happen once Beta 1 comes out. Until then, I don't think RGBA will be enabled by default unless otherwise specified.

This wasn't cancelled. Just delayed, if it was put off. Look at Karmic for example: It changed quite a bit starting with the Beta, and only after the Beta did it look radically different from Jaunty. It's the same pattern here.

---

### Post by gnomeuser on 2010-02-18
Let's reanimate this zombie thread with a bit of good news. Today the client side decoration work hit the Lucid repos.

[https://launchpad.net/ubuntu/+source/gtk+2.0/2.19.5-1ubuntu3/+changelog](https://launchpad.net/ubuntu/+source/gtk+2.0/2.19.5-1ubuntu3/+changelog)

---

### Post by om26er on 2010-02-20
@gnomeuser can you please explain what client side window decoration is? I have read all over the internet and no where its explained. Thanks
PS: this patch also caused cpu usage to hog

---

### Post by psyke83 on 2010-02-20
> **om26er said:**
> @gnomeuser can you please explain what client side window decoration is? I have read all over the internet and no where its explained. Thanks
PS: this patch also caused cpu usage to hog

I can't explain what client-side window decorations will be exactly, but the CPU issue (also mentioned in [another thread]("http://ubuntuforums.org/showthread.php?t=1410357")) is in the process of being fixed. Reported as bug [#523949.]("https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/523949")

---

### Post by alexmurray on 2010-02-20
See here for some info about client side decorations in GTK: [http://live.gnome.org/GTK+/ClientSideDecorations](http://live.gnome.org/GTK+/ClientSideDecorations)

---

