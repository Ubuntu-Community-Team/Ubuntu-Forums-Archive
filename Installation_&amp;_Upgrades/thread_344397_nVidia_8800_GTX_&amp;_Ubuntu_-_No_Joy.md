---
title: "nVidia 8800 GTX &amp; Ubuntu - No Joy"
date: 2007-01-22
forum: Installation &amp; Upgrades
---

### Post by Kerry Lange on 2007-01-22
I've installed some new hardware:

Asus P5LD2
Intel Core 2 6600
nVidia 8800 GTX
DDR2 667

The Edgy & Fiesty Live CDs barfed on my new hardware. The Live CD went fine until it tried loading the video drivers. I got that screen that displays when the GDM won't load and here's the short output I got:

Failed to start your X server...

Fatal server error:
(EE) No devices detected
No screens found f"

That was it. When I looked for the details, I saw all of the cards the video driver supports and the 8800 isn't one of 'em. I guess it's a case of waiting until we get support for the 8800 series nVidia card.

Are there plans to support the 8800 series cards in the near future?

---

### Post by merher on 2007-01-23
I am having the same problem and have the exact same hardware you do (except i have the e6700) 

here are some screens that I took if it helps anyone to solve the problem.

[IMG]http://img.photobucket.com/albums/v144/Black_op51/pic4.jpg[/IMG]

---

### Post by Saibot on 2007-01-23
Read my post on this page
[http://ubuntuforums.org/showthread.php?t=343696]("http://ubuntuforums.org/showthread.php?t=343696")

It can be done on a fresh install, but I have a second computer here to help with searching for the right commands.  You have to do everything from the terminal and I'm no expert on that.

---

### Post by merher on 2007-01-25
c'mon how hard can it be to add support for a newer card. with the growing popularity of ubuntu it needs to be on the bleeding edge.

---

### Post by Kerry Lange on 2007-01-30
Still no joy.  

I'm glad *someone's* got it to work but I haven't been able to.  I downloaded a copy of the alternate CD so I could do an install in text mode but even that isn't working.  It's not because of the card this time but because during the install I get a message telling me I don't have the correct CD to do the install.  I've checked the ISO file and it's fine and I'm in the midst of re-burning the CD to see if there was a flaw introduced while burning the CD.

While trying to boot to the original install, there's no option for entering text mode, since I get that message telling me there's no TTY available.  I'm not even getting the busybox prompt anymore.  It just hangs.

---

### Post by Juzz on 2007-01-30
I got mine working again - however by using my laptop to connect to my desktop while the desktop was up (but nothing loaded on the screen).

I followed most of the steps here:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

step 1:

```
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.1-0ubuntu3_all.deb
```

then step 2:

```
sudo dpkg -i envy_0.8.1-0ubuntu3_all.deb
```

Then run the envy script from the laptop (it ended in a fail code), but now I could press CTRL + ALT + F1 to get a prompt on my desktop and I could kill remaining Xserver processes and run the script again and this time with success.

Hope this helps

---

### Post by nhooey on 2007-02-22
If you ever have a video card that doesn't work with ANY window manager, no matter what operating system, chances are the VESA standard drivers will work.

So, for you guys, here's how to solve this problem.

Don't actually type quotes (" ") when I tell you to type something.

1. When X says it can't start, tell it to piss off
2. Press CTRL+ALT+F1 to get to a console
3. Type "sudo su" and press enter
4. Type "vim /etc/X11/xorg.conf" and press enter.
5. Type this:
/"nv"
and press enter. I typed that on its own line because you actually have to type the quotes this time.
6. You should now see a line that says:
Driver "nv"
7. This is the shitty old vi version of vim, so you have to replace "nv" with "vesa", which is annoying.
8. Move the cursor to the 'n'
9. Press 'x' twice to get rid of 'n' and 'v'
10. Press 'i' for insert, then type "vesa"
11. Press Escape, and type: ":wq", that's colon, then 'w' and 'q'. Then press enter
12. You've just saved the file and told stupid X to use the vesa driver
13. Type "exit" to get out of super-user mode
14. Type "startx" and press enter.
15. Then double-click the "install" icon, and you can begin installing xubuntu or ubuntu.

---

### Post by kiaran on 2007-02-23
I'm going to give this a try on my system as soon as I get a chance. Thank you for outling the directions in such detail. 

I go to work on Monday at a new job that is all linux based so I really need to get linux setup at home and I don't want to resort to Red Hat or Suse or any other non-ubuntu linux!!

---

### Post by kiaran on 2007-02-23
One other question for nhooey: how do you know all these commands? how did you possibly figure out how to solve this problem? Is there documentation on this whole system? Are you a contributing programmer? The reason I ask is because I would like to become more proficient with linux but as it is I just throw up my hands whenever something goes wrong. Is there a good book to get you a basic understanding of all the different aspects of a linux system?

Thanks!

---

### Post by Kerry Lange on 2007-02-23
I actually got it working but ended up installing Feisty with the alternate CD.  I had the added problem of having an Intel-based MB with a jmicron IDE chip, which caused problems (i.e. the CD drive wasn't recognized by Edgy).

I installed Feisty, rebooted, then installed the latest nVidia drivers and all is working with my 8800 GTX.

---

### Post by Xited on 2007-02-25
I am attempting to install Ubuntu from the cd. But I have the nvidia 8800 card so I get the same error as previously posted. I have used wget to dl envey and I used it installs the driver. I can then use startx to start the gui but it only contains the windows manager no programs or anything. I would like to know what command I have to run to start the installation process again after envy has installed the driver.

Thanks

---

### Post by Xited on 2007-02-28
Nevermind. I dl the alternative iso and installed ubutu using the text mode. Then used envy to install the nvidia driver.

---

### Post by Frickalik on 2007-05-17
Listen to EnHooey. Use the alternate Cd and follow his steps and it works.

---

### Post by desertboy on 2007-05-20
> **nhooey said:**
> If you ever have a video card that doesn't work with ANY window manager, no matter what operating system, chances are the VESA standard drivers will work.

So, for you guys, here's how to solve this problem.

Don't actually type quotes (" ") when I tell you to type something.

1. When X says it can't start, tell it to piss off
2. Press CTRL+ALT+F1 to get to a console
3. Type "sudo su" and press enter
4. Type "vim /etc/X11/xorg.conf" and press enter.
5. Type this:
/"nv"
and press enter. I typed that on its own line because you actually have to type the quotes this time.
6. You should now see a line that says:
Driver "nv"
7. This is the shitty old vi version of vim, so you have to replace "nv" with "vesa", which is annoying.
8. Move the cursor to the 'n'
9. Press 'x' twice to get rid of 'n' and 'v'
10. Press 'i' for insert, then type "vesa"
11. Press Escape, and type: ":wq", that's colon, then 'w' and 'q'. Then press enter
12. You've just saved the file and told stupid X to use the vesa driver
13. Type "exit" to get out of super-user mode
14. Type "startx" and press enter.
15. Then double-click the "install" icon, and you can begin installing xubuntu or ubuntu.



Thank you so much I've managed to get it to boot, this has taken months of anguish, thank you. :KS

---

### Post by nhooey on 2007-10-02
Sorry for the late reply, but I've been using Linux for 10 years. That's how I know how to solve the problem with all of those commands. =)

You're just going to have to read tons of guides and learn the commands. The only thing I did in my instructions is edit a configuration file, and the concept of using vesa drivers I actually know from using Windows. If something complicated doesn't work (real video drivers), then try something simple (crappy simple video drivers).

---

