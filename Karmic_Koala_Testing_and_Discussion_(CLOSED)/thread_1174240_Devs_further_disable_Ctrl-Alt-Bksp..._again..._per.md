---
title: "Devs further disable Ctrl-Alt-Bksp... again... perhaps."
date: 2009-05-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Kareeser on 2009-05-30
Link from the Arch Linux forums: [http://bbs.archlinux.org/viewtopic.php?id=73064](http://bbs.archlinux.org/viewtopic.php?id=73064)

Apparently, the latest xorg-server package 1.6.1.901-1 on arch disables Ctrl-Alt-Bksp on user systems even if the "DontZap" flag is set to "False" in their xorg.conf.

Ironically enough, the solution is...

... another line in xorg.conf to re-enable ctrl-alt-bksp.

```
Option "XkbOptions" "terminate:ctrl_alt_bksp"
```

Just a heads up, since Arch packages are a bit ahead... Since the update comes from upstream, I'm not sure whether it'll come to Karmic **sooner** rather than later... although I'm fairly certain Jaunty users won't have to deal with this :)

---

### Post by Gourgi on 2009-05-30
i hope it is just a mistake that xorg devs will look at it soon
it is very funny though :D

---

### Post by Kareeser on 2009-05-30
Here is the original specification:
[http://lists.freedesktop.org/archives/xorg-devel/2009-April/000627.html](http://lists.freedesktop.org/archives/xorg-devel/2009-April/000627.html)

Reading it further, it seems as though they're implementing this as a *more elegant* solution to the Ctrl-Alt-Bksp problem, and coding in a hard fix instead of relying on a Server Flag in xorg.conf. Ahem... but since the option is activated by a line in xorg.conf, it seems a little roundabout and pointless. :P

I still don't understand the reasoning behind this fiasco... it would've been easier to have Ctrl-Alt-Bksp pressed twice/thrice. Problem solved.

---

### Post by MacUntu on 2009-06-17
Seems dead now.

---

### Post by ronacc on 2009-06-17
here we go again :(

---

### Post by MacUntu on 2009-06-17
Added
```
hal_set options terminate:ctrl_alt_bksp
```
at the end of /usr/lib/hal/debian-setup-keyboard - as a workaround.

Adding
```
<merge key="input.xkb.options" type="string">terminate:ctrl_alt_bksp</merge>
```
to /usr/share/hal/fdi/policy/10osvendor/10-x11-keymap.fdi doesn't work for me (found this for Fedora and Arch).

---

### Post by tepsipakki on 2009-06-17
Why go through all that trouble, and not just check the conf named "key sequence to kill the X server" from the gnome keyboard settings?

---

### Post by MacUntu on 2009-06-17
> **tepsipakki said:**
> Why go through all that trouble, and not just check the conf named "key sequence to kill the X server" from the gnome keyboard settings?

Whew, totally missed that. When was this option introduced? =D>

---

### Post by tepsipakki on 2009-06-17
Along with the feature to set the shortcut as an xkb combo, ie. with xkeyboard-config 1.6.

---

### Post by tepsipakki on 2009-06-17
note that it will likely be configurable later on, the gui looks a bit weird since you can't change the combo from there.

---

### Post by ktp on 2009-06-17
> **Kareeser said:**
> Here is the original specification:
[http://lists.freedesktop.org/archives/xorg-devel/2009-April/000627.html](http://lists.freedesktop.org/archives/xorg-devel/2009-April/000627.html)

Reading it further, it seems as though they're implementing this as a *more elegant* solution to the Ctrl-Alt-Bksp problem, and coding in a hard fix instead of relying on a Server Flag in xorg.conf. Ahem... but since the option is activated by a line in xorg.conf, it seems a little roundabout and pointless. :P

So agreed...I could buy the old argument to disable by default but this seems like people are running out of things to do.  :lolflag:

---

### Post by ronacc on 2009-06-19
> **tepsipakki said:**
> Why go through all that trouble, and not just check the conf named "key sequence to kill the X server" from the gnome keyboard settings?

I must be dense , I can't find that conf setting . directions please .

---

### Post by Wise Ferret on 2009-06-19
> **ronacc said:**
> I must be dense , I can't find that conf setting . directions please .

Add it yourself mate ;)
Just add a custom command (in gnome keyboard shortcut or in ccsm if you use compiz), use "pkill x" as your command and define it to work with ctrl+alt+bksp.
Nice and easy.

---

### Post by MacUntu on 2009-06-19
> **ronacc said:**
> I must be dense , I can't find that conf setting . directions please .

System > Preferences > Keyboard. "Layouts" tab > "Layout Options..." > "Key sequence to kill the X server" > enable the checkbox. ;)

No way to accidentally enable this... :lolflag:

---

### Post by dagrump on 2009-06-19
Add another step for my old dumb tail to remember, just to get things to work like they're supposed too.
I guess there's a way to change it, so, it's still our OS of choice, just mix it the way you like it. 
I guess I'm just getting grumpy, & that is SO not like me.

---

### Post by ronacc on 2009-06-19
thanks MacUntu , Ihad looked in there but hadn't drilled down that last step >layout options . they sure hid that one :oops:

---

### Post by ranch hand on 2009-06-19
I just did it in System->Preferences->Keyboard Shortcuts.  Just hit "add" name and set command and then set the shortcut.

I have to admit that i never thought of doing it this way.  Seems to work and is EASY.  Nice thanks.

---

### Post by danellisuk on 2009-09-17
It is excellent that the developers have added a simple way to enable zapping again.  After enabling that setting, it didn't even require a restart to take effect.  Thanks for that one!

---

### Post by Motorhead Kaze on 2009-09-19
...I know I missed something being in Hardy for so long, but exactly WHY is ctrl+alt+bksp not set to kill X by default anymore? Is it because so many changes are now accepted on-the-fly without restarting or were people against having this preset kill option?

---

### Post by Motorhead Kaze on 2009-09-19
Actually, I don't really need to know why...

I cannot seem to get the keyboard shortcut to work. The thing will not accept ctrl+alt+bksp...insane thing. "Suspend" is what I want...no? Wish it just said "Kill X"...more hints please?

---

### Post by slakkie on 2009-09-19
> **tepsipakki said:**
> Why go through all that trouble, and not just check the conf named "key sequence to kill the X server" from the gnome keyboard settings?

Because others don't use Gnome? If a solution can be posted that helps Gnome, KDE, FVWM, etc etc etc users that is a better solution then only helping Gnome users :) IMHO.

---

### Post by dakira on 2009-10-20
Here are four ways re-enabling ctrl-alt-backspace:
[https://wiki.ubuntu.com/X/Config/DontZap](https://wiki.ubuntu.com/X/Config/DontZap)

The sad thing: dontzap did not only disable the above combo but also ctrl-alt-+ (plus). This combo would reset your display to the default resolution. That was VERY handy when a game didn't return the screen from its (800x600) resolution.

Now you have to restart X instead of just hitting a simple combo. Thanks xorg!

---

### Post by philinux on 2009-10-20
Forget all that.

Alt+SysRq+k

Kills the x session and takes you to the login screen. Simple ;)

---

### Post by dakira on 2009-10-20
> **philinux said:**
> Forget all that.

Alt+SysRq+k

Kills the x session and takes you to the login screen. Simple ;)

I assume you did not read, what I wrote above? dontzap didn't only kill ctrl-alt-backspace. It also killed ctrl-alt-plus which would reset the screen-resolution to its default. There is no replacement for that and people who actually play games with Ubuntu tend to use this a lot.

---

### Post by kansasnoob on 2009-10-20
Look and learn instead of just screaming:

[ATTACH]132578[/ATTACH]

---

### Post by Static- on 2009-10-20
```
setxkbmap -option terminate:ctrl_alt_bksp
```


just have that run in your startup items, and everything works :)

---

### Post by dakira on 2009-10-21
> **Static- said:**
> ```
setxkbmap -option terminate:ctrl_alt_bksp
```

just have that run in your startup items, and everything works :)

Nope. Doesn't re-enable ctrl-alt-plus.

---

### Post by Static- on 2009-10-21
> **dakira said:**
> Nope. Doesn't re-enable ctrl-alt-plus.


it enables ctrl+alt+bkspc 


not +

---

### Post by elewton on 2009-10-21
Should the use really be given the option of setting the kill sequence?  Isn't that an administrative thing?

---

### Post by Starks on 2009-10-21
What is CTRL+Alt+Plus supposed to do?

---

### Post by VMC on 2009-10-21
> **Starks said:**
> What is CTRL+Alt+Plus supposed to do?

Nothing, since there is no "Plus" key. As already stated, I think they mean Ctrl+Alt+Backspace.

---

### Post by seeker5528 on 2009-10-23
That's not: 'Ctrl'+'Alt'+'Plus'....

But: 'Ctrl'+'Alt'+'+'

Or: 'Ctrl'+'Alt'+'-'

To change to higher or lower screen resolutions.

Later, Seeker

---

### Post by dakira on 2009-10-25
> **Starks said:**
> What is CTRL+Alt+Plus supposed to do?

If you'd care to read just a couple of posts above you'd see my post about what it does.

dontzap not only disables CTRL-ALT-BACKSPACE but also CTRL-ALT-+. If any program (usually games) would leave you stuck in a weird screen resolution you could just hit ctrl-alt-+ and everything was back to normal. Now you have to restart the entire X-Server to get back to the default resolution.

Some might argue you could use xrandr to do that, but xrandr only works with opensource drivers. Most people I know use the nvidia or ati/amd drivers.

---

