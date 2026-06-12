---
title: "Fixing Really Ugly Plymouth With Nvidia Driver"
date: 2010-04-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zenarcher on 2010-04-03
I'm running Kubuntu Lucid Beta 1 (64 bit) with the proprietary Nvidia video driver.  It's been really annoying when I boot up and get the ugly Kubuntu screen, especially since I encrypt my hard drive.  I don't even see the box for entering my passphrase, due to the large, low-color Kubuntu screen.  I just have to enter the passphrase, which does work, at least.

Anyway, doing some searching around,I found a real easy fix for the Kubuntu start up screen.  Maybe I'm the last one to find it, but if you're using the proprietary Nvidia graphics driver and don't like the looks of the Ubuntu/Kubuntu screen, here's an easy way to fix it!

Here is what you have to do to get Plymouth working with proprietary Nvidia drivers:

Step 1: we must edit the /etc/default/grub file.

Open a terminal and paste this:

$ sudo gedit /etc/default/grub

On line #18, uncomment (uncomment = remove the “#” in front of the line “#GRUB_GFXMODE=640×480” and change the resolution to whatever you want ***(in my particular case, I changed it to 1680x1050).*** Here is how it should look:

GRUB_GFXMODE=1680x1050

Step 2: edit the /etc/grub.d/00_header file.

$ sudo gedit /etc/grub.d/00_header

And find the following line: “gfxmode=${GRUB_GFXMODE}” (it’s line 103 on my computer) and under it, paste this:

set gfxpayload=keep

Step 3: update Grub 2:

To update the GRUB, simply run the following command:

$ sudo update-grub

Once you complete the above steps, restart the computer and you should see the nice Plymouth screen

Here's where I found the information:

[http://www.sucka.net/2010/03/nvidia-drivers-ubuntu-10-04-lucid-lynx/](http://www.sucka.net/2010/03/nvidia-drivers-ubuntu-10-04-lucid-lynx/)

It really worked great for me and so much easier to enter my passphrase at startup!

Hope it helps someone else!

Cheers, 
zenarcher

---

### Post by ibuclaw on 2010-04-03
I just switched to the xorg-edgers ppa for Nouveau - to which I think I'll happily stay, but nice find all the same! :)

Regards

---

### Post by HydroDiOxide on 2010-04-05
Great! Now I can use the nvidia driver AND have a nice splash! Works like a charm.

btw: I can't get grub to use my 05_debian_theme settings. Probably nothing to do with ur settings.

---

### Post by RazVayne on 2010-04-05
*
As a side note,after applying this,I no longer have to boot with i915.modeset=0.Atleast thats outta the way!

---

### Post by sparker256 on 2010-04-05
> **ibuclaw said:**
> I just switched to the xorg-edgers ppa for Nouveau - to which I think I'll happily stay, but nice find all the same! :)

Regards

Does it support 3D Games. As I run X-Plane this is a must for me.

Bill

---

### Post by ibuclaw on 2010-04-05
> **sparker256 said:**
> Does it support 3D Games. As I run X-Plane this is a must for me.

Bill

It currently only supports 3D **Software** Acceleration, not Hardware Acceleration - so games will most likely run dog slow on your system.

Also, as great as it is to have the ability to have fun whizzing effects (although 'xcompmgr -n' is all I need and use), not all bits and pieces have been implemented for all cards/models yet, so some things may cause random glitches or artifacts on the screen (if I can find it, a picture of the compiz cube I took a while ago)

edit: [http://ubuntuforums.org/attachment.php?attachmentid=149235&d=1267913982](http://ubuntuforums.org/attachment.php?attachmentid=149235&d=1267913982)

---

### Post by praveenthivari on 2010-04-05
> **ibuclaw said:**
>  [http://ubuntuforums.org/attachment.php?attachmentid=149235&d=1267913982](http://ubuntuforums.org/attachment.php?attachmentid=149235&d=1267913982)

Wat kind of effect is tht. It looks awesome.How to enable it?

---

### Post by sparker256 on 2010-04-05
> **ibuclaw said:**
> It currently only supports 3D **Software** Acceleration, not Hardware Acceleration - so games will most likely run dog slow on your system.

Also, as great as it is to have the ability to have fun whizzing effects (although 'xcompmgr -n' is all I need and use), not all bits and pieces have been implemented for all cards/models yet, so some things may cause random glitches or artifacts on the screen (if I can find it, a picture of the compiz cube I took a while ago)

edit: [http://ubuntuforums.org/attachment.php?attachmentid=149235&d=1267913982](http://ubuntuforums.org/attachment.php?attachmentid=149235&d=1267913982)

Thanks for the info. I am running the Nvidia 195.36.15 driver.

I have three installs of 10.04. One works the best that I can tell correctly. 

The other two do boot after I have made my boot selection but my grub2 theme stays on without the boot selection text for a while them my Plymouth theme shows up for a short time then the desktop is displayed.

Not sure what is different but just trying to get info as how to make all work the same.

The one install is 10.04 64 bit on the same machine that my 32 bit install works correctly on.

The other install in on a different machine is 10.04 32 bit with a nivida card but have the same symptoms. 

Thanks Bill

---

### Post by zaphod777 on 2010-04-05
great find worked like a charm.

---

### Post by Rackstar on 2010-04-05
I'm gonna leave it this way for now, I want to see it fixed automatically by the updates. But great find anyhow!

---

### Post by sparker256 on 2010-04-05
if I use step 2 when I boot I am always boot into low res mode.

> Step 2: edit the /etc/grub.d/00_header file.

$ sudo gedit /etc/grub.d/00_header

And find the following line: “gfxmode=${GRUB_GFXMODE}” (it’s line 103 on my computer) and under it, paste this:

set gfxpayload=keep

When I only use the first step I have it working as I described above.

Bill

---

### Post by xir_ on 2010-04-05
Thank for the guide. Unfortunately it doesn't work with ati as you cant log on to other tty instances, or see plymouth. Instead you get a series of lines and dots at the top of the screen.

---

### Post by jahLux on 2010-04-05
> **zenarcher said:**
> I'm running Kubuntu Lucid Beta 1 (64 bit) with the proprietary Nvidia video driver.  It's been really annoying when I boot up and get the ugly Kubuntu screen, especially since I encrypt my hard drive.  I don't even see the box for entering my passphrase, due to the large, low-color Kubuntu screen.  I just have to enter the passphrase, which does work, at least.

Anyway, doing some searching around,I found a real easy fix for the Kubuntu start up screen.  Maybe I'm the last one to find it, but if you're using the proprietary Nvidia graphics driver and don't like the looks of the Ubuntu/Kubuntu screen, here's an easy way to fix it!

Here is what you have to do to get Plymouth working with proprietary Nvidia drivers:

Step 1: we must edit the /etc/default/grub file.

Open a terminal and paste this:

$ sudo gedit /etc/default/grub

On line #18, uncomment (uncomment = remove the “#” in front of the line “#GRUB_GFXMODE=640×480” and change the resolution to whatever you want ***(in my particular case, I changed it to 1680x1050).*** Here is how it should look:

GRUB_GFXMODE=1680x1050

Step 2: edit the /etc/grub.d/00_header file.

$ sudo gedit /etc/grub.d/00_header

And find the following line: “gfxmode=${GRUB_GFXMODE}” (it’s line 103 on my computer) and under it, paste this:

set gfxpayload=keep

Step 3: update Grub 2:

To update the GRUB, simply run the following command:

$ sudo update-grub

Once you complete the above steps, restart the computer and you should see the nice Plymouth screen

Here's where I found the information:

[http://www.sucka.net/2010/03/nvidia-drivers-ubuntu-10-04-lucid-lynx/](http://www.sucka.net/2010/03/nvidia-drivers-ubuntu-10-04-lucid-lynx/)

It really worked great for me and so much easier to enter my passphrase at startup!

Hope it helps someone else!

Cheers, 
zenarcher


I'm running Lucid 64bit Beta 2 [GNOME] on nVidia GeForce 9400  - with all latest updates.
Thanks for the effort, but there's no "/etc/default/grub" file to edit.
Any ideas how to accomplish your fix in Gnome?

---

### Post by Paqman on 2010-04-05
> **zenarcher said:**
> 
Open a terminal and paste this:

$ **sudo gedit** /etc/default/grub


Just a tip: using sudo with graphical apps is bad practice. Use sudo for command line apps, and gksu for graphical ones.

---

### Post by Uncle Spellbinder on 2010-04-05
> **jahLux said:**
> I'm running Lucid 64bit Beta 2 [GNOME] on nVidia GeForce 9400  - with all latest updates.
Thanks for the effort, but there's no "/etc/default/grub" file to edit.
Any ideas how to accomplish your fix in Gnome?

Lucid Beta, 32-bit (Gnome), nVidia GeForce 9800GT. I have [I]/etc/default/grub
[/I]


*sudo gedit /etc/default/grub*

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by sparker256 on 2010-04-05
> **jahLux said:**
> I'm running Lucid 64bit Beta 2 [GNOME] on nVidia GeForce 9400  - with all latest updates.
Thanks for the effort, but there's no "/etc/default/grub" file to edit.
Any ideas how to accomplish your fix in Gnome?

On my 64 bit install this is what I get with the following command.

bill@game-64-1004:~$ gksu gedit /etc/default/grub

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

Bill

---

### Post by Voynix on 2010-04-05
> **jahLux said:**
> I'm running Lucid 64bit Beta 2 [GNOME] on nVidia  GeForce 9400  - with all latest updates.
Thanks for the effort, but there's no "/etc/default/grub" file to edit.
Any ideas how to accomplish your fix in Gnome?

Are you still running the legacy grub package? Have you been upgrading  ubuntu without any fresh installs? I think Grub2 is not upgraded automatically unless you do a fresh installation .

If I am not mistaken, "/etc/default/grub" is a grub2 specific file.  After I upgraded from grub to grub2 and applied the above instructions, I  got rid of the error messages, plymouth shows up and I have the right  resolution.

if you want to know more about grub2 and how to upgrade, see here: [https://wiki.edubuntu.org/Grub2](https://wiki.edubuntu.org/Grub2)

---

### Post by 98cwitr on 2010-04-05
that works...awesome thanks.

---

### Post by icest0rm on 2010-04-06
Hi,
did the fix as suggested, set GFXMODE at 1440x900 (my display res) but getting the ubuntu logo in pluymouth all shifted to left and not centered as it should be...
any hint?

thanx

---

### Post by ffi on 2010-04-06
> **Rackstar said:**
> I'm gonna leave it this way for now, I want to see it fixed automatically by the updates. But great find anyhow!

I think they will leave it like this. 

Anyway thanks zenarcher

---

### Post by zaphod777 on 2010-04-06
> **Paqman said:**
> Just a tip: using sudo with graphical apps is bad practice. Use sudo for command line apps, and gksu for graphical ones.

Why is that? I have never had a problem with it. Will it keep the program open if you close the cmd window? 

I actually prefer that so I don't accidental leave a program running with root access after I have done the task I needed to do.

---

### Post by bash on 2010-04-06
> **zaphod777 said:**
> Why is that? I have never had a problem with it. Will it keep the program open if you close the cmd window?

To quote the Ubuntu Help files:

> You should never use normal sudo to start graphical applications as root. You should use gksudo (kdesudo on Kubuntu) to run such programs. gksudo sets HOME=~root, and copies .Xauthority to a tmp directory. This prevents files in your home directory becoming owned by root. (AFAICT, this is all that's special about the environment of the started process with gksudo vs. sudo).

---

### Post by zaphod777 on 2010-04-06
> **bash said:**
> To quote the Ubuntu Help files:

good to know thanks.

---

### Post by jahLux on 2010-04-06
> **Voynix said:**
> Are you still running the legacy grub package? Have you been upgrading  ubuntu without any fresh installs? I think Grub2 is not upgraded automatically unless you do a fresh installation .

If I am not mistaken, "/etc/default/grub" is a grub2 specific file.  After I upgraded from grub to grub2 and applied the above instructions, I  got rid of the error messages, plymouth shows up and I have the right  resolution.

if you want to know more about grub2 and how to upgrade, see here: [https://wiki.edubuntu.org/Grub2](https://wiki.edubuntu.org/Grub2)

Thanks much, Voynix.
I was indeed running the old GRUB, having previously 'upgraded' to Lucid instead of doing a fresh-install.
All's well in UBUNTU land again!

---

### Post by Speque on 2010-04-06
Thanks, the fix worked for me.

---

### Post by chriss on 2010-04-11
Thanks. Works fine.

Is there something to do at future updates of grub or something?

And the shutdown splash screen disappeared. When i shutdown i only see a black screen.

chriss

---

### Post by jymbob on 2010-04-11
> **xir_ said:**
> Thank for the guide. Unfortunately it doesn't work with ati as you cant log on to other tty instances, or see plymouth. Instead you get a series of lines and dots at the top of the screen.

The problem here (in my case) was a ```
GRUB_CMDLINE_LINUX_DEFAULT="vga=795"
```
line in /etc/default/grub.

Remove this, and apply only step #1 of the fix above, and you should get Plymouth and tty back.

---

### Post by LeeDaugherty on 2010-04-15
Using Lucid Beta-2, NVidia 195, GeForce 6200.  The above hack (using 1600x1200) causes Plymouth to flicker alot, I see a properly formatted screen for about 3 seconds, then X dumps to low-res with a no-memory NVidia error.  Does the hack not work with Beta 2?

EDIT:
I realized I had compiz on full, so I cut that, and then no plymouth splash (I do see a flash of broken pipe errors), and low-res error.  Tried different resolutions as well to no avail.  I'll keep trying different things.

---

### Post by TunaCanTommy on 2010-04-15
Read the posts in this thread . . . 

[http://ubuntuforums.org/showthread.php?p=9123643#post9123643](http://ubuntuforums.org/showthread.php?p=9123643#post9123643)

I'm running a GeForce 6200 also and this above thread cleared up a bunch of stuff for me.  Mainly . .  try using the "alternative method" of installing the Nvidia driver. No need to black-list Nouveau from what I experienced.  You may get the occasional "running in low res" message, but I just reboot and it's fine.

---

### Post by itsjustarumour on 2010-04-15
> **sparker256 said:**
> Does it support 3D Games. As I run X-Plane this is a must for me.

Bill

Interesting article on Phoronix comparing the two drivers:

[http://www.phoronix.com/scan.php?page=article&item=fedora_nouveau_power&num=1](http://www.phoronix.com/scan.php?page=article&item=fedora_nouveau_power&num=1)

Page 2 compares framerates for Open Arena - standard NVidia driver produced 5.6 times as many frames/sec as the Nouveau driver.

---

### Post by Kosmonaut on 2010-04-16
@icest0rm (and others):

I also had this "shifted" boot logo. What I did to have it in the center, was to edit /etc/default/grub in this way: 
Untill there is a real fix for that issue, I changed:

GRUB_CMDLINE_LINUX="vga=792"
and
GRUB_GFXMODE=1024x768

Don't forget to update grub after changing those parameters...

(I found this by playing around with different variations in /etc/default/grub, without really having an idea what I did. Sometimes by setting other resolutions and vga modes I had logos that were shifted, then no logo, then no tty...etc...etc.. )

Maybe you find the right setting for 14400*900....

K.

---

### Post by saltydog on 2010-04-18
This workaround doesn't work for me. I have set GFXMODE to 1440x900 (my monitor resolution) but as soon as grub starts the monitor complains for a bad resolution and goes totally black. I had to remove "set gfxpayload=keep", but plymouth is still looking bad at low resolution.

Running GeForce 7300 with 195-driver

---

### Post by autocrosser on 2010-04-18
I've used a lower resolution than my monitor to "fix" the problem....I'm running a 26" @ 1900x1200 & if I set it to that---everything goes bonkers....  So I used 1024x768 & it centres very nicely, plus is not too big or small.

---

### Post by Chromagnum on 2010-04-18
Did you guys notice, if you don't do anything with plymouth, left it like it was, it is starting to shape it up? 

I used to get, like, 640x480 and the color really meshed up. But now, it is higher than that. It still used 4:3 ratio instead of 16:9 (my monitor ratio), but the logo, the background color, seems pretty nice now. 

Mine nvidia fx5500. I was wondering, if you guys left grub and header with the default setting, also get the same result like mine?

---

### Post by saltydog on 2010-04-18
> **autocrosser said:**
> I've used a lower resolution than my monitor to "fix" the problem....I'm running a 26" @ 1900x1200 & if I set it to that---everything goes bonkers....  So I used 1024x768 & it centres very nicely, plus is not too big or small.

I did the same, fixing resolution at 1024x768 while the monitor is 1440x900, but it this case Gnome was claiming that the resolution was wrong and I had a blank desktop.

---

### Post by autocrosser on 2010-04-18
> **Chromagnum said:**
> Did you guys notice, if you don't do anything with plymouth, left it like it was, it is starting to shape it up? 

I used to get, like, 640x480 and the color really meshed up. But now, it is higher than that. It still used 4:3 ratio instead of 16:9 (my monitor ratio), but the logo, the background color, seems pretty nice now. 

Mine nvidia fx5500. I was wondering, if you guys left grub and header with the default setting, also get the same result like mine?

Yes--I tried that & still do about every couple of days.....Still looks MUCH better mucking with the bits.  It also helps that I love to tinker with my OS...I can't ever leave anything stock for more that 10 minutes or so.....:P

---

### Post by autocrosser on 2010-04-18
> **saltydog said:**
> I did the same, fixing resolution at 1024x768 while the monitor is 1440x900, but it this case Gnome was claiming that the resolution was wrong and I had a blank desktop.

Hmmmm...I don't remember my vga charts as well as I use to, but you might do some looking to see if there is a lower than 1400x900 that you could use....have you tried 1280x720 or 720x576?

---

### Post by eexpress on 2010-04-22
within /etc/default/grub
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
I do those step, plymouth is ok, but tty become black. I really want tty specially when i play fps game. :D

```
GRUB_CMDLINE_LINUX_DEFAULT="vga=788 quiet splash"
```
i add vga=788, plymouth goes to low resolution.

```
#GRUB_CMDLINE_LINUX_DEFAULT="vga=788 quiet splash"
```
i disable this line, tty back, plymouth disappear.

so, how to get this two all back. btw, my laptop is at 1280x800.

---

### Post by arqbrulo on 2010-04-26
Well, I did steps 1, 2 and 3. On step 1 I did not use my default resolution. I used 1024x768 instead of 1440x900.

Also, I added an extra step. I was told to comment (add #) to the "GRUB_CMDLINE_LINUX_DEFAULT" line, but instead I left it UNcommented and it looks like so: GRUB_CMDLINE_LINUX_DEFAULT="vga=795 quiet splash" (previously it did not have vga=795, so I added it).

With this I got plymouth with a decent resolution, and I got tty. The only thing is that instead of getting "ubuntu" with the new font and new logo, I get the text "ubuntu 10.04" with some ugly font. I still prefer this to what I had, but if anybody knows how to fix it, I will be very grateful.

---

### Post by wnelson on 2010-04-26
When using vga=7xx make sure that a frame buffer display driver is being loaded. Do all as root.
I use vesafb. 
Check in /etc/modprobe.d/blacklist-framebuffer.conf
Comment out the #blacklist vesafb or what ever frame buffer display driver you want to use.

I also created the following
echo FRAMEBUFFER=y | sudo tee  /etc/initramfs-tools/conf.d/splash

This worked for me.

---

### Post by arqbrulo on 2010-04-26
Thanks for the tip, wnelson, but it did not work for me. I commented the nvidiafb driver and it did not help. I also commented out the vesafb and same thing. Also, something I noticed is that the logo displayed when I'm loging OUT is the default "ubuntu" with new font and the new logo, but it's not so when I'm loging IN.

---

