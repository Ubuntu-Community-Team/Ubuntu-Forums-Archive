---
title: "Changing Screen Resolution"
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by macguy918 on 2007-01-17
I am new to ubuntu but have successfully installed it about 5 times now on both Virtual Machines in Parallels on a Mac system and multiple times on an old P-III HP 7840 machine with 512 MB RAM and an integrated graphics card (Intel 85810E).

I am disappointed in how hard it is to change the screen resolution from the default install resolution of 1024 x 768 to something like 1280 x 1024.  I have a NEC Multisync 95 monitor that supports up to 1600 x 1200 so my hardware is fully capable and it works fine in Windows or OS X.

I tried editing the xorg.conf file and adding the screen resolutions there but that didn't change anything.  I still have a maximum resolution in ubuntu of 1024 x 768.

I also tried sudo dpkg-reconfigure -phigh xserver-xorg and indicated that my monitor would support 1280 x 1024.

Unfortunately, after that, when I restarted, I got an X11 error which gave me no graceful way to even get to console commands.  The only way I could recover was to completely reinstall Ubuntu.  Which, unfortunately, I am getting pretty good at.

However, something as simple as changing screen resolution should not require this deep a level of geekiness.  

I would appreciate some suggestions about how to actually make this resolution change, as well as some suggestions about how to undo the changes if they make Ubuntu inaccessible at startup as how happened to me twice.

Thanks

---

### Post by an.echte.trilingue on 2007-01-17
First off, when you use dpkg-reconfigure xserver-xorg, it creates a backup file of your old xorg.conf called xorg.conf.<datetime>.  All you have to do is log in in recovery mode and copy the backup to xorg.conf.

Now, what errors are you getting, exactly?  What is your video card?  Is the driver for it installed?

It might also be helpful to post your xorg.conf

```
However, something as simple as changing screen resolution should not require this deep a level of geekiness. 
```
I understand your frustration, but bear in mind that installing an OS is never easy.  I am sure we can figure this out.

Edit:  I just saw that you included your vid card info...  

Take care,
-mat

---

### Post by lotacus on 2007-01-17
Your monitor supports up to 1600x1200. During Ubuntu installation, you will come to a part where it lists all the configurations it has made. You can click on the links within that list to change any part you want. When you do this for your monitor it is best to choose the HIGHEST supported mode of your monitor.

If you go to boot into Ubuntu and it gives you obscure error messages in a blue box (*which I have had many times*), I have learned two things. Click out of those messages. hit ctrl f2 through f7. These are your virtual consoles. Log in and type the following:

**sudo dpkg-reconfigure xserver-xorg** go through all the steps. All the defaults should be left alone unless they do not match your hardware whatsoever. IF in doubt leave it be. The configuration app usually inputs SAFE settings that work with all hardware (*much like a "safe mode" in windows*). When you get to your monitor section, it will ask what type of detection you want. there is a basic, intermediate and advanced.

**Basic:** All you do is enter your monitors screen size ie: 19 for 19 inches. (*usually this doesn't work well. I tried this for a 17" monitor and xorg for some reason made the resolution all screwy and I had to put 15"*)

**Intermediate:** This section lets you choose what usually would be presented during a normal Ubuntu installation. You choose your screen size and resolution.

 **Advanced:** Here you would choose your monitors Horizontal and Vertical refresh rates (*maximum*) You can either enter fixed numbers seperated by commas ie: 60,75,80,85 or a range seperated by a dash ie: 60-120hz (*leave out the hz*) You will have to do this for BOTH the horizontal AND the vertical (*which will be presented to you on the next screen*) It is strongly advised that you know these settings for your monitor.

Oh, I forgot, one more thing, before it presents you with those steps above, it will ask you to choose what modes you would like for your monitor. It will give you a preset list ie: 640x480 800x600, 1024x768 and so on. Choose only the ones you would like used for Ubuntu. Always choose at least 3 modes. If you choose only one, then you will not have a fallback resolution if your settings are funked, and you will not have the option to change resolutions if you wanted to, later while using Ubuntu. I choose 800x600, 1024x768, 1280x1024.

After doing this you will be presented with the monitor timings. It will ask if you want the configuration to be written to xorg. Always choose yes.

If things get messed up, drop to console as described earlier, browse to  /etc/X11/ (**cd /etc/X11**)and type **dir ls** (*You may want to try dir xorg*. This wlil present you with only the relevent info*)you will see xorg.conf and xorg.conf.(timeanddate). You may also see xorg.conf~ *For me the xorg.conf~ was the most recent backup.*

choose one of those and type the following:

**sudo mv xorg.conf xorg.garbage**
(*seeing as how that xorg.conf doesn't work for you. This way you will know not to use it*).

next choose a xorg.conf file from the list of backups.

then type this:

**sudo mv xorg.conf.200702112103 xorg.conf**

Replace the xorg config in this example with one that actually matches what you see in console.

now you can reboot.

**reboot**

---

### Post by macguy918 on 2007-01-24
Thanks.  Scanning the error logs at the blue screen during bootup led me to a simple error in the xorg.conf file where I had changed the name of the monitor from generic monitor to what i actually have in one location but failed to change the name in another location.

Once I fixed that error I was able to reboot and the resolutions are correct.

The thing that threw me more than anything was that I could not figure out how to get to a command line prompt from that blue screen error where it walks through the error logs.  I had a blinking cursor, and could type and see what i typed, but I couldn't figure out how to break out of that mode into a command line where I could edit the xorg.conf file.

Somehow I finally got to the command line and got it done, but I have no idea what I did that put me in command line mode.

Oh well...it all works now.

---

### Post by Tim T on 2007-01-29
just signed up to say that this is my second day of ubuntu and this helped me a ton. now i know i don't need to reinstall when things break lol! i'm cruising perfectly @ 1280x1024, and nothing broke when I followed your method!

---

