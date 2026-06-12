---
title: "Desktop won't load &amp; terminal is illegible"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by m3s3lf on 2011-05-09
After upgrading from 10.10 to 11.04, my machine was freezing as the desktop was loading. The mouse pointer would move and some of the basic shortcut keys would work, but nothing on the screen was responsive.

I've got the NVIDIA 7300 LE video card, so i thought it was a conflict between that and UNITY (which I have ZERO interest in running), so I move over to a terminal login and this is what it looks like:
[http://i56.tinypic.com/j8jrm8.jpg](http://i56.tinypic.com/j8jrm8.jpg)
(click for pic - apparently, not everybody uses a 55" LCD as a monitor)

I can type like a regular terminal window, but obviously I can't read anything. I ran 'sudo apt-get remove unity' (and then 'sudo apt-get install gnome' when that didn't work) but the desktop still doesn't load and the terminal login tabs are still completely illegible.

So, what is my next course of action?

Thank you,
Billy

---

### Post by AlphaLexman on 2011-05-09
Can you 'Ctrl-Alt-F1' to get a terminal login screen?

You could at least see what you are typing!

**FWIW:** I had / have an old setup that gets alot of used hardware just to test it. I [COLOR=Blue]had[/COLOR] the exact same video card installed, and on a Live CD ( I don't remember which version, somewhere between 9.04 -10.10) I got a similar garbled screen, I did 'Ctrl-Alt-F1' and then another 'Ctrl-Alt-F7' and the X11 environment was normal again. I never really kept that machine the same, so I couldn't reproduce the problem.

It doesn't hurt to try it though.

Good Luck!

---

### Post by m3s3lf on 2011-05-09
Yeah, that photo *is* after a ctrl+alt+F1! I can type but I can't read what I'm typing, so I've got to type carefully. 

Now when I try that again though, I just get a black screen. Ctrl+alt+F7 gives me black screen, but a working cursor (for what that is worth!)

There doesn't seem to being a ssh server running... I don't know what to do.

Any help would be greatly appreciated!
Billy

---

### Post by AlphaLexman on 2011-05-09
Try a Live CD (if you have one) you can at least mount the drive and read config files.

---

### Post by m3s3lf on 2011-05-09
Ok, then what? I don't have any reason to think that a live cd won't work, I just don't know what to do you after that. I figure that I should probably try changing graphics card drivers, but I can't do that from a live cd, right?
Thanks,
Billy

---

### Post by AlphaLexman on 2011-05-09
> **m3s3lf said:**
> Ok, then what? I don't have any reason to think that a live cd won't work, I just don't know what to do you after that. I figure that I should probably try changing graphics card drivers, but I can't do that from a live cd, right?
Thanks,
Billy
The kernel will most likely pick the correct driver, that is not the problem, you probably have an edited config file prior to your upgrade that is messing things up. I am personally against advising users to re-install to fix everything.

You will need to look at these files:
/etc/X11/xorg.conf
~/.xsession-errors

Some more questions:

[LIST]
[*]Do you get a valid grub screen?
[*]Do you get a graphical gdm login screen? Or do you have auto-login enabled?
[*]How do you enter your user password?
[*]I seem to remember there is a keycode to force a text login, but I can't remember it right now, maybe somebody else knows...
[/LIST]

---

### Post by m3s3lf on 2011-05-09
> **AlphaLexman said:**
> The kernel will most likely pick the correct driver, that is not the problem, you probably have an edited config file prior to your upgrade that is messing things up. I am personally against advising users to re-install to fix everything.

You will need to look at these files:
/etc/X11/xorg.conf
~/.xsession-errors

Some more questions:

[LIST]
[*]Do you get a valid grub screen?
[*]Do you get a graphical gdm login screen? Or do you have auto-login enabled?
[*]How do you enter your user password?
[*]I seem to remember there is a keycode to force a text login, but I can't remember it right now, maybe somebody else knows...
[/LIST]

I had just formatted / and reinstalled 10.10 last week.  Unless there were config files stored on /home, they weren't customised (/home is on a separate partition).

Here is the contents of the .xsessions-errors
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-PYq0fb
GNOME_KEYRING_PID=1384
GNOME_KEYRING_CONTROL=/tmp/keyring-PYq0fb
GNOME_KEYRING_CONTROL=/tmp/keyring-PYq0fb
SSH_AUTH_SOCK=/tmp/keyring-PYq0fb/ssh

** (gnome-settings-daemon:1391): WARNING **: Key binding (custom0) is invalid
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
gnome-session[1296]: WARNING: Could not launch application 'dropbox.desktop': Unable to start application: Failed to execute child process "dropbox" (No such file or directory)
gnome-session[1296]: WARNING: Could not launch application 'gmailwatcher.desktop': Unable to start application: Failed to execute child process "gmailwatcher" (No such file or directory)
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing staticswitcher options...done
Initializing resize options...done
Initializing fade options...done
Initializing scale options...done
I/O warning : failed to load external entity "/home/billy/.compiz/session/102536515628010a9f130497489685386600000012960033"
Initializing session options...done
Initializing nautilus-gdu extension
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"
Starting unity-window-decorator

(nautilus:1423): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(nautilus:1423): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1423): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1423): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1423): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1423): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1423): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1423): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1423): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1423): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1423): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1423): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1423): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1423): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1423): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1423): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1423): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1423): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1423): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:1423): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1423): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1423): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1423): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1423): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
```

And the contents of xorg.conf
```


Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

Oddly enough, after a couple reboots, now I'm not getting the desktop wallpaper, just a black screen and sometimes a cursor.  I can't get to the terminal screen at all any more.

Once I was able to get to the login screen. Normally, it logs me in automatically, but I could swear that I pushed ctrl+alt+F1 and that's where it brought me. I chose "Ubuntu Classic (enhanced)" or whatever thinking that the problem might be that it's still trying to load UNITY, but it froze at the same spot as before.  Now I can't get back to that login screen.

Also once, I was able to get the grub menu.  I only have one OS installed, so I normally never see this menu either.  It's supposed to show me the menu when I press shift during boot, right?  I've been trying that, which is what I thought I did the first time, but I can't get back to that menu either.

To answer your questions, 
* Do you get a valid grub screen? 
**Not really (see above)**
* Do you get a graphical gdm login screen? Or do you have auto-login enabled?  **Auto login - I was able to get back to it once, but wasted the opportunity**
* How do you enter your user password?
**I don't enter a password to login**
* I seem to remember there is a keycode to force a text login, but I can't remember it right now, maybe somebody else knows...
**When I was able to switch over to a text login, I did have to login, but I can't get back there any more.**

Thanks for the help!  I really appreciate it!
Billy

---

### Post by wilee-nilee on 2011-05-09
Hope you get this fixed, you might notice in the reply panel a paperclip this is for uploading pictures, so they don't fill the whole screen.

There is also, a way to wrap the text you have posted to make it easier to read, click on the (#) in the reply panel and paste the text between the code tags.

If you're inclined you can go back and wrap the text manually with the instructions in my sig.;)

---

### Post by MAFoElffen on 2011-05-09
> **AlphaLexman said:**
> The kernel will most likely pick the correct driver, that is not the problem, you probably have an edited config file prior to your upgrade that is messing things up. I am personally against advising users to re-install to fix everything.

You will need to look at these files:
/etc/X11/xorg.conf
~/.xsession-errors

Some more questions:

[LIST]
[*]Do you get a valid grub screen?
[*]Do you get a graphical gdm login screen? Or do you have auto-login enabled?
[*]How do you enter your user password?
[*]I seem to remember there is a keycode to force a text login, but I can't remember it right now, maybe somebody else knows...
[/LIST]

The keyboard shortcut is <cntrl><alt><F1>

+1 on AlphaLexman's advice...
Go to this sticky:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
Follow the troubleshooting flowchart.  Once you can get into a text console session, please post your /etc/X11/sorg.conf and the results of 
```

sudo hwinfo --framebuffer
sudo hwinfo --monitor
xrandr -q
lspci | grep VGA

```If "hwinfo" is not installed yet, please install it via 
```

sudo apt-get install hwinfo

```This will tell those here what you have as hardware (video card and monitor), what modes each supports, what drivers it is using and what the configuration file is telling it to do...

Edit-- I see "since" that you posted "some" of the Xorg.conf... but I'd really like ti see the whole file contents to confirm that it is valid.

**Note for others**"  If you are posting a log,file or code, you usually wrap them in **[CODE]** tags.  If it is "long", (such as a syslog) then please wrap them in **[HTML]** tags and it will adda vertical srcollbar and make the post smaller in size.

---

### Post by Expander on 2011-05-09
I think your screen above is because of the "
**New Ubuntu 11.04 supports 10 Indian languages", :D:D:D**


Maybe the indian languages ****** up everything lol.

---

### Post by AlphaLexman on 2011-05-09
There a couple / few lines that stand out to me...
> **m3s3lf said:**
> 
** (gnome-settings-daemon:1391): WARNING **: Key binding (custom0) is invalid

gnome-session[1296]: WARNING: Could not launch application  'dropbox.desktop': Unable to start application: Failed to execute child  process "dropbox" (No such file or directory)

I/O warning : failed to load external entity "/home/billy/.compiz/session/102536515628010a9f130497489685386600000012960033"

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net  usershare' returned error 255: net usershare: cannot open usershare  directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.



In conclusion, I think your nvidia driver was 'built-in' to your previous kernel version, and the upgrade, updated your kernel version, but did not install the proprietary nvidia patch. So I believe you will need to update the newest kernel to include the nvidia patch.

You can find the update script at [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

---

### Post by m3s3lf on 2011-05-09
> **wilee-nilee said:**
> Hope you get this fixed, you might notice in the reply panel a paperclip this is for uploading pictures, so they don't fill the whole screen.

There is also, a way to wrap the text you have posted to make it easier to read, click on the (#) in the reply panel and paste the text between the code tags.

If you're inclined you can go back and wrap the text manually with the instructions in my sig.;)

Yeah, I was posting from my phone and couldn't resize the picture in order to use the paperclip thing.  I assure you, it would have been easier for me than finding a host and uploading it there, copying and pasting the url (all from my phone).  I'm either browsing on a 55" LCD TV or a 3.8" cell phone, so it's hard for me to tell what it would look like to you all.

Now that I edited the original post, all the text should wrap for you, right?  It seems like it would be easier to read a config file or error log without the wrapping text, but wouldn't that be the [code] tags you suggest?

LMK if you want me to change it somehow.

Thanks,
Billy

---

### Post by redfish77 on 2011-05-09
I had the same problem using a NVIDIA GeForce card connected to a Sharp HDTV with a DVI to HDMI cable. 

In the grub menu, I added the following to the end of the boot line "vga=771" . It showed legible text when X crashed, but I was then able to Alt+F1 to switch to a terminal. I then was able to edit my /etc/X11/xorg.conf file under the screen section to include the following line: Option "UseDisplayDevice" "DFP" . It then booted into X with no crashes using the nvidia v173 proprietary drivers.

---

### Post by m3s3lf on 2011-05-09
> **MAFoElffen said:**
> Once you can get into a text console session, please post your /etc/X11/sorg.conf and the results of 
```

sudo hwinfo --framebuffer
sudo hwinfo --monitor
xrandr -q
lspci | grep VGA

```If "hwinfo" is not installed yet, please install it via 
```

sudo apt-get install hwinfo

```This will tell those here what you have as hardware (video card and monitor), what modes each supports, what drivers it is using and what the configuration file is telling it to do...

Will do, just as soon as I get to a terminal.

> **MAFoElffen said:**
> 
Edit-- I see "since" that you posted "some" of the Xorg.conf... but I'd really like ti see the whole file contents to confirm that it is valid.

I assure you, that is the whole file.

> **MAFoElffen said:**
> 
**Note for others**"  If you are posting a log,file or code, you usually wrap them in **[CODE]** tags.  If it is "long", then warap them in **[HTML]** tags and it will adda vertical srcollbar and make the ppost smaller in size.
Didn't wilee-nilee request that I make it wrap?  I'll change it to whatever you guys want me to.  EDIT - OK, I see now that he probably meant that I should "wrap" the text I pasted in the [code] tags, not that the wanted the text to wrap.

Thanks,
Billy

---

### Post by m3s3lf on 2011-05-09
> **redfish77 said:**
> I had the same problem using a NVIDIA GeForce card connected to a Sharp HDTV with a DVI to HDMI cable. 

In the grub menu, I added the following to the end of the boot line "vga=771" . It showed legible text when X crashed, but I was then able to Alt+F1 to switch to a terminal. I then was able to edit my /etc/X11/xorg.conf file under the screen section to include the following line: Option "UseDisplayDevice" "DFP" . It then booted into X with no crashes using the nvidia v173 proprietary drivers.

I'll try that!  Thank you!

I push the shift key at boot to show the grub menu?

Thanks!
Billy

---

### Post by m3s3lf on 2011-05-09
> **AlphaLexman said:**
> There a couple / few lines that stand out to me...


In conclusion, I think your nvidia driver was 'built-in' to your previous kernel version, and the upgrade, updated your kernel version, but did not install the proprietary nvidia patch. So I believe you will need to update the newest kernel to include the nvidia patch.

You can find the update script at [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Hmmm... seems logical.  I'll see what I can do in that direction.  Thank you for your help!
Billy

---

### Post by redfish77 on 2011-05-09
> **m3s3lf said:**
> I'll try that!  Thank you!

I push the shift key at boot to show the grub menu?

Thanks!
Billy

Yes, if it does not display automatically. Then you have to press 'e' to edit your kernel boot line. Make sure "vga=771" is the last text on the linux ....... line .

These instructions helped a bit:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

