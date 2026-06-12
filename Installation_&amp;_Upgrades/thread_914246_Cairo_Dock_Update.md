---
title: "Cairo Dock Update"
date: 2008-09-08
forum: Installation &amp; Upgrades
---

### Post by stat30fbliss on 2008-09-08
When I updated my Cairo dock a few days ago, I lost my Mac OSX theme.  Anyone know where it went, or how I can get it back.

Heres a shot of my Themes Drop-Down menu

---

### Post by Partyboi2 on 2008-09-08
Download from [[COLOR=Blue]here[/COLOR]]("http://www.gnome-look.org/content/show.php/Mac+OSX+Leopard+Cairo-Dock+theme?content=72085") and extract it to ~/.cairo-dock/themes/
[B]
[/B]

---

### Post by stat30fbliss on 2008-09-09
> **Partyboi2 said:**
> Download from [[COLOR=Blue]here[/COLOR]]("http://www.gnome-look.org/content/show.php/Mac+OSX+Leopard+Cairo-Dock+theme?content=72085") and extract it to ~/.cairo-dock/themes/
[B]
[/B]

I apologize, but I am still rather ignorant to navigating the file system.  I still dont understand how to navigate to ~/.cairo-dock/themes/

Is there a specific folder that is filed under. File System or Home folder?

---

### Post by stat30fbliss on 2008-09-09
Well, I believe I found the folder.  I went usr>share>cairo-dock>themes

But when I went to extract it I got this Command Line Output error message.

```
tar: Mac OSX Leopard/launchers/firefox.svg: Cannot open: No such file or directory
tar: Mac OSX Leopard/launchers/ekiga.svg: Cannot open: No such file or directory
tar: Mac OSX Leopard/launchers/amarok.svg: Cannot open: No such file or directory
tar: Mac OSX Leopard/launchers/02vlc.desktop: Cannot open: No such file or directory
tar: Mac OSX Leopard/launchers/01xchat.desktop: Cannot open: No such file or directory
tar: Mac OSX Leopard/launchers/01vmware-workstation.desktop: Cannot open: No such file or directory
tar: Mac OSX Leopard/launchers/01rhythmbox.desktop: Cannot open: No such file or directory
tar: Mac OSX Leopard/launchers/01pitivi.desktop: Cannot open: No such file or directory
tar: Mac OSX Leopard/launchers/01ooo-writer.desktop: Cannot open: No such file or directory
tar: Mac OSX Leopard/launchers/01ooo-impress.desktop: Cannot open: No such file or directory
tar: Mac OSX Leopard/launchers/01ooo-calc.desktop: Cannot open: No such file or directory
tar: Mac OSX Leopard/launchers/01nautilus.desktop: Cannot open: No such file or directory
tar: Mac OSX Leopard/launchers/01gnome-terminal.desktop: Cannot open: No such file or directory
tar: Mac OSX Leopard/launchers/01gdesklets.desktop: Cannot open: No such file or directory
tar: Mac OSX Leopard/launchers/01gcalctool.desktop: Cannot open: No such file or directory
tar: Mac OSX Leopard/launchers/01gaim.desktop: Cannot open: No such file or directory
tar: Mac OSX Leopard/launchers/01firefox.desktop: Cannot open: No such file or directory
tar: Mac OSX Leopard/launchers/01file-roller.desktop: Cannot open: No such file or directory
tar: Mac OSX Leopard/launchers/01f-spot.desktop: Cannot open: No such file or directory
tar: Mac OSX Leopard/launchers/01evince.desktop: Cannot open: No such file or directory
tar: Mac OSX Leopard/launchers/01contacts.desktop: Cannot open: No such file or directory
tar: Mac OSX Leopard/launchers/01audacity.desktop: Cannot open: No such file or directory
tar: Mac OSX Leopard/plug-ins/clock/clock.conf: Cannot open: No such file or directory
tar: Mac OSX Leopard/plug-ins/dustbin/dustbin.conf: Cannot open: No such file or directory
tar: Mac OSX Leopard/plug-ins/rendering/rendering.conf: Cannot open: No such file or directory
tar: Mac OSX Leopard/plug-ins/file-manager/file-manager.conf: Cannot open: No such file or directory
tar: Mac OSX Leopard/plug-ins/clock: Cannot mkdir: No such file or directory
tar: Mac OSX Leopard/plug-ins/dustbin: Cannot mkdir: No such file or directory
tar: Mac OSX Leopard/plug-ins/rendering: Cannot mkdir: No such file or directory
tar: Mac OSX Leopard/plug-ins/file-manager: Cannot mkdir: No such file or directory
tar: Mac OSX Leopard/launchers: Cannot mkdir: No such file or directory
tar: Mac OSX Leopard/plug-ins: Cannot mkdir: No such file or directory
tar: Mac OSX Leopard/cairo-dock.conf~: Cannot open: No such file or directory
tar: Mac OSX Leopard/readme: Cannot open: No such file or directory
tar: Mac OSX Leopard/cairo-dock.conf: Cannot open: No such file or directory
tar: Mac OSX Leopard/bg.png: Cannot open: No such file or directory
tar: Error exit delayed from previous errors
```

---

### Post by Partyboi2 on 2008-09-09
> **stat30fbliss said:**
> I apologize, but I am still rather ignorant to navigating the file system.  I still dont understand how to navigate to ~/.cairo-dock/themes/

Is there a specific folder that is filed under. File System or Home folder?

You can navigate to this location by entering ~/.cairo-dock/themes/ into the "Location"  "Goto Bar" Looking at the screenshot that I have provided make sure you have have choosen "text-based location bar" by pressing the button labelled 1 then enter ~/.cairo-dock/themes/ in the location bar which I labelled 2

---

### Post by fabounet on 2008-09-09
the MacOSX theme is part of the official themes package, so you should find it in the themes list.
If not, just install the corresponding .deb
How did you install the dock ?

---

### Post by stat30fbliss on 2008-09-09
I installed the dock through the instructions off of tombuntu.com I believe.

I did everything through the terminal.  Everything worked fine for like a week, and then I updated Cairo.  There was like an 850kb update available, and I lost my OSX, and the general usability just slowed dramatically when navigating the themes manager or customizing.  

The dock itself works fine.  I am using a derivative of the Aero theme, but I had gotten very cozy with my OSX dock, and would love to get it back. :confused:

---

### Post by fabounet on 2008-09-09
don't you have it in the themes list ?
most of the themes are now on a distant server, but this one is on your hard disk.

---

### Post by stat30fbliss on 2008-09-09
> **fabounet said:**
> don't you have it in the themes list ?
most of the themes are now on a distant server, but this one is on your hard disk.

Yeah, it definitely is not in the themes list.  Any ideas on where else it could be hiding?

---

### Post by fabounet on 2008-09-10
did you install it from the Cairo-Dock repository or from Berlios ?
if so, the themes are installed with the dock, they should be in /usr/share/cairo-dock/themes
otherwse, you may have to install a cairo-dock-data package, or an approaching name.

---

### Post by stat30fbliss on 2008-09-10
> **fabounet said:**
> did you install it from the Cairo-Dock repository or from Berlios ?
if so, the themes are installed with the dock, they should be in /usr/share/cairo-dock/themes
otherwse, you may have to install a cairo-dock-data package, or an approaching name.

Are there any commands I can run in my terminal to get these updates going?

---

### Post by fabounet on 2008-09-11
[http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en]("http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en")
to install the dock from our repository.
you'll always have the last stable version.

---

