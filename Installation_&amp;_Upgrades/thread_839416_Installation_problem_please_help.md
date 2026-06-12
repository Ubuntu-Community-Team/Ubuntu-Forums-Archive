---
title: "Installation problem: please help"
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by pbanker on 2008-06-24
I am relatively new to linux.I am trying to install on ubuntu Version 8.04 (April 2008) on acer amd 64. This laptop doesn't have an OS. When trying to install after spalsh screen where rectangle moves, i get message loading kernel.

Then i get this message:

[157.817529] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.
[159.573837] go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version4)

and the screen goes to standard orange screen. Can you please tell me how to resolve this that i can get past this issue to continue installation? I don't know how to load firmware.

Do you think i should install 7.10 that i don't face this issue?? if so where can i get the 7.10 image?

Thanks in advance ..appreciate the help.

---

### Post by pytheas22 on 2008-06-24
What does the "standard orange screen" look like?  I'm not sure what you mean there.

I don't actually think that your problem is related to the b43 messages.  Those are normal; you're not supposed to have the firmware installed until later.  I think you're seeing the messages only because you're being dumped to a terminal where error messages are being shown, and they're one of the error messages, but they're not related to your real problem.  The real problem is probably an issue with X.

So please describe the orange screen in greater detail, and also please tell us which graphics card and motherboard you're using.

Also, you can download the image for 7.10 from releases.ubuntu.com/7.10/ if you want to see if that works better.  It would be a lot better for you to use 8.04, since it's a long-term-support release and is newer.  But if 7.10 works (which it might) then at least it helps to narrow down the possible causes of the problem.

---

### Post by pookieman on 2008-08-11
Hi

I am a complete novice and am having very similar problems to the person that posted originally. Basically I have tried to run the LIVECD install. After a while, the bar scrolling disappears the error 

b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load failed.

appears. I've googled etc and found a link to this article:

go to [http://linuxwireless.org/en/users/Dr...devicefirmware](http://linuxwireless.org/en/users/Dr...devicefirmware) and download the correct firmware (version4)

This is all fine, but how do I untar when I can't even boot into the OS? Am I being really thick here? The laptop is a DELL Inspiron 1300, it has Windows on it. Should I upgrade the firmware from within Windows first? Is that possible. 

I've seen other posts talking about modifying the install but this is burnt on a CD. I wanted to do a clean install but I then thought maybe if I install into Windows it will work. The copy worked, there is now a ubuntu directory on my C drive. But when I boot into it I have the same problem, after a while the screen goes blank and nothing. Is there a combo that I can press which will give me a terminal or something.

I don't want to fail at the first hurdle there must be a solution to this.

Thanks for any help you can offer, or point me in the direction of other posts. I've got the latest distribution ubuntu-8.04.1-desktop-i386.iso

---

### Post by pytheas22 on 2008-08-11
b43 is not the issue here.  b43 is just a wireless driver, and by default Ubuntu doesn't ship with the firmware for it installed (because it's proprietary), so b43 dumps complaints to the virtual terminal about the firmware not being there.  You can easily install the firmware later; this is not a big deal.  But the absence of the firmware is not the reason that you're unable to start a graphical interface.

The likely culprit is your video driver.  Do you know the exact model of your graphics card?  If you tell me that, I might be able to make suggestions on how to solve the problem.

If you don't know the model of your video card, let me know and I'll tell you how to figure it out on Ubuntu without logging in graphically.

---

### Post by pookieman on 2008-08-12
The graphics card according to Windows is 

Mobile Intel 915GM/GMS, 910GML Express Chipset - this must be some intel integrated graphics card

---

### Post by pytheas22 on 2008-08-12
Intel video should work well, but there are two different drivers for it, and maybe switching to the older one would help.  To do so, first press control-alt-F2.  You should come to a textual login screen.  Log in if you're not already (the username is probably "ubuntu" and the password I think is blank).  Then open your xorg.conf file with the command:
```

sudo nano /etc/X11/xorg.conf
```

Scroll down through the file until you come to the "device" section (about halfway down).  It should look like this:
```

Section "Device"
	Identifier	"Configured Video Device"
EndSection
```

and you want it to look like this:
```

Section "Device"
	Identifier	"Configured Video Device"
        **driver          "i810"**
EndSection
```

After you've written in the changes, press control-O (the letter, not zero) to save the file.

After you've saved it, press control-alt-F7.  This will bring you back to the screen that I guess it's hanging on now.  Once there, press control-alt-backspace to restart X.  If you're lucky, things will work now.

If none of this helps (and I'm not sure how well it will work, because I'm not used to dealing with the environment on the installation CD before the installer even starts), you could try installing using the alternate-install CD.  Go to [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and choose the option that says "Click here to download the alternate CD."  This CD doesn't use a graphical installer and will hopefully allow you to install the system normally.  It's definitely worth a shot.

---

### Post by pookieman on 2008-08-13
I tried something slightly different, and have a slightly different issue now! I ran the install LIVECD from windows and chose the option to install alongside Windows, this seemed to work, I rebooted, picked ubuntu. 

I then pressed escape at the boot screen and choose safe graphics mode. Now the installation screen came up with the orange bird like background.

The partioning/identifying file systems dialog comes up, this takes about an hour to complete, once it gets to 100%, the screen just goes blank!

I thought maybe the laptop isn't powerful enough, it's a celeron 1.5ghz, 256mb memory, this should be just about enough. I'd like to provide more information, but I don't know how to access any sort of log as the screen is just blank. One thing I did notice was the harddisk light continues to flicker, but I can't believe it's still doing something, I left it running for hours and nothing came back.

Is there a key combination that will get me to a CLI?

---

### Post by pytheas22 on 2008-08-13
> Is there a key combination that will get me to a CLI?

Yes, if you press control-alt-F2, you should be brought to a command-line (as long as the live CD works the same way as normal Linux).  From there, if you run the command:
```

dmesg | less
```

you'll get a log, in chronological order, of everything that's happened since the system rebooted.  If you see anything interesting, google it or let me know what it is.

Also, 256 megabytes is really the bare minimum that you should have for running a graphical live CD; this could indeed be the problem.  You may want to check out the alternative CD, which uses much less memory.

---

### Post by pookieman on 2008-08-13
Apologies I re-read your previous reply, RE: how to get to a command prompt. OK I think I know what the problem might be, I ran 'free' and got this:

Total     used     free
247440    240848   6592

So this might just be an issue of not being enough memory, I'm hoping this is all that is going on. I'm going to order some from ebay today, and I'm hoping that will speed things up. In theory does the install use swap? It's weird when I did df -k, I can see a bunch of file systems, but I haven't configured any yet, can I setup some swap for the install to use in the meantime, I guess not.

---

### Post by pytheas22 on 2008-08-13
Memory could be the issue.  Generally 256 megabytes is the recommended minimum for a live CD, although even with that you might have problems.  I had a tired old Pentium III with 256 megabytes once and I never got even the Xubuntu live CD to boot at all on it.  But I was able to install with the alternative CD and Xubuntu ran fine thereafter.

Also, it's normal for Linux to be using all of the memory (according to 'free'), because it tries to always be doing stuff with it (like preload things that it thinks you're going to want later, so that they'll load faster), so just because you have very little free doesn't necessarily mean that memory is the problem.  For instance, I have 2 gigabytes of memory in my machine but still only 45 megabytes free right now, and I'm not running any applications besides Firefox, Evolution and Pidgin:

```
$free -m
             total       used       free     shared    buffers     cached
Mem:          2006       1961         45 
```

If memory were the issue, then installing using the alternative CD would probably work better, because that installer requires much less RAM.  Before you buy more RAM, I'd give the alternative installer a try.

---

