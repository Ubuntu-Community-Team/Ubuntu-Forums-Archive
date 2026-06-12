---
title: "Installed Xubuntu 20.04 then problems with root"
date: 2020-07-29
forum: Installation &amp; Upgrades
---

### Post by Jim_Robinson on 2020-07-29
I had a working Xubuntu 18.04 LTS system until I had a power cut.

So I installed Xubuntu 20.04 using USB key. There were no obvious issues during the installation. I had also thought I had checked out for possible problems using the Live USB Key.

I normally use "scite" as my prime editor and I can use it as editor of choice when logged into the normal user but when I login into root to edit .bashrc and other bash files I have set up on the original system. I receive an error 
```
goto root 
using an alias 
alias root="sudo su - "


```

Type scite and get the following  error message 
 
Unable to init server : Could not connect: Connection refused
(scite:27613) Gtk-WARNING ***cannot read this section because  it is in colour dark blue ***: Cannot open display

Repeated using Thunar
prompt $ thunar
similar error message
Failed to initialize Xfconf : Cannot autolaunch D-Bus with X11 $Display  
Unable to init server : Could not connect: Connection refused
(thunar:27638) Gtk-WARNING ***cannot read this part of the error because it is in colour dark blue*** : Cannot open display

Any suggestions polite ones please[IMG]https://ubuntuforums.org/images/icons/icon7.png[/IMG] will be received gratefully. I would to like keep using this PC as a nfs-server.

I have been seen several suggestions on the web with similar errors with manjaro linux and xcfe. and they suggest that the problem is related to using wayland.

Best Wishes
Jim

---

### Post by Impavidus on 2020-07-30
It's best not to run any GUI applications as root. It comes with many problems. To edit text files as root, use the sudoedit command. You can use the EDITOR environment variable to let it use any text editor you like.

---

