---
title: "Gutsy GUI Good, but no console"
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by fsmithred on 2007-10-16
How can I get to a plain old console without X? I have a fresh install of gutsy rc, and gnome comes up fine, but I cannot get to a console no matter what I try. If I ctrl-alt-F1, I see a screen filled with psychedelic colors. Last night I proved that a working console is hiding under those colors, because I was able to shut down by typing commands, even though I couldn't see what I was doing.

I'm not the only person with this problem. I ran into someone in IRC yesterday with the same thing, also using nvidia card.

Now it gets weird -
I tried changing the runlevels so that gdm wouldn't start until runlevel 4, hoping to boot into a non-gui environment. It booted, and I could alt-Fn to different consoles. To make sure that I was really seeing different one (they all look the same) I decided to put something on the screen, so I ran uname -a, only to find out that I'd somehow booted my debian kernel, which is on another partition. Running startx brought me into the ubuntu gui.

At that point, I rebooted into debian, ran grub-install /dev/sda and then tried to boot into ubuntu again. All I got was black screen. So I booted back into debian, chrooted to the ubuntu partition to re-run update-rc.d and put the runlevels back to default. Now, it boots into gui again.

Motherboard is ASUS M2V, vid card is GeForce 6200LE, using nv driver.


Problem #2, maybe related -
How can I see the boot messages scroll by as I'm booting? I edited menu.lst to get rid of the splash, and now all I see is black screen until the orange login screen appears.. 
I changed -
#defoptions=quiet splash
to -
#defoptions=vga=791

---

### Post by TNakos on 2007-10-16
i had a problem where i had no task bars... just ctrl alt backspace

---

### Post by ajslater on 2007-10-16
knowing what your kernel params do is helpful.

quiet = don't show boot console messages
splash = show the nifty ubuntu progress bar
vga=791  = set the console to vga mode 791


what you did with the boot parms should have worked. but it looks like there are bugs in gutsy.
vga=791 worked with the feisty kernel for me, but causes no console to display on gutsy. try removing it. for the example you gave this would mean no default options.

looks like there's  a bug with usplash or with the quiet option too. on my macbook pro i get consoles and boot output with none of the above options and, like you, no consoles with 'quiet splash'.

hth

AJ

---

### Post by fsmithred on 2007-10-16
Thanks. Removing the default options corrected it. I can see my boot messages, and I can get to a console. The console font doesn't look right - it's too thin (light).  But that's probably a different matter. I noticed the same thing when I installed 64studio.

---

### Post by ysidoro on 2007-10-17
> **ajslater said:**
> what you did with the boot parms should have worked. but it looks like there are bugs in gutsy.
vga=791 worked with the feisty kernel for me, but causes no console to display on gutsy. try removing it. for the example you gave this would mean no default options.


Yes!  I have upgraded from Feisty and vga=791 do not work.  
Kernel = 2.6.22-14-generic 

Removing vga=791 from kernel options restore console with default fonts.

I hope that you can check and correct this problem to stable Gutsy release.

Ysidoro

---

### Post by fsmithred on 2007-10-17
Someone in IRC pointed me to this -

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910)


I tried the trick with update-initramfs, but vesafb still wasn't loading on boot. If I get ambitious, and if my X quits locking up, I might recompile a kernel. Would be kinda nice if I could just download it through update manager, though.

---

### Post by honeydew on 2007-10-21
I am also experiencing this issue.. if anyone knows a fix please let me know..   I enjoyed using ubuntu server on machine and the hires console...

---

### Post by RedSquirrel on 2007-10-21
> **honeydew said:**
> I am also experiencing this issue.. if anyone knows a fix please let me know..   I enjoyed using ubuntu server on machine and the hires console...
The link provided by fsmithred has the answers. The following procedure worked for me:

  1. sudo nano -w /etc/initramfs-tools/modules and add fbcon and vesafb

  so my /etc/initramfs-tools/modules looks like:
  fbcon
  vesafb

  2. sudo update-initramfs -u -k all -v

  3. sudo nano -w /etc/modprobe.d/blacklist-framebuffer
  change the line "blacklist vesafb" to "# blacklist vesafb"

  4. reboot and everything is fine

---

### Post by honeydew on 2007-10-21
> **RedSquirrel said:**
> The link provided by fsmithred has the answers. The following procedure worked for me:

  1. sudo nano -w /etc/initramfs-tools/modules and add fbcon and vesafb

  so my /etc/initramfs-tools/modules looks like:
  fbcon
  vesafb

  2. sudo update-initramfs -u -k all -v

  3. sudo nano -w /etc/modprobe.d/blacklist-framebuffer
  change the line "blacklist vesafb" to "# blacklist vesafb"

  4. reboot and everything is fine

thanks for the tips.. however I tried this and it didnt work for me.  Or is my goal different than yours? I am trying todo vga=791 in the grub boot menu...

---

### Post by RedSquirrel on 2007-10-21
Yes, that's exactly what I mean, vga=791. Some users posted other approaches in the [thread]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910"), such as using nvidiafb instead of vesafb if you have an nvidia card. Mine worked with the procedure above, but you may have to try something else.

---

### Post by honeydew on 2007-10-22
o nice.. I unblacklisted the intelfb.. and this worked for me.. thanks for the tips redsquirrel!!

---

### Post by nambla on 2007-11-08
> **RedSquirrel said:**
> The link provided by fsmithred has the answers. The following procedure worked for me:

  1. sudo nano -w /etc/initramfs-tools/modules and add fbcon and vesafb

  so my /etc/initramfs-tools/modules looks like:
  fbcon
  vesafb

  2. sudo update-initramfs -u -k all -v

  3. sudo nano -w /etc/modprobe.d/blacklist-framebuffer
  change the line "blacklist vesafb" to "# blacklist vesafb"

  4. reboot and everything is fine

additionally i had to do:

sudo echo "vesafb" >> /etc/modules

or for all hardcore users "modprobe vesafb" every single time you boot ;)

now everything works fine for me and vga=791 :)

---

### Post by jdarias on 2007-11-21
> **RedSquirrel said:**
> Yes, that's exactly what I mean, vga=791. Some users posted other approaches in the [thread]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910"), such as using nvidiafb instead of vesafb if you have an nvidia card. Mine worked with the procedure above, but you may have to try something else.

Redsquirrel, i´m trying to solve this issue too, but i had no success.
i added fbcon and nvidiafb to /etc/initramfs-tools/modules, unblacklisted nvidiafb, and then i added video=nvidiafb:1280x1024-32@60 to my kernel line in menu.lst.

Altough the console showed in hires with this setup, it broke my X: it doesn´t start, it just leaves the monitor without signal, so i rolled back everything. The x server is using the nvidia proprietary driver, may it be a conflict with the two of them?

Also if i try vesafb, instead, nothing happens. please help...

---

### Post by RedSquirrel on 2007-11-21
> **jdarias said:**
> Redsquirrel, i´m trying to solve this issue too, but i had no success. ... Also if i try vesafb, instead, nothing happens. please help...

I wish I could. Unfortunately, I don't have any other suggestions to fix the problem (other than watching the relevant thread(s) on launchpad to see if a solution appears at some point). :(

(It might be worth it to use feisty instead, or maybe another distro altogether.)

---

