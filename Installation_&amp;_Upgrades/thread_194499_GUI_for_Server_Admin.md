---
title: "GUI for Server Admin"
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by edlentz on 2006-06-11
Can someone tell this noob is there is a Admin GUI for the Dapper Server?  I am using SME-Server at the moment.  It has a real nice Admin GUI for administering various things, email, ClamAV, shared folders, etc.  The down side is that it won't run MySql 5/PHP5.  So I have been spoiled with the GUI.  Besides Webmin is there anything out there?

Thanks!!

---

### Post by Abhi Kalyan on 2006-10-24
Hi edlentz
try
sudo apt-get install ubuntu-desktop
on the prompt
It worked for me-
doubt: what does "noob" mean?

---

### Post by edlentz on 2006-10-24
Thanks Abhi for the reply.  I was looking for something like Webmin.  I am using the Desktop version now.  Maybe you know, if I install the server version and apply what you suggested, will that give me a leaner system than using the Desktop version?  I want soemthing easy to maintain (using a gui if possible) and still be fast and secure.  BTW noob, is short for noobie.  I am an old guy and I take longer to learn things as I get older.  

Thanks again!

---

### Post by Abhi Kalyan on 2006-10-25
You are welcome edlentz,
As far as know-(thats about couple of days)
You can install the server version.
Then apply the Gnome GUI on it, The server installation comes with a command interface, Installing a GUI is only a matter of running the command given above. Then startx.

As for leaness of the system am not that adept. Security and speed are once again questions for whihc am not qualified to answer yet.

What i could do is give you contact who could provide you the necessary details.
search for post by the user name swhihc i have given below-
You should be able to contact them from there.

Referring me might not work as i dont know if they remember me.
The contacts:

(Anonii)
(Artificial Intelligence)
Ashrael
bforbes
byen
(dolphinsonar)
(Foudre)
gn2
(Grey)
Iarwain ben-adar
maniacmusician

People whose names are within brackets gave me great solutions-This worked for me Hope it works for you too.

You could mail me 
[email]abhi.kalyan@gmail.com[/email]
Sincerely
Abhi Kalyan

---

### Post by Abhi Kalyan on 2006-10-25
CREDITS - brentoboy

instead of apt-getting the entire ubuntu-desktop. you might consider a "best of both worlds" approach to Servier-GUI-ness.

140 clients is a decent number. If you had 5 or 10, I would say "who cares, add the GUI -- you'll never notice it" But, 140 clients is probably worth taking the time to squeeze out the best you can get.

install an empty "server" install (not the lamp stack -- unless you want all that stuff) I mean the bare bones minimal install.

when it kicks you to a command prompt after the first boot to the new system:
Code:

cd /etc/apt #always backup the original before ruining a file sudo cp ./sources.list ./original.sources.list #give yourself the Universe and Multiverse Repos sudo nano ./sources.list #Edit the file by removing the "#" that comment out the universe lines #save the file #make sure you have the latest pathes sudo apt-get update sudo apt-get dist-upgrade #now add a simple core sudo apt-get install x-window-system-core xfonts-base xserver-xorg xterm firefox leafpad synaptic openbox gkrellm feh emelfm mc openbox-themes obconf

“x-window-system-core , xfonts-base, xserver-xorg” are your basic gui system – they are not optional.

“xterm” is a terminal emulator for use inside of the gui environement – not optional. If you want to swap it out for aterm or some other terminal emulator – go ahead, just dont bother me about it if it doesnt work.

“firefox” You need a functional browser, and firefox works great. some people say “that is too bloated for my server” but honestly now, most of the time, you arent even running the GUI, so it isnt taking up memory. And, when you need a browser on your server for whatever you want something that works.

“leafpad” leafpad is my text editor of choice. it is a lot like mousepad (the xfce4 text editor) I chose it because it is desktop agnositc, and therefor has no extra dependancies that arent needed. I also choose it because it is feature rich and easy to use, and it is designed to be easy on day one, very very easy learning curve.

“synaptic” Synaptic is the GUI equivalent of apt-get. Strictly speaking, it is not necessary, but I recommend it because package management is a fundamental part of system administration. If you arent interested in gui tools that make adminstration point and click, what are you doing here in the first place?

“openbox” Openbox is a Window Manager. Openbox is my favorite light weight window manager. It is very very minimalistic. Right click the desktop -> you get the menu. Excelent choice for servers.

“gkrellm” is a nice little application that charts CPU, disk and active net interfaces in a graphical feedback sort of way. It is a wonderful way to see how much of your systems resources are in use. And, when your server is running a gui, it is nice feedback to have.

“feh” feh serves two purposes: It lets you set background to something other than the default X black and white dithered eye-crushing background, and it is a small image viewer that will let you view jpgs and things down the road if you need to. I highly recommend it, if you dont want it, dont install it.

“emelfm” is a file manager that implements the popular two-window design. It features a simple GTK+ interface, a flexible file typing scheme, and a built-in command line for executing scommands without opening an xterm.

“mc” Midnight Commander is a text-mode full-screen file manager, somewhat akin to the Xtree Pro Gold file manager for DOS that was popular in the pre-windows 3.1 days. It also implements the popular two-window design like emelfm, but it has the advantage of being available even if you are not running the X gui system. It also includes a subshell for command execution, as well as an internal editor with syntax highlighting and an internal viewer with support for binary files.

“openbox-themes” these are optional but quite small, so I install them. You need this package in order to have choices about how window decorations look inside of openbox. Feel free not to add this one

“obconf” this also is for managing the minimal eye-candy available inside of openbox, if you dont care what fonts are used, and just want a functional system, you can conveniently not install this package without running into any whiplash.

---

now, before you start your gui, lets pretty it up a bit (believe me, this is necessary)

#go to the home directory of the primary administrator, not ROOT, a person with sudo ability. You will *never* start X as root -- that is considered poor form, and for good reason.

Code:

cd ~ nano .xinitrc

put this inside there:
Code:

feh --bg-scale /etc/xdg/openbox/bg.png & gkrellm & x-terminal-emulator & exec openbox

that will give you a pretty background, automatically open gkrellm, a terminal, and launch openbox for you when you "startx"

in order to have a nifty background you will have to get one and put it here: /etc/xdg/openbox/bg.png
(if you get a jpg, you should fix it in .xinitrc -- but I recommend a png because they generally require less resources)

to get a graphic, go to gnome-look.org and find a url to download, or just use this one:
[http://www.gnome-look.org/content/pre1/47154-1.png](http://www.gnome-look.org/content/pre1/47154-1.png)

Code:

cd /etc/xdg/openbox wget [http://www.gnome-look.org/content/files/47154-Ubuntu_CrystalSoul_1024x768.png](http://www.gnome-look.org/content/files/47154-Ubuntu_CrystalSoul_1024x768.png) cp ./47154-Ubuntu_CrystalSoul_1024x768.png ./bg.png

that will download a decent background and name it correctly so that your xinitrc file will display it for you.

anyway, now would be a good time to launch a gui...
Code:

startx

when you are done with your gui (durring normal server operation, the gui isnt important...) close it. Right click the desktop, and exit openbox. it will take you back to the prompt, and you can "exit" your way back to the login screen.


Havnt tried this out yet, but working towards it, Thought you might want to know. Cheers-
Please do post back when you try this out- 
you should add

brentoboy

to your buddy list
Thank you
All the best
Sincerely
Abhi Kalyan

---

### Post by Abhi Kalyan on 2006-10-25
check this link out
[http://www.ubuntuforums.org/showthread.php?t=275576](http://www.ubuntuforums.org/showthread.php?t=275576)

---

