---
title: "Problem after installing KDE"
date: 2012-04-05
forum: Installation &amp; Upgrades
---

### Post by The_Autonomist on 2012-04-05
SO, i upgraded from 11.10 to 12.04. No issues except that my window decorations wouldn't work. So, i Googled it, and saw that someone said to install kde (kwin) so that's what i did...

Now i don't know what HAPPENED. But now, i can't log into Ubuntu. My pretty lightdm Ubuntu 12.04 log in screen is gone and has been replaced with this: 

[IMG]http://lightbox-photos.s3.amazonaws.com/photos/e681469f2a84ce11af1438a5fe3f415f_348303_lrg.jpg[/IMG]

I keep typing in my Ubuntu username and password...but it isn't working. I'm terrified because I use UBuntu 98% of the time and only log onto Win7 (which i'm on now) for iTunes.

Can someone please help me reverse this or fix this???? How do i get my regular Ubuntu back???

---

### Post by zombifier25 on 2012-04-05
Hi,
to recover windows border you have to install KDE... what kind of tips have you been reading? :P
The problem here is that when you install KDE, you chose KDM as your login manager, thus replacing the default LightDM.
OK, get in a terminal by Ctrl - Alt - F1, log in and type this
```
sudo dpkg-reconfigure lightdm
```and choose LightDM at the choices. It will bring your old login manager back.

---

### Post by UnknownFearNG on 2012-04-05
On a side note, please don't make a duplication of your problem in other threads. Keep it to one category, please.

---

### Post by 23dornot23d on 2012-04-05
[COLOR=Red]**See Post 2 ..... as this may be the quicker fix ....**[/COLOR]
beat me to reply

Other thing to consider ....

Do you have caps lock on .... ( as your username and password should still work here )

________________________

Do the following .... but write it or print it out .....

[COLOR=Blue]**Ctrl + Alt + F2 ( console )**[/COLOR]
will take you to a console
**[COLOR=Blue]Login[/COLOR]**
( you still need your username and password to get in )

once you have logged in type

[COLOR=Blue]**sudo apt-get install lightdm**[/COLOR]

it may ask you which desktop manager you want to use - choose lightdm

reboot ......
it should then log in as it did before ....

---

### Post by The_Autonomist on 2012-04-06
Thanks guys! I'm all fixed up. 

And i didn't know which thread to post in...because the issue was half and half. So i just did both? Sorry...

Would anyone happen to know why my window borders are gone, though?

i'm searched the forums and the only solution i could really find was "compiz --replace"

But when i type that in terminal i get:

> ebonilm@ebonilm-HP-Pavilion-dv6-Notebook-PC:~$ compiz --replace
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing grid options...done
Initializing move options...done
Initializing mousepoll options...done
Initializing place options...done
Initializing animation options...done
Initializing wall options...done
Initializing gnomecompat options...done
Initializing resize options...done
Initializing unitymtgrabhandles options...done
Initializing opacify options...done
Initializing session options...done
Initializing obs options...done
Initializing wobbly options...done
Initializing workarounds options...done
compiz (expo) - Warn: failed to bind image to texture
Initializing expo options...done
Initializing scale options...done
Initializing ezoom options...done
Initializing staticswitcher options...done
Segmentation fault (core dumped)

Screen geometry changed:
   0x0x1366x768

Initializing unityshell options...done
WARN  2012-04-05 23:31:42 unity.libindicator <unknown>:0 Desktop file '/home/ebonilm/.local/share/applications/nautilus-home.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-04-05 23:31:42 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-writer.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-04-05 23:31:42 unity.libindicator <unknown>:0 Desktop file '/usr/local/share/applications/google-chrome.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-04-05 23:31:42 unity <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/window62914566: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window62914566
WARN  2012-04-05 23:31:42 unity <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/application0x9821c0: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x9821c0
WARN  2012-04-05 23:31:42 unity <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/application0x9821c0: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/application0x9821c0
Setting Update "command"
Setting Update "open_effects"
Setting Update "close_effects"
Setting Update "close_random_effects"
Setting Update "minimize_effects"
Setting Update "minimize_random_effects"
Setting Update "curved_fold_amp_mult"
Setting Update "glide2_away_position"
Setting Update "toggle_handles_key"
Setting Update "opacity_matches"
Setting Update "map_effect"
Setting Update "next_key"
Setting Update "alt_tab_forward"
Setting Update "panel_opacity"
Setting Update "launcher_opacity"
Setting Update "icon_size"
Setting Update "autohide_animation"
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
Segmentation fault (core dumped)


then it just stops...

---

### Post by 23dornot23d on 2012-04-06
Can you show us a screenshot of what you have ........ now .....

or what you want to run - is it UNITY

**sudo apt-get install unity**

or gnome-shell

**sudo apt-get install gnome-shell**

or kde ?

**sudo apt-get install kde-full**

any one of these should give you a full desktop ......

---

### Post by markbl on 2012-04-06
> **The_Autonomist said:**
> 
I keep typing in my Ubuntu username and password...but it isn't working. I'm terrified because I use UBuntu 98% of the time and only log onto Win7 (which i'm on now) for iTunes.

Can someone please help me reverse this or fix this???? How do i get my regular Ubuntu back???

FFS, don't overwrite your essential OS with a beta version next time!

---

### Post by The_Autonomist on 2012-04-06
^^ that didn't happen because i upgraded to a beta over my stable OS, it happened because i was an idiot and misinterpreted something i read online. it also happened because i decided to experiment with something i didn't know about. i upgrade to betas over OS' all the time. i figured the FINAL Beta would be safe enough to upgrade to...

> **23dornot23d said:**
> Can you show us a screenshot of what you have ........ now .....

or what you want to run - is it UNITY

**sudo apt-get install unity**

or gnome-shell

**sudo apt-get install gnome-shell**

or kde ?

**sudo apt-get install kde-full**

any one of these should give you a full desktop ......

well, i was in Ubuntu Unity. but, i'm now using Gnome because the fact that my window borders are gone in Unity for NO reason was pissing me off. So, i'm using Gnome for now. 

I don't think you understood my issue though, i already have unity and gnome installed...why would i need to reinstall them. i said that my window BORDERS in Unity were missing and am asking how to get them back. i'm confused by your response. O_O

---

### Post by mörgæs on 2012-04-06
Next time please use a more informative title.

---

### Post by The_Autonomist on 2012-04-06
...do you have an idea of what's going on?

---

### Post by 23dornot23d on 2012-04-06
Your answer is here 

[http://askubuntu.com/questions/88922/window-borders-missing-gtk-window-decorator-segmentation-fault](http://askubuntu.com/questions/88922/window-borders-missing-gtk-window-decorator-segmentation-fault)

---

### Post by The_Autonomist on 2012-04-08
^^ that did NOT work for me, and i was only able to delete the .compiz-1 and .gnome-2 folders. i did not/do not have a .gconf2 folder...

BUT, i looked in the side bar of "related issues" and came across this [http://askubuntu.com/questions/85089/window-title-bars-are-disappearing](http://askubuntu.com/questions/85089/window-title-bars-are-disappearing) which DID work! atleast, it's working now.

thread marked as solved...:)

---

