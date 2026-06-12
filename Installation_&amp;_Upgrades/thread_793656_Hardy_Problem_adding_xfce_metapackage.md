---
title: "Hardy: Problem adding xfce metapackage"
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by bamsan on 2008-05-14
Hi,

I just installed Hardy, and it works perfectly. Then, out of my curiousity, I installed xfce desktop metapakage and xfce restricted metapackage. The instalation was ok and I was able to logoff gnome and login into xcfe. Then I play a little bit with compiz in order to match my gnome desktop. Everything's good

Then I restart my pc. I got the xubuntu login, and sound. typed name and password, login screen disappeared, and was stucked with blank cyan screen and mouse pointer only. At this point, there was no post-login sound and the harddrive lamp was blinking every 2 secs or so.

So, I powered off my pc and boot into gnome. Everthing is fine. Please help me revive my xfce

My hardware is: ACER 5920G; Dual Core 2,2G; Ram 4GB; nvidia 8600M/512; HDD 250G AHCI mode. Dual booting with Vista, XP, Ubuntu 8.04

Thanks,

---

### Post by zenwalker on 2008-05-14
SO that means, u did some corruption ot the XFCE desktop ?

---

### Post by bamsan on 2008-05-14
> **zenwalker said:**
> SO that means, u did some corruption ot the XFCE desktop ?

Well, I'm not sure about the curruption, since there's no visible error message at all. My system just stuck in the cyan screen

---

### Post by Izobalax on 2008-05-14
> **bamsan said:**
> Well, I'm not sure about the curruption, since there's no visible error message at all. My system just stuck in the cyan screen
Same problem here, except after installing the xfce metapackage, I've NEVER been able to boot into Xfce. 

Help would be appreciated.

/izo\

---

### Post by bamsan on 2008-05-15
Just found out that re-installing the xfce metapackage from the repository will 'partly' solve the problem. I can login again into xfce

This time, I play again with compiz, and apparently there was something fishy between compiz, metacity and xfce default WM and maybe with Emerald too. Now, if compiz is enabled, then I logoff, when I login again into xfce, all windows and dialogs will have no title-bar. Also there's no desktop effects. I must use compiz fusion icon to reload the window Manager to put those title-bars back and re-enable desktop effects

---

### Post by lipidicman on 2008-05-16
> **Izobalax said:**
> Same problem here, except after installing the xfce metapackage, I've NEVER been able to boot into Xfce. 

Help would be appreciated.

/izo\

I have the same experience.  I was using AptonCd and thought the problem may have been related to that.  I had an issue with msttcorefonts needing an additional download.  When I have fixed that I will retry the Xubuntu install and let you know

---

### Post by bamsan on 2008-05-16
I found this: [http://wiki.xfce.org/faq#xfce_installer](http://wiki.xfce.org/faq#xfce_installer)
under the sub-toipc 'Setting up GDM'

> 
If you installed Xfce system-wide and you want to use the GNOME Display Manager (gdm) to start your Xfce session, you will have to create a .desktop file to teach gdm how to start the Xfce session. This is a sample desktop file, Xfce.desktop:

  [Desktop Entry]
  Encoding=UTF-8
  Name=Xfce 4.4 Session
  Comment=Use this session to run Xfce 4.4 as your desktop environment
  Exec=/usr/local/bin/startxfce4
  Icon=/usr/local/share/pixmaps/xfce4_xicon1.png
  Type=Application

It is usually enough to simply copy the example file to the Session directory used by gdm; this directory is usually located in /etc/dm/Sessions, /etc/X11/gdm/Sessions, /usr/share/xsessions, /usr/X11/share/gnome/xsessions or some other location, refer to the documentation of your system for details. You need to restart gdm after you created the file.


And I tried to find the .desktop file inside my hardy installation but found nothing. Do u think that this is probably the cause ?

---

### Post by lipidicman on 2008-05-16
Right, just tried XFCE on the internet connected machine.  It worked when I installed it a few days ago.  Now it is like the machine I updated with my AptOnCD disc.

So is it a problem caused by an update that I got recently?  All I know is it used to work and now it doesn't and the thread is only a couple of days old

BTW I found I can do a CTRL-ALT-BACKSPACE to get back to the login screen

---

### Post by lipidicman on 2008-05-16
There has just been an update.  I can now load XFCE

I also tried
sudo apt-get update
sudo apt-get install xubuntu-desktop
but that had no effect, telling me I had the latest version

---

### Post by bamsan on 2008-05-16
Every time I get into xfce, all my windows and dialogs have no title bars. I must use fusion-icon to 'reload window manager' to put back the title bars.

Is there an easier way to 'reload window manager' ? with command line perhaps ?

Thx

---

### Post by Izobalax on 2008-05-18
I still can't boot into the Xfce desktop AT ALL. All I get is the light orange standard Ubuntu screen and then nothing happens. 

PLZ HALP. 

/izo\

---

### Post by lipidicman on 2008-05-19
On my home machine I have the same problem.  There I installed Ubuntu hardy and added Xubuntu via my AptonCD disc.  The machine I made the aptonCD disc on works though.  Curious

---

### Post by bamsan on 2008-05-19
I have the same experience as lipidicman. Sadly, my 'good' installation only last for several sessions. However, if I hit ctrl-alt-backspace and re-login, I can get through

Sometimes, it take several ctrl-alt-backspace to go through

---

### Post by lipidicman on 2008-05-19
Interesting, so it is hit and miss?

Tried and that is the case here.  Worked on the second try

I'll try my home machine again later

---

### Post by Izobalax on 2008-05-23
> **Izobalax said:**
> I still can't boot into the Xfce desktop AT ALL. All I get is the light orange standard Ubuntu screen and then nothing happens. 

PLZ HALP. 

/izo\
Still having the same problem with this. 

/izo\

---

### Post by lipidicman on 2008-05-28
On my laptop I haven't managed to get XFCE at all.  Blank screen, no activity

edit: Did a fresh install (video driver issues), recovered packages with my aptoncds and now I have got in (once at least)

---

### Post by Izobalax on 2008-05-31
> **Izobalax said:**
> Still having the same problem with this. 

/izo\
New computer, fresh install of Hardy, installed Xfce-metapackage, problem remains. 

Is the package broken or something?

/izo\

---

### Post by Izobalax on 2008-06-06
Bump.

---

### Post by bford16 on 2008-06-22
I'd like to add my "two cents," but I'll admit from the beginning that I have a different setup: a fresh install of Xubuntu Hardy without Compiz or Emerald. What I DO have is experience with Xfce.

The Xfce environment is designed on purpose to auto-load a small set of applications and services. If you want more, you have to load them yourself.  For instance, gnome-screensaver is loaded automatically in GNOME, but in Xfce it is not (although it is installed by default in Xfce). To load gnome-screensaver at startup, you have to add an entry to "Autostarted Apps" in Settings Manager. The same is true of vino, which is the latest Remote-desktop server. If you want to run a vino-server at startup, you must add an entry to load /usr/lib/vino/vino-server.

So what I suggest is that you may have to manually set both Compiz and Emerald to run at startup.  (I had to do this in GNOME, too, for Emerald.)

---

### Post by listener13 on 2008-06-23
I've tried to delete gnome-screensaver. It's mystics but now all right. I've tried to kill X11 5 times and every time XFCE started successfully. Good luck!

---

