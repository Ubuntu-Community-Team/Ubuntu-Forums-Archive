---
title: "Grub -&gt; Grub 2. How  ??"
date: 2010-03-31
forum: Installation &amp; Upgrades
---

### Post by Tom_T on 2010-03-31
Currently running Ubuntu 9.04 on my Acer Aspire One D150, multi booting Win Xp, Win 7 and Ubuntu.

Can I upgrade to Grub 2 and use one of the nice themes ?? Sora ?

How ??

Thanks :)

---

### Post by Bachstelze on 2010-03-31
Why don't you just upgrade to Ubuntu 9.10?

---

### Post by kaizokuroof on 2010-03-31
Hey dude, this may point you in the right direction.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

[http://www.ubuntu-inside.me/2009/06/howto-upgrade-to-grub2-on-ubuntu-jaunty.html](http://www.ubuntu-inside.me/2009/06/howto-upgrade-to-grub2-on-ubuntu-jaunty.html)

Updating grub is fairly simple I believe.. Just a few commands. anywho let me know if you need some more help. I'll give you commands if you can't figure it out.

Kaizoku roof.

P.S. "Why don't you just upgrade to Ubuntu 9.10?" That doesn't help and now we know why your post count is so high, you post useless posts. Thanks.

---

### Post by bean123 on 2010-03-31
Actually, Sora is a BURG theme. Currently BURG only has binary package for karmic and lucid, but supporting jaunty is quite simple, I just upload a new one. Launchpad is in maintenance mode right now, I'd upload it when it's normal again.

BTW, BURG and grub legacy/grub2 can coexist, you can switch between them by using burg-install or grub-install to install the boot code to MBR/BS.

Here is the installation guide for BURG:
[http://code.google.com/p/burg/wiki/InstallUbuntu](http://code.google.com/p/burg/wiki/InstallUbuntu)

---

### Post by raymondh on 2010-03-31
> **bean123 said:**
> Actually, Sora is a BURG theme. Currently BURG only has binary package for karmic and lucid, but supporting jaunty is quite simple, I just upload a new one. Launchpad is in maintenance mode right now, I'd upload it when it's normal again.

BTW, BURG and grub legacy/grub2 can coexist, you can switch between them by using burg-install or grub-install to install the boot code to MBR/BS.

Here is the installation guide for BURG:
[http://code.google.com/p/burg/wiki/InstallUbuntu](http://code.google.com/p/burg/wiki/InstallUbuntu)

Bean .... what do yo mean by "upload a new one" ?

Thanks

raymodn

---

### Post by Tom_T on 2010-03-31
Thanks :)
So 9.10 will upgrade me to Grub 2 ?

Does Grub 2 offer the same graphical imagery as BURG ?
it it both or either one ?

Thanks :)

---

### Post by yetiman64 on 2010-03-31
Tom_T

The 2 links kaizokuroof posted are the very information I used to put grub2 onto my desktop 9.04 install - will work if followed closely and carefully.

If you're used to manipulating grub by manually editting menu.list now, don't be tempted to edit menu.cfg (menu.list replacement) when you install grub2. menu.cfg is controlled by /etc/defaults/grub and 5 or 6 other scripts in the folder /etc/grub.d .

Have fun.

---

### Post by LinuxTAd on 2010-03-31
Tom, Welcome  : )

 From my experience, updating from 9.04 to 9.10 will *not* upgrade grub to grub2. You must do this manually.

> GRUB 2 by default

GRUB 2 is the default boot loader for new installations with Ubuntu 9.10 RC, replacing the previous GRUB "Legacy" boot loader. Existing systems will not be upgraded to GRUB 2 at this time, as automatically reinstalling the boot loader is an inherently risky operation.
Source: [http://www.ubuntu.com/getubuntu/releasenotes/910overview](http://www.ubuntu.com/getubuntu/releasenotes/910overview)


 Also, I just tried to upgrade from grub to grub2 with my previous 9.04 install, and I can tell you not to bother. The 9.04 repos have have unfixed bugs and missing modules. You *may* need some of the modules to perform tasks to multi boot. 

Jaunty Bug: [https://bugs.launchpad.net/ubuntu/jaunty/+source/grub2/+bug/376879](https://bugs.launchpad.net/ubuntu/jaunty/+source/grub2/+bug/376879)

Your options are to upgrade to Grub2 from the source (I am not sure if Karmic repos will work), or update your Ubuntu to 9.10 and then manually update Grub from there. Either way, I would back your data up if you have anything important you want to keep.   ;)

After spending all this time on Grub2 and having looked at Burg, I wish I would have spent my time on Burg :p WoW! However, I am not messing with anything for awhile, it is working :P

Best of luck!

---

### Post by bean123 on 2010-03-31
> **raymondh said:**
> Bean .... what do yo mean by "upload a new one" ?

Thanks

raymodn

I upload a source package to launchpad, then it'd be compiled to generate the binary package.

> **Tom_T said:**
> Thanks :)
So 9.10 will upgrade me to Grub 2 ?

Does Grub 2 offer the same graphical imagery as BURG ?
it it both or either one ?

Thanks :)

No, grub2 theme is much simpler, it doesn't support advanced features like theme selection menu and folding. BTW, BURG also support grub2 theme, you can try both and see the difference.

---

### Post by Tom_T on 2010-03-31
Thanks for the replies..

[IMG]http://nsa14.casimages.com/img/2010/03/29/100329092527773189.png[/IMG]

How do I get this ???  I like :)

---

### Post by bean123 on 2010-03-31
Ok, it's done now. The launchpad PPA contains binary packages for jaunty, karmic and lucid.

---

### Post by bean123 on 2010-03-31
> **Tom_T said:**
> Thanks for the replies..

[IMG]http://nsa14.casimages.com/img/2010/03/29/100329092527773189.png[/IMG]

How do I get this ???  I like :)

This looks quite similar to the radiance theme, you should be able to get this effect with minor modification.

BTW, here are screenshots of available themes in burg-themes package:
[http://code.google.com/p/burg/wiki/Screenshots](http://code.google.com/p/burg/wiki/Screenshots)

---

### Post by Tom_T on 2010-03-31
Possibly a daft question..

How does the theme know what OS's are installed ? or does it read from grub ?

---

### Post by bean123 on 2010-03-31
> **Tom_T said:**
> Possibly a daft question..

How does the theme know what OS's are installed ? or does it read from grub ?

It relies on os-prober to detect installed OS (same as grub2).

---

### Post by Tom_T on 2010-03-31
Ok installed BURG as per:
[http://code.google.com/p/burg/wiki/InstallUbuntu](http://code.google.com/p/burg/wiki/InstallUbuntu)

Rebooted and got the nice screen with my OS's listed. (Ubuntu, XP Home & XP pro)

But only the XP's boot !! How do I get Ubuntu to boot again ??

Also a couple of quick questions:

Is it possible to edit the text that appears on the menu's ?  Instead of XP Home / XP Pro, I could put the users names.

Can I password protect any entry ? In grub I have one entry that needs a password.

Any way to change the icons used ?

last one where do I find this theme  ??
[IMG]http://nsa14.casimages.com/img/2010/03/29/100329092527773189.png[/IMG] It isn't on the 't' menu !!

Thanks :)

---

### Post by bean123 on 2010-03-31
> **Tom_T said:**
> Ok installed BURG as per:
[http://code.google.com/p/burg/wiki/InstallUbuntu](http://code.google.com/p/burg/wiki/InstallUbuntu)

Rebooted and got the nice screen with my OS's listed. (Ubuntu, XP Home & XP pro)

But only the XP's boot !! How do I get Ubuntu to boot again ??

You can press 'c' to open a console window, and enter these commands manually:

```

linux16 (hd0,1)/vmlinux root=/dev/sda1
initrd16 (hd0,1)/initrd.img

```

That's assumed your root is at /dev/sda1, you need to change partition number accordingly.

Once inside linux, you can edit /boot/burg/burg.cfg and change linux/initrd command to linux16/initrd16, this should at least get it booting. 

I'd install a 9.04 system tomorrow to see what's wrong.

> 
Also a couple of quick questions:

Is it possible to edit the text that appears on the menu's ?  Instead of XP Home / XP Pro, I could put the users names.


Yes, you can edit the generated burg.cfg, change the text in menuentry statement, although it'd be overwritten each time you run update-burg.

> 
Can I password protect any entry ? In grub I have one entry that needs a password.


See this wiki page:
[http://code.google.com/p/burg/wiki/Authentication](http://code.google.com/p/burg/wiki/Authentication)

> 
Any way to change the icons used ?


Yeah, the icons are in /boot/burg/themes/icons, large icons are for refit, grey/hover icons are for sora and radiance, small are for other themes.

> 
last one where do I find this theme  ??
[IMG]http://nsa14.casimages.com/img/2010/03/29/100329092527773189.png[/IMG] It isn't on the 't' menu !!

Thanks :)

It's not in burg-themes yet, I'd contact the artistic author to see if it can be added soon.

---

### Post by Tom_T on 2010-04-01
Many Thanks.
I'll look into this tonight.

How do I find the author of the image ?

---

### Post by bean123 on 2010-04-01
> **Tom_T said:**
> Many Thanks.
I'll look into this tonight.

I just install 9.04 and burg seems to be working fine. Although it disable kernel output by default, so the screen might seem frozen for a while but it's actually running in the background. If you want to see all the kernel messages, edit /etc/default/burg, change the value of GRUB_CMDLINE_LINUX_DEFAULT and add GRUB_GFXPAYLOAD_LINUX option:

```

GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""
GRUB_GFXPAYLOAD_LINUX="text"

```

And run update-burg to generate a new burg.cfg.

> How do I find the author of the image ?
No worry, I will contact him to get the artwork.

---

### Post by Tom_T on 2010-04-01
Thanks bean123

I had left the PC for about 20 minutes.. just in-case, but it never booted Ubuntu.

Today I installed Ubuntu 9.10 on to a colleagues PC along side Vista.
That went fine, so we installed BURG. Worked fine..

I'll have a look at this later and let you know how I get on.
Thanks for reporting the image. I'd like to see that :)

---

### Post by Tom_T on 2010-04-03
reinstalled BURG last night and had the same issue with Ubuntu not booting.

Rebooted, press 'c' and typed this in to the command :

> linux16 (hd0,1)/vmlinux root=/dev/sda3
initrd16 (hd0,1)/initrd.img

My Ubuntu install is sda3, so I'm hoping the above was right.. any how I got some error messages and it didn't work.

I'll try this again later today and will post the errors I get !
Regards

---

### Post by bean123 on 2010-04-03
> **Tom_T said:**
> reinstalled BURG last night and had the same issue with Ubuntu not booting.

Rebooted, press 'c' and typed this in to the command :



My Ubuntu install is sda3, so I'm hoping the above was right.. any how I got some error messages and it didn't work.

I'll try this again later today and will post the errors I get !
Regards

You need to change root device as well, it'd be:
```

linux16 (hd0,3)/vmlinux root=/dev/sda3
initrd16 (hd0,3)/initrd.img 

```

BTW, could you try the method in #18 to enable boot message ? It should give some hint as to where it hangs.

---

### Post by Tom_T on 2010-04-03
I'm doing this now and will post results back in a couple of minutes !

---

### Post by Tom_T on 2010-04-03
This is my burg file:
```

# If you change this file, run 'update-burg' afterwards to update
# /boot/burg/burg.cfg.

GRUB_DEFAULT=0
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""
GRUB_GFXPAYLOAD_LINUX="text"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1024x768

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

# Use the previous selected theme, you can also specify a theme to be used
# In the boot menu, use hotkey 't' to popup a theme selection menu
GRUB_THEME=saved

# Use the previous folding option, its value can be 'yes', 'no' or 'saved'
# In the boot menu, use hotkey 'F7' to show the full list, 'f' to toggle
# between folding modes.
GRUB_FOLD=saved

# Add user with burg-adduser, then use GRUB_USERS to config authentication.
# The following example means user1 can boot Ubuntu, no password is needed to
# boot Windows, user1 amd user2 can boot other OS. Superusers can boot any OS
# and use hotkeys like `c' to enter console mode.
#GRUB_USERS="*=user1,user2:ubuntu=user1:windows="
```

Using it like that and I can boot Ubuntu, but I get lots of text on screen and it seems to take longer to get to a GUI login screen.

If I use the original burg file, Ubuntu won't boot:
```
GRUB_DEFAULT=0
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

It just crashes.. So how do I get Ubuntu to work without all the text ??
Thanks :)

---

### Post by Tom_T on 2010-04-03
Just tried:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
#GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""
GRUB_GFXPAYLOAD_LINUX=""

That failes to load Ubuntu !

---

### Post by bean123 on 2010-04-03
> **Tom_T said:**
> Just tried:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
#GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""
GRUB_GFXPAYLOAD_LINUX=""

That failes to load Ubuntu !

You can keep the quiet option, this should avoid most output.

As for GRUB_GFXPAYLOAD_LINUX, you can set it to keep (default) or text (don't set it to blank), "keep" means keeping the current graphic mode, while "text" means switch to text mode before booting. Normally, "keep" can reduce the number of mode switches before entering GUI, but if it doesn't work, you can try "text".

---

### Post by Tom_T on 2010-04-04
Thanks.
Got it working with:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_GFXPAYLOAD_LINUX="keep"
```

Had to edit my burg.cfg to change **linux & initrd** to **linux16 & initrd16**. Any way to force this as it is overwritten on an update. ?
Seems to be working well.

Had one issue with XP, it started to boot and then gave the error: **autocheck not found**, 
at which point it rebooted and around we went. This turned out to be due to the XP partition having become hidden. Using gparted I removed the hidden flag and thats working fine now !

Next question..  
I have 3 OS's installed: Ubuntu, XP Pro (me) & XP Home (wife)
Anyway to have a different icon for each XP ? Just so it's clear which is mine and which is hers !!

Thanks :)

---

### Post by bean123 on 2010-04-25
New PPA package 2010.04.25, now you can do all the tasks using variables in /etc/default/burg, no need to edit burg.cfg manually:

```

GRUB_LINUX16=true

```
Use linux16/initrd16 to load linux.

```

GRUB_TITLE_OVERRIDE="/dev/sda5=Windows 1:/dev/sda6=Windows 2"

```
Change menu title for OS. You need to replace /dev/sda5 and /dev/sda6 to the real windows partition.

```

GRUB_CLASS_OVERRIDE="/dev/sda5=win1:/dev/sda6=win2"

```
Change class for OS. With new class, you can set different icon, refers to this wiki on how to add customized icons: [http://code.google.com/p/burg/wiki/ThemeCustomization](http://code.google.com/p/burg/wiki/ThemeCustomization)

BTW, I have just open a BURG forum at:

[http://www.burgloader.com/bbs/](http://www.burgloader.com/bbs/)

In the themes section, ingalex has post many new themes.

---

