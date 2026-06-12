---
title: "If you can not edit properties of applications in menus..."
date: 2010-01-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ankspo71 on 2010-01-13
Hi, 
Re: Ubuntu Lucid Alpha 1 bug
I have a bug reported that shows editing of certain pre-existing application entries in the menu is not possible by clicking on the "properties" button in the gnome menu editor (alacarte). If you have trouble with this too, you can say "this affects me too" at:
[https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/499754](https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/499754)
(The link provides more details)
(originally reported on 2009-12-23)


I believe the problem is the incorrectly named application entries located in 
```
~/.local/share/applications
```None of my packages preinstalled by ubuntu, or installed by apt-get (command line) have the *.desktop file extension in this directory.
For example, the file firefox should be named 'firefox.desktop', not just 'firefox'.
If I rename firefox to firefox.desktop, it will allow me to view and modify the firefox menu entry using the gnome menu editor (alacarte).

   Duplicates of this bug:   
[LIST]
[*]       [ Bug #497931]("https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/497931")
[*]       [ Bug #505673]("https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/505673")
[/LIST]
PS. I'm sure this effects all types of shortcuts (ex: in the panel, on the desktop, etc).
Thanks.

---

### Post by mc4man on 2010-01-13
What are you trying to edit in alacarte?

If it's icons then the <whatever>.desktop in ~/.local/share/applications needs to be marked as "trusted" before it's icon can be changed or one assigned in cases where a default one doesn't exist

All new .desktop entries in  ~/.local/share/applications will be <whatever>.desktop and seen as a text file unless they are **first created** by going to alacarte -> properties of an app **and** trying to change the icon, then the .desktop will change to just <whatever> and be seen as an empty text file

So you need to create the .desktop, then go to  ~/.local/share/applications, d. left click on the <whatever>.desktop and mark as 'trusted', then back in alacate change/assign an icon. 
(or open the .desktop in gedit and manually edit,  needed in some cases.

(there a several ways that .desktops are created in  ~/.local/share/applications, one is just opening the properties of any app in alacarte - as soon as you click on the properties it will be created (with a .desktop extension

edit: what the point of this whole "trusted" deal is I don't know, it actually first showed up in karmic

---

### Post by ankspo71 on 2010-01-13
Hi,
So this is a permissions problem and not an file extension problem? 
I must have assumed that every application entry in /home/james/.local/share/applications should all have the *.desktop extension just like every applications enty in /usr/share/applications does.

It isn't any particular program's shortcut that I need to edit, it's just that I see there is a bug somewhere causing alacarte not being able to allow the editing of entries in the menu.

Technically I can't edit any of the shorcuts to programs in the gnome menu that were installed by default, or installed when I used 'sudo apt-get install packagename'.

But I have no problem at all editing anything that was not installed with the above methods, such as any shortcut that I personally created, or a shortcut that was created from an installer (such as my google earth installation, or from wine w/windows apps).

In karmic, jaunty, hardy?, etc, I was able to edit firefox, thunderbird, and gedit shortcuts and many more, but not in my installation of Lucid. The properties dialog doesn't appear when I click on the "properties" button of the desired entries in alacarte.

Thanks,

For reference I will put the output of my directories below...

Output of /usr/share/applications:
```
james@Lucid:~$ ls /usr/share/applications
alacarte.desktop
alltray.desktop
apport-gtk-mime.desktop
at-properties.desktop
audacity.desktop
banshee-1-audiocd.desktop
banshee-1.desktop
banshee-1-media-player.desktop
baobab.desktop
billard-gl.desktop
bluetooth-properties.desktop
brasero-copy-medium.desktop
brasero.desktop
brasero-nautilus.desktop
bum.desktop
byobu.desktop
ccsm.desktop
cgmail.desktop
checkbox-gtk.desktop
chromium-bsu.desktop
compiz.desktop
computer-janitor-gtk.desktop
criticalmass.desktop
default-applications.desktop
defaults.list
desktop.C.cache
desktop.en_US.UTF-8.cache
display-properties.desktop
easytag.desktop
emerald-theme-manager.desktop
empathy.desktop
eog.desktop
evince.desktop
evolution-2.2.desktop
evolution.desktop
evolution-mail.desktop
exo-preferred-applications.desktop
file-roller.desktop
firefox.desktop
foobillard.desktop
fslint.desktop
f-spot.desktop
f-spot-import.desktop
f-spot-view.desktop
gcalctool.desktop
gconf-editor.desktop
gdebi.desktop
gdmsetup.desktop
gedit.desktop
gimp.desktop
gksu.desktop
gmenu-simple-editor.desktop
gnome-about.desktop
gnome-about-me.desktop
gnome-appearance-properties.desktop
gnomecc.desktop
gnome-color-chooser.desktop
gnome-dictionary.desktop
gnome-font-viewer.desktop
gnome-hearts.desktop
gnome-mastermind.desktop
gnome-nettool.desktop
gnome-network-properties.desktop
gnome-panel.desktop
gnome-power-preferences.desktop
gnome-screensaver-preferences.desktop
gnome-screenshot.desktop
gnome-search-tool.desktop
gnome-settings-mouse.desktop
gnome-sound-recorder.desktop
gnome-sudoku.desktop
gnome-system-log.desktop
gnome-system-monitor.desktop
gnome-terminal.desktop
gnome-theme-installer.desktop
gnometris.desktop
gnome-volume-control.desktop
gnome-wm.desktop
gnomine.desktop
gparted.desktop
gpilotd-control-applet.desktop
gstreamer-properties.desktop
gucharmap.desktop
gufw.desktop
hplj1020.desktop
ibus-setup.desktop
jockey-gtk.desktop
keepassx.desktop
keybinding.desktop
keyboard.desktop
language-selector.desktop
lastfm.desktop
mahjongg.desktop
manage-print-jobs.desktop
metacity.desktop
mimeinfo.cache
miro.desktop
mount-archive.desktop
my-default-printer.desktop
nautilus-autorun-software.desktop
nautilus-browser.desktop
nautilus-computer.desktop
nautilus.desktop
nautilus-file-management-properties.desktop
nautilus-folder-handler.desktop
nautilus-home.desktop
network-scheme.desktop
neverball.desktop
neverputt.desktop
nm-connection-editor.desktop
nvidia-settings.desktop
onboard.desktop
onboard-settings.desktop
openoffice.org-calc.desktop
openoffice.org-draw.desktop
openoffice.org-impress.desktop
openoffice.org-math.desktop
openoffice.org-writer.desktop
orca.desktop
palimpsest.desktop
parcellite.desktop
pinball.desktop
PlayOnLinux.desktop
pysdm.desktop
python2.6.desktop
rhythmbox.desktop
screensavers
sdl-ball.desktop
seahorse.desktop
session-properties.desktop
shares.desktop
software-properties-gtk.desktop
sol.desktop
soundconverter.desktop
sound-juicer.desktop
sun-java6-controlpanel.desktop
sun-java6-java.desktop
sun-java6-javaws.desktop
sun-java6-policytool.desktop
synaptic.desktop
synaptic-kde.desktop
system-config-printer.desktop
Thunar-bulk-rename.desktop
Thunar.desktop
Thunar-folder-handler.desktop
thunar-settings.desktop
thunar-volman-settings.desktop
thunderbird.desktop
time.desktop
tomboy.desktop
totem.desktop
trackballs.desktop
transmission.desktop
tsclient.desktop
ubuntu-about.desktop
ubuntuone-client-applet.desktop
ubuntu-software-center.desktop
update-manager.desktop
usb-creator-gtk.desktop
users.desktop
vinagre.desktop
vinagre-file.desktop
vino-preferences.desktop
vlc.desktop
window-properties.desktop
wine-browsedrive.desktop
wine.desktop
wine-notepad.desktop
wine-uninstaller.desktop
wine-winecfg.desktop
xfce4-panel-manager.desktop
xmoto.desktop
xsane.desktop
yelp.desktop

```Output of /home/james/.local/share/applications:
```

james@Lucid:~$ ls /home/james/.local/share/applications
alacarte-made-1.desktop
alacarte-made.desktop
brasero
cgmail
defaults.list
empathy
evolution
evolution-mail
firefox
foobillard
f-spot
gcalctool
gimp
gnome-search-tool
Google-googleearth.desktop
Google-googleearth.desktop.undo-0
lastfm
mimeapps.list
mimeinfo.cache
miro
openoffice.org-draw
sun-java6-javaws
thunderbird
Track Mania Nations For Ever.desktop
transmission
tsclient
ubuntuone-client-applet
userapp-sh-UTV15U.desktop
vinagre
wine
wine-browsedrive
wine-extension-chm.desktop
wine-extension-gbx.desktop
wine-extension-hlp.desktop
wine-extension-htm.desktop
wine-extension-html.desktop
wine-extension-ini.desktop
wine-extension-rtf.desktop
wine-extension-txt.desktop
wine-extension-wri.desktop
wine-extension-xml.desktop
xsane
```Note: I am not able to edit any of the above that doesn't have a *.desktop extension (unless I manually rename them to ****.desktop first.

---

### Post by ankspo71 on 2010-01-13
Hi again ;)

If I run alacarte from the terminal, and 'try' to click on the properties button of the firefox entry, I immediately get the following error:

```
james@Lucid:~$ alacarte
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/Alacarte/MainWindow.py", line 625, in on_properties_button_clicked
    self.on_edit_properties_activate(None)
  File "/usr/lib/pymodules/python2.6/Alacarte/MainWindow.py", line 379, in on_edit_properties_activate
    self.editor._MenuEditor__addUndo([item,])
  File "/usr/lib/pymodules/python2.6/Alacarte/MenuEditor.py", line 428, in __addUndo
    undo_path = util.getUniqueUndoFile(file_path)
  File "/usr/lib/pymodules/python2.6/Alacarte/util.py", line 109, in getUniqueUndoFile
    filename, extension = os.path.split(filepath)[1].rsplit('.', 1)
ValueError: need more than 1 value to unpack
james@Lucid:~$ 
```Thanks again,

---

### Post by mc4man on 2010-01-13
There are no .desktops installed to  ~/.local/share/applications by default, they are added from various actions, one of which is **just opening the properties** of any installed app in alacarte. (no editing needed.

Fool around a little and you'll see - 

Open  ~/.local/share/applications and alacarte

delete a .desktop and then open the properties of that app in alacarte - you'll see a new <whatever>.desktop created in  ~/.local/share/applications with the .desktop ext.
Double left click on it, mark as trusted, and it will change to <whatever> with the icon as specified in the .desktop (and then the menu icon can be changed

> 
Technically I can't edit any of the shorcuts to programs in the gnome menu that were installed by default, or installed when I used 'sudo apt-get install packagename'.

This does sound like an issue - though not apparent here, you should be able to open the properties of any installed app from alacarte

---

### Post by mc4man on 2010-01-13
just saw your last post - you appear to have a problem locally - see screen which sorta shows it all...
(after marking as trusted the smplayer.desktop will change to smplayer with the specified (in the .desktop) icon

---

### Post by ankspo71 on 2010-01-13
I tried to see if I could get them to prompt me to mark them as trusted applications. I clicked on 'firefox' located at /home/james/.local/share/applications/firefox and all I am presented with is gedit opening it up as a text file. It did not prompt me to make it a trusted application like a newly created shortcut on the desktop. As I look at the permissions of the file, I can see it is marked as ' -rw-r--r-- '. If I make it executable to ' -rwxrwxrwx ' it doesn't change anything, still opens directly into gedit as a text file, and it's still not editable in alacarte. The permissions say the owner is me and group is me too, as well as the folder.

I'm stumped.... If bad file names to shortcuts were actually contained in each and every deb file in the repos, then everyone would have this problem. ](*,)

Oops, you are replying faster than I can type lol.
I'll go over your last two posts in a sec and see what I can figure out.

---

### Post by ankspo71 on 2010-01-13
Hi mc4man

I can do almost exactly what you did with having nautilus open to ~/.local/share/applications and running alacarte from the terminal. Now I am deleting rhythmbox. A rhythmbox.desktop was not created yet.... but I am am now clicking on rhythmbox properties in alacarte and it only restored the original rhythmbox file (no rhythmbox.desktop). No properties dialog box opened and I am presented with the following error...

james@Lucid:~$ alacarte
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/Alacarte/MainWindow.py", line 625, in on_properties_button_clicked
    self.on_edit_properties_activate(None)
  File "/usr/lib/pymodules/python2.6/Alacarte/MainWindow.py", line 377, in on_edit_properties_activate
    self.editor._MenuEditor__addUndo([(file_type, os.path.split(file_path)[1]),])
  File "/usr/lib/pymodules/python2.6/Alacarte/MenuEditor.py", line 428, in __addUndo
    undo_path = util.getUniqueUndoFile(file_path)
  File "/usr/lib/pymodules/python2.6/Alacarte/util.py", line 109, in getUniqueUndoFile
    filename, extension = os.path.split(filepath)[1].rsplit('.', 1)
ValueError: need more than 1 value to unpack

Did you get any error messages?

---

### Post by mc4man on 2010-01-13
No I can run alacarte without error ( that's your main issue

To clarify something - 
Most apps can be edited from alacarte without doing anything in ~/.local/share/applications

Some do need to be marked as trusted, and all user-appXXXXXX.desktops need to be 
(I only change/assign icons to user-app.desktops, not 'regular' apps, so that could of been a bit of mis-info I presented you with - that all need to be which isn't the case

Of the regular installed apps that do, it only needs to be done once (and can be done only once) - firefox is an example

The first time I opened the properties of firefox in alacarte it created a firefox.desktop which needed to be marked as trusted before the menu icon could be changed

Now that it's been marked as trusted if I was to delete the firefox entry in ~/.local/share/applications and open it's properties in alacarte a proper firefox.desktop would be created in ~/.local/share/applications as firefox with the firefox icon, and i'd be free to change it's menu icon in alacarte

(hope not too confusing...

---

### Post by ankspo71 on 2010-01-13
Hi mc4man,
Thank you so much for all the help.

I finally have good news. I fixed it. It only took me 5 minutes to download a new alacarte source package and compile the source myself. I can now edit any menu entry I like in alacarte.

If anyone needs to fix alacarte in Ubuntu Lucid (alpha 1) (gnome-desktop), see below.

I got alacarte from gnome 2.29.4 - alacarte version 0.12.4 found here:
[http://www.icewalkers.com/download/GNOME/1075/dld/](http://www.icewalkers.com/download/GNOME/1075/dld/)

I think the dependencies were** intltool **and **libgnome-menu-dev**
(when you run ./configure it will tell you)

./configure
make
sudo make install

done

:P

---

