---
title: "Desktop installation on LAMP server"
date: 2007-05-02
forum: Installation &amp; Upgrades
---

### Post by nicker on 2007-05-02
So, I was having a hard time searching for this.  I successfully installed the LAMP server since I'm really going to be running the LAMP stack and work on learning a lot about databases.  I wanted to get the desktop installed as well so I can run the gui.  I did the usual **sudo apt-get install ubuntu-desktop[/B which installed fine.  I then had to do [B]sudo apt-get install nautilus**] which worked as well, and **sudo apt-get install xorg**.  Now when I start up the machine gdm loads and I can login to gdm fine.  I get the first two icons loading in ubuntu, not sure what the first one is and the second one is nautilus.  Then I get the desktop screen.  Except there's nothing there.  I can create a new folder by right clicking on the desktop but there are no top or bottom system bars for the desktop.  I'm thinking that the screen is too big for the display but I'm not sure.

Any ideas on how to fix this?   Do I need to load other things before I can actually use the desktop and all the applications that come with the real desktop version?

---

### Post by ohgod on 2007-05-02
Very strange.  I just did this and had no problems.  I installed ubuntu 7.04 server with the LAMP option, then ran 'sudo apt-get install ubuntu-desktop'.  Everything worked great.  

I'm surprised you had to install nautilus by hand...the ubuntu-desktop package should include that I believe.

Sorry I couldn't help :(

---

### Post by nicker on 2007-05-02
I'm assuming everthing is actually installed.  I really only installed nautilus separately because it was taking so long to load that I figured it wasn't there.

I'm thinking the only real problem might be that the screen is too big for my monitor.  Any ideas on how to fix this?

---

### Post by haricharan on 2007-05-02
try this 
Press Alt+F2 and type gnome-terminal and then
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by nicker on 2007-05-02
Thanks.  I had done that last night and still had the same problem.  I tried it once more right now over ssh at work.  I'll see if it worked when I get home and maybe retry it again.

---

### Post by nicker on 2007-05-02
I got home now and tried
sudo dpkg-reconfigure xserver-xorg
and I reconfigured it.  This still didn't work and I can't view the top or bottom system bars on the desktop.  Any other ideas?

---

### Post by zvacet on 2007-05-03
Maybe this can help you

[https://help.ubuntu.com/community/FixVideoResolutionHowto]("https://help.ubuntu.com/community/FixVideoResolutionHowto")

---

### Post by nicker on 2007-05-03
Ha.  I got it to work.  It ended up being really simple.
I went back and entered
```
sudo apt-get update
```
then I re-entered
```
sudo apt-get install ubuntu-desktop
```
This time it installed all of the desktop components that I needed.  It turned out it wasn't a screen size problem after all.  

Thanks for the help.

---

### Post by ksy on 2007-05-11
When I ran 'sudo apt-get install ubuntu-desktop',
I got a 'package not found' kind of error.

I haven't linked up the machine to a network or Internet. Not sure if this is the cause of my not being able to install the desktop.

Anyone can help me with this?
My intention is to do development on the same test server machine.

Thanks in advance.

---

