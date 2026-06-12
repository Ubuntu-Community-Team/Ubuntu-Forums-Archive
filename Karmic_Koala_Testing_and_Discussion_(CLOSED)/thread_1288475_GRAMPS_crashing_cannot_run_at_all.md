---
title: "GRAMPS crashing cannot run at all"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Merovius on 2009-10-11
Sorry if this is the wrong place for this. I Have been running GRAMPS (or trying to) after update to Karmic. It crashes almost instantly or right after opening the data base. If I run it from the terminal I get this;

:~$ gramps
/usr/share/gramps/ViewManager.py:221: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips = gtk.Tooltips()
/usr/share/gramps/ViewManager.py:359: DeprecationWarning: Use the new widget gtk.Tooltip
  open_tips = gtk.Tooltips()
/usr/share/gramps/ViewManager.py:804: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.disable()
/usr/share/gramps/DataViews/GrampletView.py:1104: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tooltips = gtk.Tooltips()
/usr/share/gramps/DataViews/GrampletView.py:1105: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tooltips.set_tip(frame, msg)
/usr/share/gramps/DataViews/GrampletView.py:177: DeprecationWarning: Use the new widget gtk.Tooltip
  gui.tooltips = gtk.Tooltips()
/usr/share/gramps/DataViews/GrampletView.py:178: DeprecationWarning: Use the new widget gtk.Tooltip
  gui.tooltips.set_tip(gui.scrolledwindow, msg)
/usr/share/gramps/ViewManager.py:888: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(button, page_title)
/usr/share/gramps/Filters/SideBar/_SidebarFilter.py:44: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tooltips = gtk.Tooltips()
/usr/share/gramps/Filters/SideBar/_SidebarFilter.py:122: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tooltips.set_tip(widget, tooltip)
/usr/share/gramps/DataViews/PedigreeView.py:530: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tooltips = gtk.Tooltips()
/usr/share/gramps/DataViews/PedigreeView.py:531: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tooltips.enable()
/usr/share/gramps/DataViews/MediaView.py:281: DeprecationWarning: Use the new widget gtk.Tooltip
  self.ttips = gtk.Tooltips()
/usr/share/gramps/DataViews/MediaView.py:283: DeprecationWarning: Use the new widget gtk.Tooltip
  ebox, _('Double click image to view in an external viewer'))
Database is locked, cannot open it!
  Info: Locked by steve@steve-desktop
/usr/share/gramps/DataViews/RelationView.py:425: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tooltips = gtk.Tooltips()
** (gramps.py:2605): DEBUG: NP_Initialize
** (gramps.py:2605): DEBUG: NP_Initialize succeeded
** (gramps.py:2605): DEBUG: NP_Initialize
** (gramps.py:2605): DEBUG: NP_Initialize succeeded
** (gramps.py:2605): DEBUG: NP_Initialize
** (gramps.py:2605): DEBUG: NP_Initialize succeeded
** (gramps.py:2605): DEBUG: NP_Initialize
** (gramps.py:2605): DEBUG: NP_Initialize succeeded
Segmentation fault (core dumped)
steve@steve-desktop:~$ 

Can anybody let me know if this is a GRAMPS issue or maybe something that will come around as Karmic reaches completion? :confused:

---

### Post by dinxter on 2009-10-11
its runs fine here, are you using the most recent version?
$ apt-show-versions gramps
gramps/karmic uptodate 3.1.2-1

---

### Post by dinxter on 2009-10-11
maybe check ~/.gramps/grampsdb/ and see if the database(s) have the lock file even though they arent open, this can happen if the program has crashed at some point.

---

### Post by Merovius on 2009-10-11
Thanks for responding, I get,

gramps/karmic uptodate 3.1.2-1

Same as you.

I have found some posts on the gramps forum about deprecation errors but they don't mention crashing. I tried turning off Compiz and it will let gramps run for a minute or two but then down it goes.

I tried a reinstall but it had no effect either. Guess I'll have to keep my eyes on the forums until I see something.

---

### Post by Merovius on 2009-10-11
I will check as you advised. database has been locked a few times after crashing. I logged off/on and then forced it to unlock. (inside GRAMPS) It still crashed.

:confused:

---

### Post by Merovius on 2009-10-11
I checked the files as indicated and see no sign that they are locked...

Thanks again.

---

### Post by dinxter on 2009-10-11
deprecation warnings shouldnt be the issue, do you get the same behaviour from a clean install, ie, one where you have no pre-existing .gramps folder (dont delete this obviously!) Perhaps its something left over from settings/databases from a previous version of gramps. Remember to  
$ubuntu-bug gramps
if you still have this bug

---

### Post by Merovius on 2009-10-11
I will have to try this. Should I just rename.gramps to .gramps.old and then install fresh?

Or I could move it to another partition. Data base is on Ubuntu One so I am not worried about that to much.

---

### Post by dinxter on 2009-10-11
something like
$mv ~/.gramps ~/.gramps.backup
as long as you have a backup if you need one
Then run the program again and see if it crashes, if it does then best report the bug and add the steps taken that caused the crash if possible

---

### Post by Merovius on 2009-10-11
Thanks for the help. Will do as advised.

---

### Post by Sweevo on 2009-10-11
Not that this will help you too much, but I've just checked and get exactly the same problem as you.

Gramps opens fine, but once it tries to load my database I get the same core dump as you.

I haven't opened Gramps for quite a while, but I know that it was working fine on Alpha 4 as I tested in when I first installed the Alpha release.

---

### Post by Merovius on 2009-10-11
Well, after backing up the .gramps file and using synaptic to uninstall and reinstall I had the same issue. I decided to uninstall again and download from the GRAMPS site for the reinstall. That seems to have fixed it. Not sure why. I did loose a small amount of the last work I had done a few weeks ago. Not sure why. A few media items I had added are not there.No great loss they are still in the image cache file and can be redone.

I did file a bug and found another person had already done so. I added myself to the bug.

Thanks for all the help.

---

### Post by dinxter on 2009-10-11
can you post links to the launchpad bug or upstream report please

---

### Post by Merovius on 2009-10-11
This is the one I believe is the same as mine.

[https://bugs.launchpad.net/ubuntu/+source/gramps/+bug/448670](https://bugs.launchpad.net/ubuntu/+source/gramps/+bug/448670)

---

### Post by Merovius on 2009-10-11
I just added a note to let them know I seem to have worked it out. Hope it helps someone out.

Never put in a bug report before or commented on Launchpad. Hopefully I did it all correctly.

---

### Post by dinxter on 2009-10-11
you should change the status of the bug from new to confirmed if you suffer the same bug, lets the developers know its not a 'one off'

---

### Post by Merovius on 2009-10-11
Done.

I had no idea "I" could do that...:)

Thanks

---

### Post by Sweevo on 2009-10-11
Hi

I just tried doing the same thing (uninstalling via Synaptic and then reinstalling from the 9.04 Gramps deb file from Sourceforge) but I still get the same core dump...

Which Deb file did you use and where did you get it from?

Thanks

Sweevo

---

### Post by Merovius on 2009-10-11
I used the one for Jaunty on this page. Under Ubuntu and derivatives.

[www.gramps-project.org/wiki/index.php?title=Installation#Automatic_download_and_install_of_GRAMPS](www.gramps-project.org/wiki/index.php?title=Installation#Automatic_download_and_install_of_GRAMPS)

---

### Post by Sweevo on 2009-10-11
That's a shame - that's the same file that I've tried...

Still getting the same seg fault (core dumped) :(

Not tried a reboot yet - I'll give that a try later, although don't think it'll help.

I'll keep an eye on the Gramps bug on launchpad to see what happens

Thanks for your help

Sweevo

---

### Post by Merovius on 2009-10-11
Did you do as dinxter suggested and backup the .gramps folder? I did that first both ways I tried it.

---

### Post by Sweevo on 2009-10-11
Brilliant!

I renamed my old .gramps folder, then started Gramps - it loaded fine...

I then closed gramps and copied the grampsdb folder from my old (renamed) .gramps folder to my new .gramps folder.

I started Gramps again, selected my database and it opened and worked correctly!

Thanks so much for your help.

Sweevo

---

### Post by Merovius on 2009-10-11
Thanks to dinxter. He's the one that sent me in the right direction.

---

