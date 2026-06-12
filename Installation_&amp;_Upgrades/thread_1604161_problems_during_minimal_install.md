---
title: "problems during minimal install"
date: 2010-10-23
forum: Installation &amp; Upgrades
---

### Post by jtkhouston on 2010-10-23
Im trying to do a minimal install on an old HP pavilion (celeron 2.2 Ghz, 248 MB ram). the disc went through its menus and no problems except DHCP fail, so I selected configure network later. I now have a sort of functioning command line linux on the computer but I'm unable to connect to the internet or get packages from a cdrom. My internet is DSL through AT&T, phone line into their router and wifi on our computers, internal cards in laptops and usb antennas on the desktops, including this one ( MS model mn-710). Ive read through lots of posts on how to fix this type of problem but can't seem to fix it in some of the suggested ways. I tried to add some packages ( ex. wireless-tools) from the cd but couldn't apt-get them and tried to edit the "sources.list" file but when I used sudo nano there was apparently nothing in the file. I really want to make this work but I'm getting a bit frustrated. Does anyone know what sorts of files and packages get added on over the internet that I may be missing? sorry if this is a bit rambling. also, lsusb output showed all the usb ports with yhe wireless antenna listed, but for some reason linux isn't using it and lspci gave back something like
link encap: local loopback
inet addr:127.0.0.1 mask 255.0.0.0
and I don't remember the rest.

---

### Post by coffee412 on 2010-10-23
> **jtkhouston said:**
> Im trying to do a minimal install on an old HP pavilion (celeron 2.2 Ghz, 248 MB ram). the disc went through its menus and no problems except DHCP fail, so I selected configure network later. I now have a sort of functioning command line linux on the computer but I'm unable to connect to the internet or get packages from a cdrom. My internet is DSL through AT&T, phone line into their router and wifi on our computers, internal cards in laptops and usb antennas on the desktops, including this one ( MS model mn-710). Ive read through lots of posts on how to fix this type of problem but can't seem to fix it in some of the suggested ways. I tried to add some packages ( ex. wireless-tools) from the cd but couldn't apt-get them and tried to edit the "sources.list" file but when I used sudo nano there was apparently nothing in the file. I really want to make this work but I'm getting a bit frustrated. Does anyone know what sorts of files and packages get added on over the internet that I may be missing? sorry if this is a bit rambling. also, lsusb output showed all the usb ports with yhe wireless antenna listed, but for some reason linux isn't using it and lspci gave back something like
link encap: local loopback
inet addr:127.0.0.1 mask 255.0.0.0
and I don't remember the rest.

Hi, Lets see if I can help a bit here.

I am under the impression that you dont have a graphical screen - Just a command line. We need to fix that first. What video card is installed in your computer?

Did you try booting from the cd and choosing to run it live first to make sure things work? Try that. Im interested in knowing if your graphics work.

then we can move on to wireless

---

### Post by jtkhouston on 2010-10-23
hi 
as afr as I know, there isn't supposed to be a gui in the alternate cd install, that was kind of the point. I was trying to get to a trimmed down KDE desktop on this machine, I used 9.10 by the way. from what I understood about doing a minimal install, command line only is what you get and you build up from there. I didn't try the cd I burned as a live disk, I think install is the only option on it.

---

### Post by jtkhouston on 2010-10-24
ok ,ignore the original post. I didn't realize that there were more than one variety of alternare cd's and I downloaded and burned the ubuntu version, not the kununtu version so I'm starting over. I was able to edit the sources.list file so I could add packages from the cd. Now all I have to do is figure out what to fix so the system doesn't automatically try to use the ethernet card to go online. My apologies to anyone who read this post and thanks to anyone who tried to help.

---

