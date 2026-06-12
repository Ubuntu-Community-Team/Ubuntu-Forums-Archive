---
title: "[SOLVED] Tried everything in forums-failure to boot fluxbuntu alt on laptop"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by GeneralSpecific on 2008-07-24
Installed on old Toshiba Tecra 550cdt laptop.
[COLOR="Navy"]266mhz
96mb ram
4gb hd[/COLOR]

Installed fluxbuntu 7.10 alternate install: It installed fine but when I rebooted it hangs.

When I reboot in recovery mode it hangs then drops to busybox shell, the error is somthing like this:

[INDENT][COLOR="Red"][I]check root= bootarg cat /proc/cmdline
or missing modules, devices cat /proc/modules ls /dev
ALERT!  /dev/disk/by-uuid/***/ does not exist. Dropping to a shell![/I][/COLOR][/INDENT]

Then gives me the initramfs prompt.

I can boot off the cd in rescue mode and make a shell in my root partion (/dev/hda1)  

I then udated and upgraded everything I could (using apt-get) including upgrading to the 2.6.22-15-generic kernel (had 2.6.22-14-generic) no luck, I get the same error from booting any of them.

[INDENT][COLOR="Navy"]I tried everthing in this thread, that worked for others:[/COLOR]

[http://ubuntuforums.org/showthread.php?t=282956&highlight=alert%21+%2Fdev%2Fdisk%2Fby-uuid]("http://ubuntuforums.org/showthread.php?t=282956&highlight=alert%21+%2Fdev%2Fdisk%2Fby-uuid")

Which basically involved creating the initramfs script for the generic kernel.

[COLOR="navy"]and here:[/COLOR]

[https://launchpad.net/ubuntu/+source/initramfs-tools/+bug/67256]("https://launchpad.net/ubuntu/+source/initramfs-tools/+bug/67256")

Which I think was updating that script.[/INDENT]
to no avail...

I also tried to edit the /ect/fstab and /grub/menu.lst for one of the kernels, to use:

/dev/hda1 instead of: uuid=***

I succeded, but it did not solve the problem, now it says it can't find the dev/hda1 instead of the uuid.

Any help would be appreciated, I have exhausted all the idea's I can find.

---

### Post by snowpine on 2008-07-24
Hi General, I had a similar problem on my old Dell laptop; it would hang when it got to the stopwatch screen. The solution was easy: 

At boot, press esc to for Grub options.
Press 'e' to edit the first 'Ubuntu 7.10 kernel'.
Scroll down to the second line that starts with 'kernel' and press 'e'.
Backspace to delete the word 'splash'.
Press Enter.
Press 'b' to boot.

Once logged in, open a terminal and:
    ```
sudo nano /boot/grub/menu.lst
```
Delete all instances of the word 'splash' (including those commented out).

Hope that works for you! Unfortunately, that is my only suggestion. :)

---

### Post by snowpine on 2008-07-24
(double post, sorry)

---

### Post by GeneralSpecific on 2008-07-24
Snowpine, thank you for trying to help. It was a new suggestion, and I tried it right away.

Unfortunately didn't work.  It still won't boot, but I do get to watch...

*loading, please wait...*

for a couple min. and then receive the _same error message._

Anyone else have a suggestions?  I need this laptop by this weekend and I am loathe to put win98 back on it...

---

### Post by kerry_s on 2008-07-24
try dsl linux, those specs might be to low even for fluxbuntu.

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

also you want to use a distro with older kernels, newer kernels have cut out older support to make way for the new, for example: on my old rig nothing past 2.6.18 kernel works on it.

---

### Post by GeneralSpecific on 2008-07-24
Thanks Kerry,

DSL does run wonderfully on it, I had it dual booting DSL and win98 for quite a while.

Unfortunately I need to run a large program (windows program-thru wine)  and I could never figure out how to get it to install when running DSL(I  did a frugal install, live cd off the hd)

I will try installing an older kernel, and let you know how it works, nothing else has...

---

### Post by kerry_s on 2008-07-24
i use a custom debian install, etch has the 2.6.18 kernel that works on my laptop and i use the software from lenny/testing repo.

so you might want to try an etch install, built lite.

i use the net installer:
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso)

at package selection, uncheck everything, that will give you a base install to build up on.

log in as root:
apt-get install xorg fluxbox
exit

log in as your user:
startx

then just continue building up from there, adding what you want. custom is the way to go.

just incase you don't know apt-get:
[http://www.debian.org/doc/manuals/apt-howto/](http://www.debian.org/doc/manuals/apt-howto/)

---

### Post by GeneralSpecific on 2008-07-25
Thank you so much, it worked like a charm!

I have fluxbox running and am working to add extra programs.

No more windoze98!!

---

### Post by kerry_s on 2008-07-25
> **GeneralSpecific said:**
> Thank you so much, it worked like a charm!

I have fluxbox running and am working to add extra programs.

No more windoze98!!

that's great, don't forget if you get stuck, you can still get help here, just use the debian section or other os. there are a lot of debian users here who can help. ;)

---

