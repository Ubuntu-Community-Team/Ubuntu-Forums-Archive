---
title: "xsplash - How to disable it ?"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by foreverubun2 on 2009-10-10
I liked the Karmic Splash screen until I updated and it went back to the color one(Which I hate). How do I go back to all-white?

PS: Devs, please make this changeable without too much terminal usage, especially no kernel header changes. Or just change it back to shut me up.

---

### Post by Devport on 2009-10-24
Come on - 2 splash screens, how useless considering the additional load / initialization times and the inconsistent user experience. In addition its a waste of work time since there already is an X splash system. Besides this I think with KMS it makes way more sense to have a non-X splash and switch to X in almost real time when its loaded. X will never load fast / early enough to be a good place for a system splash.

So how do I disable it ?

---

### Post by Xgen on 2009-10-24
Rename /usr/share/images/xsplash?

---

### Post by Devport on 2009-10-24
> **Xgen said:**
> Rename /usr/share/images/xsplash?
Like in every professional software one needs to hack arond in system files ? What about a configuration somewhere ?

---

### Post by Ichtyandr on 2009-10-24
an easy way is to remove "xsplash" package from Synaptic

---

### Post by Hallavej on 2009-10-24
> **Ichtyandr said:**
> an easy way is to remove "xsplash" package from Synaptic

That is not a solution on a netbook because it will remove desktop-switcher, ubuntu-desktop and  ubuntu-netbook-remix as well.

---

### Post by Ichtyandr on 2009-10-24
it does remove ubuntu-desktop package on the desktop version as well, but afaik isn't it a dummy package (and also the "ubuntu-netbook-remix")? 
the desktop-switcher is a deal-breaker I guess

---

### Post by ranch hand on 2009-10-24
xsplash is more than an image.  It is when xorg is coming on line.  I doubt that the GDM login will com up without it.  Might be hard to get in that way.

The boot order is usplash, xsplash, GDM, xsplash, desktop.  I do not think altering that is going to give you a happy time.

---

### Post by MacUntu on 2009-10-24
> **Devport said:**
> Like in every professional software one needs to hack arond in system files ? What about a configuration somewhere ?

Would be nice, but isn't there. Xsplash is just another program, if you don't like it, uninstall it.

---

### Post by cyberkilla on 2009-10-24
If X loads earlier on in the boot process with Karmic, even if you do remove xsplash, you might not get the usual console output instead. Idk.

---

### Post by nitrofurano on 2009-10-26
i'm curious to know about how to disable it - i used startupmanager to disable up to Jaunty, but it doesn't work on Karmic - it seems we need other tools or edit other configuration files? which are them?

---

### Post by aa.ivanov on 2009-10-27
> **ranch hand said:**
> xsplash is more than an image.  It is when xorg is coming on line.  I doubt that the GDM login will com up without it.  Might be hard to get in that way.

The boot order is usplash, xsplash, GDM, xsplash, desktop.  I do not think altering that is going to give you a happy time.

Actually it's as hard as commenting out a total of 8 (eight) lines in two GDM configuration files. 

Xsplash is hooked up for appearance on GDM initization (/etc/gdm/Init/Default) and on new session startup i.e. after login (/etc/gdm/PreSession/Default). The actual code looks like this:

```
if [ -x '/usr/bin/xsplash' ];
then
        /usr/bin/xsplash --daemon
fi
```

Commenting out the Init/Default results in black screen instead of the chocolate-brownish xsplash prior to the login screen being shown. Commenting out the PreSession/Default file results in the good old visual behavior I'm used to - Gnome being loaded and bringing my desktop to screen bit by bit.

---

### Post by ranch hand on 2009-10-27
I went a different route in getting rid of the "chocolate overdose induced diahria color image.  I choose an image for my wallpaper and use it for the menu background and replace the xsplash images with it too.  GDM uses the /usr/share/images/xsplash/bg_2560x1600.jpg image.

I think it looks kind of neat that way.

---

### Post by foreverubun2 on 2009-10-27
Is there a method for this yet? There probably should be considering Karmic comes out in 2 days.

---

### Post by opensensesolutions on 2009-10-27
Since I started testing Karmic, I have switched the boot parameters in /etc/default/grub from "quiet splash" to "noquiet nosplash" (and ran update-grub) but it still doesn't display all messages.  Now I only get the very basic usplash messages like this:
...
Starting Common Unix Printing System: cupsd
PulseAudio configured for per-user sessions
...
and not all output that any init script sends to stdout or stderr. Since this was not a problem in Jaunty I'm guessing this is a bug/oversight in Karmic.  Now do I have to rewrite all my init scripts to output all useful information specifically as usplash/lsb init messages?

I just don't understand why we should hide all of the boot up messages behind a pretty picture.  Seeing a few messages scroll by during boot up certainly won't hurt anyone, and in many cases it makes it easier to debug things if there is a hardware or network problem.  In cars they replaced useful gauges with "idiot" lights because they were cheaper, but for a computer this makes no sense.

---

### Post by aa.ivanov on 2009-10-28
I took a peek at the /usr/share/images/xsplash directory.. it looks like there are 7 background images, each optimised for a certain resolution. Plus 4 different sizes of the Ubuntu logo, as well as 4 throbber images. 

Since I have found no xsplash configuration file, I assume these images and the path to them are hardcoded in xsplash... 

Has anyone seen any documentation on xsplash?

---

### Post by MacUntu on 2009-10-28
man xsplash

---

### Post by aa.ivanov on 2009-10-28
Thanks! It summarizes it quite well :)

```
aivanov@ubuntu:~$ man xsplash
No manual entry for xsplash
See 'man 7 undocumented' for help when manual pages are not available.
```

---

### Post by MacUntu on 2009-10-28
Gnaaa, sitting at a Win-box. :)

'xsplash --help' it is. :P

---

### Post by nitrofurano on 2009-10-28
for now what i did were renaming /usr/bin/xsplash to /usr/bin/xsplash_ - but i'm affraid this doesn't last after the next update..

which .sh file calls xsplash on boot? i'm about editing it as soon as i know which file is - anyone knows?

---

### Post by 23meg on 2009-10-28
Threads merged. Please do a search before starting new threads.

---

### Post by pelle.k on 2009-10-28
> **nitrofurano said:**
> for now what i did were renaming /usr/bin/xsplash to /usr/bin/xsplash_ - but i'm affraid this doesn't last after the next update..

which .sh file calls xsplash on boot? i'm about editing it as soon as i know which file is - anyone knows?

Nah, that an ugly hack ;) If you look at the $PATH variable, you would see that **/usr/local/bin** have a higher priority than **/usr/bin**
```
echo $PATH
```
So, just create an empty file in /usr/local/bin with the same name
```
sudo touch /usr/local/bin/xsplash
```
Maybe one needs to chmod it too. I dont have karmic installed ATM so i can't tell.
```
sudo chmod +x /usr/local/bin/xsplash
```

**That said, this is an ugly hack too (sort of). Does anyone know how to disable xsplash, *properly*?**

---

### Post by nitrofurano on 2009-10-28
anyway, that tip from aa.ivanov works fine! :) (/etc/gdm/PreSession/Default and /etc/gdm/Init/Default)

anyway, "man xsplash" and "xsplash --help" doesn't works

another issue: when i were trying to see what xsplash is all about, i edited all the pictures from /usr/share/images/xsplash , writing their resolution with GIMP, and saw the 1440x900 picture were loaded in my default 1280x960 display - so, i created a 1280x960 picture from a 1280x1024 crop, and xsplash insisted on displaying 1440x900 picture.. - really weird..

---

### Post by nitrofurano on 2009-10-28
@aa.ivanov and @pelle.k - that 8 line commenting on that 2 files is useful, but when someone can improve it to be changed in a simpler way, please let us know - it's scarry how Gnome configuration tools are becoming more limited - enabling and disabling xsplash could be as simple as choosing menu:system/preferences or menu:system/administration

---

### Post by MacUntu on 2009-10-28
```
test@test:~$ sudo xsplash --help
Usage:
  xsplash [OPTION...] xsplash

Help Options:
  -h, --help               Show help options
  --help-all               Show all help options
  --help-gtk               Show GTK+ Options

Application Options:
  -g, --gdm-session        Run in gdm session
  -b, --background         Filename for background image
  -d, --daemon             Run in daemon mode
  -l, --logo               Filename for logo image
  -t, --throbber           Filename for throbber image
  -f, --frames             Number of frames for the throbber (default 50)
  -p, --pingpong           Whether to reverse throbber directions
  -x, --timeout            Timeout (in seconds - 15s by default) 
  -s, --add-signal         Add a signal to listen for.
  --display=DISPLAY        X display to use
```

Now you can change whatever you want in /etc/gdm/PreSession/Default and /etc/gdm/Init/Default.

But back to topic: I still don't understand what's wrong with simply uninstalling Xsplash if you don't want it. I mean it's not something you turn on and off on a daily basis. :-k

---

### Post by aa.ivanov on 2009-10-29
@MacUntu
The idea is that other things depend on xsplash. On a normal desktop/laptop it would uninstall ubuntu-desktop which being a meta-package does not pose a big issue. But I think I've heard a complaint from netbook users that it actually breaks something for them.

As for me - I'm just curious about the new animal on the farm. Ubuntu drops the usplash (which it reasons to be plymouth like) in favour of the rhgb-like xsplash (and the rhgb was dropped out of fedora for some time advancing plymouth). Looks interesting... to say the least :P

---

