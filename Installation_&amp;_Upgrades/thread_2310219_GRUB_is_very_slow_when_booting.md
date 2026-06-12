---
title: "GRUB is very slow when booting"
date: 2016-01-17
forum: Installation &amp; Upgrades
---

### Post by Steam. on 2016-01-17
When my PC boots, the grub menu is like a slide show.Goes up, then down, then up again to list all the options, the screen update is so slow, even the keypresses respond after a second or two.I don't know what to do, resolution in grub is 640x480, my monitor's default res should be 1920x1080, I have a GTX 760. It is very annoying as I tend to waste an extra 20 seconds scrolling through the options.

---

### Post by grahammechanical on 2016-01-17
Remember, the Grub menu is loaded before Linux is loaded and therefore before a video driver is loaded. Grub is using the default screen resolution set by the motherboard. And that motherboard setting is designed to be compatible with any monitor attached to the motherboard. Grub does not know the default resolution of the monitor and Grub does not care that it does not know.

It is possible to change the size of the text used in the Grub boot menu to make it smaller. But this is really a side issue. Is it not?

When you enter the motherboard boot system settings utility (UEFI) does it behave as it should? Or is screen update also slow? And the key presses slow to respond?

Regards.

---

### Post by ajgreeny on 2016-01-17
How many options in the grub menu do you get?

Normally there will not be many showing on the grub menu screen as it now uses a separate menu page for the Advanced options, ie, all the older kernels on the system that would not normally be needed when booting.

Lets see the output of terminal command ```
dpkg -l linux-image*
```

---

### Post by Steam. on 2016-01-17
> **ajgreeny said:**
> How many options in the grub menu do you get?

Normally there will not be many showing on the grub menu screen as it now uses a separate menu page for the Advanced options, ie, all the older kernels on the system that would not normally be needed when booting.

Lets see the output of terminal command ```
dpkg -l linux-image*
```


```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  linux-image    <none>       <none>       (no description available)
un  linux-image-3. <none>       <none>       (no description available)
ii  linux-image-4. 4.2.0-16.19  amd64        Linux kernel image for version 4.
ii  linux-image-ex 4.2.0-16.19  amd64        Linux kernel extra modules for ve

```

I also have my windows options, as I dualboot linux and Windows, below the ubuntu options. Also I do not have a UEFI board, for the guy above. MSI X58 PRO-E here. And the BIOS is swift. It does not do this when I use the windows bootloader per se, or anything else. Just grub. It is not supposed to be like that, is all I know. I've had older versions of Ubuntu installed wayyy before, and it didn't go this slow. It is literally a slideshow.

---

### Post by oldfred on 2016-01-18
Have you installed the nVidia proprietary driver, from repository?

And check available video modes with vbeinfo (only in grub)?
 From a grub command line to see available settings pressing <c> & escape to get back to menu
vbeinfo

Grub tries now to use screen size settings from Ubuntu installer.
But, you can set a fixed size, best to change to your correct size if availabe per vbeinfo:

 Use command line editor grub's on set gfxmode=640x480
and just remove the # as that makes that line a comment.
sudo nano /etc/default/grub
or
gksu gedit /etc/default/grub
# then 
sudo update-grub


 Details on settings in /etc/default/grub
 info -f grub -n 'Simple configuration'
> `GRUB_GFXMODE'
     Set the resolution used on the `gfxterm' graphical terminal.  Note
     that you can only use modes which your graphics card supports via
     VESA BIOS Extensions (VBE), so for example native LCD panel
     resolutions may not be available.  The default is `auto', which
     tries to select a preferred resolution.  *Note gfxmode::.


---

### Post by Steam. on 2016-01-19
> **oldfred said:**
> Have you installed the nVidia proprietary driver, from repository?

And check available video modes with vbeinfo (only in grub)?
 From a grub command line to see available settings pressing <c> & escape to get back to menu
vbeinfo

Grub tries now to use screen size settings from Ubuntu installer.
But, you can set a fixed size, best to change to your correct size if availabe per vbeinfo:

 Use command line editor grub's on set gfxmode=640x480
and just remove the # as that makes that line a comment.
sudo nano /etc/default/grub
or
gksu gedit /etc/default/grub
# then 
sudo update-grub


 Details on settings in /etc/default/grub
 info -f grub -n 'Simple configuration'

I've set it now to 1920x1080x32, but it still is the same thing.As my english isn't the best, I can't exactly google for what I want to tell you, and [this thread here ]("http://forums.linuxmint.com/viewtopic.php?f=46&t=195567")describes the guy having the same thing, screen clearing from bottom to top. Also I am using this driver, as gaming performance is best with it.

[IMG]http://i.imgur.com/v7f4eos.png[/IMG]

---

### Post by oldfred on 2016-01-20
That looks like it should be a good nVidia driver.
Did you only install that one?
And did you check while rebooting and grub command line vbeinfo?

---

