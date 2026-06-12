---
title: "Installing on mac x11"
date: 2011-04-13
forum: Installation &amp; Upgrades
---

### Post by Fxy on 2011-04-13
Hey all

Looking to see if it is possible to install ubuntu, kde, gnome or something on mac x11 app...

...Have done a few googles but can't find anything useful :?



Thanks in advanced

---

### Post by cfr42 on 2011-04-13
What are you trying to do exactly?

Ubuntu is an operating system - like OS X or Windows - so it isn't something you'd run with X11. 

When you use Apple's X11 application, you are doing two things. First, you are using Xwindows. This is a graphical layer a bit like Apple's Aqua interface. The difference with Xwindows is that you can use many different windows managers with it depending on how you like your windows to look and behave. The second thing launching Apple's X11 application does is it starts Apple's windows manager for X11. By default, this runs in "rootless" mode so that your Aqua desktop doesn't disappear and you can use X11 and Aqua windows at the same time.

If you prefer, you can use another window manager with Apple's X11. (Originally, I seem to remember you had to do this because Apple hadn't released their own.)

KDE and Gnome are, among other things, window managers as I understand it, though they do a lot more than this. So I don't know if you could use these as well as Apple's window manager but I'd assume not unless there is some special mode for this. You wouldn't want two applications trying to manage the windows at the same time. So if you installed KDE and/or Gnome, you'd presumably want to use those instead of Apple's window manager. It is possible to do this by changing the default configuration so that it launches the window manager of your choice rather than Apple's default.

So the question is why you'd want to. There are good reasons why somebody might wish to do this but without knowing what you're hoping to do, it isn't possible to say how you would go about it.

Note that although I believe my answer to be basically correct, it is possible that there are nuances here I've misunderstood. Note, too, that I have not used any Apple OS later than Tiger and X11 - and Apple's implementation and window manager - have certainly changed since then.

So as well as saying what you want to do exactly, it would probably be helpful to say which version of OS X you are running and on what hardware.

---

### Post by Fxy on 2011-04-14
What i am trying to do is to install gnome/ubuntu/kde panels inside x11...

...I use x11 alot for running non mac applications etc & developing different little things.  It would be nice to have some sort of panel or something instead of using commands to complete everything.

I remember reading somewhere before in a magazine that it was possible to change the default x11 window manager & replace it with your own, but google gives me nothing useful when i search, thats why i decided to ask here ;)

Mac 0S X Ver.10.6.6 is what versions im currently running & thats on a 2yr old standard macbook model.

---

### Post by cfr42 on 2011-04-14
Let me preface this by saying that I am using 10.4.11 on PPC and have never used a later version of the OS or an Intel. So things might have changed. The following assumes they have not.

Basically, X11 is using a configuration file. Apple installs a default one. If you want to use something different, you just install your own in your home directory. Apple's is called ```
xinitrc
``` and lives at ```
/etc/X11/xinit/xinitrc
```. Yours should be in your home directory and called ```
.xinitrc
```. So the easiest thing to do is to copy Apple's configuration to your home directory, add a dot at the beginning and then edit it as you wish. In the version I have, starting the window manager comes right at the end:
```

exec quartz-wm

```Basically, you need to comment this line out and replace it with an alternate. For example, you might do this:
```

#exec quartz-wm
exec /sw/bin/sawfish

```to start sawfish as your window manager, if you'd installed sawfish in /sw/bin. (This line is probably based on fink and is very likely not correct for you. It certainly wouldn't do anything on my machine!) Obviously, you replace ```
/sw/bin/sawfish
``` with the path to your favourite alternative.

Note that most alternatives will not be able to run in "rootless" mode so you will not have access to the Aqua interface at the same time. Though things may have changed now. There did used to be one rootless manager (Orboro-something?) but this was before Apple released quartz-wm. However, I suspect things have come some way with X11 on OS X between the version I'm able to run and the one you have, so you may find you have more options and flexibility.

I'm pretty certain you can run Gnome. I don't know much about KDE but I'd assume that's possible, too. Since Ubuntu is an entire OS, you don't want Ubuntu unless you want to boot into Ubuntu rather than OS X or otherwise play with two operating systems. But Gnome and KDE are "just" desktop environments so should be fine. You can also see in the xinitrc file how to start any programmes you'd like started by default when you start X11.

---

