---
title: "Installing Feisty on a PC with GeForce 3"
date: 2007-07-11
forum: Installation &amp; Upgrades
---

### Post by Akira_Oni on 2007-07-11
I have an older model computer using a p3 processor (not sure of all the specs) and 384 megs of ram which I'm trying to install Ubuntu on. However when I try to boot from disk it gives the following messages:

[PHP]236.778472 - Buffer I/O error on device fd0, logical block 0
274.8570061 - Buffer I/O error on device fd0, logical block 0[/php]

Then, as it's initializing processes, it provides this error:

[php]iTCO_wdt: failed to reset No_Reboost flag. Reboot failed due to hardware.[/php]

During a normal launch, it would freeze with a blank screen shortly after this point. However when launching in Graphically safe mode, the black screen is shortly followed by a message that XWindows has failed, followed shortly by a command line screen with the screenname Ubuntu.

I'm not really sure how to proceed with installation, especially without the graphical interface. Sorry I'm a noob.

---

### Post by Qrk on 2007-07-11
Use the command:

```
sudo dpkg-reconfigure xserver-xorg
```

and choose a driver other than the one currently selected (on the second screen), such as 'vesa,' which is very stable but slow. 

Once you go through the configuration (if you don't know what something means, just press enter and you will be fine 99% of the time)

Once that is done, use the command:
```
startx
```
and you should be ready to go.

---

### Post by Akira_Oni on 2007-07-11
After attempting the steps I was directed to, I was given the following response:

[php](WW) VESA: No Matching Device section for instance (BUS ID: PCI:1:9:0) found
(EE) VESA (0): Cannot read V_BIOS
(EE) Screen(s) found, but none have a usable configuration.

Fatal Server Error:

no screens found

XIO: fatal IO error 104 (connection reset by peer) on Xserver ":0.0" after 0 requests (0 known processed) with 0 events remaining.[/php]

Upon rebooting the system information stated that my card type was VGA/EGA, so I tried it with a VGA setup. The screen went black for a moment, like it might be successful, however returned this error:

[php](WW) VESA: No Matching Device section for instance (BUS ID: PCI:1:9:0) found
(EE) VESA (0): Cannot read V_BIOS

Backtrace: 

0: /usr/bin/X11/X(xf86SigHandler+081) [0x80c5d91]

*** Insert Long backtrace here ***

11:  /usr/bin/X11/X(FontFileCompleteXLFD+0x1e1) [0x8073ab1]

Fatal Server Error:
Caught signal 11. Server Aborting

XIO: fatal IO error 104 (connection reset by peer) on Xserver ":0.0" after 0 requests (0 known processed) with 0 events remaining.[/php]

Please forgive me that I didn't do the entire backtrace. I had to write all this on paper and take it to another pc to post this. 

The video card has worked with several other distros, such as DSLinux and Fedora, without issue. However I really would like to move back to using Ubuntu. Can anyone help me with this?

---

### Post by Qrk on 2007-07-11
I'm not sure if I know of a driver that will work if the so-called "safe" ones don't. 

However, considering that it is a geforce3 graphics card, why don't you try installing ubuntu with the alternate cd. 

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) (check the alternate cd box)

This will allow to install Ubuntu without X. Don't worry, the installer is just as easy to use as the graphical one.

Once you get Ubuntu installed, you can install the correct driver for your card with:

```
sudo nano /etc/apt/sources.list
```

Remove the # from the lines which only have one # (not two, ##)

Now you can run a:

```
sudo apt-get update
```

Once you've done that, type in:

```
sudo apt-get install nvidia-glx
```

Now you should reboot. 

If you don't boot into a graphical environment after all this, run:

```
sudo dpkg-reconfigure xserver-xorg
```

again and select "nvidia" as your driver on the second screen. With a 

```
startx
```

you will hopefully be on your way. 

Ubuntu use to use the alternate cd installer as the default. In the spirit of user-friendlyness to new people, they changed it to be a lovely livecd instead. The other side of the coin is that people who don't have supported hardware can't install using the traditional method. Don't fear, once the alternate version is installed, it is the exact same thing.

---

### Post by Akira_Oni on 2007-07-13
Ok, so I've tried twice to install this version. Each time I downloaded from a different source, and burned onto a separate cd using different computers. However the installers keep failing. The first time the data came out corrupt, and wouldn't load. THe second disk just wouldn't load the installer. Could it be my disk drive?

---

### Post by Akira_Oni on 2007-07-14
*** Bump ***

---

### Post by Akira_Oni on 2007-07-14
Ok, I did get it to install, but it installed with X set as default and I can't make the system convert to command line. I tried CTRL+BACKSPACE, CTRL+ALT+BACKSPACE, CTRL+ALT+F1... What else should I do?

---

### Post by Pumalite on 2007-07-14
256 MB RAM or less>Xubuntu Alternate CD

---

### Post by Akira_Oni on 2007-07-14
I have a 128 stick and a 256 stick installed. It's just the video card which won't cooperate.

---

### Post by Pumalite on 2007-07-14
When you get stuck without a graphical interface try: sudo dpkg-reconfigure xserver-xorg
Most of the answers would obvious to you, when you get to driver: choose 'vesa' Exit. Then startx

---

### Post by Akira_Oni on 2007-07-15
Perhaps I should explain more clearly.

My video card does not currently support the GUI. Therefore when I attempt to load it I get a black screen. My only recourse is to attempt to correct the issue by command line,  however I am having difficulties accessing the interface.

So to recap, I'm not stuck without a graphical interface, I'm stuck in it. Any suggestions of what I can use?

BTW: Vesa hasn't worked yet.

---

### Post by Akira_Oni on 2007-07-15
Ok, so I rebooted in recovery mode and it forced the command line interface from root. I've used the nano command and typed in what you told me at the bottom of the page. However when I use "apt-get update" it returns an error telling me that 'Install' is not recognized. And, of course, I don't have an install location to install this without it.

*edit*

I have been able to "apt-get install nvidia-glx"  which then installed nvidia-glx-new, however now it's not working. When I autodetect with dpkg-reconfigure it lists an intel chip. I think it may be reading my onboard video first, and ignoring my GeForce. How do I make it recognice the installed chip as the primary one?

---

### Post by dvastator82 on 2007-07-18
Try oldest driver from [http://www.nvidia.com/object/linux_display_archive.html](http://www.nvidia.com/object/linux_display_archive.html)
i using Version: 1.0-8776 and don't have any problems.

---

### Post by lukalock on 2007-08-25
Ok,  I did everything suggested in this thread, but now after the Ubuntu "orange bar" loading screen, instead of going to the login screen like I was hoping, it just goes to a black screen and stays there...

any ideas?  I have been working at this for over 3 weeks now and have tried every possible fix listed...

is Ubuntu just not meant to run with an NVidia graphics card???

---

### Post by Pumalite on 2007-08-25
Post your specs. You might need a 'Legacy' driver.

---

