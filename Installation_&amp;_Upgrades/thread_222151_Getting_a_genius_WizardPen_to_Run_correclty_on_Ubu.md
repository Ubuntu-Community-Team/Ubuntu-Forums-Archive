---
title: "Getting a genius WizardPen to Run correclty on Ubuntu (Dapper)"
date: 2006-07-24
forum: Installation &amp; Upgrades
---

### Post by Jontom on 2006-07-24
Right so it took me a while but I've finaly got my genius WizardPen working properly, i've seen a couple of people having trouble with this on the forums so here are the basic steps I took to get it working (Stressing that I am not an expert, this is just an accumulation of info from the web and it may mess up your system irrevocably:-) I use nano as an editor as its simple and where I say sudo you will have to enter your password.

1. 	Download the driver from:
          [http://www.stud.fit.vutbr.cz/~xhorak28/wizardpen-driver-0.5.0.tar.gz]("http://www.stud.fit.vutbr.cz/~xhorak28/wizardpen-driver-0.5.0.tar.gz")

Open a console and cd to the directory you downloaded the file to extract the driver package:
 
        tar -zxvf wizardpen-driver-0.5.0.tar.gz

cd to extracted folder wizardpen-driver-0.5.0

        cd wizardpen-driver-0.5.0
        
        then type:

	xmkmf

You may get an error saying that there is no file Server.tmpl if so type: 
        
        sudo ln -s /etc/X11/config/cf /usr/X11R6/lib/X11/config 
        
This creates a symlink to the folder where the Server.tmpl file is found on Ubuntu, then:
	
        xmkmf

	sudo make
	
        sudo make install

make install copies the file to the wrong directory for ubuntu so:

	sudo cp wizardpen_drv.o /usr/lib/xorg/modules/input/

2. Now you need to make a new udev rule to identify your wizardpen

For more information read the info at this link:
     [http://reactivated.net/writing_udev_rules.html]("http://reactivated.net/writing_udev_rules.html")
	
Basically what this means is to put an identifier in /dev that specifically points to your device so that X can find it upon starting.

Firstly run:

        udevinfo -a -p $(udevinfo -q path -n /dev/input/mouse1) 

[this should give you some information about your wizardpen. I used mouse1 in the above code assuming that you have a normal mouse attached as well and the wizardpen, if this does not give you information about your wizardpen then you should check the contents of /dev/input tho see whats there and run the above again substituting what you find from /dev/input]

	Here is some of my output for the above code

jontom@Grisly:~$ udevinfo -a -p $(udevinfo -q path -n /dev/input/mouse1)

udevinfo starts with the device the node belongs to and then walks up the
device chain, to print for every device found, all possibly useful attributes
in the udev key format.
Only attributes within one device section may be used together in one rule,
to match the device for which the node will be created.

device '/sys/class/input/input3/mouse1' has major:minor 13:33
  looking at class device '/sys/class/input/input3/mouse1':
    KERNEL=="mouse1"
    SUBSYSTEM=="input"
    SYSFS{dev}=="13:33"

follow the "device"-link to the physical device:
  looking at the device chain at '/sys/devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0':
    BUS=="usb"
    ID=="1-2:1.0"
    DRIVER=="usbhid"
    SYSFS{bAlternateSetting}==" 0"
    SYSFS{bInterfaceClass}=="03"
    SYSFS{bInterfaceNumber}=="00"
    SYSFS{bInterfaceProtocol}=="02"
    SYSFS{bInterfaceSubClass}=="01"
    SYSFS{bNumEndpoints}=="01"
    SYSFS{interface}=="Tablet WP5540U"
    SYSFS{modalias}=="usb:v5543p0004d0000dc00dsc00dp00ic03isc01ip02"

  looking at the device chain at '/sys/devices/pci0000:00/0000:00:1d.0/usb1/1-2':
    BUS=="usb"
    ID=="1-2"
    DRIVER=="usb"
    SYSFS{bConfigurationValue}=="1"
    SYSFS{bDeviceClass}=="00"
    SYSFS{bDeviceProtocol}=="00"
    SYSFS{bDeviceSubClass}=="00"
    SYSFS{bMaxPacketSize0}=="8"
    SYSFS{bMaxPower}=="100mA"
    SYSFS{bNumConfigurations}=="1"
    SYSFS{bNumInterfaces}==" 1"
    SYSFS{bcdDevice}=="0000"
    SYSFS{bmAttributes}=="a0"
    SYSFS{configuration}==""
    SYSFS{devnum}=="4"
    SYSFS{idProduct}=="0004"
    SYSFS{idVendor}=="5543"
    SYSFS{manufacturer}=="UC-LOGIC"
    SYSFS{maxchild}=="0"
    SYSFS{product}=="Tablet WP5540U"
    SYSFS{speed}=="1.5"
    SYSFS{version}==" 1.10"

Check your SYSFS{product} value: mine is "Tablet WP5540U"

Once you are sure that you have found the correct info for your wizardpen then run:

        sudo nano /etc/udev/rules.d/10-local.rules

Edit the new file (10-local.rules) with this information:

        BUS="usb", KERNEL="event*", SYSFS{product}="Tablet WP5540U",              
        NAME="input/%k", SYMLINK="Tablet"

Replacing the SYSFS{product} with your value

        Ctrl-X to exit and say yes to save changes

3. Now edit xorg.conf to load your device with the newly created symlink made by udev:

        sudo nano /etc/X11/xorg.conf

add this to your xorg.conf
      
        Section "InputDevice"
        Identifier "tablet"
        Driver "wizardpen"
        Option "Device" "/dev/Tablet"
        EndSection

and in the Section "ServerLayout"

        InputDevice "tablet" "AlwaysCore" 

(This is because you cannot have more than one CorePointer)

         Ctrl X and say yes to save changes

Now do this:

         sudo /etc/init.d/udev restart

This restarts udev and you should check the /dev directory to see if Tablet is present

         ls /dev

4. Right now comes the part where X may not start if you haven't done everything correctly (This happens when the module is loaded but the device isnt found - well for me anyway I got a screen half black and half white with and a glibc error):

         Restart the X-server

         Ctrl-alt-bksp

* You should be able to get into another console by trying ctrl-alt-f8 followed by ctrl-alt-f6 if X doesnt start, if all else fails ctrl-alt-del should work or simply reset and start in recovery mode :-( *

Assuming all goes well login and test your pen. For me it sort of worked as in the cursor was stuck to the bottom of the screen (i.e the panel) and was therefore fairly useless, fortunately this can be resolved by opening a console and changing to the wizardpen source directory

         cd wizardpen-driver-0.5.0 

         Change directory to the calibrate directory

         cd calibrate

         make

         you may get some errors but the prog should still compile

         sudo ./wizardpen-calibrate /dev/Tablet

Then follow the instructions putting the tip in diagonally opposite corners of the tablet.

The output can then be added to the information you added in xorg.conf

        sudo nano /etc/X11/xorg.conf

here is the output I got

Section "InputDevice"
Identifier "tablet"
Driver "wizardpen"
Option "Device" "/dev/Tablet"
Option          "TopX"          "2413"
Option          "TopY"          "5194"
Option          "BottomX"       "29783"
Option          "BottomY"       "30785"
Option          "MaxX"          "29783"
Option          "MaxY"          "30785"
EndSection

This defines the size of the tavblet and should correct the problem with the wizardpen

         ctrl-X and save changes

restart the x server

         ctrl-alt-bksp

Right, login again and check if everything is working.

You will probably find that the buttons on the pen are not mapped correctly.

To change this you need to make another udev rule defining your normal mouse specifically 

This is fairly easy to do but once again youd better check that the device is in /dev after you restart udev and you have edited your xorg.conf or X will probably fail to start:

Your normal mouse is probably found in mouse0 in /dev/input so try

        udevinfo -a -p $(udevinfo -q path -n /dev/input/mouse0)

Check the output

device '/sys/class/input/input1/mouse0' has major:minor 13:32
  looking at class device '/sys/class/input/input1/mouse0':
    KERNEL=="mouse0"
    SUBSYSTEM=="input"
    SYSFS{dev}=="13:32"

follow the "device"-link to the physical device:
  looking at the device chain at '/sys/devices/pci0000:00/0000:00:1d.1/usb2/2-2/2-2:1.1':
    BUS=="usb"
    ID=="2-2:1.1"
    DRIVER=="usbhid"
    SYSFS{bAlternateSetting}==" 0"
    SYSFS{bInterfaceClass}=="03"
    SYSFS{bInterfaceNumber}=="01"
    SYSFS{bInterfaceProtocol}=="02"
    SYSFS{bInterfaceSubClass}=="01"
    SYSFS{bNumEndpoints}=="01"
    SYSFS{modalias}=="usb:v046Ep5520d0090dc00dsc00dp00ic03isc01ip02"

you only really need the SYSFS{dev} identifier

sudo nano /etc/udev/rules.d/10-local.rules

and add this line to it replacing your SYSFS{dev} value

KERNEL="mouse*", SUBSYSTEM="input", SYSFS{dev}="13:32", NAME="input/%k", SYMLINK="usbmouse"

the SYMLINK value can be any name you want but give it something meaningful so you can look for it in /dev easily

          Ctrl-X and save changes

Now edit xorg.conf

          sudo nano /etc/X11/xorg.conf

all you have to do here is change the path to the device to point to the symlink created by udev

          option "Device" "/dev/usbmouse"

Ctrl-X and save changes

now restart udev and look for usbmouse (or whatever you called it) in /dev

          sudo /etc/init.d/udev restart

          ls /dev

If its there then:

          Ctrl-Alt-Bksp
          
Login again and the pen buttons should be correct.

Phew!

---

### Post by LTBookman on 2006-07-24
Thank you! I finally got my tablet working! But there's still a problem. My primary mouse starts sometimes as /dev/input/mouse0 and sometimes as /dev/input/mouse1, so I have to modify after every restart that value SYSFS{dev}="13:xx".

Any help with that? TIA.

---

### Post by Jontom on 2006-07-25
Great ! not sure why the mouse should change around

You should be able to get around this with udev, using a more specific parameter from the udevinfo like (SYSFS{idProduct}) should point to the right mouse, see the link on writing udev rules I gave.

Jontom

---

### Post by LTBookman on 2006-07-25
Thanks again, I used SYSFS{modalias} and it works perfectly now. :D

---

### Post by Jontom on 2006-07-28
Cool, glad to see you got it working so easily!

Jontom

---

### Post by daller on 2006-08-03
.

---

### Post by daller on 2006-08-06
.

---

### Post by Jontom on 2006-08-08
Hi Sorry I took so long to reply, I'm not at home at the moment and I dont have access to my dsl line. Anyway, this exact same thing happened to me, I had to move my box because we're building and I left most of the peripherals behind, so it couldnt find the device. I'm assuming that the fault lies with the driver (i.e. it can't deal with the device not being there once its loaded) so the only thing I can think of is to write some sort of script when you start X up that checks to see if the device is there and if not unloads the driver or even better stops the driver  being loaded.

I will have a look into it

---

### Post by daller on 2006-08-09
I've found a temporary solution, which I've added to my howto:

[https://wiki.ubuntu.com/TabletSetupWizardpen](https://wiki.ubuntu.com/TabletSetupWizardpen)

It makes X start without the black/white screen... But doesn't cover the hotplug issue... (If you disconnect it after starting X, X will freeze!)

Please let me know, if you have an easier solution!

---

### Post by Jontom on 2006-08-25
Seems like this suggestion from the drivers forum is a better solution:

One needs to comment out the lines:



if ((local) && (local->fd >= 0))

   xf86CloseSerial(local->fd);

if (local)

   xf86DeleteInput(local, 0);



around about line 634 in the wizardpen.c file.


I havent tried this yet but it looks promising

Jontom

---

### Post by prokoudine on 2006-09-02
Does anyone still have the tarball with the driver around? The download link above doesn't work anymore.

---

### Post by ShadowRage on 2006-09-03
To make things MUCH easier on you guys, I made a deb. however, it's 64 bit.

I dont have too many issues with plug and play, because I never unplug my tablet, dont see a need to. I havent had to change any udev rules or anything.

However, you can minimalise the compiling and have some snazzy premade packages from my 64 bit repositories:

```

deb http://dev.acidchat.net/apt dapper main
deb-src http://dev.acidchat.net/apt dapper main

```

then apt-get install wizardpen-driver
or apt-get source wizardpen-driver

If you dont have 64-bit, you can omit the binary repository and keep the source repository in your sources.list and attempt to build the package for i386. (needs build-essential, dh_make, dpkg-buildpackage, fakeroot, etc ) as I dont know how to make 32 bit packages on a 64 bit machine yet.


Also, read /usr/share/doc/wizardpen-driver/README.Debian for more info.

---

### Post by daller on 2006-09-03
> **ShadowRage said:**
> 
I dont have too many issues with plug and play, because I never unplug my tablet, dont see a need to. I havent had to change any udev rules or anything.

Well, I have a laptop, so it would be nice to be able to unplug it!

---

### Post by prokoudine on 2006-09-03
> **ShadowRage said:**
> To make things MUCH easier on 
However, you can minimalise the compiling and have some snazzy premade packages from my 64 bit repositories:


apt-get update says:

Ign [http://dev.acidchat.net](http://dev.acidchat.net) dapper/main Sources

Anyway,I need it not for me, but for a non-Ubuntu user.

---

### Post by daller on 2006-09-04
Well, simply install it from the tarball!

Everything is explained here: (don't be scared!)

[https://wiki.ubuntu.com/TabletSetupWizardpen](https://wiki.ubuntu.com/TabletSetupWizardpen)

...and tablet-shortcuts will be supported soon!

---

### Post by prokoudine on 2006-09-04
I'm afraid, you haven't read carefully, what I wrote.

The tarball **is not available for download**. I didn't ask for debs, I asked for the tarball :)

**Update**: the download link seesn to work again. No warries then :)

---

### Post by daller on 2006-09-23
Any of you guys interested in getting the shortcut-areas on the tablet working?

I've made a little app, that supports identifying the AREAS!

Problem is that the tablet AREA seems to be configured BAD (a driver issue) - Pressing a shortcut will move the cursor to the border of the screen! - Any solutions to this?

---

### Post by NickABusey on 2006-10-09
My tablet doesn't have shortcut areas, but your driver got it working. Everything works now, except for pressure sensitivity. Is there anyway to enable this?

---

### Post by daller on 2006-10-10
> **NickABusey said:**
> My tablet doesn't have shortcut areas, but your driver got it working. Everything works now, except for pressure sensitivity. Is there anyway to enable this?

What is the **make** and **model** of the tablet?

Try running "wacdump /dev/tablet-event" - There is a PRESSURE-parametre, see if it changes upon pressure.

Maybe wacdump is not in your system, as far as i remember, it's in the **wacom-tools** package

---

### Post by PriceChild on 2006-10-10
Could i maybe suggest using```
sudo checkinstall
```instead of ```
sudo make install
```In this howto. It produces a deb package which is much more easily handled by the you and the system. Plus you can remove it more easily if you delete your building dir.

---

### Post by daller on 2006-10-10
> **PriceChild said:**
> Could i maybe suggest using```
sudo checkinstall
```instead of ```
sudo make install
```In this howto. It produces a deb package which is much more easily handled by the you and the system. Plus you can remove it more easily if you delete your building dir.

Does it only create a deb, or does it also install it?

If it only creates the deb, this means that there should be added an extra line to the howto. - Which is not needed! (The howto is long enough already!)

In my guide it's not needed to run "make install" or "checkinstall"

May I also suggest that we work on a wiki-howto, instead of on this forum.

My guide for example: [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)

---

### Post by ophuls on 2006-10-26
Hi, daller,  I see you are really active trying to make this tablets work and hope you can help me with this. Since i upgraded to edgy mi pen no longer works. (I know your howto is for dapper, but i see you are marked as edgy testing user, so...) Anyway, I recreated your howto step by step after the upgrade, and still no luck. The tablet mouse do work, and even the pen is recognized by ./calibrate, but when I start X i get this in xorg.log:

```
(II) LoadModule: "wizardpen"
(II) Loading /usr/lib/xorg/modules/input/wizardpen_drv.so
dlopen: /usr/lib/xorg/modules/input/wizardpen_drv.so: undefined symbol: __stack_chk_fail_local
(EE) Failed to load /usr/lib/xorg/modules/input/wizardpen_drv.so
(II) UnloadModule: "wizardpen"
(EE) Failed to load module "wizardpen" (loader failed, 7)
```

Also, in compilation, I get wizardpen_drv.SO, not .O.
Any tips? Thank you in advance.

---

### Post by daller on 2006-10-26
I think I cracked the nut!

Use this copy command instead!

```
sudo cp wizardpen_drv.so /usr/lib/xorg/modules/input/
```

The xorg-people keep changing setup :(

(The guide is from today based on Edgy! - And this issue has been fixed!)

---

### Post by daller on 2006-10-26
Well... No, ended up the same way:

(II) LoadModule: "wizardpen"
(II) Loading /usr/lib/xorg/modules/input/wizardpen_drv.so
dlopen: /usr/lib/xorg/modules/input/wizardpen_drv.so: undefined symbol: __stack_chk_fail_local
(EE) Failed to load /usr/lib/xorg/modules/input/wizardpen_drv.so
(II) UnloadModule: "wizardpen"
(EE) Failed to load module "wizardpen" (loader failed, 7)
(EE) No Input driver matching `wizardpen'

---

### Post by ophuls on 2006-10-26
Wow, you are even faster than I thought! But yes, I try that and also I try changing the name to wizardpen_drv.o, and even copying wizardpen.o and wizardpen.h, probably a very stupid thing to do, but I know nothing about compiling stuff. I even downloaded other versions of GCC, and compiled the driver with them. Nothing. I hope you can solve this, any help you need, tip me.

---

### Post by daller on 2006-10-26
This is a way to install MY version of the driver from dapper.

It works on all of my 3 test machines!

[https://help.ubuntu.com/community/TabletSetupWizardpen#head-2b7a38de2ee5f77258591f0f1e7984a761bed268](https://help.ubuntu.com/community/TabletSetupWizardpen#head-2b7a38de2ee5f77258591f0f1e7984a761bed268)

---

### Post by ophuls on 2006-10-26
Oh, you are great!!

---

### Post by daller on 2006-10-27
> **ophuls said:**
> Oh, you are great!!

Was that a "It worked!" ?

If so, I'll have that part in my howto, until I figure out how to compile under edgy.

Just curious, what tablet do you have?

If not an "WP5540U" I would appreaciate if you posted the output from calibrate!

I would also like to know the brand/model of the tablet.

---

### Post by ophuls on 2006-10-28
Yes, it worked perfectly.
I have this
Tablet WP8060U
Genius Mousepen 8x6 (this if I recall correctly).
Calibrate give me this:
```
          Option          "TopX"          "0"
        Option          "TopY"          "0"
        Option          "BottomX"       "32747"
        Option          "BottomY"       "32762"
        Option          "MaxX"          "32747"
        Option          "MaxY"          "32762"
```

But I get this only if I try to use all the possible space that the tablet can handle. If I restrict to the rectangle that is draw over the tablet, I get
```
          Option          "TopX"          "826"
        Option          "TopY"          "2626"
        Option          "BottomX"       "32747"
        Option          "BottomY"       "32762"
        Option          "MaxX"          "32747"
        Option          "MaxY"          "32762"
```
This is what I use normally, but it leaves out the tablet hotspots, so probably you are asking me for the first output, not this one.

Thank you very much, and pardon my English.

---

### Post by daller on 2006-10-28
> **ophuls said:**
> Yes, it worked perfectly.

NICE!

Great to hear that!

Added the output the the guide!

About the AREA, I use the area that excludes the HOTSPOTS!

The hotspot-configuration works best, if it's outside the drawing-area (you would hate to make a DOT every time you press a HOTSPOT?)

Well, again! - Awesome!

---

