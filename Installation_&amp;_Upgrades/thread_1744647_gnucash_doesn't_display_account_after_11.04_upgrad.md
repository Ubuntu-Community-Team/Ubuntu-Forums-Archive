---
title: "gnucash doesn't display account after 11.04 upgrade"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by js0000 on 2011-04-30
hi

i have a large data file for gnucash of several years in age. when i did the upgrade, gnucash starts and loads, and the main account appears to load, but there is nothing displayed. just an empty gray space where the alternating colors of the ledger should be.

the account listing loads, and i can view other smaller accounts just fine. but the main ledger does not display. however, if i click on some areas of the screen, it will display what i assume is the underlying text in the bottom status bar.

and when a window or some other graphic element 'over writes' any area, some remnants of the former image remain.

any clues?

---

### Post by tjevans on 2011-04-30
I am sorry that I have no solution, but I want to add that I have precisely the same issue after the 11.04 upgrade. 

Moreover, I have two 'accounts' in gnucash (checking and savings), and one loads fine while the other will not load precisely as described by js0000 below.

> **js0000 said:**
> hi

i have a large data file for gnucash of several years in age. when i did the upgrade, gnucash starts and loads, and the main account appears to load, but there is nothing displayed. just an empty gray space where the alternating colors of the ledger should be.

the account listing loads, and i can view other smaller accounts just fine. but the main ledger does not display. however, if i click on some areas of the screen, it will display what i assume is the underlying text in the bottom status bar.

and when a window or some other graphic element 'over writes' any area, some remnants of the former image remain.

any clues?

---

### Post by tjevans on 2011-04-30
I have tried many obvious things (wiping .gnucash, staring a new account all together and importing my data, ...).  Still the same. All accounts work fine except for Checking. 

Major bummer!

---

### Post by JoePer on 2011-04-30
I am also unable to see the end of my largest account - mu checkbook register.  I can see the first part of it by using a jump from another account, but the latest data is not displayed.  Bummer!

---

### Post by JoePer on 2011-04-30
I find the problem can be fixed by going to View->Filter By ... and changing the range of dates displayed

---

### Post by tjevans on 2011-04-30
Many thanks JoePer!

---

### Post by danacajun on 2011-04-30
I just did a fresh install of Ubuntu 11.04 and am having the same issue with my largest account.  All my other accounts are fine.  Adjusting the filter to only show a subset of the file works ok to see data.  I just set it to view from 01/01/2011 to the latest date.

I cannot remember what version of gnucash I was using before but now I am using 2.4.2.  I am not sure if the gnucash file is corrupt or there is just a bug in 2.4.2 dealing with large files.  But, I think it is a bug because I restored an older version of my gnucash files and the problem still persists.

---

### Post by up2early on 2011-04-30
Also did upgrade to 11.04 and use GNUCash 2.4.2. Same issue, account tab opens but the two checking accounts I use this for do not load in their normal tabs. Changing the date range did not help for me.

---

### Post by danacajun on 2011-04-30
Found this bug against 2.4.2 which seems to describe the problem:

[https://bugzilla.gnome.org/show_bug.cgi?id=648965]("https://bugzilla.gnome.org/show_bug.cgi?id=648965")

---

### Post by mgml on 2011-04-30
I'm experiencing the same problem and I upgraded to 2.4.5 from 

[http://www.ubuntuupdates.org/ppa/getdeb_apps?dist=natty](http://www.ubuntuupdates.org/ppa/getdeb_apps?dist=natty) 

to see if the problem was fixed in a later edition, and is not. The filter date works, but every time I close the account and re-open it, I have to re apply the filter, therefore, not a potential fix for me.

My problem has been gone away after applying the latest updates from Ubuntu.

---

### Post by sgk1945 on 2011-05-01
I had the problem after updating to 11.04.  The workaround that I found was to open the account then select "Windows" + "New window with page".  This is an extra step but at least it will work until a fix is available. - Good Luck!

---

### Post by danacajun on 2011-05-01
Thanks!  Windows > New Window with Page worked for me, too.  Not perfect but easier than setting the date filter each time and all the data is visible as well.

But, in order to get this to work I had to set my registers to not open by default in a new window:  Edit > Preferences > Register Defaults > uncheck Register opens in a new window.  Then, after opening the account, selecting Window > New Window with Page works fine.

---

### Post by radiohacker on 2011-05-01
gnucash won't even start for me.  

gnc.bin-Message: main: binreloc relocation support was disabled at configure time.

Found Finance::Quote version 1.17
The program 'gnucash' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 18683 error_code 8 request_code 142 minor_code 1)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by dlmoak on 2011-05-02
Same problem.  I mainly wanted to try 11.04 to see what the new desktop was like.  I wound up doing a fresh install of 10.10 afterwards so that Gnucash would work the way it used to.  I'll try 11.04 after the problem with Gnucash is fixed.

---

### Post by rozen on 2011-05-07
Hi,

I experienced the same problem and worried that it might be the gnucash transition from 2.2.9 to 2.4.2.  To test that idea I went back to 10.10 and built from source 2.4.5 which I have been happily using 2.4.5 for a couple of days with no problems.  

I then went back to natty and tried to build 2.4.5 there and ran into some problem with SAM which I have not been able to resolve.  My conclusion is that the port in the repository was properly built, tested or verified.

I will probably end up not doing Natty.

Don

---

### Post by lkraemer on 2011-05-09
This bug was fixed in the package [B]overlay-scrollbar - 0.1.12-0ubuntu1
[/B]
---------------
overlay-scrollbar (0.1.12-0ubuntu1) natty-proposed; urgency=low

  * New upstream release.
    - Updated blacklist:
      * -deja-dup
      * -inkscape
      * -lshw-gtk
      * +vmplayer
    - some apps show grey overlay instead orange even if the window is
      focused (LP: #771511)
    - anjuta doesn't display scrollbar after resetting the layout (LP: #771563)
  * debian/control
    - Changed maintainer to ~ubuntu-desktop

overlay-scrollbar (0.1.10-0ubuntu1) natty-proposed; urgency=low

  * New upstream release.
    - Updated blacklist:
      * vmware (LP: #770625)
      * gnucash (LP: #770304)
      * pgadmin3, codeblocks and codelite (LP: #769232)
    - liferea and cardapio requires
      GDK_POINTER_MOTION_MASK (LP: #769217) (LP: #769460)
    - liboverlay doesn't work in detached tabs (LP: #769427)
    - Scrollbar's slider appears away from the mouse (LP: #763707)
 -- Ken VanDine <email address hidden> Wed, 27 Apr 2011 10:23:24 -0400


REF:
[https://bugs.launchpad.net/ubuntu/+source/overlay-scrollbar/+bug/770304](https://bugs.launchpad.net/ubuntu/+source/overlay-scrollbar/+bug/770304)

lk

---

