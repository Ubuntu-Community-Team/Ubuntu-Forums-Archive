---
title: "Anyone using the Plymouth PPA?"
date: 2009-03-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by bpl07 on 2009-03-01
Has anyone experimented with the Plymouth PPA packages in jaunty?

[https://launchpad.net/~plymouth-dev/+archive/ppa](https://launchpad.net/~plymouth-dev/+archive/ppa)

---

### Post by Jay_Bee on 2009-03-01
Well, without KMS support in the kernel it's really not much of a use, but it's still nice to know the work is being done.

---

### Post by bpl07 on 2009-03-01
> **Jay_Bee said:**
> Well, without KMS support in the kernel it's really not much of a use, but it's still nice to know the work is being done.

You can get 2.6.29 from here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29-rc6/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29-rc6/)

There should be a ppa for the kernel you can add to your software sources soon, but for now this should work for testing purposes.

---

### Post by red_team316 on 2009-03-01
Holy Cow, I was just about to post something similar to this but for plugin development. THE PPA IS UP!!!!

---

### Post by dBuster on 2009-03-01
I am using the pythoneers ppa or did at least to get updated to Alpha 5 and get around the broken package issue.  Have not tried the one posted here.  Is it the same or do they have other packages for upgrading??

---

### Post by MadsRH on 2009-03-01
Does anyone know what it look like? Is it just fadeing in/out or is it some kind of effect?

---

### Post by MacUntu on 2009-03-01
Without proper drivers it's just a different splash screen (the famous one from Fedora with a different Logo). I needed to activate the vesafb framebuffer via the VGA=... thing in the kernel line of GRUB.

Text mode doesn't really work - it spams the progress bar between the output of the init scripts (they need to be reworked too).

Plymouth seems to be more CPU consuming than Usplash:

[img]http://img.xrmb2.net/images/538967.png[/img]

[img]http://img.xrmb2.net/images/223708.png[/img]

However, boot times didn't change.

---

### Post by bpl07 on 2009-03-01
What version of grub are you using?

---

### Post by MacUntu on 2009-03-01
The current Jaunty version (0.97-29ubuntu50).

---

### Post by Starks on 2009-03-01
> **bpl07 said:**
> You can get 2.6.29 from here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29-rc6/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29-rc6/)

There should be a ppa for the kernel you can add to your software sources soon, but for now this should work for testing purposes.

No KMS support though.

---

### Post by autocrosser on 2009-03-01
I'd really like to test it, but until nVidia has KMS support it would be text only for me :(

---

### Post by BwackNinja on 2009-03-01
Ooooh, I'll be checking this out once I can get the time to make my radeon KMS and DRI2 work properly...

I wouldn't butcher this install to do that, got space for another few :P

---

### Post by MacUntu on 2009-03-03
> **autocrosser said:**
> I'd really like to test it, but until nVidia has KMS support it would be text only for me :(

Nope: [http://www.youtube.com/watch?v=a1U0dK2HpUk](http://www.youtube.com/watch?v=a1U0dK2HpUk)

But rather useful. :)

---

### Post by go7Ul1ai on 2009-03-03
I'm using it, it's all text like and get these weird blue bars going across the screen :P

---

### Post by red_team316 on 2009-03-03
> **autocrosser said:**
> I'd really like to test it, but until nVidia has KMS support it would be text only for me :(

adding a vga= line to your kernel line in grub worked fine on Fedora 10 for me with a 8800GTS 512.

---

### Post by autocrosser on 2009-03-04
Works for me--I've been wanting too....so here goes....

---

### Post by Nullack on 2009-03-04
Im going to wait until the FOSS NVIDIA driver improves in GIT before doing this. Its not robust.

---

### Post by plun on 2009-03-04
> **MacUntu said:**
> Nope: [http://www.youtube.com/watch?v=a1U0dK2HpUk](http://www.youtube.com/watch?v=a1U0dK2HpUk)

But rather useful. :)

Nice....;)

What vga resolution are you guys using ?

Tested and I only get a "Black screen" (no death...)

also read Fedoras wiki about it:

[http://fedoraproject.org/wiki/Releases/FeatureBetterStartup#User_Documentation](http://fedoraproject.org/wiki/Releases/FeatureBetterStartup#User_Documentation)

'vga=0x318' also gives "nada"....

:confused:


(nVidia 8600GT, 180.35 and 64 bit, -RC7 kernel)

---

### Post by Starks on 2009-03-04
I'm getting the same as plun.

---

### Post by portis on 2009-03-04
I'm using an Intel 965 laptop.

I just compiled a 2.6.29rc6 kernel myself. Because the precompiled kernel doesnot enable KMS, and passing i915.modeset=1 led to an unknown boot option warning. So I compiled myself, with i915 compiled into the kernel, and KMS enabled by default. I then run update-initramfs to get the plymouth to function with this new kernel image.

Well, after reboot, plymouth did appear, but not in a perfect state. I got a blank screen first, and then some text booting message, and then a plymouth screen, ("bizcom", I think). And then the GDM replaced it. I also noticed that the VT-swith does not work, and some functionalities of xrandr no longer work. Anyway, it's beginning to work, although far from flickering-free.

In my opinion, you can use plymouth either with KMS or with framebuffer. If your video card is supported by KMS, you can just enable it in the kernel. Otherwise, you have to pass the vga=xxx before boot process.

---

### Post by MacUntu on 2009-03-04
You can try vga=ask to get a list of supported resolutions. I'm using vga=795 (0x31B) for 1280x1024x32.

---

### Post by Starks on 2009-03-04
How do you compile i915 in and enable KMS by default?

Is there more to it than selecting "Enable modesetting on intel by default (DRM_I915_KMS)"?

---

### Post by MacUntu on 2009-03-04
This is something I've found somewhere on the net: you don't need to recompile the kernel with this setting as it can be activated via the kernel boot line. You need to compile the video driver yourself (reverting a patch that disables KMS support) and install a newer version of libdrm (linux-libc-dev doesn't seem to be KMS-ready).

Don't know if that's true and if it will work as I don't have an i915 chipset.

---

### Post by plun on 2009-03-04
> **MacUntu said:**
> You can try vga=ask to get a list of supported resolutions. I'm using vga=795 (0x31B) for 1280x1024x32.

OK thanks...  "mission critical" issue again...:D

vga=ask works OK and I have a few VGA modes and tons of Vesa modes.

IF I choose a VGA mode it is only text based...:confused:

---

### Post by MacUntu on 2009-03-04
And if you choose a VESA mode (just enter the character in front of the mode, eg. "k")? :)

---

### Post by plun on 2009-03-04
> **MacUntu said:**
> And if you choose a VESA mode (just enter the character in front of the mode, eg. "k")? :)

OK... mission failed...:---)

I wonder what differs....:confused:

---

### Post by MacUntu on 2009-03-04
Maybe too small, too low color depth - wild guessing.

---

### Post by idn on 2009-03-04
hi, does anyone know if kms is supported on the ati driver?

---

### Post by scaine on 2009-03-04
I'm not personally using any of this stuff, but I noticed this article regarding KMS in the Noveau driver and thought you might find it interesting :
[http://www.phoronix.com/scan.php?page=news_item&px=NzEwMA](http://www.phoronix.com/scan.php?page=news_item&px=NzEwMA)

Apparently this will be in Fedora 11.

---

### Post by nyarnon on 2009-03-08
Well I'm into candy (all kinds) and this is just freaking cool. It even runs on my eeepc 1000h. Love it :-)

---

### Post by plun on 2009-03-10
> **MacUntu said:**
> Maybe too small, too low color depth - wild guessing.

No wrong kernel....   it works with 2.6.28-9 which is within repo now..;)

---

### Post by red_team316 on 2009-03-11
> **plun said:**
> No wrong kernel....   it works with 2.6.28-9 which is within repo now..;)

Are you saying you got graphical boot with your NVIDIA card? If so, let us know how you got it working with what driver and card...Every attempt I've had with my 8800GTS is like running into a brick wall. Last kernel I tried was 2.6.29-rc7 and all I could get was the 3-color progress bar.

---

### Post by autocrosser on 2009-03-11
Yes--I'm interested plun----is it working for you?  And if so, how did you do it?????

---

### Post by red_team316 on 2009-03-11
> **autocrosser said:**
> Yes--I'm interested plun----is it working for you?  And if so, how did you do it?????

Autocrosser for my EVGA 8800GTS 512, I just downloaded the 2.6.28-9 kernel, headers, firmware from the repo. I then updated my linux-libc/gcc/etc all so I can compile the driver. I then downloaded the 180.37 x86_64 NVIDIA driver from Phoronix Forums(It points you to NVIDIA's FTP, it's not on the main page yet). I then Did a Ctrl+Alt+F1 to switch to VT1. From there I logged in and:
sudo /etc/init.d/kdm stop (or gdm if you use gnome)
cd mydata/NVIDIA (separate partition where I keep my drivers handy)
sudo sh NVIDIA-Linux-x86_64-180.37-pkg2.run
Built the driver rather than download from NVIDIA (I always do this)
It gave me OpenGL lib error but may have installed GL libs (sometimes I get this but it's somewhat non-trivial)
sudo /etc/init.d/kdm start (to my suprise it actually fired KDM right back up unlike previous drivers on intrepid/jaunty)
Reboot.
At GRUB, rather than letting it boot into the new kernel, I highlighted the correct line and pressed "E" to edit it. Then I selected the kernel line and pressed "E" again to edit it. I then appended vga=893 (Thats 1920x1200 for me =D ) and hit enter. Then I hit "B" to actually boot from it.

I saw the crusty Bizcom splash and the amazing solar flare!

Hopefully this helps some others get it working with NVIDIA. The vga=0x318 works also but since my native vga=893 line works, it's all the better.

It finally seems that NVIDIA is starting to release some halfway decent driver updates. One thing though, I didn't get the NVIDIA logo when X fired back up. It always used to do this by default when building the driver from scratch but didn't this time. Do I manually have to add a logo option to it? I know in the past, the ubuntu-repo drivers always had this disabled, but I prefer to see the logo so that I know it is working properly as I never rely on the restricted manager(It has borked my system more times than I want to remember)

EDIT: Hmm, apparently the Logo option doesn't work anymore oh well... :/

Here's the xorg.conf the 180.37 driver generated on Jaunty Alpha 5 for reference:
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Fri Mar  6 01:04:17 PST 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```



Now I can actually start working on a plugin :) It's really great to see this finally working on ubuntu-based. I can only hope this makes it's way back to Debian. This splash is really going to flesh out with several different distros contributing.

---

### Post by plun on 2009-03-11
> **autocrosser said:**
> Yes--I'm interested plun----is it working for you?  And if so, how did you do it?????

OK and I figured it out....

When Plymouth is installed splash is removed and also in the command syntax.

Just install plymouth from ppa

```
sudo gedit /boot/grub/menu.lst
```


```
title        Ubuntu jaunty (development branch), kernel 2.6.28-9-generic
uuid        18b2cb8e-50c1-47b8-a2a9-e867aed579a3
kernel        /boot/vmlinuz-2.6.28-9-generic root=UUID=18b2cb8e-50c1-47b8-a2a9-e867aed579a3 ro **splash vga=ask**
initrd        /boot/initrd.img-2.6.28-9-generic
quiet
```


I still have "vga=ask" because I will test more ....  1280x1024x16 works

;)

---

### Post by nyarnon on 2009-03-11
@plun & autocrosser,

If you have a intel card like I have on my eeepc 1000h (that thing keeps marveling me) you don't need to set the vga when using the latest kernel.
Just install from ppa. On my 64bit machine running a NVidia I had to set it.

Did anyone try changing the logo? I did easy and cool :-)

---

### Post by portis on 2009-03-11
The 2.6.29 kernels from kernel-ppa have disabled intel KMS, how you use that with plymouth?

> **nyarnon said:**
> @plun & autocrosser,

If you have a intel card like I have on my eeepc 1000h (that thing keeps marveling me) you don't need to set the vga when using the latest kernel.
Just install from ppa. On my 64bit machine running a NVidia I had to set it.

Did anyone try changing the logo? I did easy and cool :-)

---

### Post by plun on 2009-03-11
> **nyarnon said:**
> On my 64bit machine running a NVidia I had to set it.

Did anyone try changing the logo? I did easy and cool :-)

Yup... I am a nVidia freak  :D


Some more facts about frame buffers and resolutions (table)

[https://wiki.ubuntu.com/FrameBuffer](https://wiki.ubuntu.com/FrameBuffer)


How did you change the logo (also animated)  ???

---

### Post by nyarnon on 2009-03-11
@plun

well I do use the sun and with the loge I mean 

/usr/share/plymouth/bizcom.png

Just used the same format and after regenerating init.rd it shows up as expected. Will try later to use different formats. Pitty I haven't the time to toy around with it or I would create a howto :-)

To beat you to it:

sudo dpkg-reconfigure linux-image-`uname -r`

---

### Post by plun on 2009-03-11
> **nyarnon said:**
> @plun

well I do use the sun and with the loge I mean 

/usr/share/plymouth/bizcom.png

Just used the same format and after regenerating init.rd it shows up as expected. Will try later to use different formats. Pitty I haven't the time to toy around with it or I would create a howto :-)

To beat you to it:

sudo dpkg-reconfigure linux-image-`uname -r`

OK, thanks !

/usr/share/plymouth/solar for other pics....

Now we just needs a real artwork artist....:D

---

### Post by biasquez on 2009-03-11
on last ubuntu kernel plymouth works well? i have nvidia card with 180.35 driver but i can't use vt1 ( blank screen ). how can fix it?

---

### Post by plun on 2009-03-11
> **biasquez said:**
> on last ubuntu kernel plymouth works well? i have nvidia card with 180.35 driver but i can't use vt1 ( blank screen ). how can fix it?

I am on **180.37** and vt works but...  I must press Ctrl-alt-F1 **twice** then it works.

---

### Post by biasquez on 2009-03-11
> **plun said:**
> I am on **180.37** and vt works but...  I must press Ctrl-alt-F1 **twice** then it works.

ok, plymouth works ( last part of boot some code like starting log etc... is shown for few seconds) but i can't use virtual terminal...i have fresh install of jaunty and my xorg.conf is fine...


EDIT: which guide do you use to install latest nvidia driver?

---

### Post by cb951303 on 2009-03-11
ok, just to clarify things in my mind: does the "vga=xxx" thing enables KMS for nvidia, or is it just eye candy graphics without the KMS and works just like old splashes?

---

### Post by nyarnon on 2009-03-11
@cb951303

No it enables the vesa mode of plymouth which in essence gives you the same artwork and fun experience.

@plun 

the vt problem exists longer and is not plymouth related.

---

### Post by nyarnon on 2009-03-11
> **plun said:**
> OK, thanks !

/usr/share/plymouth/solar for other pics....

Now we just needs a real artwork artist....:D

Try this one :-) I know kewl ;-)

---

### Post by autocrosser on 2009-03-11
Awh!!!!---it needs to be the D!!!!!!:lolflag:

Or maybe the original.....

Or The UFP.........Star Trek forever!!

---

### Post by nyarnon on 2009-03-11
Just gave the Solar background a rework, this was just the toy we missed, wonder how long it will take till someone messes up his initrd :-)

---

### Post by autocrosser on 2009-03-11
I'm going to start making a Ubuntu one this evening---What would everyone want it to look like?  I'm thinking along the lines of the new GDM login with a rotating Ubuntu logo.....Thoughts-ideas welcome........looks like the elements are easy to work with.

---

### Post by nyarnon on 2009-03-11
Well would be nice if it fits onto the gdm login, but the new one doesn't give much options. And the problem with solar is the alignment in the right bottom corner you may consider using the spinfinity instead of solar to achieve that.

---

### Post by autocrosser on 2009-03-11
Sounds good---I'll start playing with it in about 4~5 hours from now......

---

### Post by nyarnon on 2009-03-11
Maybe you'll find some more usefull info here

[http://digitizor.com/2009/02/03/the-definitive-plymouth-guide-for-fedora-10/](http://digitizor.com/2009/02/03/the-definitive-plymouth-guide-for-fedora-10/)

forget it, nothing there :-(

---

### Post by autocrosser on 2009-03-11
Anything at this point helps :D  I'm going to talk to plymouth maintainers (PPA) also tonight...looks like I need to dig into the .so files at /usr/lib/plymouth too....

---

### Post by red_team316 on 2009-03-11
> **autocrosser said:**
> Anything at this point helps :D  I'm going to talk to plymouth maintainers (PPA) also tonight...looks like I need to dig into the .so files at /usr/lib/plymouth too....

autocrosser, are you a programmer also? Maybe we can collaborate on it.

I have already looked at the 3 ubuntu-plymouth packages and none of them contain the proper source. The source can be obtained through git. It provides the source to build plymouth as well as the plugins. Not sure how well they will mesh with ubuntu's build of plymouth so definitely get in contact with the PPA maintainers :)
[http://www.freedesktop.org/wiki/Software/Plymouth](http://www.freedesktop.org/wiki/Software/Plymouth)

You might also find it beneficial to subscribe to the plymouth mailing list. Take a look at the archives in December 2008. The "plymouth question" thread contains some useful info to start off. 
[http://lists.freedesktop.org/archives/plymouth/2008-December/000013.html](http://lists.freedesktop.org/archives/plymouth/2008-December/000013.html)

Make sure you have these installed before running autogen.sh and make:
```

sudo apt-get install build-essential g++ gcc make automake autoconf libcairo-dev libtool libpango1.0-dev libgtk2.0-dev libgtk2.0-0  

```
The actual plugin .so's are output to this directories:
whereveryoursourceis/plymouth/src/plugins/splash/solar/.libs
What to do with them from there is up to you. You can sudo make install, but that will replace plymouth and all plugins and I'm not sure exactly 100% where everything else needs to go if one was to copy only certain files needed yet. Awhile back I looked into this a little but haven't done much since until the ubuntu PPA's were up. Thus I'm back at it again :)

---

### Post by autocrosser on 2009-03-12
No so much a programmer as a graphic artist--I know enough programming to get me by....I'm much better with html/xml

I know what I want to end up with--look at the new GDM with the 3d-ish logo in the bottom-right---My thought is to animate the 3d logo in place & use a black background with a yellow/orange/gold ubuntu where the "bizcom" is now--change the progress bar to ubuntu colours--The "solar" plugin with proper mods will do nicely--I've been looking at sources this evening--have the git from freedesktop & have sent out several e-mails--I really just need a document on creating the plugin .so's--I'm open to collaborate work too...

I whipped up a quick ubuntu logo to replace the horrid bizcom ...just get the .png & put it in /usr/share/plymouth--just name it bizcom.png--so no conflicts---

Then do:  sudo plymouth-set-default-plugin solar
and:  sudo dpkg-reconfigure linux-image-`uname -r`

To cover your bases....

---

### Post by red_team316 on 2009-03-12
> **autocrosser said:**
> No so much a programmer as a graphic artist--I know enough programming to get me by....I'm much better with html/xml

I know what I want to end up with--look at the new GDM with the 3d-ish logo in the bottom-right---My thought is to animate the 3d logo in place & use a black background with a yellow/orange/gold ubuntu where the "bizcom" is now--change the progress bar to ubuntu colours--The "solar" plugin with proper mods will do nicely--I've been looking at sources this evening--have the git from freedesktop & have sent out several e-mails--I really just need a document on creating the plugin .so's--I'm open to collaborate work too...

I whipped up a quick ubuntu logo to replace the horrid bizcom ...just get the .png & put it in /usr/share/plymouth--just name it bizcom.png--so no conflicts---

Then do:  sudo plymouth-set-default-plugin solar
and:  sudo dpkg-reconfigure linux-image-`uname -r`

To cover your bases....

I just successfully compiled a working .so as a proof-of-concept that shows some simple modifications to it. As you can see in the attached image, I did a simple change in the throbber X position to show up at 1/4 of the screen width. Also, I changed the gradient colors to fade from red to yellow(The gradient is a little grainy but I'm not sure if thats just part of the code or something to do with the framebuffer at this point). And I did it with a simple makefile. Copying the .so files over to the proper directory, but for now the throbber images still point to the spinfinity folder. 

I don't really want to produce anything based off of solar/spinfinity or anything existing. It's got to be new and fresh. So since your better in the graphics dept than progging, I'd say whip up something that we can use that doesn't look like any existing plugin. I can handle the programming end hopefully if the concept art is prepared and or a decent explanation of what the end result will look like. I'm pretty decent at graphics too but figure this way better allocates resources if your not into programming much.

I can't look at GDM atm because I run kubuntu and it's late :P If theres a screenie somewhere or vid maybe you can point me to it.

Eventually, later down the line, I'll probably make a Parallax Plugin that will really show off what was limiting my parallax usplash from being all that it could.

---

### Post by autocrosser on 2009-03-12
Sounds good---I'll get it together over the next couple of days--with the weekend coming up I'll have some time for it--the rotation will be the hardest---the rest of it is a basic walk...


I threw together another logo for grins--not what I really want it to look like--but is still better than that bizcom.png--as before--rename & throw it in the /plymouth folder

---

### Post by red_team316 on 2009-03-12
> **autocrosser said:**
> Sounds good---I'll get it together over the next couple of days--with the weekend coming up I'll have some time for it--the rotation will be the hardest---the rest of it is a basic walk...


I threw together another logo for grins--not what I really want it to look like--but is still better than that bizcom.png--as before--rename & throw it in the /plymouth folder

Okay then. I'll work on getting some simple plugin directory structure and makefile stuff set up, and do a little documentation on some stuff and maybe this weekend we can whip something halfway concrete for testing.

---

### Post by autocrosser on 2009-03-12
Information from Ray Strode:

Hi Dean,

> I'm looking for information or documents on creating the plugin .so's.
> I've played around with the end files to change some images, but I
> really want to start creating plugins--can anyone point me the right way?


There's no documentation yet.  It's something I really want to have,
but haven't been able to prioritize time for yet.

The best bet is to start with a simple plugin (say fade-in) and copy
it and start editing it. You can experiment without rebooting by
running
plymouthd manually and then typing

plymouth --show-splash

(or the various other plymouth commands.  see plymouth --help).

useful key combos: ctrl-v will turn on verbose mode, ctrl-T will turn
on KD_TEXT mode which makes vt switches works and shows redraw
behavior, ctrl-G goes back to KD_GRAPHICS mode.

If you have any questions about how things work, feel free to ask them here.

Hopefully we'll have a better docs story at some point in the near future.
[COLOR=#888888]
--Ray[/COLOR]


Nice info to start with.....

---

### Post by nyarnon on 2009-03-12
@autocrosser
Thanks that IS usefull information saves rebooting. Thanx.

---

### Post by plun on 2009-03-12
Yup, thanks for info.. !!

But.. howto stop this "thing" if started within a tty...:confused::D


I also tested from source but that broke Plymouth for me.....

---

### Post by nyarnon on 2009-03-12
Kill the daemon or kill the console?

---

### Post by red_team316 on 2009-03-12
> **plun said:**
> Yup, thanks for info.. !!

But.. howto stop this "thing" if started within a tty...:confused::D


I also tested from source but that broke Plymouth for me.....

Open another tty and login and type:
sudo plymouth --quit

Although I've been working on a simple script that will incorporate the switch vtt start/stop of plymouth, and eventually integrate it into a plugin switcher/creator.

There is some more useful info, I've been typing up. Most of it is from the mailing list and/or my own experimentation. I'll post it when it get it completed. I might have it done by tonight or Friday. I know Ray is lacking on documentation so I'll post it to the mailing list too. Not sure how he wants it formatted or anything but right now I've got it formatted for the forum with tags.


Like I said earlier, it's probably not wise to install the source from git unless you know all the flags and such that need to be passed to configure. --prefix=/usr is one of them. Once you have autogenerated your configure file, type ./configure --help to see what extra switches there are. The PPA maintainers really need to supply this information so that others can get up and running without having to guess how they compiled it.

---

### Post by autocrosser on 2009-03-12
Your could also open system monitor & kill the process from there---

Onto thoughts-------

I'm going to start working with images this evening--I plan to have a working animated 3D Ubuntu logo like the new GDM one working sometime Sat (pacific time) I expect it to need 50 steps or so (hoping for less--depends on how smooth the step-transition is)...So, I'm looking first (because it would be easy?) moding the solar plugin--adding a animated Ubuntu where the sun is now--black background--Ubuntu Logo in place of the "bizcom.png (need to see if we can increase the present 290x78 pixel size box--red-team???) gold or orange or tan 2px bordered black logo (I have the official Ubuntu font--no problem there)--Is the progress-bar gradient? If so, do we need to define the start/finish colours?

I really like the gradient red at the bottom of the new GDM---what about making it the progress-bar??  Would have to define a sized 50/100px box & think about feathering the side borders--I think it would look nice for it to move cross the screen from left to right somewhat fog-like.....worst case would be to animate it using about 50/75 steps......

Another thought would be to "fill" the Ubuntu logo as the progress-bar.....

What thinks everyone?????

---

### Post by nyarnon on 2009-03-12
Sounds good to me. Would be good to have a c++ programmer taking care of a rewrite of the solar sorce to make it compatible I think.

---

### Post by autocrosser on 2009-03-12
Red_team is going to tackle that one.....I want to look more at the sorce-code, but I really am more comfortable pushing pixels.............maybe it's from all the years working with Macs......

I just contacted one of the desktop art team members---I'm hoping to get the logo raw image used in the new GDM---will save me lots of work.......(image of crossed fingers) ;)

---

### Post by red_team316 on 2009-03-12
> **autocrosser said:**
> Your could also open system monitor & kill the process from there---

Onto thoughts-------

I'm going to start working with images this evening--I plan to have a working animated 3D Ubuntu logo like the new GDM one working sometime Sat (pacific time) I expect it to need 50 steps or so (hoping for less--depends on how smooth the step-transition is)...So, I'm looking first (because it would be easy?) moding the solar plugin--adding a animated Ubuntu where the sun is now--black background--Ubuntu Logo in place of the "bizcom.png (need to see if we can increase the present 290x78 pixel size box--red-team???) gold or orange or tan 2px bordered black logo (I have the official Ubuntu font--no problem there)--Is the progress-bar gradient? If so, do we need to define the start/finish colours?

I really like the gradient red at the bottom of the new GDM---what about making it the progress-bar??  Would have to define a sized 50/100px box & think about feathering the side borders--I think it would look nice for it to move cross the screen from left to right somewhat fog-like.....worst case would be to animate it using about 50/75 steps......

Another thought would be to "fill" the Ubuntu logo as the progress-bar.....

What thinks everyone?????

50 frames shouldn't be bad at all as long as the images aren't really large. The spinfinity throbber has 30-some frames and the .so file produced is really tiny. Considering I've done a ~100MB usplash before(LOL I know thats pretty crazy, and that included fullscreen frames for 4 different resolutions), I really dont see it should be a problem considering with plymouth:
1) You don't need extra graphics for other resolutions. The same graphics should be able to be used for all resolutions and scaled properly from what I hear.
2) You're using PNG. While Usplash could do this too, it did not support alpha-blended transparency. If you are really talented at graphics, you could alpha-overlay an image on top of another to save filesize yet produce some interesting and variable results.
3) Appears to have alot more options concerning what you can do with it. I think you can even use OpenGL with it but haven't looked into that atm.
4) The solar plugin is a paltry 88.8KB, we have plenty of room to work with considering what was achieved there.
5) The solar flares are generated by code, not graphics, so that saves space and really expands the possibilities of what you can do.

Make the images any size you want. The 290x78 graphic can be changed to whatever you like. It can be dealt with. Just don't go crazy large.

Seriously, whatever you come up with we'll make it a reality. It appears that the sky is the limit, which is why I have been so excited about plymouth.

I'm installing GDM right now to see what you mean...

---

### Post by autocrosser on 2009-03-12
Just click on my user name :)

I just sent you another message---I'm including the background.png for you to look at....contacted the desktop team member that did it---hoping to get the image files......Am waiting to hear back from him--got some other work to do now--will look in about an hour or so from now............

---

### Post by Starks on 2009-03-12
This logo customization sounds incredibly awesome.

---

### Post by autocrosser on 2009-03-13
Quick Rough---

---

### Post by red_team316 on 2009-03-13
> **autocrosser said:**
> Just click on my user name :)

I just sent you another message---I'm including the background.png for you to look at....contacted the desktop team member that did it---hoping to get the image files......Am waiting to hear back from him--got some other work to do now--will look in about an hour or so from now............

Now that I'm looking at it, I'm visualizing the 3D Logo kind of arcing through the air from the left side of the screen. When it reaches slightly left of center of the screen a flash of light occurs(1 frame fullscreen) etching a 3D logo outline(or maybe just 2D) into the black background. At that same moment, the Ubuntu text next to it fills across and acts as the progressbar. All the while, the actual 3D logo keeps arcing until it lands in the corner as shown. That way, when it switches to GDM, it will be a smoother transition since the logo will already be there. The progress using gradients similar to solar plugin, and the 3D logo using fading alpha channels to leave a tracer effect while arcing through the air.

EDIT: Or maybe a streak that flys horizontal through the middle of the logo at that point to reveal the ubuntu text and progressbar. Just saw the rough. I really think a glow around the text would work wonders for the black bg. yet, color-themed orangish-red, maybe even hueing possibly if we can figure that out.

I think it meshes with with most of your ideas so far. Thoughts?


hehe I found it. I rarely ever click over in that direction :P

If you can get the image files or possibly the model that would be really helpful. Even though I'm a kde guy, I must say, it is really nice looking. From what I'd saw of the wallpapers so far though I haven't been too impressed. Somewhere I saw someone made a jackalope standing up on it's hind legs, that was actually the closest depiction of a jackalope I've seen yet. Although I can't remember if it was more logoish or more artsy. The Ibex wallpaper I thought turned out great even though it was somewhat abstract. Simple yet bold.

---

### Post by autocrosser on 2009-03-13
I like the arc idea--waiting to see if I can get the artwork--Thinking it needs to rotate slowly whilst in the arc (like being thrown?)--Try the burst, but I think it might be too much....The logo could "uncover" the Ubuntu logo & progress bar--or just skip the bar---use the logo as the "bar"

It's shaping up--I'll know more tomorrow---time to turn in--Friday is generally "fun" :(

---

### Post by nyarnon on 2009-03-13
> **red_team316 said:**
> 50 frames shouldn't be bad at all as long as the images aren't really large. <cut>
Make the images any size you want.

Don't forget that they are going to be stored in initrd. So you really want to contemplate the size especially considering that your average install has 2 or three kernels.

---

### Post by autocrosser on 2009-03-13
OK--Kenneth Wimer got back to me & it's really positive!!!!

Hi Dean, 

On Mar 13, 2009, at 3:31 AM, Dean Loros wrote: 

[INDENT]Hi Ken-- 

I'm working loosely with Plymouth development & members of Jaunty- 
testing forum at Ubuntu-forums...Working to create a Ubuntu-specific 
Plymouth plugin & I would like to use the 3D-ish logo image that is in 
the new GDM theme---Do you have access to the artwork or can you put me 
in touch with someone who can?  I am planning to animate it & would love 
the raw file that was cut to create the GDM background (and having the 
raw file would decrease my work time :) )....Any info would be very 
helpful... 
[/INDENT] 
I created all the artwork and can give you all the pieces you need :-) 

The logo was made with a 3D renderer, everything else is svg. I'd love to help create any pics you need to realize this. If you have a mockup of what you have in mind send it to me and we can work on getting something together. 

Cheers, 
Kenneth 



So, I'm going to point him towards this thread & include any other info I can think of......


So here we go!!!!

---

### Post by plun on 2009-03-13
> **autocrosser said:**
> 
So here we go!!!!

Great work and thanks !...:D

"The power of open source".....

---

### Post by cb951303 on 2009-03-13
I emailed NVIDIA to have an official word on the status of KMS support. Here is the response

> 
Hello,

Thanks for your message. We have no current plans to support KMS in the near term, but knowing that it is important to our users will help to prioritize our future work.

Regards,
Roland
NVIDIA


no flicker-free boot exp for us nvidia users :/

---

### Post by red_team316 on 2009-03-13
> **nyarnon said:**
> Don't forget that they are going to be stored in initrd. So you really want to contemplate the size especially considering that your average install has 2 or three kernels.

Yes, I understand that. I definitely want the boot process to be as fast as it can be. The transparency support will really help in this area for overlaying images. Even if we used a static 800x600 image as the background, it wouldn't be any bigger than a standard usplash .so file. 800x600 frames would be a out of the question though.

> **autocrosser said:**
> OK--Kenneth Wimer got back to me & it's really positive!!!!

Hi Dean, 

On Mar 13, 2009, at 3:31 AM, Dean Loros wrote: 

[INDENT]Hi Ken-- 

I'm working loosely with Plymouth development & members of Jaunty- 
testing forum at Ubuntu-forums...Working to create a Ubuntu-specific 
Plymouth plugin & I would like to use the 3D-ish logo image that is in 
the new GDM theme---Do you have access to the artwork or can you put me 
in touch with someone who can?  I am planning to animate it & would love 
the raw file that was cut to create the GDM background (and having the 
raw file would decrease my work time :) )....Any info would be very 
helpful... 
[/INDENT] 
I created all the artwork and can give you all the pieces you need :-) 

The logo was made with a 3D renderer, everything else is svg. I'd love to help create any pics you need to realize this. If you have a mockup of what you have in mind send it to me and we can work on getting something together. 

Cheers, 
Kenneth 



So, I'm going to point him towards this thread & include any other info I can think of......


So here we go!!!!

Good stuff man. I contacted Kenneth awhile back after watching the UDS developer vid on plymouth. He was pretty swamped at the time but did get back to me. Hopefully, he can interpret most of the idea and get us some something we can work with fairly quickly, considering he created it, manipulating it to fit our needs should be fairly easy. I wonder what 3D renderer he used?

I did get a splash testing script whipped up last night. It's eventually gonna be part of [COLOR="Red"]PHENIX[/COLOR] (Plymouth Hyper-Extension for *NIX), which will aid in testing and creating new plugins.
> 
phe·nix      (f&#275;'n&#301;ks)  Pronunciation Key 
n.   Variant of phoenix. 

> 
plug-in    (pl&#365;g'&#301;n')  Pronunciation Key 
An accessory software or hardware package that is used in conjunction with an existing application or device to extend its capabilities or provide additional functions. 

[http://dictionary.reference.com/browse/phenix](http://dictionary.reference.com/browse/phenix)
[http://dictionary.reference.com/browse/hyperextension](http://dictionary.reference.com/browse/hyperextension)

I think it is a fitting name considering that Plymouth is by far the most advanced bootsplash yet. Extension being somewhat synonymous with plug-in. Also, the name kind of derives from the mythology of the phoenix, since plymouth is rising in place of usplash. And eventually, someday, may be replaced by an even better bootsplash.



I'll polish off the rest of my documentation and post it later tonight.

---

### Post by MacUntu on 2009-03-13
That's the latest news about Nvidia and KMS I know about: [http://www.nvnews.net/vbulletin/showpost.php?p=1841465&postcount=4](http://www.nvnews.net/vbulletin/showpost.php?p=1841465&postcount=4) 

On the other hand there's nouveau. It supports KMS, doesn't it? Well, no 3D then but still better than nothing.

---

### Post by plun on 2009-03-13
> **MacUntu said:**
>  It supports KMS, doesn't it? Well, no 3D then but still better than nothing.

Well... just make it better then W7.... ;)

 a glowing line and a flying in logo....

---

### Post by Knorr on 2009-03-13
> **autocrosser said:**
> Quick Rough---

Great work with the plugin. I'll look forward to seeing the results.

I would like to comment to your rough mockup. I think the logo and throbber is in a somewhat different style than the background. The colors seems a bit off, and the edges a bit too rough.

I would prefer the logo and throbber to look more in the line of something like the attached image.

It's the logo from the current usplash theme. A bit conservative perhaps. ;)

I'm not that good with artwork, but I hope it shows what kind of style I'm thinking about.

---

### Post by autocrosser on 2009-03-13
Ya--that's better than mine--the progress bar should be about half the size....

So, let's use the current usplash logo artwork--fill the ubuntu instead of a progress bar & not have the ubuntu appear until the human logo passes by it...How is that sounding.....

---

### Post by DanaG on 2009-03-14
I tried installing Plymouth, and never managed to get it to display anything during boot -- even with a custom-compiled radeon-KMS kernel.  I ran 'strace' on plymouthd, and it seems to be trying to do something (drawing?) on ttyS0, and of course, failing.  What tty is plymouth supposed to draw on?  There don't seem to be any config files for it.  Even manually launching plymouthd and running plymouth --show-splash doesn't work.
So far, I am rather not impressed.  =þ

---

### Post by red_team316 on 2009-03-14
[SIZE="6"]**Jaunty Plymouth PPA Plugin Development Tutorial**[/SIZE]
**1)** Make sure you have the proper driver installed for your graphics card. 
The NVIDIA Blob 180.37 appears to work fine with kernel 2.6.28-9 for 8xxx series GPU's.

**2)** Create a file in the "/etc/apt/sources.list.d" directory called "PlymouthPPA.list"

**3)** Open up PlymouthPPA.list and add the following lines to it:
```

## PPA for Plymouth Developers
deb http://ppa.launchpad.net/plymouth-dev/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/plymouth-dev/ppa/ubuntu jaunty main

```

**4)** Paste the following text into a file and save it as PlymouthPPA.key (This is for package authentication)
```

-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESZry+wEEALgDkQimObkreCwcP37Cqtn/UFSCFn4/T6yG3+x58O3fQP8Iu7O7krAK9UuC
VqemCdhqIz1SVHsKQXa6uCtMRW0Nx0OD7F1kxH9mNwNCXe52zD0ppRsK//Gjj+MCkZV3Thi1
0o2R1Upj6GeAxkvF7Q/5IxRMFWWpUjLShnD3YrhfABEBAAG0JUxhdW5jaHBhZCBQUEEgZm9y
IFBseW1vdXRoIERldmVsb3BlcnOItgQTAQIAIAUCSZry+wIbAwYLCQgHAwIEFQIIAwQWAgMB
Ah4BAheAAAoJENLY63m8yx9XV9IEALBEHP+5M+mzzUIbW8WWmYrs/zsKc74kMQ2/M1V0/+Jz
jUDKAaDO7IO/spuOwrLldPEyVeJaadhYkuwDUi3/75P6wO56n/NdZxAE4J8eDdurOPTF1OAn
pNVpwhf/3dcDOtU2OmyPnQ/8xc9zo4sXqVj3nfl6PK726GOCpsts6vcp
=zUTq
-----END PGP PUBLIC KEY BLOCK-----

```

**5)** Add the key either through synaptic/adept or with the terminal:
```

sudo apt-key add PlymouthPPA.key

```

**6)** Open up synaptic/adept or a terminal and update your package list and install these packages:
```

sudo apt-get update
sudo apt-get install git-core build-essential g++ gcc make automake autoconf libcairo-dev libtool libpango1.0-dev libgtk2.0-dev libgtk2.0-0  
sudo apt-get install plymouth libplymouth2 libplymouth-dev

```

**7)** Open up your /boot/grub/menu.list and append vga=XXX to your kernel line, where XXX is the number for your desired resolution. 
If you don't know what this should be, you can use vga=ask. If your driver supports KMS, then this step is probably completely unneccesary.

**8 )** At this point, you should have plymouth installed and can reboot to see the wacky bizcom/fedora hack. So reboot and when you're back you can install the plymouth source so you can improve it or create plugins.

**9)** Create a directory somewhere that you plan to download the source to. This can be /home/username/plymouth or whatever location you desire. 

**10)** Open up a terminal, cd to the plymouth directory you just made, and git the source code :)
```

git clone git://git.freedesktop.org/git/plymouth

```

**11)** Now go to the newly created plymouth directory and it will have a file called autogen.sh in it. In the terminal type: 
```

./autogen.sh --prefix=/usr --with-logo=/usr/share/plymouth/bizcom.png

```
replacing bizcom.png with something a little nicer if you like.

**12)** Now if you didn't get any error messages, you should be ready to type:
```

make 

```
from there, you can "sudo make install" if you wish but you're probably better off not doing so unless you are developing for the plymouth library rather than a plugin. If you just want to make your own plugin, then keep reading...

**13)** Browse to the "/yourplymouthgitdirectory/plymouth/src/plugins/splash/plugin-name" directory and you will notice that there are Makefiles in each splash directory. Open a terminal here and type:
```

make

```
on a successful compilation of the plugin, you will notice a new directory called .libs (if you can't see it, then enable viewing of hidden files and folders). This directory is where the .so plugin file is stored. To install the built plugin, type:
```

sudo make install

```
in the plugin directory where you made it.

[SIZE="5"]**How to change the default plugin for bootup**[/SIZE]
```

sudo /usr/sbin/plymouth-set-default-plugin spinfinity

```
replace spinfinity with whatever plugin name you want to use. For instance, replace spinfinity with solar.

[SIZE="5"]**How to test a plugin without rebooting**[/SIZE]

If you want to test the plugin without having to restart the machine, save this script and run it in a terminal:
sudo sh phenix-test-plugin.sh [TimeInSeconds]
```

#!/bin/bash
# Phenix - Plymouth Hyper-Extension for *NIX
# Plugin Testing Script
# Copyright (c) 2009 Jonathan Greig (red_team316)
#
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# as published by the Free Software Foundation; either version 2
# of the License, or (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA.

echo "Testing Plymouth Plugin..."
init 3                             # change to runlevel 3 (typical runlevel for text console login)
chvt 8                             # switch to virtual terminal 8
plymouthd                          # start the plymouth daemon
sleep 1                            # wait a second 
plymouth --show-splash             # show splash while we...
sleep "$1"                         # wait X amount of seconds before quitting
plymouth --quit                    # stop plymouth
chvt 7                             # switch back to the desktop
echo "Done."

```

[SIZE="5"]**The proper way to install a plugin from source**[/SIZE]
In the "/yourplymouthgitdirectory/plymouth/src/plugins/splash/plugin-name" directory type:
```

make
sudo make install
sudo /usr/sbin/plymouth-set-default-plugin the-name-of-the-plugin
sudo /usr/libexec/plymouth/plymouth-update-initrd

```

[SIZE="5"]**How to make a single plugin**[/SIZE]
On Jaunty, with the PPA packages and git source installed, you can copy one of the plugin directories to somewhere else on your drive and work on it from there.
```

pkg-config --cflags plymouth-1

```
returns "-I/usr/include/plymouth-1", so you will need to add the extra ply/ or plybootsplash/ in your #include lines. Otherwise you can simply specify them manually at the terminal as such:
```

gcc -fPIC -I/usr/include/plymouth-1/plybootsplash -I/usr/include/plymouth-1/ply `pkg-config --libs plymouth-1` -shared -o plugin.so plugin.c

```
You will need to remove the include "config.h" from your plugin. Since you're working separate of the git source, it isn't really needed, but it's still good to take a look at config.h to familiarize yourself with whats in there.
You will also need to add several #defines with the headers at the top of the plugin and manually specify the paths to the required files there. If you are wondering what these #defines originally were, then look at the Makefile 
that was generated for the splash in the git source. Once you that done, your splash should build with no problems. plugin.so will be generated in the same directory. You can now manually transfer the .so file to 
/usr/lib/plymouth/whateveryourpluginnameis.so and the graphics folder to /usr/share/plymouth/whateveryourpluginnameis

---

### Post by Knorr on 2009-03-14
> **autocrosser said:**
> Ya--that's better than mine--the progress bar should be about half the size....

So, let's use the current usplash logo artwork--fill the ubuntu instead of a progress bar & not have the ubuntu appear until the human logo passes by it...How is that sounding.....

That sounds great. If there's time. The bootsplash is not active for very long, but I guess adjustments to the speed of the animation is the key.

---

### Post by plun on 2009-03-14
I also wonder if there is a way to handle the short interrupts with text mode during boot ?  one short before and a longer after Plymouth runs.


Great guide red_team :D

---

### Post by MacUntu on 2009-03-14
N1, red_team! 

Any of you "in-touch-with-the-devs"-guys knows about the status of the usplash message wrapper for the text mode? Right now text mode is a mess because init scripts use the usplash message commands.

> **Knorr said:**
> The bootsplash is not active for very long

Yes, maybe they should make the boot slow again for Karmik. :D

---

### Post by xtoudi on 2009-03-14
Hmmmm when I add vga=ask and choose 348 (1400x1050x16) - it is obviously working. But when I add vga=348 then boot screen is blank. Also TTY is blank. Strange, is it?

---

### Post by vishalrao on 2009-03-14
i think you need to put vga=0x348 something like that IIRC

edit: this link says you enter the decimal version of the number: [http://wiki.antlinux.com/pmwiki.php?n=HowTos.VgaModes](http://wiki.antlinux.com/pmwiki.php?n=HowTos.VgaModes)

so 348 would be vga=840

---

### Post by xtoudi on 2009-03-14
> **vishalrao said:**
> i think you need to put vga=0x348 something like that IIRC

edit: this link says you enter the decimal version of the number: [http://wiki.antlinux.com/pmwiki.php?n=HowTos.VgaModes](http://wiki.antlinux.com/pmwiki.php?n=HowTos.VgaModes)

so 348 would be vga=840

Thanks!! vga=0x348 works!!
Also thanks for that link!

---

### Post by autocrosser on 2009-03-14
OK--here is a "work-in-progress"  Open in GIMP & look at it with the various elements on/off--red_team & I are playing with it now....Not certain that it's the end result--there are several other ideas "in the works" :)

---

### Post by plun on 2009-03-15
Thanks autocrosser...

This was difficult....;)


 a photo just on the fly

[[img]http://ubuntu-pics.de/thumb/11071/dsc_0413_1No60y.jpg[/img]](http://ubuntu-pics.de/bild/11071/dsc_0413_1No60y.jpg)

Change colour for the animation and "ubuntu" must probably be the "Bizkom"...

:D

---

### Post by nyarnon on 2009-03-15
> **autocrosser said:**
> OK--here is a "work-in-progress"  Open in GIMP & look at it with the various elements on/off--red_team & I are playing with it now....Not certain that it's the end result--there are several other ideas "in the works" :)

Nice work, can some one change the sun animation in a way that the ubuntu ring shouws some flames or somithing alike?

---

### Post by red_team316 on 2009-03-15
> **nyarnon said:**
> Nice work, can some one change the sun animation in a way that the ubuntu ring shouws some flames or somithing alike?

working on it as I speak(not flames though lol)

---

### Post by andrek on 2009-03-15
Damn, I bet it's gonna be awesome.
I can't wait anymore! :)

---

### Post by autocrosser on 2009-03-15
Wow plun--that's very interesting---Is that my text/blur you're using? ;-) (looks like the 100% blur & text--add the 50% in the merge--it will look brighter)

You might try removing the bizcom.png from the folder---or use one of my other ones I've posted.....

We've got Kenneth Wimer (he did the GDM artwork) doing a rotating version of his 3D human logo.....Just wait---it's going to look very cool!!!!

---

### Post by plun on 2009-03-15
> **autocrosser said:**
> Wow plun--that's very interesting---Is that my text/blur you're using? ;-) (looks like the 100% blur & text--add the 50% in the merge--it will look brighter)

You might try removing the bizcom.png from the folder---or use one of my other ones I've posted.....

We've got Kenneth Wimer (he did the GDM artwork) doing a rotating version of his 3D human logo.....Just wait---it's going to look very cool!!!!

OK... I got trouble when I shot this photo with a Nikon camera..heavy backlight from a spring sun...:D

Nevertheless I think orange and yellow "flames" can be something instead of blue. If also the Ubuntu logo rotates its a bonus...

---

### Post by nyarnon on 2009-03-18
> **plun said:**
> OK... I got trouble when I shot this photo with a Nikon camera..heavy backlight from a spring sun...:D

Nevertheless I think orange and yellow "flames" can be something instead of blue. If also the Ubuntu logo rotates its a bonus...

That was my idea :-) The logo and the dark setup asks for it, but let's see a rotating logo might be a surprise if it doesn't get to big that is. Dant forget is has to go into initrd and we want fast boot times.

---

### Post by Starks on 2009-03-18
Can the logo have a shine/glow/sparkle effect instead of something ripped from Solar?

---

### Post by red_team316 on 2009-03-18
> **Starks said:**
> Can the logo have a shine/glow/sparkle effect instead of something ripped from Solar?

What we are working on will look nothing like solar. That's guaranteed.

---

### Post by Zorael on 2009-03-18
WTB Kubuntu flavor of whatever you're cooking up. :3

---

### Post by Starks on 2009-03-18
> **red_team316 said:**
> What we are working on will look nothing like solar. That's guaranteed.
Is there a bzr/svn/git repo I can test with?

---

### Post by red_team316 on 2009-03-18
> **Zorael said:**
> WTB Kubuntu flavor of whatever you're cooking up. :3

I hope I can get a variant of the artwork, as I would also like one too.

> **Starks said:**
> Is there a bzr/svn/git repo I can test with?

Not at this point. It's still in early stages and only demonstrates circular/elliptical/oscillating movement. I do have a standalone plugin source atm that will be incorporated into a .deb package when complete.

If anyone would like to start working on more plugins, they can copy any of the splash plugin folders over to somewhere else on their hard-drive and use the attached makefile to modify and build their own.

---

### Post by DanaG on 2009-03-18
Hmm, what can I do to make Plymouth work for me?  For me, it does literally *nothing* -- just boots in text mode.  I strace'd the plymouthd, and it seems to be trying to do something to ttyS0 -- yes, SERIAL console.

---

### Post by autocrosser on 2009-03-18
> **red_team316 said:**
> I hope I can get a variant of the artwork, as I would also like one too.


As far as the artwork--as soon as I see the 3D logo it should not be hard to do a Kubuntu variant--would have to change the  GDM screen to match--if Kubuntu uses GDM??? (sorry, I've never done Kubuntu, so I do not know)--Are you wanting the full logo with the gears?

I guess that opens the door for Xubuntu & Edubuntu also ;)  Let me have artwork in hand to work with first......... I'm going on a weekender, so I'll be able to get down to it next week...Have not heard back from Ken yet, so assuming next week is a good bet.

---

### Post by Starks on 2009-03-18
Red, can you post the WIP plugin source or binary?

---

### Post by autocrosser on 2009-03-18
> **DanaG said:**
> Hmm, what can I do to make Plymouth work for me?  For me, it does literally *nothing* -- just boots in text mode.  I strace'd the plymouthd, and it seems to be trying to do something to ttyS0 -- yes, SERIAL console.


Have you tried to add a vga to your kernel line?

---

### Post by DanaG on 2009-03-18
I've actually even tried it with a kernel built specifically with radeon KMS.... still no-go.  sudo plymouth --show-splash just makes the screen blink once... and then return right back to the terminal I was on.

Edit: oh, and I was able to confirm that kms itself was working... when I went back to usplash on it, *that* was running at native resolution -- and so was the console.

---

### Post by red_team316 on 2009-03-19
> **autocrosser said:**
> As far as the artwork--as soon as I see the 3D logo it should not be hard to do a Kubuntu variant--would have to change the  GDM screen to match--if Kubuntu uses GDM??? (sorry, I've never done Kubuntu, so I do not know)--Are you wanting the full logo with the gears?

I guess that opens the door for Xubuntu & Edubuntu also ;)  Let me have artwork in hand to work with first......... I'm going on a weekender, so I'll be able to get down to it next week...Have not heard back from Ken yet, so assuming next week is a good bet.

Oh yes, gears are the tell tale sign lol :) I'm not sure if Ken already has a variant or what but once we get something to work with, we can build from there as neccessary. I PM'ed darkmaster who creates OpenGEU to ask if he is going to use plymouth in future releases but he hasn't responded. I'm sure the variants shouldn't be too hard to whip up, especially if Ken is willing to let go of the model or work with us on them.

> **Starks said:**
> Red, can you post the WIP plugin source or binary?

Patience. At this point it isn't anything worth testing. We've confirmed that it does in fact work, so no worries there. Until we get some art to work with, you're better off making something from the factory plugins shipped with the GIT source using my Makefile I posted above. Anyone who has the ability to copy the spinfinity(or solar or whatever) GIT plugin folder somewhere else on their drive, drop my makefile in there, and type "make" in a terminal is on their way to making their own plugin.

If anyone else wants to help out by making some 3D spinning variant logos similar to the one pictured in GDM, then feel free to submit something. The variants obviously dont have to look exactly the same as the ubuntu one but should be similar in nature.

> **DanaG said:**
> I've actually even tried it with a kernel built specifically with radeon KMS.... still no-go.  sudo plymouth --show-splash just makes the screen blink once... and then return right back to the terminal I was on.

Edit: oh, and I was able to confirm that kms itself was working... when I went back to usplash on it, *that* was running at native resolution -- and so was the console.
If you add plymouth:debug to your grub kernel line, you will get extra output possibly suggesting why it is failing or at what point.


EDIT: Simple 3D kubuntu model with no rendering. This is what we are looking for but variants and with nice texturing/rendering. I whipped this one up in about an hour. Surely there are others other than autocrosser that have some sort of Graphics/CAD/3D Modeling experience...I just can't really do many fancy rendering effects without bazillions of effort(mainly because I haven't done it in ages). Plus I'm supposed to be coding, not doing all the gfx :P

---

### Post by autocrosser on 2009-03-19
> **red_team316 said:**
> Oh yes, gears are the tell tale sign lol :) 

Sorry 'bout that--I am not the one to use KDE(I still liken Gnome to Mac OS 8.6--which I still have running on a mid-90's pizza box mac--very fond memories of the 8 series Mac OS)---but that is another story.........And true, once I get the basic artwork--changes are not too hard :)


Hmmm--I can see the gears turning--LOL (quite really you know--would be a fun effect)

---

### Post by red_team316 on 2009-03-19
> **autocrosser said:**
> Sorry 'bout that--I am not the one to use KDE(I still liken Gnome to Mac OS 8.6--which I still have running on a mid-90's pizza box mac--very fond memories of the 8 series Mac OS)---but that is another story.........And true, once I get the basic artwork--changes are not too hard :)


Hmmm--I can see the gears turning--LOL (quite really you know--would be a fun effect)

Can you work with these models? I don't know if Blender or something else could because I'm not real familiar it, but there are much better options for animating 3D models.

---

### Post by plun on 2009-03-19
> **autocrosser said:**
> Have you tried to add a vga to your kernel line?

also to set solar and rebuild the image

```

sudo plymouth-set-default-plugin solar

sudo dpkg-reconfigure linux-image-`uname -r`

``` 


I have it working but with a text mode interrupt in the end....but that seems to be in the higher division to solve....:confused:

---

### Post by Zorael on 2009-03-19
As for whether KDE uses gdm; no - KDE has its own **k**dm. Furthermore KDE 4 introduced a new (rewritten) version of kdm (like everything else).

Besides art, the theme .xml files look like this.
```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE greeter SYSTEM "greeter.dtd">
<!--
Copyright 2008 Urs Wolfer <uwolfer @ kde.org>
Copyright 2008 Oswald Buddenhagen <ossi @ kde.org>

This program is free software; you can redistribute it and/or
modify it under the terms of the GNU General Public License as
published by the Free Software Foundation; either version 2 of 
the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.
-->
<greeter id="theme">
	<style font="Sans 12" window-text-color="#C7C7C7"
	       base-color="#C7C7C7" alternate-base-color="#666666"
	       text-color="#000000" disabled-text-color="#808080"/>
	<item type="svg" id="background" background="true">
		<normal file="background.svg"/>
		<pos anchor="c" x="50%" y="50%" width="100%" height="100%"/>
	</item>

	<item type="rect" id="greeter">
		<pos y="50%" x="50%" anchor="c" width="box" height="box"/>

		<fixed>
			<item type="svg">
				<normal file="oxygen-box.svg" element="topleft"/>
				<pos anchor="nw" x="0" y="0" width="11" height="11"/>
			</item>
			<item type="svg">
				<normal file="oxygen-box.svg" element="top"/>
				<pos anchor="n" x="50%" y="0" width="-21" height="11"/>
			</item>
			<item type="svg">
				<normal file="oxygen-box.svg" element="topright"/>
				<pos anchor="ne" x="-0" y="0" width="11" height="11"/>
			</item>
			<item type="svg">
				<normal file="oxygen-box.svg" element="left"/>
				<pos anchor="w" x="0" y="50%" width="11" height="-21"/>
			</item>
			<item type="svg">
				<normal file="oxygen-box.svg" element="center"/>
				<pos anchor="c" x="50%" y="50%" width="-21" height="-21"/>
			</item>
			<item type="svg">
				<normal file="oxygen-box.svg" element="right"/>
				<pos anchor="e" x="-0" y="50%" width="11" height="-21"/>
			</item>
			<item type="svg">
				<normal file="oxygen-box.svg" element="bottomleft"/>
				<pos anchor="sw" x="0" y="-0" width="11" height="11"/>
			</item>
			<item type="svg">
				<normal file="oxygen-box.svg" element="bottom"/>
				<pos anchor="s" x="50%" y="-0" width="-21" height="11"/>
			</item>
			<item type="svg">
				<normal file="oxygen-box.svg" element="bottomright"/>
				<pos anchor="se" x="-0" y="-0" width="11" height="11"/>
			</item>
		</fixed>

		<box orientation="vertical" xpadding="15" ypadding="15" spacing="10">
			<item type="rect" id="banner">
				<pos width="box" height="box" min-width="100%"/>
				<box orientation="horizontal" spacing="10">
					<item type="label" id="welcome">
						<pos anchor="w" y="50%"/>
						<normal color="#8BAFBA" font="Sans 16"/>
						<stock type="welcome-label"/>
					</item>
					<item type="rect" id="spacer1">
						<pos expand="true"/>
					</item>
					<item type="pixmap" id="branding">
						<normal file="branding-icon.png"/>
					</item>
				</box>
			</item>
			<item type="rect" id="content">
				<pos width="box" height="box"/>
				<box orientation="horizontal" spacing="10">
					<item type="list" id="userlist">
						<pos max-height="30%^^"/>
					</item>
					<item type="rect" id="verify">
						<pos width="box" height="box"/>
						<box orientation="vertical" spacing="2">
							<item type="rect" id="talker">
								<pos anchor="n" x="50%" width="box" height="box"/>
								<box orientation="vertical" xpadding="2" ypadding="2" spacing="2">
									<item type="label">
										<pos x="5"/>
										<stock type="username-label"/>
									</item>
									<item type="entry" id="user-entry">
										<pos width="150" height="22"/>
									</item>
									<item type="label">
										<pos x="5"/>
										<stock type="password-label"/>
									</item>
									<item type="entry" id="pw-entry">
										<pos width="150" height="22"/>
									</item>
								</box>
							</item>
							<item type="rect" id="pam-error-placeholder">
								<pos width="100%" height="box"/>
								<box orientation="horizontal">
									<item type="label" id="dummy1">
										<normal alpha="0" font="Sans Bold 12"/>
										<text/>
									</item>
									<item type="label" id="pam-error">
										<pos anchor="c" x="50%" y="50%" expand="true"/>
										<normal color="#C7C7C7" font="Sans Bold 12"/>
										<text/>
									</item>
								</box>
							</item>
							<item type="label" id="caps-lock-warning">
								<normal color="#C7C7C7" font="Sans 12"/>
								<pos anchor="c" x="50%" y="50%"/>
								<stock type="caps-lock-warning"/>
							</item>
						</box>
					</item>
				</box>
			</item>
		</box>

	</item>

	<!-- bottom bar and session buttons -->
	<item type="rect" id="footer">
		<pos x="-0" y="-75" min-width="50%" width="box" height="43" anchor="e"/>
		<fixed>
			<item type="svg">
				<normal file="oxygen.svg" element="footer-background"/>
				<pos width="1980" height="43"/>
			</item>
		</fixed>
		<box orientation="horizontal" spacing="10" xpadding="10">
			<item type="rect" id="session_button" button="true">
				<pos y="50%" anchor="w" width="box" height="box"/>
				<box orientation="horizontal" spacing="10" xpadding="10">
					<item type="pixmap">
						<normal file="session.png" tint="#ffffff"/>
						<prelight file="session.png"/>
						<active file="session.png" tint="#ffffff"/>
						<pos y="50%" anchor="w"/>
					</item>
					<item type="label">
						<normal color="#C7C7C7" font="Sans 12"/>
						<prelight color="#ffffff" font="Sans 12"/>
						<active color="#666666" font="Sans 12"/>
						<pos y="50%" anchor="w"/>
						<stock type="session"/>
					</item>
				</box>
			</item>
			<item type="rect" id="system_button" button="true">
				<show modes="console" type="system"/>
				<pos y="50%" anchor="w" width="box" height="box"/>
				<box orientation="horizontal" spacing="10" xpadding="10">
					<item type="pixmap">
						<normal file="system.png" tint="#ffffff"/>
						<prelight file="system.png"/>
						<active file="system.png" tint="#ffffff"/>
						<pos y="50%" anchor="w"/>
					</item>
					<item type="label">
						<normal color="#C7C7C7" font="Sans 12"/>
						<prelight color="#ffffff" font="Sans 12"/>
						<active color="#666666" font="Sans 12"/>
						<pos y="50%" anchor="w"/>
						<stock type="system"/>
					</item>
				</box>
			</item>
			<item type="rect" id="spacer2">
				<pos expand="true"/>
			</item>
			<item type="label" id="clock">
				<pos anchor="w" y="50%"/>
				<normal font="Sans 12" color="#C7C7C7"/>
				<text>%c</text>
			</item>
			<item type="rect" id="spacer3">
				<pos width="15"/>
			</item>
		</box>
	</item>

	<item type="rect" id="timed-label">
		<pos anchor="c" x="50%" y="20%" width="box" height="box"/>
		<box orientation="vertical" xpadding="50" ypadding="5" spacing="0">
			<item type="label">
				<normal color="#C7C7C7" font="Sans 12"/>
				<pos x="50%" anchor="n"/>
				<stock type="timed-label"/>
			</item>
		</box>
	</item>

</greeter>
```
Extract the [kdm package](http://packages.ubuntu.com/jaunty/kdm[/url) for further perusal.

---

### Post by autocrosser on 2009-03-19
> **red_team316 said:**
> Can you work with these models? I don't know if Blender or something else could because I'm not real familiar it, but there are much better options for animating 3D models.

Blender & Wings3 can't--I'm going on a trip starting tonight, so I'll look into software next week....

---

### Post by DanaG on 2009-03-19
What formats *can* Blender (and such) open / import?  I have AutoCAD, so if need be, I can convert from dwg or dxf to whatever other formats AutoCAD happens to be able to export to.

---

### Post by autocrosser on 2009-03-19
> **DanaG said:**
> What formats *can* Blender (and such) open / import?  I have AutoCAD, so if need be, I can convert from dwg or dxf to whatever other formats AutoCAD happens to be able to export to.


Well--Wings 3D can work with Adobe Illustrator 8 (AI), Wavefront (OBJ), 3D Studio (3DS) & Nendo (NDO).

Blender--3D Studio, AC3D, COLLADA, FBX Export, Wavefront OBJ, DEC Object File Format, DirectX, Lightwave, MD2, Motion Capture, Nendo, OpenFlight, PLY, Pro Engineer, Radiosity, Raw Triangle, Softimage, STL, TrueSpace, VideoScape, VRML, VRML97, X3D Extensible 3D, xfig export--It is saying that it can work with DXF files, but that only causes an error--so It really needs another format.

I really don't have a preference as long as I can open it & work with it........

---

### Post by red_team316 on 2009-03-20
> **autocrosser said:**
> Well--Wings 3D can work with Adobe Illustrator 8 (AI), Wavefront (OBJ), 3D Studio (3DS) & Nendo (NDO).

Blender--3D Studio, AC3D, COLLADA, FBX Export, Wavefront OBJ, DEC Object File Format, DirectX, Lightwave, MD2, Motion Capture, Nendo, OpenFlight, PLY, Pro Engineer, Radiosity, Raw Triangle, Softimage, STL, TrueSpace, VideoScape, VRML, VRML97, X3D Extensible 3D, xfig export--It is saying that it can work with DXF files, but that only causes an error--so It really needs another format.

I really don't have a preference as long as I can open it & work with it........

Attached is a .3DS, hopefully that will work. Not sure what all the options for export needed to be but DanaG may be able to help out there if this doesn't work.


> **Zorael said:**
> As for whether KDE uses gdm; no - KDE has its own **k**dm. Furthermore KDE 4 introduced a new (rewritten) version of kdm (like everything else).
Hopefully GDM/KDM themes are compatible now then. That was my biggest concern with kdm in the past is that a gdm or kdm theme wouldn't work vice versa.

[quote=plun]
I have it working but with a text mode interrupt in the end....but that seems to be in the higher division to solve....
[/quote]
autocrosser and I have been experiencing the same thing. It may have to do with that ubuntu doesn't completely have wrappered some usplash stuff or NVIDIA issues. I think this is probably more a ubuntu issue at this point as plymouth has to be integrated with the bootup process.

---

### Post by DanaG on 2009-03-20
I booted with plymouth:debug, and it seems to be insisting on loading the details.so plugin specifically, instead of loading the default.so, which is a symlink to solar.so.

---

### Post by autocrosser on 2009-03-20
Well--I can get both Blender & Wings3D to see the file--have to do some reading to start editing---am leaving at 5:30am tomorrow for Portland--I'll keep in touch & will be able to start work Monday evening--Wife & I needed to take a break in a larger city.....

---

### Post by andrek on 2009-03-28
Any progress in the new theme?

---

### Post by autocrosser on 2009-03-29
Nothing to write about quite yet--red_team just set-up a new computer, so he has been involved there & I had a very hard week :( --I promise to get back to it tomorrow....

---

### Post by Milos_SD on 2009-03-30
How can I make this work on Nvidia? I compiled 2.6.29 kernel. Do I need to enable some option in it for this to work?

---

### Post by autocrosser on 2009-03-30
As there is no kernel mode setting for nvidia---you need to add the vga for your screen size--I'm running 1920x1200, so my kernel line looks like: 
/boot/vmlinuz-2.6.28-11-generic root=UUID=fc1446a5-94e9-40f8-9ebb-2442107fc13c ro quiet splash concurrency=shell vga=893

You just need to get the number for your screen for it to work......

---

### Post by Milos_SD on 2009-03-31
I tryed that with vga=ask and then selecting my resolution, but all I get is a black screen all the way before GDM starts.

---

### Post by autocrosser on 2009-03-31
I just tried the 2.6.29 kernel (ubuntu kernel tree) & I just get black screen also--I'll check into it---

---

### Post by MacUntu on 2009-04-01
> **autocrosser said:**
> I just tried the 2.6.29 kernel (ubuntu kernel tree) & I just get black screen also--I'll check into it---

Here too.

Working

# CONFIG_DRM is not set

Not working

CONFIG_DRM=m
CONFIG_DRM...=m
...
...
CONFIG_DRM...=m

---

### Post by plun on 2009-04-03
> **MacUntu said:**
> Here too.

Working

# CONFIG_DRM is not set

Not working

CONFIG_DRM=m
CONFIG_DRM...=m
...
...
CONFIG_DRM...=m

Hmmm...:confused:

```
# Graphics support
#
CONFIG_AGP=y
CONFIG_AGP_AMD64=y
CONFIG_AGP_INTEL=m
CONFIG_AGP_SIS=m
CONFIG_AGP_VIA=m
**# CONFIG_DRM is not set**
CONFIG_VGASTATE=m
CONFIG_VIDEO_OUTPUT_CONTROL=m
CONFIG_FB=y
CONFIG_FIRMWARE_EDID=y
CONFIG_FB_DDC=m
CONFIG_FB_BOOT_VESA_SUPPORT=y
CONFIG_FB_CFB_FILLRECT=y
CONFIG_FB_CFB_COPYAREA=y
CONFIG_FB_CFB_IMAGEBLIT=y
```

Complete black with **Kernel 2.6.29.1** which is out since last night.

(180.44 as nVidia driver.)

---

### Post by red_team316 on 2009-04-03
Plun, Whats the difference between 2.6.28-9 and 2.6.29-1? I'm not sure where that output is coming from or I'd look.

---

### Post by plun on 2009-04-05
> **red_team316 said:**
> Plun, Whats the difference between 2.6.28-9 and 2.6.29-1? I'm not sure where that output is coming from or I'd look.

OK... the output comes from kernel config files within the /boot directory.

Maybe its possible to use an diff application and find out config diffs ??

But... soon the koala starts, its better to wait a few weeks and then go on with Plymouth..;)

---

### Post by MacUntu on 2009-04-05
:idea::
28:
CONFIG_FB_VESA=m
29 (mainline):
# CONFIG_FB_VESA is not set

---

### Post by plun on 2009-04-05
> **MacUntu said:**
> :idea::
28:
CONFIG_FB_VESA=m
29 (mainline):
# CONFIG_FB_VESA is not set

Success.... thanks !  ;)

```
# **Frame buffer hardware drivers**
#
CONFIG_FB_CIRRUS=m
CONFIG_FB_PM2=m
CONFIG_FB_PM2_FIFO_DISCONNECT=y
CONFIG_FB_CYBER2000=m
CONFIG_FB_ARC=m
CONFIG_FB_ASILIANT=y
CONFIG_FB_IMSTT=y
CONFIG_FB_VGA16=m
[B]CONFIG_FB_UVESA=y
CONFIG_FB_VESA=y[/B]
CONFIG_FB_EFI=y
CONFIG_FB_N411=m
CONFIG_FB_HGA=m
# CONFIG_FB_HGA_ACCEL is not set
```

Next challenge again....  Fix the slow gnome login....):P

---

### Post by artir on 2009-04-18
Has somebody managed to get it working on virtualbox?
I've tried with 2.29, 2.29.1 and 2.30-rc and different vga options and I can only get a black screen.
If you did it, post how.

Thanks.

---

