---
title: "desktopeffects dead"
date: 2010-01-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ronacc on 2010-01-08
after todays PM update desktop effects will not enable , >system>appearence>effects fails with this error .

```
ron@ron-desktop2:~$ gnome-appearance-properties %F

(gnome-appearance-properties:7702): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

There is no available graphics driver for your system which supports the composite extension, or the current one already supports it.

compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager

(gnome-appearance-properties:7702): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
```

I do have nvidia 195.22 installed and it is running according to nvidia-settings .

---

### Post by darco on 2010-01-08
I have the same driver except its patched for the ..33 kernel. I too lost desktop effects. I uninstalled then reinstalled the drivers and all is well.


darco

---

### Post by paul_in_london on 2010-01-08
Same here. Looked at my compiz setttings earlier and they seemed to be intact. Until I saw this thread, though, I hadn't thought to check **Appearance Preferences** -> **Visual Effects** to see whether **Extra** was still enabled.

When I tried to do this via the command line I got:

```
paul@lucid:~$ gnome-appearance-properties %F
Gtk-Message: Failed to load module "pk-gtk-module": libpk-gtk-module.so: cannot open shared object file: No such file or directory
Gtk-Message: Failed to load module "pk-gtk-module": libpk-gtk-module.so: cannot open shared object file: No such file or directory

(gnome-appearance-properties:7685): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:7686): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Gtk-Message: Failed to load module "pk-gtk-module": libpk-gtk-module.so: cannot open shared object file: No such file or directory
There is not a graphics driver available for your system which supports the composite extension, or the current driver already supports it.
compiz (core) - Fatal: Software rendering detected.
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager
Gtk-Message: Failed to load module "pk-gtk-module": libpk-gtk-module.so: cannot open shared object file: No such file or directory

(gnome-appearance-properties:7685): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:7685): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:7685): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:7685): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:7685): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:7685): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:7685): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:7685): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:7685): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:7685): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:7685): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:7685): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:7685): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:7685): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:7685): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:7685): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:7685): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:7685): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:7685): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:7685): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:7685): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:7685): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:7685): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:7685): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:7685): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:7685): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:7685): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:7685): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:7685): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:7685): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
Gtk-Message: Failed to load module "pk-gtk-module": libpk-gtk-module.so: cannot open shared object file: No such file or directory
paul@lucid:~$ 

```


NVIDIA 8800GT graphics card.

Using 2.6.33-020633rc3-generic and (according to NVIDIA X Server Settings) the 195.30 driver is loaded.

EDIT: I had to patch the 195.30 driver before I could use it with the 2.6.33 ppa kernel. Maybe I'll try reinstalling the driver as **darco **suggests...

---

### Post by paul_in_london on 2010-01-08
Ok, reinstalled the 195.30 driver, then was able to select **Extra** from **Appearance Preferences** -> **Visual Effects** without getting the previous errors.

Once I'd done that, I still had to reselect the compiz options I wanted, but it's all back to normal again now... :)

---

### Post by ronacc on 2010-01-08
I'm still on 32-9 with 195.22 , I removed and reinstalled the 195.22 driver and rebooted . No help still cannot enable effects . I don't see the 195.30 driver in synaptic , are you using the one from nvidia directly and if so do you know if patching is required for the .32-x kernel ?

---

### Post by paul_in_london on 2010-01-08
@ronacc

I have the sevenmachines nvidia ppa enabled, but when I upgrade, I've had this for quite a while:

```
The following packages have been kept back:
  nvidia-195-libvdpau{a}
```

so I used the nvidia installer to install 195.30 with 2.6.33-020633rc3 and earlier versions of that kernel. See **plun**'s post on this page about patching it:

[http://ubuntuforums.org/showthread.php?t=1358346&page=8](http://ubuntuforums.org/showthread.php?t=1358346&page=8)

Can't remember if a patch was needed for 2.6.32-x. Don't think so, but not 100% sure!

---

### Post by ronacc on 2010-01-08
from the looks of things that patch is for  the 2.6.33 kernel . I'll just suffer through without rotating the cube until the next update fixes it, atleast those godawful wobbly windows are dead too:lolflag: and the 195.22 driver is running so I have got my full 1920x108 display .

---

### Post by paul_in_london on 2010-01-08
FWIW, I've just booted from 2.6.32-9-generic to try it out (I have this set up in grub as my "previous" kernel) and I've still got my compiz cube etc. without explicitly reinstalling 195.30 on this kernel!

---

### Post by steveneddy on 2010-01-08
> **ronacc said:**
> atleast those godawful wobbly windows are dead too

You know you can turn off wobbly windows......

---

### Post by ranch hand on 2010-01-08
Well, i can say that after updating the desktop effects on my "edgers" install are once again at "extra" and the wobbly windows is turned off.

ATI card actually helped today.  Wow.

---

### Post by ronacc on 2010-01-08
how? I couldn't find out where to switch it off in metacity , It could be switched off in compiz .
I added alberto's PPA and reverted to 190.53 and have effects back and compiz is working again I'll try the 195.3 with patch if things go bad again .

---

### Post by cariboo on 2010-01-08
I just downgraded to 190.53 from Nvidia, and have desktop affects back. I like wobbly windows. :)

---

### Post by mc4man on 2010-01-08
I would think  that updated lucid packages will be showing up shortly, myself plan to do a fresh A2 install next week w/ no ppa's

[https://bugs.launchpad.net/ubuntu/lucid/+source/nvidia-graphics-drivers-180/+bug/494166](https://bugs.launchpad.net/ubuntu/lucid/+source/nvidia-graphics-drivers-180/+bug/494166)

---

### Post by ranch hand on 2010-01-09
> **ronacc said:**
> how? I couldn't find out where to switch it off in metacity , It could be switched off in compiz .
I added alberto's PPA and reverted to 190.53 and have effects back and compiz is working again I'll try the 195.3 with patch if things go bad again .
I updated, I am running that OS with the xorg.edgers ppa and their driver (ATI) and xorg version.  For a couple of days the effects were set back to "none".

After updating my three sacrificial OS' I booted to them and the "edgers" OS had the effects back to normal and unchecking the floppy windows option in the compiz control actually worked and turned the nasty buggers off.

Probably all go up the tubes tomorrow.

---

### Post by LKjell on 2010-01-09
The strange thing is I have direct rendering but wine games does not pick it up.

---

### Post by Darkshade on 2010-01-09
I was stuck with Metacity for a bunch of hours, purged every nvidia-related package, removed the sevenmachines ppa, installed the drivers shipped with ubuntu, purged again, rebooted a few times in between to see if it worked but nothing. Installed nvidia-185 again, didn't work, got tired, turned off the pc, played some guitar, turned it on again and now for some reason it's working although nvidia-settings says I have 190.53 (I could swear I installed 185). Now I'm somehow confused but happy, I'm not rebooting again in the next few days, too scared it might go away and drag me back to [s]metacity[/s] hell.

---

### Post by darco on 2010-01-09
> **Darkshade said:**
> I was stuck with Metacity for a bunch of hours, purged every nvidia-related package, removed the sevenmachines ppa, installed the drivers shipped with ubuntu, purged again, rebooted a few times in between to see if it worked but nothing. Installed nvidia-185 again, didn't work, got tired, turned off the pc, played some guitar, turned it on again and now for some reason it's working although nvidia-settings says I have 190.53 (I could swear I installed 185). Now I'm somehow confused but happy, I'm not rebooting again in the next few days, too scared it might go away and drag me back to [s]metacity[/s] hell.

was it gospel you played before rebooting?

---

### Post by Darkshade on 2010-01-09
> **darco said:**
> was it gospel you played before rebooting?

Haha no, but I'm starting to wonder how would that sound with my usual setup :D

---

### Post by paul_in_london on 2010-01-09
Compiz is gone again for me, but I haven't bothered reinstalling the 195.30 driver yet.

---

### Post by ronacc on 2010-01-09
the updates are coming thick and fast ahead of A2 I wouldn't bother with a reinstall of anything until A2 is out just update normaly .

---

### Post by paul_in_london on 2010-01-09
> **ronacc said:**
> the updates are coming thick and fast ahead of A2 I wouldn't bother with a reinstall of anything until A2 is out just update normaly .

I know what you mean. The nvidia driver "is" installed as far as NVIDIA X Server settings is concerned and also:

```
$ modprobe -l nvidia
kernel/drivers/video/nvidia.ko
```

but I can't enable compiz without "reinstalling" it (which I still haven't done)!

---

### Post by k64 on 2010-01-09
Will Desktop Effects die with an ATI card? I would like to know, since I have one.

---

### Post by mc4man on 2010-01-09
While my current install that's using the proprietary-video-improvements PPA works fine i'd did notice something

While doing re-builds of vlc 1.1 and 1.0.4, which previously were successful, they now failed on -lGL

At least here there is a broken link in /usr/lib ,"libGL.so", due to the new location of libGL.so* - /usr/lib/mesa (from the libgl1-mesa-dev package

Removing and creating a new link has resolved the vlc builds - whether that also is a factor for using drivers other than the above mentioned , I don't know...

Overall I think things will be squared away shortly anyway

edit:
while I use xv for vlc to show how things are now working right 
> [0x9c96f48] main generic debug: using opengl provider module "glx"
[0x9c96f48] main generic debug: TIMER module_need() : 381.862 ms - Total 381.862 ms / 1 intvls (Avg 381.862 ms)
[0x9bc4c58] main video output debug: using video output module "opengl"



A new update to libgl1-mesa-dev has fixed the .pc file and now links properly

---

### Post by ranch hand on 2010-01-09
> **k64 said:**
> Will Desktop Effects die with an ATI card? I would like to know, since I have one.
That is very hard to say.  They do not work with my Radeon HD 2400 PRO but they have never worked with that card on any version (Hardy>Lucid and several other Linux distros).

They do work, somewhat, with the stuff from the xorg.edgers ppa with my card.

Good luck.

---

### Post by plun on 2010-01-10
Compiz-check give me this on my laptop

```
plun@plun-laptop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc M22 [Mobility Radeon X300]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems..../compiz-check: line 488: [: 3746: binary operator expected
           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use 

```

Broke after latest mesa package update.

About Compiz-check
[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

--

---

### Post by mc4man on 2010-01-10
While obviously with nvidia I'm not having any current compiz issues and also don't particularly need opengl output for video.

But from a build perspective ( and considering some would need gl output) the last update does still present some problems with enabling opengl output.
While there's no issue with libGL.*,  the update also moved the libGLU.*'s into /usr/lib/mesa which is causing some problems. ( whether that would affect ati drivers I don't know
 
Unfortunately didn't pay close enough attention or save any build logs. or ldd results so have reverted back to the [ubuntu1]("https://launchpad.net/ubuntu/lucid/+source/mesa/7.7-0ubuntu1") builds to log some builds, ldd's and then update and see what the difference is.

(Maybe the libGLU.*'s were better off in /usr/lib or possibly this will sort itself out soon.

---

### Post by terry_gardener on 2010-01-10
after todays updates i also lost all compiz fusion and when checking glxinfo it wasn't loaded.

after reading the above posts.

i backed up the usr/lib/mesa folder and then copied the libgl.so, libgl.so.1, libgl.so.190.53, libglcore.so.1 and libglcore.so.190.53 into the mesa folder and replaced the files already in there. 

rebooted and i now have glx loaded and therefore can have compix loaded. 

screenshot of mesa folder now.

---

### Post by endemoniada on 2010-01-13
I`ve had no Compiz for a few days now a ./compiz-check gives me
> ade@laptop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation C51 [GeForce Go 6100] (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size

and glxinfo gives me
> ade@laptop:~$ glxinfo
name of display: :0.0
Error: couldn't find RGB GLX visual or fbconfig

ade@laptop:~$ 


Also in Jockey-gtk it says the nvidia driver is activated but not in use

The driver that is installed is 190.53-0ubuntu4

I`ve tried several times to purge & reinstall all things Nvidia related but to no avail,

Anybody got any suggestions on what else I can try

Thanks

---

### Post by ranch hand on 2010-01-13
They are not dead on my box.  At least not dead enough for comfort.

I do have the woblly windows shut down and it sticks.  The stupid sliding from one workstation to the next "works" (this, of coarse means I can't drag stuff from one workstation to another).

Seeing as I do not ever use this crap I thought I would see about it.  I never heard of this command for instance:
```

ike@iso-desktop:~$ ./compiz-check
bash: ./compiz-check: No such file or directory

```
but the box hasn't either so I guess that is all right.  Is this a nvidia thing or should it exist on my ATI box?

As far as the "glxinfo" goes, I have pages of it, a good bit of that means nothing to me but it is there.  There seems to be support for a lot of drivers and brands.

---

### Post by endemoniada on 2010-01-13
To install Compiz Check, in a Terminal window do

> wget [http://blogage.de/files/9124/download](http://blogage.de/files/9124/download) -O compiz-check


followed by

> chmod +x compiz-check


and finally
> ./compiz-check
 to run

About Compiz-check
[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

---

### Post by mc4man on 2010-01-13
> The stupid sliding from one workstation to the next "works" (this, of coarse means I can't drag stuff from one workstation to another).

The only 'effect' I ever use is the 'desktop cube' and "rotate cube', though not with the cube effect as seen [here]("http://ubuntuforums.org/showthread.php?p=8660492#post8660492")

Simply just to drag windows to a new desktops and by enabling 'Desktop-based viewpoint switching' be able flip to a different desktop with the scroll wheel and on a laptop the scroll area

find it invaluable

(desktop scrolling was disabled by default in karmic because it was thought to be too hard to control on laptops and some would inadvertanly switch desktops while intending something else, the fact is the default duration or acceleration was set to low for laptops and even desktops

---

### Post by dagrump on 2010-01-13
Ranch hand my box gives the same response as yours. I checked I can enable effects, of course I promptly turn them off. I am using the nvidia drivers from the repos.
I do know I can't run games as they throw a error, of course if I really wanted to run a game a could add the sym-links that are in another post. I think I'll just wait & see if it works itself out.
I don't really play games very much, of course that is because I suck at it.

Edit: well missed a few posts there. That's why I have no compiz-check, oh well...

---

### Post by ranch hand on 2010-01-13
Well this is all very interesting.  I will be over on that installs some time tomorrow and see what this is all about.

I do not use any effects on any of my "work" installs as they get on my thungas.  I normally run 6 workstations with set things that run on each.  I like it that way.

Seeing how many folks just go ape if they can't do this stuff I thought I would get the xorg-edgers stuff and see if it would actually work on my box.  I do not think it will.  My  ATI card is not well supported.

As we are in testing and I have too many installs they have to be doing something.  That one is good at irritating me do to the effects being enabled but I do not have to spend much time there.

I installed the Compiz Check stuff just now in a chroot but can't run it that way.  Needs to be run without being "root".  So tomorrow.  I can stand that crap for about 45 minutes max but that is plenty for this purpose.

Thanks a bunch for the info and help.

It struck me when reading about this on the link that there used to be a check like that in compiz manager (Hardy).  I ran it to see what the deal was and got all kinds of reasons why it would not work on this box.  I wonder why it needs to be supplied from out side now.

I also wonder if things have changed much since then.  Tomorrow I will see that too.

---

### Post by ranch hand on 2010-01-14
Geeze, I think the bugger is supposed to be able to run on here.  There must be a problem with compiz or the edgers drivers or something.

At least I think so from;
```

ike@iso-desktop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV610 video device [Radeon HD 2400 PRO]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```
Wobbly windows was back on this morning.  Settings that do work just do not stick.

Effects set in System>Prefrences>Appearance were set to normal rather than extra too.

Well thanks for your help with my education.

I have to change a desktop icon here and get out of this weird environment and back to the land of no effects to sooth my eyes and brain.

---

### Post by ronacc on 2010-01-14
I get that loss of settings sometimes too on Nvidia , its like when there is an update to gfx or compiz it resets to defaults .Also some settings disapeared from ccsm for awhile now they are back .Thats on my upgraded lucid install , I still haven't got my A2 test install to boot , I get "you need to load the kernel first " no mater what I do . Its on that IDE slave drive I was having problems with originaly .

---

### Post by ranch hand on 2010-01-14
A2 will be out sometime today, not yet.

I just updated a couple of installs and got some x updates.  May want to check that too.

You may want to check the uuid on that install too.

Did you format that with both drives "on"?  I am all SATA here but I can't boot to anywhere from my main drive (except to the installs on it) as it was "off" when the other 2 drives were formatted and there are uuid conflicts (I believe there is more to it than that but I am not knowledgeable enough to really know).

---

### Post by ronacc on 2010-01-14
uuid is ok and no conflicts , also have tried other methods including installing grub to the root partition rather than the MBR , same result .tried with no grub and boot from another install , same result , There dont seem to be any problems with the install , I can chroot in and everything works .I replaced the initrd and vmlinuz with ones from my working install ( the same -# of course ) . I'll try A2 but I don't expect any difference , it's been this way since grub2 started . I had karmic before grub2 on that drive but after grub2 started I haven't been able to get a booting install on it .

---

### Post by VMC on 2010-01-14
> **ronacc said:**
> uuid is ok and no conflicts , also have tried other methods including installing grub to the root partition rather than the MBR , same result .tried with no grub and boot from another install , same result , There dont seem to be any problems with the install , I can chroot in and everything works .I replaced the initrd and vmlinuz with ones from my working install ( the same -# of course ) . I'll try A2 but I don't expect any difference , it's been this way since grub2 started . I had karmic before grub2 on that drive but after grub2 started I haven't been able to get a booting install on it .

I went back and re-read the posts. How did grub come into the picture. After boot-up, grubs out of the picture. Unless of course it delivers some argument on the linux line.
To test the uuid theory, do a df and see if your mounted partition matches up.

---

### Post by ronacc on 2010-01-14
grub comes into the picture because as soon as you hit return at the boot line in grub to boot that partition or let it start on its own if booting from the mbr you get that it "you need to load the kernel first" message . there are a couple of other threads around about this happening and also googeling on it brings up a few  problems with the same thing on fedora .got to head off to work right now .

---

### Post by ranch hand on 2010-01-14
I am not sure how this works on ide but I would use the one on the slave drive for boot/root and install grub on that mbr and then install it on the master drive mbr and make sure that I was booting from the master drive.  This would  work on a SATA system but that is all I know.

---

### Post by VMC on 2010-01-14
> **ronacc said:**
> grub comes into the picture because as soon as you hit return at the boot line in grub to boot that partition or let it start on its own if booting from the mbr you get that it "you need to load the kernel first" message . there are a couple of other threads around about this happening and also googeling on it brings up a few  problems with the same thing on fedora .got to head off to work right now .

This is all true, but where did this "you need to load the kernel first" come up on this topic? I must be losing it, I re-read again and no mention.

Regardless, it would be nice to see the output of that "[boot-info-script]("http://sourceforge.net/projects/bootinfoscript/files/")". BTW, there is a new version - 48, if you haven't updated.

---

### Post by ronacc on 2010-01-14
I just mentioned it in passing ( see post 35) and then ranchhand responded to it and things just kind of ran on from there .

---

### Post by VMC on 2010-01-14
> **ronacc said:**
> I just mentioned it in passing ( see post 35) and then ranchhand responded to it and things just kind of ran on from there .

Yes, your right - #35. My eyesight is not what it use to be...

---

### Post by mc4man on 2010-01-15
You could keep in mind that ccsm is useful to make adjustments to compiz itself, nothing to do with 'effects'.
There are several settings that can improve the quality of your display/video playback ect., plus some default things can can be turned off, workarounds that can be enabled and or disabled.

None of this has much to do with desktop 'effects' per se.

While I do use the scroll on desktop/cube, anything else I can remove that doesn't have a negitive effect I do, plus there are a few display settings and workarounds that are positive.

Generally speaking in a 'for real' install never do go into Appearance -> Effects, just leaving it blank.

---

### Post by ranch hand on 2010-01-15
Compiz depends on the ability of the box to support effects.  Up until now mine would not, nor would it support compiz.

That is the point of the effects.

Frankly I would rather have the effects enabled and no compiz.  What I really like is no effects and no compiz.

We are in testing, however, and you have to check some things that are repugnant.

Gnome games, for instance, are actually installed  on all my 10.04 versions.  They sure are not wasting space on any of my other OS'.

Software Center is on all 10.04 versions too.  It and Add/Remove can and will/have been removed on all other OS' as being just too silly to believe.

Back to effects, if you are using metacity and want good 3d support there you need the effects.  There are those of us that have no taste and do not think compiz is anything but an irritant when actually using a computer.

---

### Post by jerrylamos on 2010-01-15
Desktop effects??

I do Full Screen internet, Full Screen word processing, Full Screen spreadsheets, Full Screen digital photography - 

And guess what!  I'll bet all that fancy "desktop effects" code is getting in the way just to find out there's nothing to do - just slowing me down!

LXDE desktop is faster and fine, but I do miss Screenshot.

That's the thing about Ubuntu, if I want to do lots of fancy desktop effects at a s-l-o-w rate, crank up KoolDesktopEnvironment KDE.  Want faster?  do LXDE.  Want lots of function?  Do Gnome.  All is just a login away....

So pile the desktop effects on KDE, thank you, give me function on Gnome, and give me speed with LXDE.

Cheers, Jerry

---

### Post by ranch hand on 2010-01-15
Hey jerry
You can install "screen shot" just fine under lxde.  Works fine.

---

