---
title: "Scrolling &quot;failed to execute&quot; messages on 14.04LTS bootup"
date: 2014-07-20
forum: Installation &amp; Upgrades
---

### Post by WB0HYQ on 2014-07-20
Since the very first re-boot on my system as it upgraded from 12.04 to 14.04 I have been getting a lot (perhaps 150) error messages on bootup right after I indicate I want Ubuntu to boot.  They scroll so fast that I cannot read them.  Most of them are as in the post title and the directory indicated is "/lib/dev/socket:.......".  That's as far as I can read before the screen clears and the system starts up.

Anyone know where these messages are coming from?  Is there some sort of boot script that needs to be looked at? Is there a methodology I can use to create a bootlog file?

And, while I'm at it, what happened to the menu item of "Startup Applications"?  It seems to have gone missing.

Bill

---

### Post by slooksterpsv on 2014-07-20
You can check the dmesg logs via terminal
```

dmesg | less

```

It depends on what the message is, I'm wondering if it has something to do with the networking as it references socket.

As for the Startup Applications menu, I have no clue, I use Xubuntu, maybe another member can jump in and reference where it's at. It should be under the System Settings area.

---

### Post by WB0HYQ on 2014-07-21
More Info:

The result of the command given to me in the last post revealed just what I was seeing.  The contents of the attached file is a partial of that output.

Bill

---

### Post by slooksterpsv on 2014-07-22
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/1182801](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/1182801) - may be related to that, the best guess I can give you for what you can do is:
1) Remove HAL
or
2) [quote=Launchpad Bugs]

R.M. Hildigerr V. (moonsdad) wrote on 2013-12-29:	#20
In order to continue using Thoggen, upon updating to Saucy, I installed the old package and it's hal dependency. Then, I began having this issue as well. Rather than remove it as a "fix", I simply commented out the offending line in /lib/udev/rules.d/90-hal.rules

Would it be better to use Michael Blennerhassett's PPA version? I'm not sure what the included arch patches are for.
[/quote]

---

### Post by WB0HYQ on 2014-07-22
According to the bug thread you posted, it seems as if my NVIDIA drivers will revert to a very small screen resolution if I simply remove HAL ( AND, I have no idea how to do that).  The second method is to "comment out the offending line" of '90-hal.rules'.  I suppose I could find that particular file, but what is the "offending line"?

Bill

---

### Post by uRock on 2014-07-22
FWIW, I am using Ubuntu 14.04 and Startup Applications is listed when searching in Unity and it works when opened.

---

### Post by WB0HYQ on 2014-07-22
True.  It does work, and I managed to find it using the Search feature, but it used to be in the "gear" menu over on the upper right of the screen.  I wonder why it was removed.

Bill

---

### Post by WB0HYQ on 2014-07-22
@slooksterpsv:  I found that there is only one line in that file to comment out, so I did.  I received some strange errors in the terminal window (see below), but the line actually was commented out.  I have yet to reboot to see if it worked.

More later.

Errors received:

bill@bill-UBU:~$ sudo gedit /lib/udev/rules.d/90-hal.rules
[sudo] password for bill: 
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory

(gedit:10123): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(gedit:10123): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
bill@bill-UBU:~$ 

I have no idea what these errors mean.

Bill

---

### Post by WB0HYQ on 2014-07-22
YES!  When I rebooted, the error message were gone.  I have my normal screen resolution and everything is running well now.

My thanks to those who helped.  As always, all these little tweaks go down in my spiral notebook for posterity.

Bill

---

### Post by stevecro2 on 2014-11-22
I took another post's suggestion and removed HAL; now have no file called 90-hal.rules and still get boot-up messages anyway. Not really worried about it because everything still starts up OK.

---

### Post by WB0HYQ on 2014-11-22
This thread is over 4 months old.  You probably ought to start a thread of your own if you are still having these problems.

Bill

---

