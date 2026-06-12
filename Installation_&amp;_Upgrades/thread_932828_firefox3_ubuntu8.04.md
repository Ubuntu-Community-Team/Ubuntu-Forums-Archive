---
title: "firefox3 ubuntu8.04"
date: 2008-09-28
forum: Installation &amp; Upgrades
---

### Post by davekenny on 2008-09-28
I have tried for the past 2 days since upgrading to hardy(8.04)
to get firefox 3.0.3 working..nothing has worked. removed adobe flash. helix, vlc and so on..Opera 9.5 seems to be working fine!!

the fustrating part. my computer upstairs has 8.04 and firefox 3.0.3..it doen't crash. and has never crashed since I upgraded to 8.04 from 7.10. not once..but the screen saver works sometimes then an upgrade and it doesn't work again..

the only other thing that odd on this computer is thunderbird cannot initialize the browser's security component..??what does this mean..
any idea on how to firefox working?

-davekenny

---

### Post by darco on 2008-09-28
run Firefox from the terminal and post the results....

darco

---

### Post by davekenny on 2008-09-29
david@david-laptop:~$ firefox &
[1] 12065
david@david-laptop:~$ ** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

[1]+  Segmentation fault      firefox
david@david-laptop:~$ 

I got this when I tried to open tools->add-ons

computer
dell inspiron 1150
pulse audio not installed

-davekenny

---

### Post by Archmage on 2008-09-29
Did you try it with a new profile?

```
firefox -P
```

If this works than either one of your add-on or theme is causing the problems.

---

### Post by davekenny on 2008-09-29
that's helping it doesn't crash now but it won't load pages either.
[www.yahoo.com](www.yahoo.com) doesn't load
progress, but its time to go to work.

-davekenny

---

### Post by Bablefish on 2008-09-29
I am on a few boards and even Windows users are STILL having problem with Firefox 3. All I can suggest is use Opera instead.

---

### Post by Archmage on 2008-09-30
> **davekenny said:**
> that's helping it doesn't crash now but it won't load pages either.
[www.yahoo.com](www.yahoo.com) doesn't load
progress, but its time to go to work.

Please excuse my stupid question. But does the internet work at all on this PC? e.g. do you get any responce from this command?

```
ping www.yahoo.com
```

---

### Post by davekenny on 2008-09-30
not stupid...but opera and other browsers work fine. just not FF3..

I learn to like Opera9.5...just something else to learn. I was hoping to stay with FF on my laptop but until the problem is fixed. i'll be using Opera

is there something that i can run to compare the version of SW between my desktop( this runs FF3.0.3) and my laptop(doesn't run FF3.0.3). both are using 8.04..

the laptop ran FF3 beta 4 without problems..but I lost gnome clock applet getting FF3 beta 4 running..

-dkenny

---

### Post by spawn. on 2008-10-16
I experienced so many crashes in Firefox 3.0, I removed the upgrade and reinstalled Firefox 2 with Adobe Flash Plug-in 10, no crashes, no hassle.

---

### Post by davekenny on 2008-10-18
where did you get firefox2 ?
I have tried lots of 'fixes' but nothing works..
with flash without flash
completely removing firefox 3 and all the other verions of 3.x
tried 3.1b1 - the latest beta version - yep crashed

-davekenny

---

### Post by spawn. on 2008-10-19
Go into 'synaptic' and 'search' --type-- > firefox 2

I added quite a few repositories to the default ones from the install, but I think it should still be there. I just installed on another laptop and 2.0 was on before they hit you with update offers. But remember to remove Firefox 3.0 version and its dependents. There's only a few of them from the upgrade.

Added: Also, I upgraded to 8.10 and when I decided to go with Firefox 3.0, I haven't notice any crash issues with Flash. Keep in mind, I'm also using the default adobe flash 9.0 that is found in the default repository. ALSO, I wouldn't recommend upgrading to 8.10 just yet either. It's still fresh and there is a security bug with a key generator. Furthermore, certain packages from the upgrade were not installable. But that is one of the risks you take when you upgrade via synaptic rather than doing a clean LiveCD install.

---

### Post by spawn. on 2008-10-19
I wanted to add that I was wrong about Firefox 2 being in the default repository on my Live CD. It came from one of my newly added repositories that I included into my 'Software Sources.' It's been awhile so I'm not sure which one it came from.

Another thing, I just re-installed Ubuntu 8.04 to see which version is installed by default and with my CD it shows 3.0 but offers to installed the following as Updates:

firefox:  meta package for the popular mozilla web browser (size: 64MB)
firefox-3.0: safe and easy web browser from Mozilla (size: 1.0MB)
firefox-3.0: Support for Gnome in Mozilla firefox (Size: 25KB)
firefox-gnome-support: meta package pointing to the latest gnome-support package for firefox (size: 64MB)

When I 'unselect' those items and install my plugins (this time using the latest non-free adobe flash 10 plugin) and extensions in the already installed version, I do not experience flash related crashes. Look for the above items and mark for removal in synaptic and see if that works.


Note: if you 'unselect' any of the above firefox upgrades, it will unselect these following upgrades as well:

xulrunner-1.9: XUL + XPCOM application runner (size: 7.0MB)
xulrunner-1.9-gnome support: Support for Gnome in xulrunner-1.9 applications (size: 37KB)

---

### Post by sundy58 on 2008-10-19
Firefox 3.0.3 was locking up on me so I tried disabling add-ons after reading this thread. Google Toolbar seems to be my problem. I was trying to enlage this picture by clicking the link [http://www.ikea.com/us/en/catalog/products/40104152](http://www.ikea.com/us/en/catalog/products/40104152) and FF would freeze and force quit was the only recourse (with my very limited knowledge). After disabling Google Toolbar it works fine and I expect all the other links that were locking up FF will now work.

---

### Post by davekenny on 2008-10-19
this afternoon I tried an interesting test. I download 8.04 live cd and booted in on the computer that FF3 crashes..interesting that FF3 ran from the live cd..

so would it hurt to backup all my files and reinstalled 8.04 fresh? one of my conecerns is that the computer is dual boot. i would like to install without formatting the linux partition if this is possible. is it?

-davekenny

---

### Post by davekenny on 2008-10-31
well... i imaged all the partitions on my drive..major backup

I then booted with the 8.04 live cd...and installed without formatting the liunx partition.

ff3.03 now works
pidgin now works..

so what was wrong?? I don't know..but it now works..

:):)

---

