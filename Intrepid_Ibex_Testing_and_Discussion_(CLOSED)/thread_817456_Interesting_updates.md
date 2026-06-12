---
title: "Interesting updates"
date: 2008-06-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Bou on 2008-06-03
Hi, There was a thread during Hardy development that people used to post new interesting updates and features. It would be handy to have something similar for Intrepid, so there it goes :)

Nautilus was updated today; now it has better keyboard navigation -pressing right on the right end will bring you to the next row, and vice versa- and a new view mode - I think it's called compressed mode.

Keep them coming!

---

### Post by disturbedite on 2008-06-04
how about jonathan riddell's kde 4.1b1 packages that break the system!  lol
only cuz the rest of the packages that certain kde packages depend on have not hit the repo yet.

---

### Post by Eclipse. on 2008-06-04
> **disturbedite said:**
> how jonathan riddell's kde 4.1b1 packages that break the system!  lol
only cuz the rest of the packages that certain kde packages depend on have not hit the repo yet.

kde4.1beta1 works fine with me, not that I tried it out for long though.

---

### Post by ccw on 2008-06-04
firefox 3.0 rc1 has been in for a week or so (its also in hardy-proposed BTW)

Perl 5.10 and gcc 4.3 are in

I'm seeing gnome 2.23 branch packages trickling in.

The transition to KDE4 as default has begun. I haven't logged into a kde session yet, but I suspect its in a broken state.

---

### Post by ccw on 2008-06-16
Via evolution backend updates: dependency on libdb4.7 has been introduced.

Almost everything else is dependent on libdb4.6. Is there a planned transition to the new branch?

---

### Post by caryb on 2008-06-16
> kde4.1beta1 works fine with me, not that I tried it out for long though.

I wonder what I'm doing wrong or have missing:confused: until I can install kde4-core I basically have a kde4 shell to work with.



Cary

---

### Post by ccw on 2008-06-17
First 2.6.26 branch kernel came in this morning.

---

### Post by BCurtisWX on 2008-06-17
> **ccw said:**
> First 2.6.26 branch kernel came in this morning.

What type of improvements come in kernel updates, i never understood that.  Any help would be appreciated!

---

### Post by plun on 2008-06-17
> **BCurtisWX said:**
> What type of improvements come in kernel updates, i never understood that.  Any help would be appreciated!

Linus messages can be read at Kerneltrap

[http://kerneltrap.org/Linus_Torvalds](http://kerneltrap.org/Linus_Torvalds)


Ubuntus kernel team then apply s Ubuntu specific patches.

---

### Post by ccw on 2008-06-17
> **BCurtisWX said:**
> What type of improvements come in kernel updates, i never understood that.  Any help would be appreciated!

Here's what changed from 2.6.24 to 2.6.25. The 2.6.26 branch is still in development:

[http://kernelnewbies.org/LinuxChanges](http://kernelnewbies.org/LinuxChanges)

Does anyone know if there were major changes in either SATA HD or ext3?

I booted up to 2.6.26 and thought I was about to drop my HD (maxtor 6y080m0), it was scraping like crazy. I booted back to 2.6.24 and it went back to normal.

I skimmed through changelogs but nothing stood out.

---

### Post by cecilpierce on 2008-06-17
I've had the 26 kernel for a day and a half and I though I was hearing things with that cracklin noise.
The hard drive light is not on when the noise is, weird!
The kernel works great but the drive will soon smoke I guess, anybody know why ?
Thanks.
:confused:

---

### Post by ccw on 2008-06-17
> **cecilpierce said:**
> I've had the 26 kernel for a day and a half and I though I was hearing things with that cracklin noise.
The hard drive light is not on when the noise is, weird!
The kernel works great but the drive will soon smoke I guess, anybody know why ?
Thanks.
:confused:

I think its the HD? Maybe its the speaker though?

---

### Post by plun on 2008-06-17
> **ccw said:**
> I think its the HD? Maybe its the speaker though?

No HD problems for me but I have rather high CPU and xorg is stucked on 20-30%.  It can be a compiz problem.

First I also got stuttering and crackling sound but it was solved withelp
from psyche83 excellent guide.

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

(relevant parts)  

-----------------------------------------------------

Pure eye-candy update today from Mac Slow....:)

[https://lists.ubuntu.com/archives/intrepid-changes/2008-June/001946.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-June/001946.html)

---

### Post by adamorjames on 2008-06-17
An interesting update:
Synaptic now has something called "Quick search". It uses Xapian I read.

---

### Post by durand on 2008-06-17
> **Bou said:**
> Hi, There was a thread during Hardy development that people used to post new interesting updates and features. It would be handy to have something similar for Intrepid, so there it goes :)

Nautilus was updated today; now it has better keyboard navigation -pressing right on the right end will bring you to the next row, and vice versa- and a new view mode - I think it's called compressed mode.

Keep them coming!

It's compact view. Nautilus also feels a lot faster than hardy's version (or is it just me).

---

### Post by Exsecrabilus on 2008-06-17
Are you guys all talking about Intrepid?

If so, how do you know of all these features?
Did Alpha1 get released?

---

### Post by ccw on 2008-06-17
> **Exsecrabilus said:**
> Are you guys all talking about Intrepid?

If so, how do you know of all these features?
Did Alpha1 get released?

Intrepid repos are open. Alpha CDs are just periodic snapshots/milestones of those repos.

[https://launchpad.net/ubuntu/intrepid/](https://launchpad.net/ubuntu/intrepid/)

---

### Post by ccw on 2008-06-17
> **plun said:**
> 
First I also got stuttering and crackling sound but it was solved withelp
from psyche83 excellent guide.

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)


Did you experience this with 2.6.26, or was this an earlier issue (references hardy)?

My issue is definitely 2.6.26-1 kernel related. 2.6.24-19 is fine.

---

### Post by plun on 2008-06-17
> **ccw said:**
> Did you experience this with 2.6.26, or was this an earlier issue (references hardy)?

My issue is definitely 2.6.26-1 kernel related. 2.6.24-19 is fine.

This is on a Audigy2 card. I have had some trouble with crackling/stuttering sound with 2.6.24,  worse with the 2.6.25 kernel
until I found this guide.

With 2.6.26 it was horrible, for example listening to LastFM.

I enabled the Ladspa plugin /the equalizer and I have been adjusting
these values

```
default-fragments = 8
default-fragment-size-msec = 5 

```

A little crackling is left (sometimes) and its clearly CPU related.

Hopefully also "psyche83" can comment this.

---

### Post by ShirishAg75 on 2008-06-17
> **plun said:**
> No HD problems for me but I have rather high CPU and xorg is stucked on 20-30%.  It can be a compiz problem.

First I also got stuttering and crackling sound but it was solved withelp
from psyche83 excellent guide.

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

(relevant parts)  

-----------------------------------------------------

Pure eye-candy update today from Mac Slow....:)

[https://lists.ubuntu.com/archives/intrepid-changes/2008-June/001946.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-June/001946.html)

Its also running high on my CPU, although xorg is good .
Sound is also an issue at my end on an Intel internal sound card

shirish@Mugglewille:~$ lspci | grep audio
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)

Going down on 2.6.24-17 generic solves the issue. 

Another thing padevchooser fails to open at my end. Please see if anybody has anything to add the same. 

[https://bugs.launchpad.net/ubuntu/+source/padevchooser/+bug/240761](https://bugs.launchpad.net/ubuntu/+source/padevchooser/+bug/240761)

All and any help appreciated.

---

### Post by | MM | on 2008-06-19
> **adamorjames said:**
> An interesting update:
Synaptic now has something called "Quick search". It uses Xapian I read.

This is interesting... how quick is "Quick"?

---

### Post by Exsecrabilus on 2008-06-19
And where is Quick Search?

---

### Post by adamorjames on 2008-06-19
It is to the right of the Properties icon.

How quick is it:
Well I have seen some problems. Say you type in "comp", it doesn't show compiz as one of the results. You have to type "compiz" to get compiz to show. Hopefully this will get worked out. I still prefer the normal find (ctrl + f).

---

### Post by ccw on 2008-06-26
Dark theme just came in.

---

### Post by fluteflute on 2008-06-26
> **ccw said:**
> Dark theme just came in.
Screenshot please? :D

---

### Post by psyke83 on 2008-06-26
> **fluteflute said:**
> Screenshot please? :D

Your wish is our command... ;)

The new theme set as default is called NewHuman, and the original Human-Murrine is still available (with some slight enhancements) for people who prefer lighter colours. Screenshots attached.

Hardy users can try these themes using Kenneth Wimer's PPA: [https://launchpad.net/~kwwii/+archive](https://launchpad.net/~kwwii/+archive)

Any constructive feedback on the themes would be appreciated by the art team, I'm sure.

---

### Post by soccerboy on 2008-06-26
> **psyke83 said:**
> Your wish is our command... ;)

The dark theme is called NewHuman, and the original Human-Murrine is still available (with some slight enhancements). Screenshots attached.

Hardy users can try these themes using Kenneth Wimer's PPA: [https://launchpad.net/~kwwii/+archive](https://launchpad.net/~kwwii/+archive)

It looks hard on the eyes.  I don't think I like it too much (Yay for linux) I don't have to use it.

---

### Post by psyke83 on 2008-06-26
> **soccerboy said:**
> It looks hard on the eyes.

Yep, that's true. I think you'll find it takes some time to accommodate to a dark theme (as I learned while working on UbuntuStudio). So in time you may grow to like it (or hate it more!). Yay for choice, though... ;)

---

### Post by soccerboy on 2008-06-26
> **psyke83 said:**
> Yep, that's true. I think you'll find it takes some time to accommodate to a dark theme (as I learned while working on UbuntuStudio). So in time you may grow to like it (or hate it more!). Yay for choice, though... ;)

I saw that the HumanMurrine theme also got switched to dark colors.

---

### Post by psyke83 on 2008-06-26
> **soccerboy said:**
> I saw that the HumanMurrine theme also got switched to dark colors.

That was a temporary change in version 0.19. The dark theme is now separate.

---

### Post by ccw on 2008-06-26
> **fluteflute said:**
> Screenshot please? :D

Done.

My big complaint so far is the Firefox intergration: all of the UI elements (drop downs, text boxes) look odd in brown.

What's the expected result?: it looks brown on my desktops flat panel, but charcoal on my laptop.

---

### Post by durand on 2008-06-26
I really like this theme though dark themes are a love/hate it thing.

---

### Post by Nullack on 2008-06-26
The new theme doesnt work with the Ubuntu help and about Ubuntu pages. Blue just doesnt suit my eyes, especially on a darker background.

---

### Post by Gina on 2008-06-26
Don't like it personally - I don't like dark themes in general.  I have Ubuntu-Studio available (in addition to standard Ubuntu) and I immediately changed the theme.

---

### Post by soccerboy on 2008-06-26
Not to offend any developers but is what is stated about GObject programming in this article true
[http://www.devsource.com/c/a/Techniques/Getting-Rid-of-Gobject-Oriented-Programming/](http://www.devsource.com/c/a/Techniques/Getting-Rid-of-Gobject-Oriented-Programming/)

Is it outdated?

---

### Post by RAOF on 2008-06-27
> **soccerboy said:**
> Not to offend any developers but is what is stated about GObject programming in this article true
[http://www.devsource.com/c/a/Techniques/Getting-Rid-of-Gobject-Oriented-Programming/](http://www.devsource.com/c/a/Techniques/Getting-Rid-of-Gobject-Oriented-Programming/)

Is it outdated?

It may well be true, but it's not about what you think it's about.  It's got nothing to do with glib's object-oriented C implementation, gobject.

---

### Post by Martje_001 on 2008-06-27
Is there any change the developers drop the dark theme and just go light again? It has to look clean, IMO..

---

### Post by ccw on 2008-06-27
I think the transition to KDE 4 is complete (everything looks to be at 4.0.83). Its seems to be working. Maybe a KDE-head can give better details.

---

### Post by Lev.NL on 2008-06-27
> **Martje_001 said:**
> Is there any change the developers drop the dark theme and just go light again? It has to look clean, IMO..

I think the dark theme is used to debug GUIs in dark themes. I've read something about it some time ago but I can't remember where.

---

### Post by plun on 2008-07-22
I have seen the famous Gnome Tabs....:lolflag:

In Nautilus

[https://lists.ubuntu.com/archives/intrepid-changes/2008-July/003889.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-July/003889.html)

:)

---

### Post by durand on 2008-07-22
> **plun said:**
> I have seen the famous Gnome Tabs....:lolflag:

In Nautilus

[https://lists.ubuntu.com/archives/intrepid-changes/2008-July/003889.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-July/003889.html)

:)

It's really cool :D There's also a restore from trash feature now, very useful...

btw, any way to configure the shortcuts for the tabs?

---

### Post by plun on 2008-07-22
> **durand said:**
> It's really cool :D There's also a restore from trash feature now, very useful...

btw, any way to configure the shortcuts for the tabs?


Yup... really cool  :)   just misses PCMans root opening  

The only way I can find to handle shortcuts/tabs is with a standard right click

also

gconf-editor  >  /apps/nautilus/    but its so many settings...


Maybe I also misunderstood your question ?

---

### Post by durand on 2008-07-22
Well, I guess shortcuts don't really matter..

PS: [http://g-scripts.sourceforge.net/nautilus-scripts/Execute/Misc/root-nautilus-here](http://g-scripts.sourceforge.net/nautilus-scripts/Execute/Misc/root-nautilus-here)

---

### Post by olskar on 2008-07-22
Nice update! However;

> Require beagle 0.2.4

Why? :confused:

---

### Post by amano on 2008-07-22
Maybe this is just bad wording and Nautilus only works with beagle version 2.0.4 and up, but not with lower beagle version numbers?

---

### Post by amano on 2008-07-22
> **plun said:**
> I have seen the famous Gnome Tabs....:lolflag:

In Nautilus

[https://lists.ubuntu.com/archives/intrepid-changes/2008-July/003889.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-July/003889.html)

:)

Screenshot anyone?

---

### Post by olskar on 2008-07-22
> **amano said:**
> Maybe this is just bad wording and Nautilus only works with beagle version 2.0.4 and up, but not with lower beagle version numbers?

I hope you are right, but it says it requires in the changeslist

[https://lists.ubuntu.com/archives/intrepid-changes/2008-July/003889.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-July/003889.html)

---

### Post by andrek on 2008-07-22
> **amano said:**
> Screenshot anyone?

This is how it looks on my Intrepid machine :
[[img]http://xs229.xs.to/xs229/08302/screenshot604.png.xs.jpg[/img]](http://xs229.xs.to/xs229/08302/screenshot604.png)

---

### Post by Martje_001 on 2008-07-22
Wow, andrek, that looks beautiful. How did you get that window list (+ tray)?

---

### Post by andrek on 2008-07-22
> **Martje_001 said:**
> Wow, andrek, that looks beautiful. How did you get that window list (+ tray)?

It's tint2 and trayer.
[http://code.google.com/p/tint2/](http://code.google.com/p/tint2/)
trayer available from repos

tintrc ( /home/user/.config/tint/tintrc )
```

#---------------------------------------------
# TINT CONFIG FILE
#---------------------------------------------

#---------------------------------------------
# PANEL
#---------------------------------------------
panel_mode = multi_desktop
panel_monitor = 1
panel_position = bottom left
panel_size = 900 34
panel_margin = 0 0
panel_padding = 5 5
font_shadow = 0

#---------------------------------------------
# PANEL BACKGROUND AND BORDER
#---------------------------------------------
panel_rounded = 9
panel_border_width = 2
panel_background_color = #000000 0
panel_border_color = #000000 0

#---------------------------------------------
# TASKS
#---------------------------------------------
task_text_centered = 1
task_width = 200
task_margin = 5
task_padding = 3
task_icon_size = 0
task_font = NeutraTextLightSCAlt Bold 7.5
task_font_color = #ffffff 59
task_active_font_color = #ffffff 90

#---------------------------------------------
# TASK BACKGROUND AND BORDER
#---------------------------------------------
task_rounded = 3
task_background_color = #000000 40
task_active_background_color = #000000 55
task_border_width = 1
task_border_color = #d1d1d1 34
task_active_border_color = #d1d1d1 40

#---------------------------------------------
# CLOCK
#---------------------------------------------
#time1_format = %H:%M
time1_font = sans bold 8
#time2_format = %A %d %B
time2_font = sans 6
clock_font_color = #ffffff 75

#---------------------------------------------
# MOUSE ACTION ON TASK
#---------------------------------------------
mouse_middle = close
mouse_right = none
mouse_scroll_up = toggle
mouse_scroll_down = iconify


```

to open trayer, type ( or add to autostart ) :
> trayer --edge bottom --align right --widthtype request --height 18 --expand false --transparent true --alpha 255 --margin 8 --distance 8

---

### Post by amano on 2008-07-29
[https://lists.ubuntu.com/archives/intrepid-changes/2008-July/003942.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-July/003942.html)

>    * New upstream version:
     New features and user visible changes:
     - Added support for reading and extracting alz archives
     - Added support for rzip compressed files
     - Added support for creating self-extracting zip archives.
     - Added ability to create multi-volume archives.
     - Added support for header encryption.  Implemented header encryption for
       7zip and rar archives.
     - Use the 7z command to read/write zip, cbr, cbz archives, and to
       read cabinet, arj, rar and iso archives.
     - Try to get the mime type from magic numbers if all other methods fail.
     - Now the progress dialog is exact when adding, extracting or deleting
       files for tar, zip, rar and 7zip archives (lp: #18250)
     - Do not add the backup files, that is files ending with ~, to the archive.
     - Operations are now more efficient for archives with a long file list.
     Bugfixes:
     - Fixed bug #343201 – Use p7zip for RAR archives? (lp: #44958)
     - Fixed bug #529395 – file-roller will not open 256 AES zip files
     - Fixed bug #515194 – PK 4.5 Zip files
     - Fixed bug #519046 – add x-cbr and x-cbz support (lp: #196171)
     - Fixed bug #336790 – file-roller can't open winzip-10 encrypted files
     - Fixed bug #539629 – Create archive for Trash/Computer
     - Fixed bug #506698 – 7z Filename (header) Encryption request
     - Fixed bug #542541 – icon lookup code is broken
     - Fixed bug #504584 – Incorrect comportment when extracting multi part
       rar files.


One of the most interesting updates in GNOME 2.24 will be the improvements in file-roller: Since GNOME 2.22 it supports drag and drop to the desktop. And with the current alpha it uses 7-zip for handling zip and rar archives- which will bring a massive compatibility boost. 

As my only question remains: With file-roller now relying on p7zip to open zip files, shouldn't p7zip be promoted to main then?

Can someone try to open a zip file without p7zip installed (eg. from the live desktop): Can the file still be opened?

---

### Post by Nullack on 2008-07-29
Yeah it should be moved to main. Im going to prge rars nonfree lib from my install and test it out.

---

### Post by zombiepig on 2008-08-05
The latest batch of evolution updates let evolution directly use google contacts as an addressbook source--that's a nice unexpected bonus! :)

---

### Post by cicoandcico on 2008-08-05
> **amano said:**
> 
...
Since GNOME 2.22 it supports drag and drop to the desktop. 

let's give credit to the actual authors of the work :) : the bug was not due to file-roller, but to nautilus, that didn't support drag-and-drop. a guy ported thunar's DnD capability to gnome's file manager (see [http://ubuntuforums.org/showthread.php?t=546498](http://ubuntuforums.org/showthread.php?t=546498)). one of the side effect of his work was file-roller FINALLY working when dragging files to nautilus.

---

### Post by amano on 2008-08-05
Yes, you are right. The main effort was done by Amos Brocco (and the file-roller XDS port depended on his work). One of his patches still needs help BTW: [http://bugzilla.gnome.org/show_bug.cgi?id=171655](http://bugzilla.gnome.org/show_bug.cgi?id=171655)

---

