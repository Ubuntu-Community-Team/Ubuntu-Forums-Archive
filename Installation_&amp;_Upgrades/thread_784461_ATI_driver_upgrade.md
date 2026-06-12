---
title: "ATI driver upgrade"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by TinSoldier on 2008-05-06
OK iv got Ubuntu 8.04 LTS installed, iv also installed "WINE".

I'm trying to get the 3drad.com environment 3d program to run.

It will load and seems to run but im getting a black screen where there should be a 3d interactive display showing.

I'm assuming this probably means my ATI x600 graphics driver needs updating..

I downloaded the Linux driver, but according to the ATI web site i need 5 or 6 other programs installed just to install the new drivers, it has a ".run" extension.

Problem is iv only just recently found out that most things need to be done in a terminal window, not to mention i didn't even know what to do with a .RUN extension in the first place.

But the ATI web site says i should uninstall my old driver first, i "disabled" it ( i assume thats enough ? ).

Then they expect me to know how to check for these other 5 or 6 programs being installed....

Im lost here on how to do this....

Any help greatly appreciated....

---

### Post by Pumalite on 2008-05-06
Check this:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by TinSoldier on 2008-05-07
Ok i used Pumalite's suggestion and have updated my ATI card.

Iv now got a 3d window display buuuut, the graphics are messed up and extremely choppy kinda like running at 5 FPS, i believe this is probably due to the 3drad program and being designed specifically for windows...

Don't know if its fixable or not, but ill keep checking into this...

The included screen cap shows the sky box messed up and the on-screen clickable editing icons messed up to.....

Ill edit and attach a windows screen cap of the same screen for comparisons but i have to reboot in to XP first :(  .

---

### Post by pro003 on 2008-05-07
Download the ATI driver installer: [ati-driver-installer-8-4-x86.x86_64.run]("http://ati.amd.com/support/driver.html") (this installer is for 32bit and 64bit systems)

Change to the directory you downloaded the file. Make sure that you have the universe and multiverse repositories enabled in /etc/apt/sources.list before doing these steps.

There is a detailed manual with screenshots at Ubuntu Wiki.

By default, Ubuntu did not enable the Universe and Multiverse repositories, but now in Gutsy, both Universe and Multiverse are activated by default.

Install necessary tools:

```
sudo apt-get update
```
```
sudo apt-get install build-essential fakeroot dh-make debhelper debconf libstdc++5 dkms linux-headers-$(uname -r)
```

Uninstall previous fglrx: Using Synaptic, completely remove any packages containing "fglrx" in their name.

If using 64bit make sure to collect package "ia32-libs" before you continue!

Create .deb packages:

```
sudo sh ati-driver-installer-8-4-x86.x86_64.run --buildpkg Ubuntu/gutsy
```

note: if this step fails with a signal being caught, and you are running the script on an NFS-mounted directory, copy it to a local partition, and it will work. The same error may result from insufficient disk space.

As an alternative, you can just use

```
sudo sh ./ati-driver-installer-8-4-x86.x86_64.run --buildpkg Ubuntu --autopkg
```

which will download all the needed packages by itself and also automatically detects the Ubuntu version used.

If this step fails on amd64/x86_64 with a No such file or directory message about missing files in X11R6/lib, follow these instructions and come back here. Also check that your download path does not contain spaces.

Blacklist old fglrx module from linux-restricted-modules:

As Ubuntu Gutsy's linux-restricted-modules package includes the fglrx module from an old driver version (8.37.6), we have to blacklist this module to make sure the new kernel module which is needed by the new driver will be used instead.

Ubuntu/Gnome users type in:

```
gksu gedit /etc/default/linux-restricted-modules-common
```

Add "fglrx" to the line "DISABLED_MODULES"
File: /etc/default/linux-restricted-modules-common

DISABLED_MODULES="fglrx"

Please note that after the modification above, the "Restricted Driver Manager" will signal "ATI accelerated graphics driver" not enabled (unticked). This is perfectly correct. At the end of the installation procedure it will signal in Status: "in use" (green light), but NOT enabled. It simply means that the fglrx module contained in the linux-restricted-modules package is not enabled, but another fglrx module (8.4) is in use.

You may also need to edit the file (if it exists):

```
gksu gedit /etc/modprobe.d/blacklist-restricted
```

Put a # in front of the line "blacklist fglrx", if it is present. Otherwise, the kernel module will not load automatically, and you will not get 3D acceleration.

Remove any old fglrx debs from /usr/src/:

```
sudo rm /usr/src/fglrx-kernel*.deb
```

Install .deb packages:

```
sudo dpkg -i xorg-driver-fglrx_8.476-0*.deb fglrx-kernel-source_8.476-0*.deb fglrx-amdcccle_8.476-0*.deb
```

Additional 64-bit instructions

If you have a 64 bit install, the above dpkg command will likely complain that "Errors were encountered while processing: fglrx-amdcccle". This is because of a dependency of the amdccle package on 32 bit libraries. If you receive this error, issue the following command after the above dpkg command, which will force the installation of all of the 32 bit dependencies, and then the amdccle package:

```
sudo apt-get install -f
```

Catalyst 8.3 on 64-bit systems requires the --force-overwrite command in the above dpkg command:

```
sudo dpkg -i --force-overwrite xorg-driver-fglrx_8.476-0*.deb fglrx-kernel-source_8.476-0*.deb fglrx-amdcccle_8.476-0*.deb
```

[edit] Troubleshooting Installation Errors

Kernel -rt users

If you are running the -rt kernel, you will fail to compile the kernel module with "FATAL: modpost: GPL-incompatible module fglrx.ko uses GPL-only symbol '__rcu_read_lock'". Follow the instructions on 64bitstudio.com for a workaround.


Missing kernel sources

Error! Your kernel source for kernel 2.6.22-14-386 cannot be found at
/lib/modules/2.6.22-14-386/build or /lib/modules/2.6.22-14-386/source.

You must install the specific headers package for your kernel:

```
$ uname -r
```
```
$ sudo aptitude install linux-headers-2.6.22-14-386
```

Where "2.6.22-14" is the version reported by uname.


Bad file descriptor

If you get a 'Bad file descriptor' message concerning the xorg.conf file try switching user to root and repeating the same command without sudo. This might be valid for the following commands too. (Ubuntu Gutsy installs with no password set for root by default. You can set a password for the root by typing 'sudo passwd root' first.)
[edit] Configure the Driver

    * NOTE THIS WILL ERASE SETTINGS IN /etc/X11/xorg.conf you should be sure there is a backup.
    * Note Method 2 Users: Before you carry out this step you must reboot your machine. Or else the fglrx driver will not be in use on xorg.conf and using the aticonfig options will cause a memory dump and not intialise the Driver properly.
    * Note: An alternative to the aticonfig --initial command is to edit /etc/X11/xorg.conf and replace the string "ati" with "fglrx" in the "Device" section. This way you won't lose your old "Screen" and "Monitor" settings. Afterwards you can use aticonfig for setting overlay etc. Another alternative is aticonfig --initial --force if you encounter issues with the first command. 

```
sudo aticonfig --initial
```

Then:

```
sudo aticonfig --overlay-type=Xv
```

    * Note: Alternative in the overlay-type to "Xv" can be "opengl" or "disable" if the TV-out makes problems in videos. 

for more details check [HERE]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.4_Driver_Manually")

---

### Post by TinSoldier on 2008-05-08
Ok , everything seamed to go fine, only one thing happened that wasnt covered by the install instructions, heres the text output...

Configuration file `/etc/xdg/compiz/compiz-manager'
 ==> Deleted (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : background this process to examine the situation
 The default action is to keep your current version.
*** compiz-manager (Y/I/N/O/D/Z) [default=N] ? Y
Installing new version of config file /etc/xdg/compiz/compiz-manager ...
Installing new version of config file /etc/ati/signature ...
 * Starting atieventsd                                                                                                                                                           /usr/sbin/atieventsd: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory                                                                                                                                                                          [fail]

Setting up fglrx-kernel-source (2:8.476-0ubuntu1) ...
Adding Module to DKMS build system
Doing initial module build
Installing initial module
Done.

Setting up fglrx-amdcccle (2:8.476-0ubuntu1) ...

tinsoldier@tinsoldier-laptop:~/Downloads$ 


I selected Yes...

I rebooted but now the 3drad application wont even run, it's loading screen shows up but immediately closes.

On a good note, im not getting any error box's or pop-up warnings if UBUNTU does that kind of thing....

---

### Post by Bablefish on 2008-05-08
Let me give you a heads up on that driver pro003 reccomened. It's 64 bit only and I got that straight from ATI after I called them directly. When I had problems installing the exact same driver and crashed my video driver. Let me give TinSoldier some advice if you can reinstall your OS, and start from scratch believe me it's less of a headache. I still wish I kept the default Mesa 3D driver.

---

### Post by TinSoldier on 2008-05-08
Really, you dont say.

Iv already considered doing that because this is a fairly fresh install and getting back to this point wont be hard.

My only concern here is that i don't seem to be getting 3d acceleration, i was originally able to run the app but a a crawl for FPS  ( more like FPM (M-Minutes :( ).

So how do i go about fixing this if i go for a fresh install ?, dont forget im a total newbie with LINUX/UBUNTU and its inner workings... ?.

---

### Post by Pumalite on 2008-05-08
You can install on top of the old one.

---

### Post by TinSoldier on 2008-05-08
Interesting, i went to the ATI web site and only found the 64 Bit linux drivers, haveing to register etc,etc just to ask tech support when to find the 32 Bit drivers was to much.

So i pulled a fast one :)  , i copied the 64 Bit download link 

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-4-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-4-x86.x86_64.run)

and substituted 64 with 32 and guess what i was given the 32 Bit link driver link to download ....

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-4-x86.x86_32.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-4-x86.x86_32.run) 

So apparently the web site has an error or omission or maybe removed from the web page intentionally ... cant say, soooo, im going to give gthe new 32 bit driver a try....

---

### Post by Pumalite on 2008-05-08
Good luck.

---

### Post by Bablefish on 2008-05-08
Same here...by the way your link is down

as an Alternative what about this [http://xoomer.alice.it/flavio.stanchina/debian/fglrx-installer.html](http://xoomer.alice.it/flavio.stanchina/debian/fglrx-installer.html)

---

### Post by pro003 on 2008-05-11
> Download the ATI driver installer: ati-driver-installer-8-4-x86.x86_64.run (**this installer is for 32bit and 64bit systems**)

can't you see that first line of my post? or haven't you noticed that it's the very same installer when you go up for x86 and x86_64 link?

and tinsoldier! did you first uninstall from synaptic everything that contains word "fglrx"?


cause, kinda, i've been there...:)

---

### Post by ticklj on 2008-05-11
Actually my ATI installation went well. I found some instructions
maybe 3 lines and easy for a linux newbee. However (there is always one of those) the screen was too far to the right. I installed the control panal for ATI and that showed the refresh rate at 70. I set it for 60. The screen after login is correctly positioned.
But before login completes when the Gnome manager (I think?) is
in control the screen is still too far to the right. This to my thinking means that there is a 70 somewhere else the is being used
in the early stages. Can someone tell me where this is or how/where
I can find it and fix it.

---

### Post by pro003 on 2008-05-11
try to take a closer look at your xorg.conf

otherwise place it here so we can take a look and see what can be suggested to fix this problem....

type in terminal:

```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by TinSoldier on 2008-05-12
Sad news, the 32bit driver i dowmloaded turned out to be damaged in some way, it's ok 1k in size compared to the 64bit pakage at 51M.

Apparently the file i liked to with my "quick one" wasn't the actual file on their site, i dont think i did anything wrong here cause all i did was substitute "64" with "32" and assumed i was getting the 32bit driver pakage.... :( 

So, anyway, im in the process of now finding that 32bit driver version, and will report back if and when and what the end results are if im successful....  

PS Anyone happen to have that file around and willing to share or have a link ? ..

"ati-driver-installer-8-4-x86.x86_32.run"

Back to the ati web site i go...

---

### Post by TinSoldier on 2008-05-12
Yes i did everything you said as your original post showed, iv also reinstalled ubuntu and havent changed anything with the default setup.

I checked for flg*  files in the pakage manager and non of them are installed aparently cause im not given and "un-install" option.

Im hesitant to re-install the driver process as you outlined before due to it not working in the first place...., what options are available to "undo" this driver install if i go ahead and re-try it ? ... other than re-installing ubuntu ? .

PS Also dont forget, im still a newbie..... :) . 

One other thing.. what is the proper install order for "wine"?, should i first install the video drivers before "wine" or does it matter ?.

Also Bablefish said he was told by ATI (phonecall) that that driver was 64bit only, so...... it didnt work for me the first time so im inclinded to believe Bablefish over you ( not personally questioning your knowledge but the end result say's Bablefish is correct.....).
 

> **pro003 said:**
> can't you see that first line of my post? or haven't you noticed that it's the very same installer when you go up for x86 and x86_64 link?

and tinsoldier! did you first uninstall from synaptic everything that contains word "fglrx"?


cause, kinda, i've been there...:)

---

### Post by pro003 on 2008-05-13
can't you READ? I wrote FGLRX and you have searched FLG* (see your last post)... 

By the way, go for BableFish!   

I am trying to help you and you can't even read what I wrote?:lolflag:

---

### Post by TinSoldier on 2008-05-13
ATI/AMD reply from my "ticket" was simply -

> 
We have responded to your issue.
Solution:	Dear customer,

Thank you for contacting AMD.

Since there are many distributions and versions of Linux OS, there's no support available by phone or by email for this operating system.

For more information about Linux driver support, please access [http://ati.amd.com/products/catalyst/linux.html](http://ati.amd.com/products/catalyst/linux.html)

For more information about technical support for Linux OS, please access [http://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&questionID=28027](http://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&questionID=28027)

Regards,

Pier Bottero,
AMD Technical Support


No help at all...

---

### Post by TinSoldier on 2008-05-13
On this question what should i do ?

 > Ok , everything seamed to go fine, only one thing happened that wasnt covered by the install instructions, heres the text output...

Configuration file `/etc/xdg/compiz/compiz-manager'
==> Deleted (by you or by a script) since installation.
==> Package distributor has shipped an updated version.
What would you like to do about it ? Your options are:
Y or I : install the package maintainer's version
N or O : keep your currently-installed version
D : show the differences between the versions
Z : background this process to examine the situation
The default action is to keep your current version.
*** compiz-manager (Y/I/N/O/D/Z) [default=N] ? Y
Installing new version of config file /etc/xdg/compiz/compiz-manager ...
Installing new version of config file /etc/ati/signature ...
* Starting atieventsd /usr/sbin/atieventsd: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory [fail]

Setting up fglrx-kernel-source (2:8.476-0ubuntu1) ...
Adding Module to DKMS build system
Doing initial module build
Installing initial module
Done.

Setting up fglrx-amdcccle (2:8.476-0ubuntu1) ...

tinsoldier@tinsoldier-laptop:~/Downloads$


I selected Yes...

---

### Post by jimbolaya on 2008-05-13
I couldn't get this to work for me:

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-4-x86.x86_32.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-4-x86.x86_32.run) 

I kept getting file not found.

---

### Post by TinSoldier on 2008-05-13
Yes, thats what i said a couple of messages back.... what seems to have been a 32bit driver link some time in the past has been removed from the ATI website...

 i tried to install the 32/64 bit driver again with the same results, i don't blame UBUNTU for the problems cause im trying to run a windows app under "wine" so, it appears that HP & ATI and it's propriitary drivers has lost a customer ( ME ) over this.

The next notebook i buy will not be an HP, im leaning towards a MAC... and ill be doing more research on MACS and LINUX beforehand too.

---

### Post by TinSoldier on 2008-05-14
Ok, heres a really stupid question.... but first, im giving this process a try found here

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

On this page it says to use "VIM xorg......" to open and edit this file.

I did that, entered my password, edited the settings, but .....

How do you save the new edited file in VIM ? , i closed the tab, iv clicked the "X" and it never gets updated...

I went to the directory and tried to edit it directly there using gedit that worked, but when i try to save it, it says i dont have permission to do that ? .  I did save a copy of the edited version into my documents folder, so all i need is "how to" to over write the original ? .

What am i missing here ?.

PS this page really should be updated also, cause in one place it says to enter the name you gave your monitor earlier, but what it really wants is the "identifier", i had to go back and re-read the text to figure out "identifier" = Name in this situation... :confused:

---

### Post by Pumalite on 2008-05-14
vi:
entry: i
command: 'Esc'
Save and exit: :wq
Exit without saving: :q!

---

### Post by ticklj on 2008-05-16
Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
Type  :quit<EnterEndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection
this is the entire display config. Not the X I used to know
and love. The refrish rates and other stuff is obviously some
where else in some ati catalyst place any ideas??

---

### Post by TinSoldier on 2008-05-19
Thanks for the reply, but this didn't help me....

I instead found it easier to give root a password and just overwrite the file that way... 



> **Pumalite said:**
> vi:
entry: i
command: 'Esc'
Save and exit: :wq
Exit without saving: :q!

---

### Post by TinSoldier on 2008-05-20
all in all, it seems now iv somehow got the 3drad program working under wine.

Its not perfect.... the resolution is some how set to a very low setting and the running app dosent show the 3d-rendering window properly either.

But 3drad dose seem to be getting 3d acceleration though.

Also the 3drad app dosent seem to be getting keyboard input from the consol either that it needs...

Im sort of sitting on the fence over this....windows or ubuntu or mac.....

---

### Post by Pumalite on 2008-05-20
> **TinSoldier said:**
> Thanks for the reply, but this didn't help me....

I instead found it easier to give root a password and just overwrite the file that way...

These commands work for that editor anyway for anyone that doesn't know how to use it.

---

