---
title: "Install on a laptop"
date: 2006-07-29
forum: Installation &amp; Upgrades
---

### Post by djinni on 2006-07-29
Hello,
I'm attempting to install ubuntu 6.06 LTS onto an old laptop.  It's a Toshiba Satellite 2755XDVD.  There's about 64M RAM.  I know it's not enough, but I definitely can't be upgrading hardware right now.  

The install can't get past loading the CD.  Is there another install taking up a lot less memory, so I can just get started into the boot?

Thanks.

---

### Post by dio525i on 2006-07-29
try using xubuntu iso ....takes less of everything...should work on older hardware

---

### Post by catlett on 2006-07-29
Xubtuntu runs a different window manager than Ubuntu. Ubuntu runs gnome and gnome needs at least 128ram to run but 256mb or better is what is really needed. Ubuntu's resource needs are similar to XP's needs. Sop if you don't think XP would run well on your system, then chances are Ubuntu won't run well.
Xubuntu uses XFCE as a window manager. It is more like windows 95 as far as ram goes. This is your better choice. It isn't pretty though. It is powerful and has the ability to get things done but it is "stripped down"
Here is the download link, you want to select "Alternate Install CD". It is a text based installer. I do not know why they put the xubuntu Desktop CD installer on a live session. If you could run a live session and an install, you wouldn;t be installing Xubuntu. [http://cdimage.ubuntu.com/xubuntu/releases/dapper/release/](http://cdimage.ubuntu.com/xubuntu/releases/dapper/release/)
This is the xubuntu website in case you want to see some screenshots [http://www.xubuntu.org/](http://www.xubuntu.org/)

---

### Post by djinni on 2006-07-29
i've tried the xubuntu.  it's crapping out at trying windows manager.  though the script looks to say that it's trying gnome.  after it mentions gnome, the screen blacks out and then i get digital garbage.  it's obviously something, but the pixels are all dragged across the screen.  then after a little time, it's dead.  i have to force it to shut down as the only response.

i'll try the text install next.

thanks.

---

### Post by K.Mandla on 2006-07-29
Definitely go with the alternate CD.

I don't know if your laptop has a wired NIC or not, but if it does, you could install a server first, then install xubuntu-desktop with apt-get. If you're having problems with the installer program, this might circumvent them. 

There are also some very good ideas for [low memory installations]("https://help.ubuntu.com/community/Installation/LowMemorySystems") in the wiki.

---

### Post by djinni on 2006-07-30
I got it to work with the alternate cd and text installer.  I'm not sure if I messed up the partition on the windows side, but the xubuntu came up.

Thanks for all your suggestions.

---

