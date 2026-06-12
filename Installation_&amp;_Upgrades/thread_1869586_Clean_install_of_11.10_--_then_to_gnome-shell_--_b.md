---
title: "Clean install of 11.10 -- then to gnome-shell -- beautiful, smoothly running... but.."
date: 2011-10-26
forum: Installation &amp; Upgrades
---

### Post by snoopy-2009 on 2011-10-26
Clean install of 11.10 on a new (alternate) partition -- 
then installed gnome-shell -- gnome shell DID work, wonderfully. (the CORRECT VERSION)
all is beautiful, and smoothly running... but..  

not sure what this is really... this seems like a mix between the old gnome (2?) and gnome3's gnome-shell.

      (i hope i did the screenshot correctly, attachment-manager said max width was 1024, i stuck to that..)


**i just want gnome-shell back.... the one where u hover on the "activities" menu in the top-left corner to bring up ur screen dashboard-like gui.. --with the scrollable workspace switcher on the right..**

it worked very well not too long ago, but now after reboot,  its gone... 


im not sure what happened, trying to figure out what was installed... random stuff, like i uninstalled, and then re-installed wine n some other things..

i *did however* install gtweakui  -- which i actually havent done anything with yet... maybe that caused something.. but it should have gone by my old settings, stored in my home dir. (shared across platforms)

**also, i enabled the addl FGLX driver, to see if it was compatible with gnome-shell and my gfx card yet----its not...   that *did* give me a problem right before this happened, so this could be related too...** i enabled it, restarted, booted back up and it looked like crap (what i expected from the propitery driver, same as last time i tried it, on 11.04) --so, i went to disable it, and it said it wasnt enabled--- ODD.. bec it *sure as hell looks that way!-- *so i enabled it AGAIN, rebooted, *THEN* it allowed me to disable it.. restarted, and here i am, with crap gnome-unity-mix thing... lol

i usually dont post questions often, unless im really stumped... and unfortunately, this is the case... i *TRIED* searching around a bit to try and figure it out, but im not really sure *_WHAT_ exactly i should be trying to search _FOR_*...   --point being, i ***did TRY-- ***[I]before anyone trys to say i didnt and should have..
[/I]

---

### Post by cbowman57 on 2011-10-26
alt+r-click

---

### Post by snoopy-2009 on 2011-10-26
> **cbowman57 said:**
> alt+r-click


thanks! lol simple answer for that one... 

*Now, does anyone know how i can get the gnome-shell gui back ?*

---

### Post by dino99 on 2011-10-26
into a terminal:

gnome-shell --replace

---

### Post by cbowman57 on 2011-10-26
> **snoopy-2009 said:**
> thanks! lol simple answer for that one... 

*Now, does anyone know how i can get the gnome-shell gui back ?*

From the lightdm or gdm login screen you should have a little icon that opens a menu that allows you to select GNOME or GNOME  classic, the GNOME entry is the shell.

If you select the shell, and end up in classic it is usually a problem with the video configuration.

Unless you use ATI/AMD video opening Additional Drivers (jockey-gtk) and installing the suggested driver usually cures it.

---

### Post by snoopy-2009 on 2011-10-27
> **cbowman57 said:**
> From the lightdm or gdm login screen you should have a little icon that opens a menu that allows you to select GNOME or GNOME  classic, the GNOME entry is the shell.


thanks for the help :) i appreciate the response. yup, i am aware of this-- and i tried that before posting, surprisingly, it *WAS* on  classic when i checked, but i selected just GNOME,  semi-releived thinking that was gonna be the answer... but it wasnt... as u said *next*.. 

 > **cbowman57 said:**
> 
If you select the shell, and end up in classic it is usually a problem with the video configuration.
so i take it that must be it? 

 but this following solution wont work for me, as my proprietary graphics driver (FGLRX i think?) is incompatible with something..... i dont remember to *what* *exactly*, but i know gnome-shell and this other gnome--just gnome3 w/o shell--both are completely unuseable once activated...

> **cbowman57 said:**
> 
Unless you use ATI/AMD video opening Additional Drivers (jockey-gtk) and installing the suggested driver usually cures it.and, lastly, i'm not entirely *clear* on what you're saying there..?  



in my experience, and thinking back more relating to when i struggled with getting that proprietary-driver installed, then uninstalled (once realized its still just as incompatible) what i'm thinking happened must have been to do with that situation.

so my question is, is there a way to find out a log of what the additional-drivers-program did during that process..?  it just must be missing *something*...

or what if i remove and purge gnome-shell, and reinstall again?   (or, better yet, could i just reinstall even *without* removing all the packages to redownload? --or would that need to be done as well, just to be sure nothing got corrupted there at the same time?)

if theres any specific output you'd like me to print, let me know..

thanks again


--
[3:Sixty Creative, Design, Hosting.]("http://www.3-60.com")

---

### Post by snoopy-2009 on 2011-10-27
> **dino99 said:**
> into a terminal:

gnome-shell --replace


sorry didnt see ur post there.. 

this returns the following for me, any ideas how to solve this problem? -- maybe reinstalling gnome-shell as i questioned above?

```
:~# gnome-shell --replace
gnome-shell: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```--
[3:Sixty Creative, Design, Hosting.]("http://www.3-60.com/")

---

### Post by zebx on 2011-10-27
Hi,

I have the same problem on my VPC Z21 Vaiio laptop.

On LightDM login, Unity is ok, but not for me. Gnome don't launch gnome-shell but a strange and limited Classic Gnome.

```
$ gnome-shell --replace
failed to create drawable

(gnome-shell:10791): Clutter-CRITICAL **: Unable to initialize Clutter: Unable to select the newly created GLX context
Erreur du gestionnaire de fenêtres*: Unable to initialize Clutter.

```

and 

```
$ lspci|grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

```

Any suggestion?

---

### Post by cbowman57 on 2011-10-27
@snoopy-2009, I haven't used ATI in years, just about all the success stories I've read using ATI with the shell mention they end up using the open source drivers.  I don't know how many choices you have or how to accomplish them.

@zebx, it probably booted Unity-2D for you & is likely video driver related.

---

### Post by zebx on 2011-11-07
> **cbowman57 said:**
> @zebx, it probably booted Unity-2D for you & is likely video driver related.

Many thanks for your feedback.
Could you show me the way to resolve that?

---

### Post by snoopy-2009 on 2012-01-23
> **cbowman57 said:**
> @snoopy-2009, I haven't used ATI in years, just about all the success stories I've read using ATI with the shell mention they end up using the open source drivers.  I don't know how many choices you have or how to accomplish them.



thanks so much for your feedback, sorry i apparently never got back to this thread.


i don't believe open-source drivers actually exist at this point in time. im still waiting for the correct update.  -- im not entirely sure if anyones even working on this :P lol.

everything runs fine without the FGLX driver anyway  -- well.. minus my hdmi plug, (last i checked) which i just dont try to use anymore really..

---

