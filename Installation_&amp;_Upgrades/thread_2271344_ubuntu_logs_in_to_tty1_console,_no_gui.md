---
title: "ubuntu logs in to tty1 console, no gui"
date: 2015-03-29
forum: Installation &amp; Upgrades
---

### Post by gasior.tt on 2015-03-29
Problem started after update installation. Ubuntu logs in to tty1 console and stops there.

This is the output when I try to run ubuntu in graphics safe mode:
[IMG]http://oi57.tinypic.com/29prynq.jpg[/IMG]

When I type this: 
```
sudo lshw -C display
```
and
```
lspci -nn | egrep VGA
```
I get this:

[IMG]http://s23.postimg.org/u38sw3qzf/20150322_132827.jpg[/IMG]

So I tried installing proper nvidia driver by those commands:
```

sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
ubuntu-drivers devices | grep recommended
```

I received this:

```
driver   : nvidia-349 - third-party free recommended

```

 So I did this:

  ```
sudo apt-get install nvidia-349

```

And it doesn't work. It still logs mi in to tty1 console. 

Dont' know how to repair my PC :(

---

### Post by Bashing-om on 2015-03-29
gasior.tt; Hello;

Most likely that the update broke the proprietary graphics driver, - proprietary, not under ubunu's control.
When a driver is to be (RE-)installed, one must 1st remove the old driver; I do not see where this step was done.
Try this:
```

sudo apt-get purge nvidia*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf-old
sudo apt-get update
sudo apt-get install nvidia-349

```

New hardware, and as of 14.04 release the MOTU have not verified/accepted the later drivers into the software repository. Thus the need to resort to the PPA to get a driver for this new hardware.

[INDENT][INDENT][INDENT]maybe YES
[/INDENT][/INDENT][/INDENT]

---

### Post by gasior.tt on 2015-03-29
I don't have /etc/X11/xorg.conf file.

I purged and installed nvidia driver again but ubuntu still logs in to tty1 console

---

### Post by Bashing-om on 2015-03-29
gasior.tt; Humm ...

I find it odd that there is no xorg.conf file. I know that as of version 346 that config file was still used.
Let's see if we can generate that config file:
```

sudo nvidia-xconfig

```
reboot to see the effect.

[INDENT][INDENT]what I think
[/INDENT][/INDENT]

---

### Post by gasior.tt on 2015-03-29
After that command I have:
[IMG]http://oi62.tinypic.com/2939aj6.jpg[/IMG]

after reboot same problem

---

### Post by Bashing-om on 2015-03-29
gasior.tt; Well.

A bit more info. Doing homework on it now.
I be back soonest I have something to add to the thread.

[INDENT][INDENT]'buntu, a fast moving target
[/INDENT][/INDENT]

---

### Post by steeldriver on 2015-03-29
I am surprised to see XF86Config - what version of Ubuntu are you running, and where did you get the nvidia-xconfig program from? 

I didn't think the XFree86 project was still active - it should have all been forked over to xorg, no?

---

### Post by gasior.tt on 2015-03-29
ubuntu 14.04.2
I dont really know details about nvidia installed software on my PC

---

### Post by Bashing-om on 2015-03-29
@ steeldriver; Yeah ! Me too ! I am in my learning mode once more ( OH joy ).

@gasior.tt; Well, well ..

I do not know that using XF86Config is intrinsically any different than xorg.config, but I have never ran across it before.
Let's see what we can learn before 'looking' at the file.
What results if you boot up in "recovery mode" ?

At the grub boot menu -> advanced options, select the recovery console.
Can you now boot to the GUI , degraded graphics is acceptable at this point .
If you are able to boot to the GUI we can be fairly certain it is a graphics driver issue.
Then perhaps we can tweak on the config file to set an appropriate video mode (??)

else, well what errors do we get from the system when we start X from the terminal ... that be the next thing to look at.

[INDENT][INDENT]which way did he go, George
[/INDENT][/INDENT]

---

### Post by gasior.tt on 2015-03-29
do you mean graphics failsafe mode?

---

### Post by gasior.tt on 2015-03-29
running in recovery mode graphics failsafeX outputs this:
[IMG]http://s15.postimg.org/ihv8gaauz/20150330_002054.jpg[/IMG]

---

### Post by gasior.tt on 2015-03-29
when i run recovery mode graphics failsafeX i get this:
[IMG]http://s15.postimg.org/ihv8gaauz/20150330_002054.jpg[/IMG]

---

### Post by Bashing-om on 2015-03-29
gasior.tt; Humm ... curious and curiousior 

What in the world are we working with ?
Post back the outputs of terminal commands:
```

echo $DESKTOP_SESSION " " $XDG_CURRENT_DESKTOP
ls /usr/share/xsession
ls -al /usr/bin/X

```
To see.

I had not expected to see "GDM" But we can see that xinit is trying to start ' /etc/X11/xorg.conf ' rather than the installed 'XF86Config' .
Everybody got their learning hats on ?

[INDENT][INDENT]what to do, oh what to do
[/INDENT][/INDENT]

---

### Post by steeldriver on 2015-03-29
What does 

```

dpkg -S $(which X)

```

say? what about

```

dpkg -l | grep xserver

```

---

### Post by gasior.tt on 2015-03-29
[IMG]http://s16.postimg.org/fuxkjx9mt/20150330_010628.jpg[/IMG]

[IMG]http://s1.postimg.org/5jc7od4vz/20150330_011136.jpg[/IMG]

[IMG]http://s1.postimg.org/tblizw6wv/20150330_011121.jpg[/IMG]

---

### Post by steeldriver on 2015-03-29
Well I'm guessing here as I have never encountered this situation but I don't see any harm in starting by re-installing the base xserver-xorg package

```

sudo apt-get install --reinstall xserver-xorg

```

After that. check again to see if you have a /usr/bin/X executable

```

which X

```

---

### Post by Bashing-om on 2015-03-29
gasior.tt; Yuk;

Little of that is as I anticipate:
my results ( ubuntu 14.04 xfce ):
```

sysop@1404mini:~$ echo $DESKTOP_SESSION " " $XDG_CURRENT_DESKTOP
xfce   XFCE
sysop@1404mini:~

sysop@1404mini:~$ ls /usr/share/xsessions
xfce.desktop

sysop@1404mini:~$ ls -al /usr/bin/X
-rwsr-sr-x 1 root root 10192 Dec  9 20:30 /usr/bin/X
sysop@1404mini:~$

sysop@1404mini:~$ dpkg -S $(which X)
xserver-xorg: /usr/bin/X
sysop@1404mini:~$

sysop@1404mini:~$ dpkg -l | grep xserver
ii  x11-xserver-utils                     7.7+2ubuntu1                         amd64        X server utilities
ii  xserver-common                        2:1.15.1-0ubuntu2.7                  all          common files used by various X servers
ii  xserver-xorg                          1:7.7+1ubuntu8.1                     amd64        X.Org X server
ii  xserver-xorg-core                     2:1.15.1-0ubuntu2.7                  amd64        Xorg X server - core server
ii  xserver-xorg-input-all                1:7.7+1ubuntu8.1                     amd64        X.Org X server -- input driver metapackage
ii  xserver-xorg-input-evdev              1:2.8.2-1ubuntu2                     amd64        X.Org X server -- evdev input driver
ii  xserver-xorg-input-mouse              1:1.9.0-1build1                      amd64        X.Org X server -- mouse input driver
ii  xserver-xorg-input-synaptics          1.7.4-0ubuntu1                       amd64        Synaptics TouchPad driver for X.Org server
ii  xserver-xorg-input-vmmouse            1:13.0.0-1build1                     amd64        X.Org X server -- VMMouse input driver to use with VMWare
ii  xserver-xorg-input-wacom              1:0.23.0-0ubuntu2                    amd64        X.Org X server -- Wacom input driver
ii  xserver-xorg-video-all                1:7.7+1ubuntu8.1                     amd64        X.Org X server -- output driver metapackage
ii  xserver-xorg-video-ati                1:7.3.0-1ubuntu3.1                   amd64        X.Org X server -- AMD/ATI display driver wrapper
ii  xserver-xorg-video-cirrus             1:1.5.2-1build1                      amd64        X.Org X server -- Cirrus display driver
ii  xserver-xorg-video-fbdev              1:0.4.4-1build1                      amd64        X.Org X server -- fbdev display driver
ii  xserver-xorg-video-glamoregl          0.6.0-0ubuntu4                       amd64        X.Org X server -- graphics acceleration module based on OpenGL
ii  xserver-xorg-video-intel              2:2.99.910-0ubuntu1.4                amd64        X.Org X server -- Intel i8xx, i9xx display driver
ii  xserver-xorg-video-mach64             6.9.4-1build1                        amd64        X.Org X server -- ATI Mach64 display driver
ii  xserver-xorg-video-mga                1:1.6.3-1build1                      amd64        X.Org X server -- MGA display driver
ii  xserver-xorg-video-modesetting        0.8.1-1build1                        amd64        X.Org X server -- Generic modesetting driver
ii  xserver-xorg-video-neomagic           1:1.2.8-1build1                      amd64        X.Org X server -- Neomagic display driver
ii  xserver-xorg-video-nouveau            1:1.0.10-1ubuntu2                    amd64        X.Org X server -- Nouveau display driver
ii  xserver-xorg-video-openchrome         1:0.3.3-1build1                      amd64        X.Org X server -- VIA display driver
ii  xserver-xorg-video-qxl                0.1.1-0ubuntu3                       amd64        X.Org X server -- QXL display driver
ii  xserver-xorg-video-r128               6.9.2-1build1                        amd64        X.Org X server -- ATI r128 display driver
ii  xserver-xorg-video-radeon             1:7.3.0-1ubuntu3.1                   amd64        X.Org X server -- AMD/ATI Radeon display driver
ii  xserver-xorg-video-s3                 1:0.6.5-0ubuntu4                     amd64        X.Org X server -- legacy S3 display driver
ii  xserver-xorg-video-savage             1:2.3.7-2ubuntu2                     amd64        X.Org X server -- Savage display driver
ii  xserver-xorg-video-siliconmotion      1:1.7.7-2build1                      amd64        X.Org X server -- SiliconMotion display driver
ii  xserver-xorg-video-sis                1:0.10.7-0ubuntu6                    amd64        X.Org X server -- SiS display driver
ii  xserver-xorg-video-sisusb             1:0.9.6-2build1
md64        X.Org X server -- SiS USB display driver
ii  xserver-xorg-video-tdfx               1:1.4.5-1build1                      amd64        X.Org X server -- tdfx display driver
ii  xserver-xorg-video-trident            1:1.3.6-0ubuntu5                     amd64        X.Org X server -- Trident display driver
ii  xserver-xorg-video-vesa               1:2.3.3-1build1                      amd64        X.Org X server -- VESA display driver
ii  xserver-xorg-video-vmware             1:13.0.2-2ubuntu1                    amd64        X.Org X server -- VMware display driver
sysop@1404mini:~$ 

```

Observations:
1) You do not appear to have X installed (/usr/bin/X). I can not conceive of a way to start an Xsession with out X !
2) No Desktop is established , not unexpected as X is not started
3) Nvidia driver ? Where ? The trident driver ... hummm ..
4) Per [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us) ; we want to install the 346 driver !!

---------------------
see what results when " sudo apt-get install --reinstall xserver-xorg " is executed .

Perhaps then ->

I have to ask, is it conceivable to take the nuclear approach, do a clean fresh install of 14.04; boot with "nomeset" and install the 346 proprietary driver ? See then if we do have a fully functional system ?

---

### Post by gasior.tt on 2015-03-29
[IMG]http://s21.postimg.org/okaptl29z/20150330_014651.jpg[/IMG]

---

### Post by Bashing-om on 2015-03-29
gasior.tt; steeldriver ... humm ..


Victim of this bug ?
[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1424466](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1424466)
such that we want to (re-)install with release 14.04.1 and then upgrade ???

Might try :
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

``` to see if there are held packages .

Just keeps getting deeper

---

### Post by gasior.tt on 2015-03-29
Yep, I ll probalby go for fresh install.

I plan to use CUDA-toolkit so I will install some nvidia dirvers straight from nvidia. Now, should I block some linux drivers stuff in some conf files? I know from experiance that if I don't blacklist some linux stuff then every dist-upgrade I will run issues and problems and challenges.

---

### Post by Bashing-om on 2015-03-29
gasior.tt; Well ..... 

As much as I would like to KNOW what is taking place ... pending steeldriver's concurrence, I do think the expedient thing to do is start afresh.
And no I do not advocate a driver install from Nvidia site. Each kernel update one would have to re-install the nvidia OEM driver. The 346 driver -per Nvidia - from the PPA should be just fine, then the package manager has a handle on it.
But CUDA does shed a different light on the subject. Have you seen:
[http://askubuntu.com/questions/451672/installing-and-testing-cuda-in-ubuntu-14-04](http://askubuntu.com/questions/451672/installing-and-testing-cuda-in-ubuntu-14-04)
There is a PPA to obtain CUDA .

Installing the Nvidia proprietary driver is supposed to take care of any needed blacklisting. In my limited experience I have not seen the need to intervene manually .

Cuda is also available in the software repository:
```

apt-cache show nvidia-cuda-toolkit

``` It is but a thought.

As you have to out-source the graphics driver, may as well out-source CUDA also.

Start all over;
[INDENT][INDENT][INDENT]If I were in this situation,
[INDENT][INDENT][INDENT]I do think I would (RE-)install
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by gasior.tt on 2015-03-30
I did fresh 14.04 ubuntu install. I installed CUDA toolkit by runing .run file form nvidia(I skipped the driver installation because I didi it manually -346 form xorg edgers ppa).

this command:

```
ls -A /etc/X11
```

outputs this:

```
app-defaults             rgb.txt  Xreset      Xsession.d
cursors                  X        Xreset.d    Xsession.options
default-display-manager  xinit    Xresources  xsm
fonts                    xkb      Xsession    Xwrapper.config
```

---

### Post by Bashing-om on 2015-03-30
gasior.tt; Good Morning ....

That output from 'X11" list looks good to me .

Is all looking good now after the fresh re-work ?

[INDENT][INDENT]when in doubt -> (RE-)install
[/INDENT][/INDENT]

---

### Post by gasior.tt on 2015-03-30
yep, its working. However few (2 or 3) crash error prompts at begenning. I just cancel them :P

---

### Post by Bashing-om on 2015-03-30
gasior.tt; Great .

How 'bout we open a new thread on this new situation; and close this one ...

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Solved by nuclear option .

[INDENT][INDENT]There is that
[/INDENT][/INDENT]

---

### Post by gasior.tt on 2015-03-30
So in your opinion, next dist-soft-upgrade should not cause any error?

---

### Post by Bashing-om on 2015-03-30
gasior.tt; Well, like this;

Until "you" as the administrator of your system change those access rights, they are cast in concrete.
( have you started now a 'useful_CLI_commands" file yet )?

see:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://mywiki.wooledge.org/Permissions](http://mywiki.wooledge.org/Permissions)

These access rights are the reason that linux (ubuntu) is so strong .

[INDENT][INDENT]It's 'buntu
[INDENT][INDENT][INDENT]have it your way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

