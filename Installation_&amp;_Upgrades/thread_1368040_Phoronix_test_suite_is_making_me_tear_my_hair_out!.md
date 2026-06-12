---
title: "Phoronix test suite is making me tear my hair out!"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by Fatfool on 2009-12-30
Now, this was supposed to be simple but as always, something just has to go wrong.

I downloaded the test suite .deb here:
[http://www.phoronix-test-suite.com/releases/repo/pts.debian/files/phoronix-test-suite_2.2.0_all.deb](http://www.phoronix-test-suite.com/releases/repo/pts.debian/files/phoronix-test-suite_2.2.0_all.deb)

installed it and I see 'Phoronix Test Suite' under 'System tools"
Great. so Ok i click it and.... nothing happens.

I check the command for that link and I find 'phoronix-test-suite gui'

Now for some moronic reason which I cannot fathom, this command is known not to work without some extra work :popcorn:

I check the documentation:
[http://www.phoronix-test-suite.com/documentation/2.2/install.html](http://www.phoronix-test-suite.com/documentation/2.2/install.html)
I see:
> There is a GTK2 interface written for the Phoronix Test Suite that can be used by running phoronix-test-suite gui. In order to use the GTK user interface, the PHP GTK module must be installed and loaded. This PHP module can be found at gtk.php.net. PHP GTK for Mac OS X can be found here. For instructions on building PHP GTK for Ubuntu/Debian, see this forum thread.
'this forum thread' leads to:
[http://ubuntuforums.org/showthread.php?t=1108731](http://ubuntuforums.org/showthread.php?t=1108731)

after jumping through multiple hoops,
I see:
5) Edit php.ini and load php-gtk module

Code:
```
sudo nano /etc/php5/cli/php.ini
```
Find "Dynamic Extensions" Section and add

Code:
```
extension=php_gtk2.so
```

I can't get through this portion as I can't seem to save this /ini file! 
[IMG]http://img.photobucket.com/albums/v140/Fatfool/iniscreenshot.png[/IMG]

Its quite surprising as .deb packages usually work fine. But like anything else in ubuntu, hoops just need to be jumped :confused:

---

### Post by Fatfool on 2009-12-31
bump bump

---

### Post by Fatfool on 2010-01-02
Erm anyone have an idea how to save?

---

### Post by Fatfool on 2010-01-04
No one uses the test suite?

---

### Post by Aikimox on 2010-01-04
I can only say - join the club. I have the same issue with Phoronix. Tried uninstalling it and installing the older version through synaptic, now I don't even see the program in the system tools anymore...

---

### Post by Aikimox on 2010-01-04
Ok, I get the same output in terminal by running both versions, so back to the newer one. I also installed the php5-cli /gd etc... and have all the packages installed following this[ link]("http://phoronix-test-suite.com/?k=downloads")
What graphics card/s do you have?

---

### Post by Aikimox on 2010-01-04
Some progress - try running the following from the terminal: **phoronix-test-suite benchmark video-extensions** see what happens ;)

---

### Post by Aikimox on 2010-01-04
So basically, you can run all the tests from terminal by typing the same **phoronix-test-suite benchmarks** _***benchmark name***_, [**here**]("http://global.phoronix-test-suite.com/?k=category&u=lightsmark") are the tests names. just did a lightsmark run and got a very low score 128 . Something is fishy with my drivers...

---

### Post by Fatfool on 2010-01-06
> **Aikimox said:**
> Ok, I get the same output in terminal by running both versions, so back to the newer one. I also installed the php5-cli /gd etc... and have all the packages installed following this[ link]("http://phoronix-test-suite.com/?k=downloads")
What graphics card/s do you have?
I tried installing it too but i was stumped at that piece of instruction above. I use an integrated HD3200 on my Minix 780G rig. intend to install an S3 Chrome 600 series card whenever its released. Once I do that, I'll come back to these forums to spam and complain about the S3 drivers on Linux lol!!

---

### Post by Fatfool on 2010-01-06
> **Aikimox said:**
> Some progress - try running the following from the terminal: **phoronix-test-suite benchmark video-extensions** see what happens ;)
Just entered It in. what exactly does it do? It seems to have started downloading some video file..

ok its done. a a benchie popped out. now where are the results.... hmmmm

---

### Post by Fatfool on 2010-01-06
```

Downloading File: mplayer-2009-06-04.tar.bz2

--2010-01-06 23:15:39--  http://www.phoronix-test-suite.com/benchmark-files/mplayer-2009-06-04.tar.bz2
Resolving www.phoronix-test-suite.com... 70.85.96.187
Connecting to www.phoronix-test-suite.com|70.85.96.187|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 15191483 (14M) [application/x-tar]
Saving to: `mplayer-2009-06-04.tar.bz2.pts'

100%[======================================>] 15,191,483   135K/s   in 97s     

2010-01-06 23:17:17 (152 KB/s) - `mplayer-2009-06-04.tar.bz2.pts' saved [15191483/15191483]


====================================
Installing Test: mplayer-base
Estimated Install Size: 30 MB
====================================


====================================
Installing Test: video-extensions
Estimated Install Size: 31 MB
====================================


Would you like to save these test results (Y/n)? Y
Enter a name to save these results: Test 1
Enter a unique name for this test run: Test 1

###########################################
If you wish, enter a new description below.
Press ENTER to proceed without changes.
###########################################

Current Description: This is a test of playing back a short video file with different video extensions supported by X.Org and MPlayer.

New Description: 

=========================================
MPlayer Video Playback Tests (Run 1 of 1)
=========================================


#########################################
MPlayer Video Playback Tests:
Supported Video Extensions


Final: -1 (GL, GL2, X-Video, XvMC, VDPAU)

#########################################

jeffery@jeffery-desktop:~$ phoronix-test-suite benchmark lightsmark


The following dependencies will be installed: 
- freeglut3-dev
- libglew1.5-dev
- libfreeimage3
- libfreeimage-dev

This process may take several minutes.
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
The following NEW packages will be installed:
  freeglut3{a} freeglut3-dev libfreeimage-dev libfreeimage3 
  libgl1-mesa-dev{a} libglew1.5{a} libglew1.5-dev libglu1-mesa-dev{a} 
  mesa-common-dev{a} xlibmesa-gl-dev{a} 
0 packages upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 20.7MB of archives. After unpacking 74.2MB will be used.
Writing extended state information...
Get:1 http://sg.archive.ubuntu.com karmic/main freeglut3 2.4.0-6.1ubuntu1 [98.9kB]
Get:2 http://sg.archive.ubuntu.com karmic/main mesa-common-dev 7.6.0-1ubuntu4 [177kB]
Get:3 http://sg.archive.ubuntu.com karmic/main libgl1-mesa-dev 7.6.0-1ubuntu4 [29.3kB]
Get:4 http://sg.archive.ubuntu.com karmic-updates/main xlibmesa-gl-dev 1:7.4+3ubuntu10 [960B]
Get:5 http://sg.archive.ubuntu.com karmic/main libglu1-mesa-dev 7.6.0-1ubuntu4 [223kB]
Get:6 http://sg.archive.ubuntu.com karmic/main freeglut3-dev 2.4.0-6.1ubuntu1 [172kB]
Get:7 http://sg.archive.ubuntu.com karmic/universe libglew1.5 1.5.1-4ubuntu1 [94.8kB]
Get:8 http://sg.archive.ubuntu.com karmic/universe libglew1.5-dev 1.5.1-4ubuntu1 [188kB]
Get:9 http://sg.archive.ubuntu.com karmic/universe libfreeimage3 3.10.0-1 [2,008kB]
Get:10 http://sg.archive.ubuntu.com karmic/universe libfreeimage-dev 3.10.0-1 [17.7MB]
Fetched 20.7MB in 2min 9s (160kB/s)
Selecting previously deselected package freeglut3.
(Reading database ... 178006 files and directories currently installed.)
Unpacking freeglut3 (from .../freeglut3_2.4.0-6.1ubuntu1_amd64.deb) ...
Selecting previously deselected package mesa-common-dev.
Unpacking mesa-common-dev (from .../mesa-common-dev_7.6.0-1ubuntu4_amd64.deb) ...
Selecting previously deselected package libgl1-mesa-dev.
Unpacking libgl1-mesa-dev (from .../libgl1-mesa-dev_7.6.0-1ubuntu4_amd64.deb) ...
Selecting previously deselected package xlibmesa-gl-dev.
Unpacking xlibmesa-gl-dev (from .../xlibmesa-gl-dev_1%3a7.4+3ubuntu10_all.deb) ...
Selecting previously deselected package libglu1-mesa-dev.
Unpacking libglu1-mesa-dev (from .../libglu1-mesa-dev_7.6.0-1ubuntu4_amd64.deb) ...
Selecting previously deselected package freeglut3-dev.
Unpacking freeglut3-dev (from .../freeglut3-dev_2.4.0-6.1ubuntu1_amd64.deb) ...
Selecting previously deselected package libglew1.5.
Unpacking libglew1.5 (from .../libglew1.5_1.5.1-4ubuntu1_amd64.deb) ...
Selecting previously deselected package libglew1.5-dev.
Unpacking libglew1.5-dev (from .../libglew1.5-dev_1.5.1-4ubuntu1_amd64.deb) ...
Selecting previously deselected package libfreeimage3.
Unpacking libfreeimage3 (from .../libfreeimage3_3.10.0-1_amd64.deb) ...
Selecting previously deselected package libfreeimage-dev.
Unpacking libfreeimage-dev (from .../libfreeimage-dev_3.10.0-1_amd64.deb) ...
Setting up freeglut3 (2.4.0-6.1ubuntu1) ...

Setting up mesa-common-dev (7.6.0-1ubuntu4) ...
Setting up libgl1-mesa-dev (7.6.0-1ubuntu4) ...
Setting up xlibmesa-gl-dev (1:7.4+3ubuntu10) ...
Setting up libglu1-mesa-dev (7.6.0-1ubuntu4) ...
Setting up freeglut3-dev (2.4.0-6.1ubuntu1) ...
Setting up libglew1.5 (1.5.1-4ubuntu1) ...

Setting up libglew1.5-dev (1.5.1-4ubuntu1) ...
Setting up libfreeimage3 (3.10.0-1) ...

Setting up libfreeimage-dev (3.10.0-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Writing extended state information...

====================================
Downloading Files: lightsmark
Estimated Download Size: 33.15 MB
====================================



Downloading File: Lightsmark2008.2.0.tar.bz2

--2010-01-06 23:24:46--  http://www.dee.cz/lightsmark/Lightsmark2008.2.0.tar.bz2
Resolving www.dee.cz... 93.185.104.14
Connecting to www.dee.cz|93.185.104.14|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 34768173 (33M) [application/x-bzip2]
Saving to: `Lightsmark2008.2.0.tar.bz2.pts'

100%[======================================>] 34,768,173   159K/s   in 4m 7s   

2010-01-06 23:28:57 (138 KB/s) - `Lightsmark2008.2.0.tar.bz2.pts' saved [34768173/34768173]


====================================
Installing Test: lightsmark
Estimated Install Size: 54 MB
====================================


====================================
Test Configuration: Lightsmark
====================================


Resolution:

1: 800 x 600
2: 1024 x 768
3: 1280 x 960
4: 1280 x 1024
5: Test All Options

Enter Your Choice: 5

Would you like to save these test results (Y/n)? Y
Enter a name to save these results: Lightsmark test 1
Enter a unique name for this test run: trial

###########################################
If you wish, enter a new description below.
Press ENTER to proceed without changes.
###########################################

Current Description: This test calculates the average frame-rate within the Lightsmark 2008. Lightsmark is an OpenGL real-time global illumination and penumbra shadow benchmark.

New Description: 


```
[http://global.phoronix-test-suite.com/index.php?k=profile&u=jeffery-24211-25158-22152](http://global.phoronix-test-suite.com/index.php?k=profile&u=jeffery-24211-25158-22152)

---

### Post by Aikimox on 2010-01-06
I think you should be hitting more than that...Did you compare your tests to similar ones on phoronix ?
Anyway, glad it's working. I think if you use KDE instead of Gnome you might be able to use the graphical interface of phoronix rather than text.

---

### Post by Fatfool on 2010-01-07
> **Aikimox said:**
> I think you should be hitting more than that...Did you compare your tests to similar ones on phoronix ?
Anyway, glad it's working. I think if you use KDE instead of Gnome you might be able to use the graphical interface of phoronix rather than text.
Dang. well, it never seemed to be running at a good frame rate. It just kept stuttering even when the FPS counter showed 30+ FPS. I had google chrome up and running though. I wonder if that had a negative effect.

and it seems gnome will work fine... 

[IMG]http://www.phoronix-test-suite.com/screenshots/pts-bardu-1.png[/IMG]

And now i'm a little afraid to reactivate the benchmark..... the suck *** PSU in my case heated up till it was unbearable to the touch. Perhaps I'll do more extensive tests once I get it replaced.
do you have a link i could use to test on your config as well? 

By the way, i can't seem to find the results. Where have they gone?

---

