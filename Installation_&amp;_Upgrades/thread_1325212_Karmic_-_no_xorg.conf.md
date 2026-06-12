---
title: "Karmic - no xorg.conf"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by LeeM on 2009-11-13
As part of an issue on screen resolution in Karmic, I noticed that my recent install of it had no xorg.conf file in /etc/X11. Previous releases always had that file, where screen resolution, etc could be set. Should that file be there, or has something changed in Karmic?

Thanks!

---

### Post by mac9416 on 2009-11-13
Hey, LeeM,

As a new feature in 9.10, xorg.conf is optional and not included by default. Apparently, xorg has become smart enough not to need it. However, you can create and use it in the same way as 9.04. 
For details, check out the Wikipedia xorg.conf page: [http://en.wikipedia.org/wiki/Xorg.conf](http://en.wikipedia.org/wiki/Xorg.conf)

Hope that clears things up!

---

### Post by markbuntu on 2009-11-13
The X consortium (the people who write and maintain X) has deprecated xorg.conf as automated functions have removed the need for it. Screen resolutions etc can now be set in user configuration applications like System/Preferences/Display in gnome and system settings in KDE4.

---

### Post by dharmaturtle on 2009-11-28
That's all well and good ... until the automatic systems don't work. I'm running Karmic under VirtualBox on a new Mac mini, and everything works well except that I can't get the native 1024 x 768 out of my oldish LCD Viewsonic VX500 monitor. The System -> Preferences -> Display says the monitor is unknown and only goes up to 800 x 600, making the screen impractical to use. (It also lists the refesh rate as 61 Hz! Huh?)

mac9416 links to a Wiki stub, which isn't much help. Nor do I feel qaulified to created a whole xorg.conf from scratch. All I want to do is run my monitor at its native resolution. And Viewsonic monitors are not exotic or anything. This seems like a reasonable request. ](*,)

FWIW, this monitor worked properly under Karmic (even though still unrecognized) when I had it attached to an old PC (since recycled) running an old nVidia card. Don't know if VirtualBox or the Mac mini (nVidia GeForce 9400) is the culprit. Any thoughts?

---

### Post by TimTang on 2009-11-29
I haven't been able to use Ubuntu since they changed this. I used to have a PERFECT pixel per pixel setup at 1366x765. I located the screen so the lost 3 pixels were on the bottom of the screen; this way the task bar was completely hidden. It was a perfect setup but now that xorg doesn't work I've never been able to use ubuntu again (it's almost 1 year now). So they managed to IMPROVE me right out of using ubuntu. Way to go guys!

---

### Post by jocko on 2009-11-29
> **dharmaturtle said:**
> That's all well and good ... until the automatic systems don't work. I'm running Karmic under VirtualBox on a new Mac mini, and everything works well except that I can't get the native 1024 x 768 out of my oldish LCD Viewsonic VX500 monitor. The System -> Preferences -> Display says the monitor is unknown and only goes up to 800 x 600, making the screen impractical to use. (It also lists the refesh rate as 61 Hz! Huh?)

mac9416 links to a Wiki stub, which isn't much help. Nor do I feel qaulified to created a whole xorg.conf from scratch. All I want to do is run my monitor at its native resolution. And Viewsonic monitors are not exotic or anything. This seems like a reasonable request. ](*,)

FWIW, this monitor worked properly under Karmic (even though still unrecognized) when I had it attached to an old PC (since recycled) running an old nVidia card. Don't know if VirtualBox or the Mac mini (nVidia GeForce 9400) is the culprit. Any thoughts?
A virtual machine will never see your real monitor, so this has nothing to do with the lack of a xorg.conf. But if you install the virtualbox guest additions you will be able to use whatever resolution you want...

---

### Post by jocko on 2009-11-29
> **TimTang said:**
> I haven't been able to use Ubuntu since they changed this. I used to have a PERFECT pixel per pixel setup at 1366x765. I located the screen so the lost 3 pixels were on the bottom of the screen; this way the task bar was completely hidden. It was a perfect setup but now that xorg doesn't work I've never been able to use ubuntu again (it's almost 1 year now). So they managed to IMPROVE me right out of using ubuntu. Way to go guys!
xorg.conf still works. It's just not included by default, as everything should be set up automatically. If you need a xorg.conf, you can create one yourself.

---

### Post by TimTang on 2009-11-29
I had and still have the one that I meticulously tweaked over a period of weeks. When I try to use it now it has no effect what-so-ever; the automation takes over, and as you can guess, it automates it to the point of no longer working. How do you turn the automation off so your own xorg.conf is recognized? I've read posts after posts on various forums yet I was never able to get it to work again. Intrepid was the last time I used Ubuntu and even then the screen was never correct. Once I upgraded I was never able to use ubuntu again. I've since downloaded every release and I can't even install any more.

---

### Post by pietjanjaap on 2009-11-29
Translated from dutch([http://sites.google.com/site/computertip/geenbeeld](http://sites.google.com/site/computertip/geenbeeld))
Or use [http://translate.google.com/](http://translate.google.com/)

A xorg.conf hass priority above the new autodetection system.
This way you can make a xorg.conf file:
- start the computer in Recovery Mode
- choose: drop to root shell
- type: Xorg -configure
(watch uppercase X and the soace between Xorg en -configure)

Now your system will make a file: /root/xorg.conf.new
- do wat the terminal says. Do you see a gray grafical screen + mouse arrow, then it's good. Close with Ctrl-alt-backspace.

- type: reboot
- restart normaal.
- copy /root/xorg.conf.new in /etc/X11/xorg.conf
- restart the computer.

Now you can put extra settings in xorg.

---

### Post by jocko on 2009-11-29
> **TimTang said:**
> I had and still have the one that I meticulously tweaked over a period of weeks. When I try to use it now it has no effect what-so-ever; the automation takes over, and as you can guess, it automates it to the point of no longer working. How do you turn the automation off so your own xorg.conf is recognized? I've read posts after posts on various forums yet I was never able to get it to work again. Intrepid was the last time I used Ubuntu and even then the screen was never correct. Once I upgraded I was never able to use ubuntu again. I've since downloaded every release and I can't even install any more.
Anything you put in xorg.conf will override the automatic settings.

---

### Post by TimTang on 2009-11-29
Thanks for that pietjanjaap I'll give that a try but first I'm going to need an installation that works, that's my main objective for now.

I'd be happy with just a 640x480, any thing that I could at least work with but I can't even get past the partitioning stage because the installer for 9.10 only sees my most valuable data storage drive and kindly offers to format it for me in order to install. I'm not quite prepared to sacrifice my lifes collection of Data for a clean installation of Koala. Why can't it see my other 3 drives.

---

### Post by dharmaturtle on 2009-11-30
> **jocko said:**
> A virtual machine will never see your real monitor, so this has nothing to do with the lack of a xorg.conf. But if you install the virtualbox guest additions you will be able to use whatever resolution you want...

Thanks, Jocko. I'll give that a try. I thought it might be something other than Ubuntu.

---

### Post by Nylo on 2009-12-01
> **pietjanjaap said:**
> 

- type: reboot
- restart normaal.
- copy /root/xorg.conf.new in /etc/X11/xorg.conf
- restart the computer.

Now you can put extra settings in xorg.

What happens when _I don't_ see the gray graphical interface, and the mouse arrow?

---

### Post by SpearZ on 2009-12-08
> **Nylo said:**
> What happens when _I don't_ see the gray graphical interface, and the mouse arrow?

Yeah, I didn't see anything either.  Just a black screen with no way out (hard reset worked for me).

Basically I think you can just copy over your old backup xorg.conf, or create a new one manually in /etc/X11
Seemed to work for me.
Seems a strange change to make though.  Why not just leave xorg.conf there, but with everything commented out?
Nice entry on the xorg wiki "For a long time, editing xorg.conf was necessary for advanced input devices and multiple monitor output to work correctly. This was regarded to be a major usability obstacle. In modern systems this is seldom necessary,"

...sounds like a Microsoft approach... "we don't recognise that problem, therefore it doesn't exist" :oops:

---

### Post by jenciso on 2009-12-19
Hi there,
having trouble with a Toshiba Satellite 1130 with a Intel Graphic card 855GM, in Karmic. Found this thread because the wrong module is loading and I was trying to add something to  xorg.conf (see [http://www.mail-archive.com/debian-x@lists.debian.org/msg86963.html]("http://www.mail-archive.com/debian-x@lists.debian.org/msg86963.html"))

Pietjanjaap said to:
> **pietjanjaap said:**
> 

This way you can make a xorg.conf file:
- start the computer in Recovery Mode
- choose: drop to root shell
- type: Xorg -configure
(watch uppercase X and the soace between Xorg en -configure)

Now your system will make a file: /root/xorg.conf.new



But here: [http://ubuntuforums.org/showthread.php?t=1130582]("http://ubuntuforums.org/showthread.php?t=1130582") they say:
> ...If there is no xorg.conf file present on your system, the following command will create a minimal configuration (which you can customize later):

```
$ sudo dpkg-reconfigure -phigh xserver-xorg
```

[COLOR="Blue"]Note: Use caution with this command, as it will overwrite any xorg.conf file already present on your system (though it will create a backup).[/COLOR]

which seems easier.

/br
/j

---

### Post by Jakey_TheSnake on 2009-12-31
Try this: 

[http://ozlabs.org/~jk/docs/mergefb/](http://ozlabs.org/~jk/docs/mergefb/)

I believe it should help.

---

### Post by jglepage on 2010-01-18
> **dharmaturtle said:**
> That's all well and good ... until the automatic systems don't work. I'm running Karmic under VirtualBox on a new Mac mini, and everything works well except that I can't get the native 1024 x 768 out of my oldish LCD Viewsonic VX500 monitor. The System -> Preferences -> Display says the monitor is unknown and only goes up to 800 x 600, making the screen impractical to use. (It also lists the refesh rate as 61 Hz! Huh?)

mac9416 links to a Wiki stub, which isn't much help. Nor do I feel qaulified to created a whole xorg.conf from scratch. All I want to do is run my monitor at its native resolution. And Viewsonic monitors are not exotic or anything. This seems like a reasonable request. ](*,)

FWIW, this monitor worked properly under Karmic (even though still unrecognized) when I had it attached to an old PC (since recycled) running an old nVidia card. Don't know if VirtualBox or the Mac mini (nVidia GeForce 9400) is the culprit. Any thoughts?
Here's what I do when I can't get X to work: use the xorg.conf created by Knoppix.  Even the most recent version of Knoppix still sets up a xorg.conf file, and Knoppix is very good at hardware detection and setup.  Once you've got a working xorg.conf file you can try it out with your ubuntu system.

---

### Post by drefooty on 2011-04-15
> **dharmaturtle said:**
> That's all well and good ... until the automatic systems don't work. I'm running Karmic under VirtualBox on a new Mac mini, and everything works well except that I can't get the native 1024 x 768 out of my oldish LCD Viewsonic VX500 monitor. The System -> Preferences -> Display says the monitor is unknown and only goes up to 800 x 600, making the screen impractical to use. (It also lists the refesh rate as 61 Hz! Huh?)

mac9416 links to a Wiki stub, which isn't much help. Nor do I feel qaulified to created a whole xorg.conf from scratch. All I want to do is run my monitor at its native resolution. And Viewsonic monitors are not exotic or anything. This seems like a reasonable request. ](*,)

FWIW, this monitor worked properly under Karmic (even though still unrecognized) when I had it attached to an old PC (since recycled) running an old nVidia card. Don't know if VirtualBox or the Mac mini (nVidia GeForce 9400) is the culprit. Any thoughts?

Same issue for me and I too had guest additions installed (VirtualBox), but still could not raise the resolution level until I added and edited the xorg file. the following post was a great solution for me for my VirtualBox:

[http://ubuntuforums.org/showthread.php?t=1336863](http://ubuntuforums.org/showthread.php?t=1336863)

Type
Drop to the terminal by doing ctrl+alt+F1
sudo service gdm stop

Then type:

sudo Xorg -configure

then to restart X

sudo service gdm start

(This will generate an xorg.conf) Below is the section I added the screen resolutions: 

The section to edit in the xorg file:
Section "Screen"
   Identifier   "Default Screen"
   Monitor      "Configured Monitor"
   Device      "Configured Video Device"
   SubSection "Display"
      Modes "1440x1440" "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
      #Virtual   2464 900
   EndSubSection

EndSection

---

