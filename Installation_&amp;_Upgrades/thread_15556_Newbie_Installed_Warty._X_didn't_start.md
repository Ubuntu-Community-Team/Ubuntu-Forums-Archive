---
title: "Newbie: Installed Warty. X didn't start"
date: 2005-02-15
forum: Installation &amp; Upgrades
---

### Post by CitricAcid on 2005-02-15
Hello!
I have installed Warty. Everything went fine. After reboot X server didn't start. How can I make it run?

-edit-
I ran Live distribution also and there everything went ok.
I forgot to add that I didn't find solution on forum. If anybody could help me please :)
-/edit-

---

### Post by lao_V on 2005-02-15
CitricAcid,

Do you see a login prompt? If so login and then type startx...

---

### Post by CitricAcid on 2005-02-15
Yes. After Alt+F1 I saw. I'll try.

---

### Post by CyrilleMortreux on 2005-02-15
[QUOTE=CitricAcid]Yes. After Alt+F1 I saw. I'll try.[/QUOTE]

And 

dpkg-reconfigure xserver-xfree86 ???

and then 

/etc/init.d/gdm start

---

### Post by CitricAcid on 2005-02-15
I forgot to add that X didn't start because of an error. It was something about that X server couldn't be loaded.

---

### Post by CyrilleMortreux on 2005-02-15
[QUOTE=CitricAcid]I forgot to add that X didn't start because of an error. It was something about that X server couldn't be loaded.[/QUOTE]

hem ;)   

Give us the log

/var/log/XFree86.0.log

To reconfigure your xserver, follow what I wrote before :

dpkg-reconfigure xserver-xfree86

You may boot from the live CD, mount your local partition, and copy the live XF86Config down on your hard disk.
Then reboot, and try to use it. 

I did it before on my laptop and that was a Knoppix who saved me from hell ;)

---

### Post by CitricAcid on 2005-02-15
[QUOTE=CyrilleMortreux]
(..) and copy the live XF86Config down on your hard disk.
Then reboot, and try to use it. 
[/QUOTE]

Ok. But where can I find XF86Config??  :?

---

### Post by CitricAcid on 2005-02-16
OK ](*,)  :oops: 
Position of XFree86 config file is shown i log :D
I have attached my log.

But there's another problem.

I tried to log in as root. I don't know p***word for root. I tried empty p***. It didn't work. I looked into the documentation and found how to set root's p***

sudo p***wd root

... but it asked me for root p*** again...

What to do? :cry:

-edit-
OK. I read FAQ 
-/edit-

---

### Post by CyrilleMortreux on 2005-02-16
[QUOTE=CitricAcid]OK ](*,)  :oops: 
Position of XFree86 config file is shown i log :D
I have attached my log.

But there's another problem.

I tried to log in as root. I don't know p***word for root. I tried empty p***. It didn't work. I looked into the documentation and found how to set root's p***

sudo p***wd root

... but it asked me for root p*** again...

What to do? :cry:[/QUOTE]

Not really that.

"sudo p***wd root" 

1st, it asks you for YOUR user p***word to ensure you're in the sudo group !
Then, it asks you to enter twice the root p***wd
Then, root account is active

XF86Config or XF86Config-4 is there /etc/X11/XF86Config

ok ?

I ain't found your logs ... (am I stupid ?), I 'm rather new to this forum.

---

### Post by CitricAcid on 2005-02-16
You aren't stupid at all :)

There is a frame "Atached files" between my message and signature. There's a link to zipped log file. Just click and download :)

Done with that p***. I read FAQ. I tried that dpkg... but probably configured it wrong and the i typed:
sudo /etc/init.d/gdm restart

But the result was the same.

I'm waiting your reply about what in my log is :)

---

### Post by CyrilleMortreux on 2005-02-16
Fatal server error:
could not open default font 'fixed';
the X server's font paths might be misconfigured, remote font server(s)
may be unreachable, and/or local fonts may not be installed or are not
configured correctly.


Ok. Now, Have a look at your /etc/X11/XF86Config
There is something wrong with your font path, I don't really see what coz I have nothing about fixed fonts in my own file.

If you find something about "fixed fonts", just try to comment the line. 

Here is the begining of my file : 

Section "Files"
        FontPath        "unix/:7100"                    # local font server
        # if the local font server has problems, we can fall back on these
        FontPath        "/usr/lib/X11/fonts/misc"
        FontPath        "/usr/lib/X11/fonts/cyrillic"
        FontPath        "/usr/lib/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/lib/X11/fonts/Type1"
        FontPath        "/usr/lib/X11/fonts/CID"
        FontPath        "/usr/lib/X11/fonts/Speedo"
        FontPath        "/usr/lib/X11/fonts/100dpi"
        FontPath        "/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

According to you log file, the XF86Config file seems to be pretty good unless you change the font path. 

You may try also to see if xfonts-base is correctly installed:

badlieutenant:/etc/X11# dpkg --status xfonts-base
Package: xfonts-base
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 7444
Maintainer: Ubuntu X Maintainers <ubuntu-devel@lists.ubuntu.com>
Architecture: all
.../...

or try to insalled it in that case : 
badlieutenant:/etc/X11# apt-get install xfonts-base
Reading Package Lists... Done
Building Dependency Tree... Done
xfonts-base is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

---

### Post by CitricAcid on 2005-02-18
I've edited XF86Config-4 (there was no XF86Config) but I didn't find anything bout fixed fonts. 
I tried to apt-get install a package that was suggested in the log (something like x-window-system-core). It has checked dependencies and downloaded 20 MB of data. After that X has started. But there still are some errors. I hadn't time to check them out so I'll tell you later what I have found.
But as I can see for know there are some problems with fonts. Looks like they're missing.

I didn't try installing xfont-base yet.

Let you know later what happend :)

---

### Post by CitricAcid on 2005-02-18
I have found in my log file something like this:

(II) Primary Device is: PCI 02:00:0
(II) ATI:  Candidate "Device" section "ATI Technologies, Inc. Radeon 9000 Pro (RV250 If)".
(WW) ATI:  PCI/AGP Mach64 in slot 2:0:1 could not be detected!
(WW) RADEON: No matching Device section for instance (BusID PCI:2:0:1) found
(--) Chipset ATI Radeon 9000/PRO If (AGP/PCI) found 


Should I worry about it?



And about fonts. There are some warnings in log:

(WW) The directory "/usr/lib/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "unix/:7100,/usr/lib/X11/fonts/100dpi/:unscaled,/usr/lib/X11/fonts/75dpi/:unscaled,/usr/lib/X11/fonts/Type1,/usr/lib/X11/fonts/Speedo,/usr/lib/X11/fonts/100dpi,/usr/lib/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"


and:


Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
Could not init font path element unix/:7100, removing from list! 



It seems that something is missing. I hope soon I can get home to try to fix it  :D

---

### Post by CitricAcid on 2005-02-18
X has started :)

Instlling x-window-system-core was enough.

Thanks for help :)

---

