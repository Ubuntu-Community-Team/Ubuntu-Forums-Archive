---
title: "How configure two screen by terminal to put this setup in script?"
date: 2017-05-14
forum: Installation &amp; Upgrades
---

### Post by sed_faster on 2017-05-14
Hello folks,

I installed this version [http://lubuntu.me/](http://lubuntu.me/)
```

user@user:~$ uname -a
Linux user 4.10.0-19-generic #21-Ubuntu SMP Thu Apr 6 17:04:57 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
user@user:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 17.04
Release:    17.04
Codename:    zesty

```

I use this script to setup my environment: 
```

## Especificar a especificações do ecra
sudo mkdir /home/xxx/.screenlayout
sudo touch /home/xxx/.screenlayout/screenlayout.sh
sudo chmod +x /home/xxx/.screenlayout/screenlayout.sh
sudo echo "#!/bin/sh
xrandr --output VGA-0 --mode 1024x768 --pos 0x312 --rotate normal --output LVDS --off --output HDMI-0 --primary --mode 1920x1080 --pos 1024x0 --rotate normal" > /home/xxx/.screenlayout/screenlayout.sh
## Especificar o layout no arranque
sudo touch /etc/init.d/screen.sh
sudo chmod +x /etc/init.d/screen.sh
sudo echo "#!/bin/bash
/home/xxx/.screenlayout/screenlayout.sh &" > /etc/init.d/screen.sh
## Especificar o teclado numerico apos o arranque
sudo sed -i 's|^exit 0.*$|# Numlock enable\n[ -x /usr/bin/numlockx ] \&\& numlockx on\n\nexit 0|' /etc/rc.local
## Alterar o panel para o segundo ecra
sudo echo "# lxpanel <profile> config file. Manually editing is not recommended.
# Use preference dialog in lxpanel to adjust config when you can.

Global {
  edge=top
  allign=left
  margin=0
  widthtype=percent
  width=100
  height=24
  transparent=0
  tintcolor=#000000
  alpha=0
  setdocktype=1
  setpartialstrut=1
  usefontcolor=1
  fontcolor=#000000
  background=0
  backgroundfile=/usr/share/lxpanel/images/lubuntu-background.png
  iconsize=24
  align=left
  monitor=1
}
Plugin {
  type=menu
  Config {
    image=/usr/share/lubuntu/images/lubuntu-logo.png
    system {
    }
    separator {
    }
    item {
      command=run
    }
    separator {
    }
    item {
      image=gnome-logout
      command=logout
    }
  }
}
Plugin {
  type=launchbar
  Config {
    Button {
      id=pcmanfm.desktop
    }
    Button {
      id=menu://applications/Internet/firefox.desktop
    }
    Button {
      id=menu://applications/Development/sublime-text-2.desktop
    }
    Button {
      id=menu://applications/Accessories/pluma.desktop
    }
    Button {
      id=menu://applications/Administration/terminator.desktop
    }
    Button {
      id=menu://applications/Accessories/org.gnome.Screenshot.desktop
    }
  }
}
Plugin {
  type=pager
  Config {
  }
}
Plugin {
  type=dclock
  Config {
    ClockFmt=%a %d-%m-%Y %r
    TooltipFmt=%A %x
    BoldFont=0
    IconOnly=0
    CenterText=0
  }
}
Plugin {
  type=taskbar
  expand=1
  Config {
    tooltips=1
    IconsOnly=0
    AcceptSkipPager=1
    ShowIconified=1
    ShowMapped=1
    ShowAllDesks=0
    UseMouseWheel=1
    UseUrgencyHint=1
    FlatButton=0
    MaxTaskWidth=150
    spacing=1
  }
}
Plugin {
  type=volumealsa
  Config {
  }
}
Plugin {
  type=indicator
  Config {
    applications=1
    datetime=0
    messages=0
    network=0
    session=0
    sound=0
  }
}
Plugin {
  type=launchbar
  Config {
    Button {
      id=/usr/share/applications/lubuntu-logout.desktop
    }
  }
}" > /home/xxx/.config/lxpanel/Lubuntu/panels/panel
## Configurar o lxrandr com as posições correctas dos ecras (VGA-HDMI-Laptop desligado) - (left to right)
sudo mkdir /home/xxx/.config/autostart
sudo chown xxx:xxx /home/xxx/.config/autostart
sudo touch /home/xxx/.config/autostart/lxrandr-autostart.desktop
sudo chmod +x /home/xxx/.config/autostart/lxrandr-autostart.desktop
sudo echo "[Desktop Entry]
Type=Application
Name=LXRandR autostart
Comment=Start xrandr with settings done in LXRandR
Exec=sh -c 'xrandr --output VGA-0 --mode 1024x768 --rate 60.00 --left-of HDMI-0 --output HDMI-0 --mode 1920x1080 --rate 60.00 --right-of LVDS --output LVDS --off'
#Config auto
#Exec=sh -c 'xrandr --output VGA-0 --auto --same-as LVDS --output HDMI-0 --mode 1920x1080 --rate 60.00 --same-as LVDS --output LVDS --off'
#Config com ecra do portatil ligado e vga desligada
#Exec=sh -c 'xrandr --output VGA-0 --mode 1024x768 --rate 60.00 --below LVDS --output HDMI-0 --mode 1920x1080 --rate 60.00 --right-of LVDS --output LVDS --auto'
OnlyShowIn=LXDE" > /home/xxx/.config/autostart/lxrandr-autostart.desktop

```

This script was my older laptop. Where I has two screen. First screen is 22" Asus and second screen is 17". The third screen was turn off, because is of my laptop. On this setup I have this hardware:

1-https://www.asus.com/us/Motherboards/PRIME-B250-PRO/
2-https://ark.intel.com/products/97123/Intel-Core-i5-7500-Processor-6M-Cache-up-to-3_80-GHz
3-SSD 120GB Kingston
4-Only two screen (VGA - 17") and (HDMI - 22")
5-8 Ram

But my output on ARanDr is: [http://imgur.com/a/9HnqJ](http://imgur.com/a/9HnqJ)
Why?
How can I fix this?
[B]
Another question:[/B]
My login it is very slow. When I turn off my pc it is very faster but when I need turn on the system need 1 minute and 49 second. This is normally?

Thanks

---

