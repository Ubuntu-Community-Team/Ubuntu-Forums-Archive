---
title: "[SOLVED] screen has horizontal flickering lines"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by alicemoon on 2008-04-26
I have just installed Hardy on 2 ccomputers - one a full install which worked perfectly (1st time the wireless worked without any hassle). The other with the wubi on my main computer running XP, all went well with this one as far as I can tell except my screen has broken horizontal flickering lines which makes viewing a pain. When it boots in the screen is fine but as soon as I see the desktop the lines begin to flicker. I have a sony tft lcd screen SDM-HS53 resolution 1024-768 60 hz. I can change resolutions but this does not help. What should I do?

---

### Post by alicemoon on 2008-04-28
can anyone help?

---

### Post by alicemoon on 2008-07-22
Just in case anyone has similar problems - I discovered that it was my graphics card a Sis Mirage 661/741/760 which was the problem - causing the lines and stopping me viewing in anything other than a low resolution. I solved this by editing the xorg conf file 

using
gksu gedit /etc/X11/xorg.conf

and adding under video device the line 
driver   "vesa"

this improved the screen and allowed me to move to 1024 x 768 resolution

---

### Post by benjaminjames on 2008-07-23
hello but i cannot find where i should put the line that you suggested could you please explain exactly where i need to put it, im a bit of a noob still :) thanks

---

### Post by alicemoon on 2008-07-25
I am not an expert at all but this is what I did

open terminal and write
[B]
gksu gedit /etc/X11/xorg.conf[/B]

it will probably ask you for your password - write it in (you can't see any writing but just put it in and press enter)

this will open an editable file

look down it for a mention of your graphics card or video device (some of the threads I read suggested I would see my graphics card or video card mentioned but all I had was the line video device)

add the line

**driver   "vesa"**

under the video device section.

save the file
be careful not to alter anything else - hope it works for you

---

### Post by dragongntx on 2008-07-25
I am also having a similar problem.  I tried this and it says

(gksu:5068): Gtk-WARNING **: cannot open display:

---

### Post by alicemoon on 2008-07-26
> **dragongntx said:**
> I am also having a similar problem.  I tried this and it says

(gksu:5068): Gtk-WARNING **: cannot open display:

ok I know very little so please check this out yourself - but I think this can happen if you are not running as root - ie you need to type sudo before the commands I have suggested.

Also I found this link which may help [http://anaaman.blogspot.com/2007/01/gtk-warning-cannot-open-display.html]("http://anaaman.blogspot.com/2007/01/gtk-warning-cannot-open-display.html")

don't give up though - it took me ages to figure out what to do as I did not get any answers to my original post and I was having internet connection problems which did not help so I had to keep switching between Ubuntu and XP - but all is well now and it's a good way to learn if a bit of a steep curve - but I am determined to switch over to Ubuntu - and you do feel good when it all finally works :)

---

### Post by Jordananders on 2009-03-14
I tyoe the gksu gedit. . . into the terminal and it asks me for a password and I do that and then I type versa in the new command line and it says that the command is not found.

---

### Post by alicemoon on 2009-03-16
> **Jordananders said:**
> I tyoe the gksu gedit. . . into the terminal and it asks me for a password and I do that and then I type versa in the new command line and it says that the command is not found.

- that's because the [COLOR="Red"]gedit[/COLOR]command should open up your xorg file and enable you to edit it. The line[COLOR="Red"] driver "vesa"[/COLOR]needs to be added into the xorg file it is not a command you put into terminal.
I wrote these posts when I was running Hardy I am not sure that they will work or if you need to do it with Ibex - I did not have the same screen problems with Ibex.
Be very careful if you alter any files and always keep a backup copy in case things go wrong.

---

