---
title: "Gnome doesn't open after install"
date: 2007-08-12
forum: Installation &amp; Upgrades
---

### Post by Trunk_z on 2007-08-12
Hey guys, 

Am trying to get back into Linux after a year or so. But am having a bit of an odd problem.

When running the Live CD, the gnome desktop runs fine, however, when installed, i can only run the Failsafe Terminal, Gnome simply will not run.

Has anyone got anything useful for this problem?

I've read up on it a bit, and it could be the graphics card (ATI Mobility Radeon 9000... its a Toshiba laptop, couple years old now), but im not sure on this.

Regards,
Chris

---

### Post by Pumalite on 2007-08-12
What version of Ubuntu have you installed and in what kind of computer?

---

### Post by Trunk_z on 2007-08-12
I've installed the latest version from this website. 7 I believe.

Its a laptop, P4 2.8 GHz, 512MB ram, 128MB ATI Mobility Radeon 9000 (shared with ram however), 60GB HDD, DVD/CD writer.

Before I installed, i had completely blanked the drive with paragon partition manager.

Just re-instaled it, but the same problem again. From the terminal, I ran the update manager, updated everything. Ran Synaptic and re-installed Gnome, it talked about dependancies, so I just ok'd it and downloaded it all. Restarted, but same problem.


Lol, as you may have guessed im used to Windows based systems, so, usually a re-install & a restart fixes the problem.

Chris

---

### Post by qamelian on 2007-08-12
> **Trunk_z said:**
> 
I've read up on it a bit, and it could be the graphics card (ATI Mobility Radeon 9000... its a Toshiba laptop, couple years old now), but im not sure on this.


This may not be very helpful, but I doubt that it's a problem with your graphics card. My laptop has the same card and it works flawlessly out of the box. 

Are any errors reported if you run startx from the command prompt?

EDIT: This could be a problem caused by the partition manager you used. Some partition managers don't play well with Linux partitions despite claims of Linux support. You should use the built-in partitioning tool on the Ubuntu CD.

---

### Post by Trunk_z on 2007-08-12
I ran the live cd, so the default partition manager was used. I just checked it on my windows pc beforehand incase the drive had anything i wanted to keep.

i ran: sudo startx
and typed in my password, it came up with:

hostname: Unknown Host
xauth: creating new authority file /home/chris/.serverauth.5183

Fatal server error:
Server is already active for display 0
          If this server is no longer running, remove /tmp/.XO-lock and start again

what does startx do btw just ooi?

Chris

---

### Post by Pumalite on 2007-08-12
Startx starts your xserver. But we may have a different problem. 128 MB of Vidoe taken out of 512 MB of RAM. You might need Alternate CD. Avoid graphics problems and other potential hardware problems. By '7' I guess you meant 7.04?

---

### Post by Trunk_z on 2007-08-12
yeah, 7.04 is the one.

I'll get downloading the alternate one now, install it and let you know.

Thanks so far, 

Chris

---

### Post by Trunk_z on 2007-08-12
Unfortunatly it didnt help =[

sorry... 

Any other ideas?

---

### Post by Trunk_z on 2007-08-12
I forgot to mention by the way, KDE worked no problems.

I used to use gnome and prefer it, so would really like to use gnome over KDE.
Did that help?

---

### Post by Trunk_z on 2007-08-12
Sorry for all these posts in a row...

I've managed to get a background with black and white squares (only a few pixels each) for a background, and the mouse in an X shape.

Is this progres?

Chris

---

### Post by Pumalite on 2007-08-12
We'll have to find out what kind of Windblows you use: XP?, Vista?. If Vista; use Vista partitioner, otherwise Vista won't let use anything else in that laptop. I also need to know specifically what you mean by: 'didn't work'. What kind of errors?. How far did you get?. Did you see Grub? Did you get a Grub error?. Did you end up with a command line?. Blank screen?.

---

### Post by Trunk_z on 2007-08-13
Sorry, I meant that using the alternative CD didnt fix the problem.

I can install with either disk fine, get to the login screen. But thats it, as soon as I log in to Gnome or Gnome Safemode (or similar, can't remember off hand) the background changes to a different orange, and then does nothing.

The only session I can run in is the failsafe terminal, so all of the error messages have come from that so far.

As for the Vista/XP, i have these machines dotted all over the house, but the laptop is only for Ubuntu. I  only used an application on Vista to check the contents of the drive and format it on a different machine.


A few posts ago, the error message:
If this server is no longer running, remove /tmp/.XO-lock and start again

I'll see if fixing that makes any differance, and let you know. I'll try to take some pics and post them up as well.

---

### Post by Trunk_z on 2007-08-13
If I just login after a clean install, I get this screen:
[[IMG]http://img79.imageshack.us/img79/7756/13082007047fm1.th.jpg[/IMG]](http://img79.imageshack.us/my.php?image=13082007047fm1.jpg)

This is the only screen i can get to (failsafe terminal):
[[IMG]http://img79.imageshack.us/img79/5438/13082007048za7.th.jpg[/IMG]](http://img79.imageshack.us/my.php?image=13082007048za7.jpg)


(Sorry for the bad pics btw, camera isnt the best taking pics of the tv)

Gotta go to work now, but the above is from a clean install this morning. I'll post more when I get home.

Thanks,
Chris

---

### Post by Pumalite on 2007-08-13
It might not be your same case, but it could help:[http://terenzioberni.blogspot.com/2007/06/ubuntu-704-on-asus-z53jr-f3jr.html](http://terenzioberni.blogspot.com/2007/06/ubuntu-704-on-asus-z53jr-f3jr.html)

---

### Post by Trunk_z on 2007-08-13
I did: sudo rm /tmp/.X0-lock (something like that), and ran "sudo startx" and the screen I got looks like this:
[[IMG]http://img461.imageshack.us/img461/9366/13082007049pg0.th.jpg[/IMG]](http://img461.imageshack.us/my.php?image=13082007049pg0.jpg)

> It might not be your same case, but it could help:[http://terenzioberni.blogspot.com/20...53jr-f3jr.html](http://terenzioberni.blogspot.com/20...53jr-f3jr.html)

After trying the above, i get an error message, the last line of which says: no screens found.

It seems like its working less now, no background. Black screen, white text.

Would the entire log written out be helpful?


EDIT: I restored the xorg.conf file and now I am back to where i started

---

### Post by Trunk_z on 2007-08-14
Gave up on Gnome so switched to XUbuntu, which uses XFCE4 =]

Thanks guys,
Chris

---

