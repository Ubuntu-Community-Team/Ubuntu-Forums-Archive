---
title: "docky updates and changing its icon from an anchor"
date: 2011-08-05
forum: Installation &amp; Upgrades
---

### Post by boblizar on 2011-08-05
if you have not noticed, this is my ubuntu master thesis....
[http://ubuntuforums.org/showthread.php?t=1836890](http://ubuntuforums.org/showthread.php?t=1836890)
check it out and share it with your friends =)

i have switched from docky to glxdock or cairodock....  it has many more features, is a little more confusing to setup, and available from synaptic repository...

alt + f2

gksu synaptic

run

to search for glxdock and install it...

add
ppa:cairo-dock-team/ppa
to your repositories to get latest stable glx dock

add if ubuntu 10.10 (probably broken on 11.10 for the time being but might work in future)

```

ppa:docky-core/ppa

```

to your synaptic ppa, refresh synaptic search for and select docky if not installed.  select inkscape also.

to return the anchor icon to blue instead of using gtk theme of ubuntu to a transparent color.

alt + f2

gconf-editor

apps > docky-2 > docky > items > docky item > hue 1

open inkscape to turn a picture into a SVG file.....  were going to use tux here but you can use other icons if you so like just rename them to "docky.svg"

[img]http://img5.imageshack.us/img5/8360/500pxnewtuxsvge.png[/img]

alt + f2
inkscape

wget [http://img5.imageshack.us/img5/8360/500pxnewtuxsvge.png](http://img5.imageshack.us/img5/8360/500pxnewtuxsvge.png)

mv $HOME/500pxnewtuxsvge.png $HOME/tux.png

open your tux png...  $HOME/tux.png

select embed

select save as

save as your user folder and name the file docky.svg

now to move the master icon in the users home directory to replace the old anchor icons

alt + f2

gnome-terminal

run

then drop 
```

sudo cp $HOME/docky.svg /usr/share/icons/hicolor/128x128/apps/docky.svg

```
then imediately drop this block of commands
```

sudo cp $HOME/docky.svg /usr/share/icons/hicolor/16x16/apps/docky.svg
sudo cp $HOME/docky.svg /usr/share/icons/hicolor/22x22/apps/docky.svg
sudo cp $HOME/docky.svg /usr/share/icons/hicolor/24x24/apps/docky.svg
sudo cp $HOME/docky.svg /usr/share/icons/hicolor/32x32/apps/docky.svg
sudo cp $HOME/docky.svg /usr/share/icons/hicolor/48x48/apps/docky.svg
sudo cp $HOME/docky.svg /usr/share/icons/hicolor/64x64/apps/docky.svg

```

(this is a re build to link to a scalable folder instead of making a mess of copied files and is more appropriate than the former solution.....  this solutions probably going to require purging previous docky files...)

```

sudo cp $HOME/docky.svg /usr/share/icons/hicolor/scalable/apps/docky.svg

```

then purge old icons

```

sudo rm /usr/share/icons/hicolor/128x128/apps/docky.svg
sudo rm /usr/share/icons/hicolor/64x64/apps/docky.svg
sudo rm /usr/share/icons/hicolor/48x48/apps/docky.svg
sudo rm /usr/share/icons/hicolor/32x32/apps/docky.svg
sudo rm /usr/share/icons/hicolor/24x24/apps/docky.svg
sudo rm /usr/share/icons/hicolor/22x22/apps/docky.svg
sudo rm /usr/share/icons/hicolor/16x16/apps/docky.svg

```

then link to the scalable image of tux

```

sudo ln -s /usr/share/icons/hicolor/scalable/apps/docky.svg /usr/share/icons/hicolor/128x128/apps/docky.svg
sudo ln -s /usr/share/icons/hicolor/scalable/apps/docky.svg /usr/share/icons/hicolor/16x16/apps/docky.svg
sudo ln -s /usr/share/icons/hicolor/scalable/apps/docky.svg /usr/share/icons/hicolor/22x22/apps/docky.svg
sudo ln -s /usr/share/icons/hicolor/scalable/apps/docky.svg /usr/share/icons/hicolor/24x24/apps/docky.svg
sudo ln -s /usr/share/icons/hicolor/scalable/apps/docky.svg /usr/share/icons/hicolor/32x32/apps/docky.svg
sudo ln -s /usr/share/icons/hicolor/scalable/apps/docky.svg /usr/share/icons/hicolor/48x48/apps/docky.svg
sudo ln -s /usr/share/icons/hicolor/scalable/apps/docky.svg /usr/share/icons/hicolor/64x64/apps/docky.svg

```


(side note if docky bitches about compositing run this command)
```

gconftool-2 -s --type bool /apps/metacity/general/compositing_manager true

```
this is my system with xfce, menu icon is also /usr/share/pixmaps/tux.png
(i use ubuntu with xfce from synaptic also installed)
[[IMG]http://img15.imageshack.us/img15/5716/screenshot1bk.jpg[/IMG]](http://imageshack.us/photo/my-images/15/screenshot1bk.jpg/)

---

