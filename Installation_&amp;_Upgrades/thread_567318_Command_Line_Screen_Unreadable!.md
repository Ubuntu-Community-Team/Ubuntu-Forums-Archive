---
title: "Command Line Screen Unreadable!"
date: 2007-10-04
forum: Installation &amp; Upgrades
---

### Post by P3RH4PS on 2007-10-04
So I'm installing Ubuntu for the first time.  I installed with alternate cd and everything is gravy except the part where it loads into Ubuntu and the screen stops receiving signal.  I hear some sort of noise that sounds like Ubuntu is doing fine, but I'm pretty sure the gfx card isn't.

AMD 64 3200
1 gig ram
nVidia GeForce 6600 GT

So I've been looking around and decided to try mintrick's advice:

> When you get the blank screen press Ctrl + Alt + F1 to get a command line.

Type "sudo dpkg-reconfigure xserver-xorg" to the line and hit enter.

Choose "nv" for your graphic card. Go through other settings, finish it.

Then restart or type startx.

(from [this]("http://ubuntuforums.org/showthread.php?t=567268&highlight=screen+goes+blank") post)

EXCEPT when I get into the command line my screen is kind of broken looking.  Gray and black jumbled verticle lines everywhere.  I can tell where there might be some (unreadable) text on the screen and I can type and make lines look all cool and jumbly.

Should I try the xserver fix (above) even if I can't actually see what's on the screen?  I don't know much about this process or much about Ubuntu GNU/Linux stuff so I don't want to get stuck halfway through the process with some irreparable damage or something.

---

### Post by P3RH4PS on 2007-10-04
[LOOKS KINDA LIKE THIS]("http://photo.ringo.com/236/236139106O356144559.jpg")

It's just a shot from my lappy webcam so...

---

### Post by philcaetano on 2007-10-04
I don't have a solution to your problem, but just posting the I have had the exact problem.  I haven't spent any time figuring out.  What I did is install the "Restritive Drivers" for my NV and they work fine. 
Also, I was able to log on in "Recover" mode and then change my xorg.conf to vesa.  Then I got the good display and installed the other drivers.

BUT I would love to know how to force the system to bring back with out booting in recover mode.

---

### Post by P3RH4PS on 2007-10-04
Is it possible you could give me a little more detail on how you did that?   I'm such a complete novice.

---

### Post by philcaetano on 2007-10-04
lol.. its the blind leading the blind :P  I'm new too.

I'm a work so I'm doing this from memory.

Well... this is what I did.   When you boot, you got a menu to select a kernel.    I selected the second option.  I think it says recovery or something on those lines.

It will then boot up the OS to command line ROOT. 

I then typed nano /etc/X11/xorg.conf  and replaced the "nv" with "vesa"  I don't remember the location exactly.  Think it was in device.

Save (I think its ctrl o) and rebooted again.  I typed reboot.  But I think you can do exit and it will continue.

This time I selected the first kernal and I got video to work again in VESA mode.

I then selected in the system / administration area restrictive drivers manager.  When you click on it.  it wil give you an option to enable nvidia drivers.

Now..that should enable nvidia drivers.

To adjust your resolution, you can either modify the xorg.conf file. (which is what I did)  or you can type a command in a terminal.  I think its called nvidia-settings  (Took me a couple of days to learn that one)

Last time I tried the nvidia-settings, it seem to give something similar to what you would get with windows.  But I could use it since I'm doing dual monitor with two different resolutions.  Which isn't easy, until you learn how to do that of course.

Hope this helps

---

### Post by P3RH4PS on 2007-10-04
Weird...  I tried that and it created a new file or something.  Anyhow... there was nothing there to change related to nv or vesa.  Could it be that I have to make a file because one doesn't exist?

---

### Post by philcaetano on 2007-10-04
Are you referring to xorg.conf ?

Are you able to get to root (The second boot option)  

If so what do you see when do you    ls /etc/X11

you should see a xorg.conf.

Remember Linux is case sensitive.  

You should not need to create a new file.  that file should exist.

---

### Post by maybeway36 on 2007-10-04
If you don't have an /etc/X11/xorg.conf, then there's ceratinly something wrong. You could also try
```
sudo dpkg-reconfigure xserver-xorg
```
Just press Enter throguh everything except the first step (the driver) sice that's all you need to change.

---

### Post by P3RH4PS on 2007-10-04
When I am configuring the thingy after entering

sudo dpkg-reconfigure xserver-xorg

I can't figure out what button allows me to add resolutions on the list.  There are the three defaults with *s next to them but what do I press to * more of them?  I've hit a number of random buttons but the only result so far is I've continued to the next screen twice and had to start the whole process over again.  

Besides all of that I've got everything mostly working now.

When running with "vesa" is that like a default crap mode (similar to running windows with no gfx installed things are choppy and stuff) because things don't seem too slow.  I tried using the envy program to automatically do everything and it seemed really cool until later when I restarted and nothing booted and I had to reconfigure the xserver-xorg back to vesa.

I guess what I'm wondering is do I really need to get these drivers working or is vesa taking care of it?

<Feels like he's asked a lot of really stupid questions.>

---

### Post by philcaetano on 2007-10-04
Have you tried the "Restricted Drivers" in like I mentions after you got the vesa up and running?

Those are going to be fast if you use it.  Since you have an NVidia.

---

### Post by P3RH4PS on 2007-10-05
When I try to use the "restricted drivers" thingy it says I don't need them.  Even after I uninstalled the envy version of the nVidia drivers.  So,  I'm thinking I need a new xorg.conf back to default.  Mostly because I was examining it and the envy program changed it a lot and when it was uninstalled it didn't change things back.  Anyone know what I can do about that?

---

### Post by P3RH4PS on 2007-10-05
I'm reinstalling to 32bit anyway so I'll get clean slate and see what I can do.  Thanks for the help guys!

---

