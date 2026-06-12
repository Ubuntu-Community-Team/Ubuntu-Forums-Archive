---
title: "Do you like this post-install script? Add your own!"
date: 2012-05-31
forum: Installation &amp; Upgrades
---

### Post by pakito15191 on 2012-05-31
I have 1 desktop computer and one laptop, as many people, and once in a while (about each 2 releases OR many bugs) I like to make fresh installations. I also have Ubuntu installed in my pen drive. So I decided to create a little script to help me making Ubuntu ready as I like it using only the regular installation and few clicks.

This is my post-installation script for Ubuntu 12.04, saved into install.sh in my home folder. Haven't tested it fully yet, but going to do so soon. Can you see any mistake? or recommend something else? It is made to work for anyone who is also interested. I love the "Change wallpaper" section.

```

#!/bin/bash

## Install programs
# Install gimp
sudo apt-get install gimp

## Change wallpaper
# WRITE HERE the direct link to the wallpaper you want.
imageurl=http://img841.imageshack.us/img841/1047/sexytattoo.jpg

# Download the image in the proper directory.
sudo wget $imageurl -O /usr/share/backgrounds/wall.jpg

# Change the main wallpaper.
gsettings set org.gnome.desktop.background picture-uri file:///usr/share/backgrounds/wall.jpg

# Change the login wallpaper
sudo sed -i '/background=/ c\background=wall.jpg' /etc/lightdm/unity-greeter.conf

## Minor tweaks
# Allow transmission to handle magnet links
gconftool-2 -t string -s /desktop/gnome/url-handlers/magnet/command "/usr/bin/transmission %s"
gconftool-2 -s /desktop/gnome/url-handlers/magnet/needs_terminal false -t bool
gconftool-2 -t bool -s /desktop/gnome/url-handlers/magnet/enabled true

## Startup scripts
# Remove startup sound
sudo rm -rf /usr/share/gnome/autostart/libcanberra-login-sound.desktop

# Add a startup script that mounts drive sda1.
cat << EOF >> ~/.config/autostart/Automount.desktop
[Desktop Entry]
Type=Application
Exec=/usr/bin/udisks --mount /dev/sda1
Name=Auto mount sda1
Comment=Automatically mount devices 
EOF

# Add a startup script that mounts drive sdb.
cat << EOF >> ~/.config/autostart/Automountb.desktop
[Desktop Entry]
Type=Application
Exec=/usr/bin/udisks --mount /dev/sdb
Name=Auto mount sdb
Comment=Automatically mount devices 
EOF

```

Most of this tasks could be done manually, but I found it easier to just run a script and let it installing and tweaking everything.

Enjoy and share your ideas. Cheers!

---

