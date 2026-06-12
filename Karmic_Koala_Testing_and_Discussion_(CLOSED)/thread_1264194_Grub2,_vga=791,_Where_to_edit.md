---
title: "Grub2, vga=791, Where to edit?"
date: 2009-09-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by blakamin on 2009-09-11
Just been playing with my new install and am having the same problems I had in 9.04 with the graphics glitch on shutdown. The old cure was to add *vga=791* to my menu.lst.
Where would I add this in grub2? Had a quick look at the wiki, but it's not giving me any joy... I "could" edit the grub.cfg file, but it looks like this is a big no-no.
Any help?


EDIT: **SOLVED** see [HERE]("http://ubuntuforums.org/showpost.php?p=8024427&postcount=17")

---

### Post by kerry_s on 2009-09-11
**gksudo gedit /etc/default/grub**

the line that has ="quiet", make it "quiet vga=791"

then you have to run> **sudo update-grub** <in a terminal

---

### Post by blakamin on 2009-09-11
Thanks kerry_s, that sort of did the trick, but a quick message flashed up... will investigate what that was further. pretty sure it was "vga=791 is depreciated, use...."
Sorta takes time to debug as it requires 2 reboots to get the result!

---

### Post by blakamin on 2009-09-12
ok, vga=791 is depreciated so I need to find how to enter "set gfxpayload=1024x768x16"
Where abouts does this happen? I can see the result in grub.cfg but where do I enter it in /etc/default

EDIT:
Nevermind, according to [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=536453]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=536453") this isn't supported

Not a good look for the masses:confused:

EDIT AGAIN: even editing the grub.cfg doesn't work.

---

### Post by dino99 on 2009-09-12
in /etc/default/grub

add this line if you don't have it :

GRUB_CMDLINE_LINUX  gfxpayload=true


that's all

---

### Post by VMC on 2009-09-12
How were you able to read grub2 output error message? I knew something was wrong. "depreciated" flashed across my screen. Is thee a way to output grub2 error messages or at least see them.

---

### Post by blakamin on 2009-09-12
I actually just rebooted and saw the "use gfxpayload" and googled that!
And, so far, nothing has worked.

---

### Post by MKdx on 2009-09-12
If you mean cl resolution, then try adding
```
GRUB_GFXMODE=1024x768
```
to /etc/default/grub, and update it.

I had flickering issue on startup and shutdown, but I fixed this with xorg.conf.

---

### Post by jerrylamos on 2009-09-12
What I do when karmic is being cranky like lately on my two intel video graphics pc's is e the desired boot image, replace "splash" with "nomodeset single" at the end of the linux line.

The default for many video graphics is the new modeset=1 which doesn't work on lots of pc's.  Like on my two intel and one of my ati pc's. 

The "single" means it should boot eventually to a recovery mode menu.   

Select root prompt and do:

nano /etc/X11/xorg.conf
Section "Device"
Identifier      "Configured Video Device"
Driver  "vesa"
EndSection

Ctrl-o
enter
ctrl-x

resume boot

"vesa" works on a bunch of pc's but not all.  It used to be slower than the default drivers; on my pc's the new default drivers with modeset=1 and "acceleration" are slower so far.  Apparently not all the "acceleration" code is debugged.

If it does indeed boot, then to make this configuration permanent maybe:
sudo gedit /etc/default/grub
edit "quiet" to "quiet nomodeset"
save

sudo update-grub

cross your fingers & reboot....

Jerry

---

### Post by VMC on 2009-09-13
Ok a got a fix on this. I followed this [**LP**]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/416772") bug and post#2. Added "gfxpayload=1024x768" to 10_linux. After update-grub everything back to normal.

---

### Post by khughitt on 2009-09-15
I just found this post which was very helpful:

[http://harrison3001.blogspot.com/2009/09/grub-2-graphical-boot-tips-to-set.html](http://harrison3001.blogspot.com/2009/09/grub-2-graphical-boot-tips-to-set.html)

Basically, there are three steps:

1. Edit /etc/default/grub and change:

    ```
GRUB_GFXMODE=1280x800
```

to the desired resolution.

2. Edit /etc/grub.d/00_header

and modify lines to look like this:

    ```

set gfxmode=${GRUB_GFXMODE}
set gfxpayload=keep
insmod gfxmod
insmod ${GRUB_VIDEO_BACKEND}

```

3. Run "sudo update-grub"

The generated grub.cfg file in /boot/grub should now have the proper settings.

---

### Post by blakamin on 2009-09-15
This gives me ```
error: unknown command 'terminal'
``` at boot... 

But that could be the failed update that everyone is having.
I get the blinking cursor of update goodness at the same time.

Bad timing I guess

---

### Post by khughitt on 2009-09-16
> But that could be the failed update that everyone is having.
I get the blinking cursor of update goodness at the same time.

Hmm. That would be my guess. I put off rebooting yesterday because of the problems with udev, etc.

If you still get the same error messages after applying the updates, perhaps post your grub.cnf file and I can see if anything looks out of place.

---

### Post by munooka on 2009-09-28
I have the same resolution 1280x800 on my DELL M1330, however when I tried editing the 00_headers file I only get garbled graphics in the terminals and shutdown screens. It also happens with 1024x768.

Any suggestions?

---

### Post by blakamin on 2009-09-29
[SIZE="1"]double post, please delete
see my last post...[/SIZE]

---

### Post by blakamin on 2009-09-29
> **munooka said:**
> I have the same resolution 1280x800 on my DELL M1330, however when I tried editing the 00_headers file I only get garbled graphics in the terminals and shutdown screens. It also happens with 1024x768.

Any suggestions?

try 800x600... there is a command to find out you panel VBE resolution, but I cant remember what it was... [http://en.wikipedia.org/wiki/VESA_BIOS_Extensions]("http://en.wikipedia.org/wiki/VESA_BIOS_Extensions")

edit:
```
hwinfo --framebuffer
```

---

### Post by blakamin on 2009-09-29
Now that the boot hassles are over...


In **/etc/default/grub**
all i did was change and uncomment ```
set gfxmode=1024x768
```

then run update-grub (to be sure)

And 

In **/etc/grub.d/00_header**
All I did was add the BOLD piece where it is in this code
```
if loadfont `make_system_path_relative_to_its_root ${GRUB_FONT_PATH}` ; then
  set gfxmode=${GRUB_GFXMODE}
  **set gfxpayload=keep**
```

IT _HAS TO GO UNDER_ "set gfxmode..." to work!!!!


then run update-grub again.

[SIZE="3"]Big thanks to pwnedd[/SIZE]


My grub.cfg has this in it
```
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768
  set gfxpayload=keep
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
```

Crossing fingers and going for 2 reboots :P


EDIT: WORKED!! I think, hard to tell without usplash start and finish. I get no terminal text at beginning but no screen mess on shutdown!

[SIZE="3"]Big thanks to pwnedd[/SIZE]

---

### Post by munooka on 2009-09-29
sudo hwinfo --framebuffer

showed that my card supports 1280x800x8/24 both these settings and all other settings I have tried scrambles the tty terminals with set gfxpayload=keep (tried 640x480, 800x600, 1024x768 with or without the x8/x24 suffix). Only the 640x480x8 setting works so far. Maybe something to do with the Nvidia card in my lappy?

Anyway thanks for the suggestions.

---

### Post by blakamin on 2009-10-23
Broken again by a "pre-RC update". Great....
:confused:

---

