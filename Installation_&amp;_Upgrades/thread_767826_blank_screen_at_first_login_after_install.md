---
title: "blank screen at first login after install"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by jmknsd on 2008-04-25
Just installed hh, and unlike gg, it installed without a hitch to my HP tx1000(TL-58 1.9Gz, NV Grforce 6150 Go, 2GB RAM, running off of an 8GB flash drive)
After I booted it back up, the gui logon page came up normally(just like on my desktop) but after I login, I get nothing but a beige background and a cursor, can also get to a terminal, but don't know what to do once there.
Google gave me "sudo dpkg-reconfigure xserver.org" 
but I got an 'xserver.org is not installed' error

Stumped, any ideas?

---

### Post by Partyboi2 on 2008-04-25
try ```
sudo dpkg-reconfigure xserver-xorg
```
not
```
sudo dpkg-reconfigure xserver.org
```

---

### Post by jmknsd on 2008-04-25
> **Partyboi2 said:**
> try ```
sudo dpkg-reconfigure xserver-xorg
```


same result
```
Package 'xserver-org' is not installed and no info is available.
```

---

### Post by Partyboi2 on 2008-04-25
make sure the last part is -xorg not org
so 
```
sudo dpkg-reconfigure xserver-xorg
```
If its typed incorrect you will get something like this displayed in the terminal window
> Package `xserver-org' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver-org is not installed

---

### Post by jmknsd on 2008-04-26
/facepalm

 got it to run, but It only asked me about the keyboard, and problem hasn't changed =/

---

### Post by Partyboi2 on 2008-04-26
Have a look to see if there are any errors reported in the Xorg.0.log file.
```
cat /var/log/Xorg.0.log | more
```
Use the enter key or space bar to scroll down. Look for any lines that start with
(EE) If there is any lines that start with (EE) write then down and post them.

---

### Post by jmknsd on 2008-04-26
I eyeballed it to be sure, but grep returned no lines with (EE) in them(except the one explaining what the markers meant)

---

### Post by jmknsd on 2008-04-26
no responses, and after searching all 5 pages of posts since I last posted, I haven't seen my problem addresed.

Sooo, bump for getting hh to work on my laptop before finals start.

---

### Post by blastus on 2008-04-26
Looks like I have the same issue here. Everything worked fine in Gutsy. Running Hardy off of an 8GB USB key with NVIDIA 8500GT card. After I login nothing happens, the screen goes blank orange with a cursor I can move around and that's about it. The FailSafe GNOME session won't even load either.

There does not appear to be any errors in dmesg or xorg logs. I have tried a DVI-HDMI cable, DVI cable, and a D-SUB cable with an LCD-TV and an LCD-Monitor and the results are the same. It's like the video card doesn't even exist as there is no evidence of even the open source nv driver in there. I have tried fixing X and reconfiguring X also.

---

### Post by jimrobb on 2008-04-26
I think I may have a similar problem. I :(installed the 8.04 Beta version to a 4G Corsair USB drive. The date I downloaded the Beta was 4/13/2008. That install went fine and I was using the system running from my USB with no problems. On 4/24 I downloaded the shipped version of 8.04 and installed it to the same USB drive the same way I installed the Beta. When complete I did a startup and it came up and asked for my ID and Password it then ran for a while put up the blank orange screen and the cursor but nothing else happened. I never get the music intro or the Heron and top line. The USB continues to flash periodically and I can move the cursor but there is no reaction to anything I do on the keyboard or the mouse. I have tried redefining partitions on the USB several times before the install even though I select use entire disk. After doing the release install multiple times I went back and installed the Beta again. It works fine. I'm a novice on Ubuntu and don't know if I am missing something obvious or not. But I don't know what else to try on installing the released version.

---

### Post by blastus on 2008-04-26
This sucks. :( 

I don't think it has anything to do with installing Hardy to a USB key. I installed Hardy the same way I installed Gutsy by creating an initramfs image and also by just rebooting after the initial installation and the results were the same...blank orange screen with a cursor that you can move around.

---

### Post by blastus on 2008-04-26
Check out this bug and workaround [Blank screen After Login from Gdm Bug #221850](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/221850)

---

### Post by dougvan on 2008-04-26
I have the exact same problem booting from a 4bg Sandisk Cruzer Micro USB drive. I did find a temp workaround.

I ran:
sudo dpkg-reconfigure xserver-xorg

In the config I told it not to use framebuffer and accepted the defaults for everything else.

I then did:
sudo killall gdm

I can now type startx from the prompt and get the GUI to come up fine. Problem is, after reboot I get the same blank screen and have to do ALT+Crl+F2 to get the terminal and do the sudo killall gdm and startx to get back in.

This will at least get you guys in and hopefully since you guys have more linux knowledge than I do, help you with a fix as well. Let me know if anything changes.

---

### Post by jmknsd on 2008-04-26
ehh, lots o problems, not many solutions.
bump for more answers!

---

### Post by jmknsd on 2008-04-27
> **dougvan said:**
> I have the exact same problem booting from a 4bg Sandisk Cruzer Micro USB drive. I did find a temp workaround.

I ran:
sudo dpkg-reconfigure xserver-xorg

In the config I told it not to use framebuffer and accepted the defaults for everything else.

I then did:
sudo killall gdm

I can now type startx from the prompt and get the GUI to come up fine. Problem is, after reboot I get the same blank screen and have to do ALT+Crl+F2 to get the terminal and do the sudo killall gdm and startx to get back in.

This will at least get you guys in and hopefully since you guys have more linux knowledge than I do, help you with a fix as well. Let me know if anything changes.
is there a better solution?

---

### Post by dr.phees on 2008-04-28
My problem is similar. After login (xfce) i have a light-blue screen. I can login into gnome, however. After logout, xfce-sessions work flawless. The problem is reproducible after every reboot.
- I reinstalled the xubuntu defaultsettings -> same problem
- /var/log/Xorg.0.log has no EE entries
- xorg.conf is the same as in gg. is that ok?

My system is a T40 Thinkpad, ATI card running on the radeon driver. glxgears is running perfectly, direct rendering is "yes", so the driver is working as it is supposed to.

---

### Post by ruatuki on 2008-04-28
Same problem with Thinkpad T42. Blastus solution (via link) worked for me.

---

### Post by jmknsd on 2008-04-29
works, but If I want to restart my window manager, I have to reboot, although I haven't tried alt-F2 startx method... rebooting seems easier and less time consuming though. wish there was a 'fix' I knew about >.>

---

### Post by Keith5698 on 2008-05-01
The link above worked for me as well.  Thank you very much!

---

### Post by ironsizide on 2008-06-18
> **dougvan said:**
> I have the exact same problem booting from a 4bg Sandisk Cruzer Micro USB drive. I did find a temp workaround.

I ran:
sudo dpkg-reconfigure xserver-xorg

In the config I told it not to use framebuffer and accepted the defaults for everything else.

I then did:
sudo killall gdm

I can now type startx from the prompt and get the GUI to come up fine. Problem is, after reboot I get the same blank screen and have to do ALT+Crl+F2 to get the terminal and do the sudo killall gdm and startx to get back in.

This will at least get you guys in and hopefully since you guys have more linux knowledge than I do, help you with a fix as well. Let me know if anything changes.

I had the same issues after installing hardy on a Corsair 16GB flash drive. My problems disappeared though after fiddling with how the drive booted. I removed GRUB from the hard drive on the laptop so I could boot without the flash drive attached and boot right into Vista (which is on the HD). Then I fiddled with the GRUB settings on the flash drive. The flash drive was listed as drive 1 and the HD as drive 0, and I wanted those reversed when booting from the flash drive.

Once I changed the drive settings in GRUB so that I could boot the flash drive properly, all of the problems with the blank screens and using the killall gdm workaround disappeared and now I have my desktop working normally.

So perhaps it's an issue with how the flash drives boot. All I know for sure is that now it all works for me normally and trying what I did may work for others as well.

---

### Post by HDave on 2008-06-21
> **dougvan said:**
> I then did:
sudo killall gdm

I can now type startx from the prompt and get the GUI to come up fine.

Many thanks to dougvan for the workaround.  Once I got into my session, my ethernet adapter was up and I could patch my system to fix it for good via:

```
sudo aptitude update
sudo aptitude safe-upgrade
```

Now all is well.  Had the problem with a Corsair Voyager 8GB stick.

---

### Post by pietjanjaap on 2008-06-22
dpkg-reconfigure xserver-xorg has changed in 8.04:


2 try this:
dpkg-reconfigure xserver-xorg is not the same anymore, now you can install your keybord and more with this.
But your videocard and monitor goes like this,
start in safe mode,
choose the last options with the x,
Here ubuntu will search and identify your monitor and videocard, so you have all your posssible settings.
Then reboot and install your videcard driver.(i use envy for this).

---

### Post by latomp on 2008-07-17
Hi, I have this same problem after upgrading to HH: login is fine, but only get orange screen and movable cursor afterwards.   However, i can't get a terminal to open from my blank desktop. I do atl-F2, ctrl-atl-F2, and all sorts of other permuations of alt, ctrl, f1 and f2 without any success.  Any suggestions?

---

### Post by wafy8a on 2008-08-03
hurmm..me also having the same orange screen and movable cursor..help me..i only have this OS only to do my work..hope u guys can help me

---

