---
title: "Pidgin 2.2.1 for Feisty"
date: 2007-09-30
forum: Installation &amp; Upgrades
---

### Post by baysao on 2007-09-30
I had built pidgin 2.2.1 deb files from source. You can download [here]("http://files-upload.com/files/533851/pidgin_2.2.1-1_i386.deb"). or [here]("http://www.box.net/shared/8kp3ff67n8")

---

### Post by yimmmy on 2007-09-30
cool thanks but they were already up here                           [http://www.getdeb.net/search.php?keywords=pidgin](http://www.getdeb.net/search.php?keywords=pidgin)

---

### Post by baysao on 2007-09-30
There was some error relate to MSN protocol in version 2.2.0 (see [Changlog]("http://developer.pidgin.im/wiki/ChangeLog")). So you may update to 2.2.1(29/09/07) to fix it.

---

### Post by outer_space on 2007-09-30
Ya ok Im going to sign up for some crap to dload your deb.

---

### Post by hyperair on 2007-10-01
I'm not willing to pay for something I can get freely, but thank you all the same.

---

### Post by jimbo99 on 2007-10-01
Yeah, that's pretty pathetic to force users to sign up for some email collecting site that resells them to spammers, and then asks us to pay them for the right to do so.

---

### Post by baysao on 2007-10-02
Oh,sorry guys. I've just upload in a freehost and share it to you. But it's too bad.So i try upload to other places. Download [here]("http://files-upload.com/files/533851/pidgin_2.2.1-1_i386.deb").

---

### Post by foxmulder881 on 2007-10-02
> **baysao said:**
> There was some error relate to MSN protocol in version 2.2.0 (see [Changlog]("http://developer.pidgin.im/wiki/ChangeLog")). So you may update to 2.2.1(29/09/07) to fix it.

Really?? I'm using 2.2.0 with MSN and I'm having no problems.

---

### Post by hyperair on 2007-10-02
I had file transfer problems. I'd upload a DEB too, but it seems there's already a deb there, and mine's for Gutsy.

---

### Post by baysao on 2007-10-02
> Really?? I'm using 2.2.0 with MSN and I'm having no problems
I'm not using MSN, but there is an announce in pidgin.im site about security bugs relate to MSN ([here]("http://www.pidgin.im/news/security/?id=23")). With 2.2.0, I have a problem : pidgin lose proxy settings when it's restarted. Now,it was fixed.

---

### Post by jimbo99 on 2007-10-06
Sorry. You can not download this file today. Download traffic for your country is empty.

The  above message is generated when an attempt to download the file is made.  It also is a spam site wanting you to pay them for the pleasure of taking your email address and selling it to the spammers.

There certainly are better sites than the two choices made in this thread.

---

### Post by hyperair on 2007-10-06
Here's a list of Gutsy's DEBs:
[http://archive.ubuntu.com/ubuntu/pool/main/p/pidgin/](http://archive.ubuntu.com/ubuntu/pool/main/p/pidgin/)

Get the debs for pidgin, pidgin-data and libpurple0. That's probably all you need actually. Then place them in the same folder, and install them all at the same time:
```

sudo dpkg -i pidgin*deb pidgin-data*deb libpurple0*deb

```

Note: be sure to get the correct packages for your architecture. It's i386 for Intel users,  amd64 for those using 64-bit processors, and powerpc for the older non-Intel Macs. Sparc I'm not sure.

---

### Post by Stud2000 on 2007-10-12
I've Feisty.
[http://archive.ubuntu.com/ubuntu/pool/main/p/pidgin/](http://archive.ubuntu.com/ubuntu/pool/main/p/pidgin/)

```
sudo dpkg -i pidgin*deb pidgin-data*deb libpurple0*deb
(Reading database ... 110518 files and directories currently installed.)
Preparing to replace pidgin 1:2.2.1-1ubuntu3 (using pidgin_2.2.1-1ubuntu3_i386.deb) ...
Unpacking replacement pidgin ...
Preparing to replace pidgin-data 1:2.2.1-1ubuntu3 (using pidgin-data_2.2.1-1ubuntu3_all.deb) ...
Unpacking replacement pidgin-data ...
Preparing to replace pidgin-dbg 1:2.2.1-1ubuntu3 (using pidgin-dbg_2.2.1-1ubuntu3_i386.deb) ...
Unpacking replacement pidgin-dbg ...
Preparing to replace pidgin-dev 1:2.2.1-1ubuntu3 (using pidgin-dev_2.2.1-1ubuntu3_all.deb) ...
Unpacking replacement pidgin-dev ...
Preparing to replace pidgin-data 1:2.2.1-1ubuntu3 (using pidgin-data_2.2.1-1ubuntu3_all.deb) ...
Unpacking replacement pidgin-data ...
Preparing to replace libpurple0 1:2.2.1-1ubuntu3 (using libpurple0_2.2.1-1ubuntu3_i386.deb) ...
Unpacking replacement libpurple0 ...
More than one copy of package pidgin-data has been unpacked
 in this run ! Only configuring it once.
dpkg: dependency problems prevent configuration of pidgin:
 pidgin depends on libc6 (>= 2.6-1); however:
  Version of libc6 on system is 2.5-0ubuntu14.
 pidgin depends on libdbus-1-3 (>= 1.1.1); however:
  Version of libdbus-1-3 on system is 1.0.2-1ubuntu4.
 pidgin depends on libdbus-glib-1-2 (>= 0.74); however:
  Version of libdbus-glib-1-2 on system is 0.73-1.
 pidgin depends on libglib2.0-0 (>= 2.14.0); however:
  Version of libglib2.0-0 on system is 2.12.11-0ubuntu1.
 pidgin depends on libgstreamer0.10-0 (>= 0.10.14); however:
  Version of libgstreamer0.10-0 on system is 0.10.12-0ubuntu2.
 pidgin depends on libgtk2.0-0 (>= 2.12.0); however:
  Version of libgtk2.0-0 on system is 2.10.11-0ubuntu3.
 pidgin depends on libgtkspell0 (>= 2.0.2); however:
  Package libgtkspell0 is not installed.
 pidgin depends on libpango1.0-0 (>= 1.18.2); however:
  Version of libpango1.0-0 on system is 1.16.2-0ubuntu1.
 pidgin depends on libsqlite3-0 (>= 3.4.2); however:
  Version of libsqlite3-0 on system is 3.3.13-0ubuntu1.
 pidgin depends on libxdamage1 (>= 1:1.1); however:
  Version of libxdamage1 on system is 1:1.0.3-3.
dpkg: error processing pidgin (--install):
 dependency problems - leaving unconfigured
Setting up pidgin-data (2.2.1-1ubuntu3) ...

dpkg: dependency problems prevent configuration of pidgin-dev:
 pidgin-dev depends on pidgin (>= 1:2.2.1-1ubuntu3); however:
  Package pidgin is not configured yet.
 pidgin-dev depends on pkg-config; however:
  Package pkg-config is not installed.
 pidgin-dev depends on libpurple-dev; however:
  Package libpurple-dev is not installed.
 pidgin-dev depends on libgtk2.0-dev; however:
  Package libgtk2.0-dev is not installed.
dpkg: error processing pidgin-dev (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpurple0:
 libpurple0 depends on libc6 (>= 2.6-1); however:
  Version of libc6 on system is 2.5-0ubuntu14.
 libpurple0 depends on libdbus-1-3 (>= 1.1.1); however:
  Version of libdbus-1-3 on system is 1.0.2-1ubuntu4.
 libpurple0 depends on libdbus-glib-1-2 (>= 0.74); however:
  Version of libdbus-glib-1-2 on system is 0.73-1.
 libpurple0 depends on libglib2.0-0 (>= 2.14.0); however:
  Version of libglib2.0-0 on system is 2.12.11-0ubuntu1.
 libpurple0 depends on libxml2 (>= 2.6.29); however:
  Version of libxml2 on system is 2.6.27.dfsg-1ubuntu3.
dpkg: error processing libpurple0 (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pidgin-dbg:
 pidgin-dbg depends on pidgin (= 1:2.2.1-1ubuntu3) | finch (= 1:2.2.1-1ubuntu3) | libpurple0 (= 1:2.2.1-1ubuntu3); however:
  Package pidgin is not configured yet.
  Package finch is not installed.
  Package libpurple0 is not configured yet.
dpkg: error processing pidgin-dbg (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 pidgin
 pidgin-dev
 libpurple0
 pidgin-dbg

```

what can i do with this?

---

### Post by hyperair on 2007-10-12
Well.. there's always the easy way out.. wait one week, then upgrade to Gutsy. =P

---

### Post by bradmayne on 2007-10-15
yeah dude your a straight up faggot queen for trying to do us dirty if i ever saw you in person i'd spit in your face and then make your whore of a mother lick it off you.  i hope you rot in hell you went against everything linux stands for you double used douchebag!

---

### Post by FredB on 2007-10-15
The simple thing to do is to go to getdeb.net.

And you'll get a fully working version of pidgin 2.2.1.

---

### Post by coldstatue on 2007-10-16
Ok, this is driving me crazy. getdeb does not have 2.2.1, only 2.2.0. So, I went to pidgin's home page, downloaded and compiled according to the instructions. Unfortunately it installed to some directory different than the one(s) expected by the awn plug, the guification deb, and the rest of the world, apparently. I tried make uninstall, make remove, make clean, and anything else I could come up with in this frustrating mess. 

I tried [http://archive.ubuntu.com/ubuntu/pool/main/p/pidgin/](http://archive.ubuntu.com/ubuntu/pool/main/p/pidgin/) as suggested above out of desperation (i'm on Feisty) but get a missing dependency for lib c6, even though I have it installed. I now how mismatched pidgin-data and pidgin installed, and I don't even know how to get rid of it. My biggest problem is that incoming text is black, on my black background, and I don't want to change my ubuntu theme - just my pidgin one. SO. If I can't get guification, libnotify, and the awn plug working, I at least want to be able to READ the incoming messages. What can I do? It's such a mess, I don't have any idea where to go from here. I know I screwed up. How do i fix it? Can I just delete some file folders?

---

### Post by hyperair on 2007-10-16
Remove both pidgin-data and pidgin packages:
```
sudo apt-get autoremove pidgin-data pidgin
```

Then start over. I really suggest you upgrade to Gutsy though. It'll be out in two days.

EDIT: Sorry I didn't see your complaint about the colour. There's this plugin called "conversation colours". Use it. You can override all the incoming messages' colours.

---

### Post by coldstatue on 2007-10-16
Thank you... seriously. I will upgrade but I really need this tonight, though I will be upgrading within the week.

---

### Post by coldstatue on 2007-10-16
Ok, so far so good but, look what happens when i go into
~/avant-window-navigator/trunk/awn-plugins/pidgin and type make
```
:~/avant-window-navigator/trunk/awn-plugins/pidgin$ make
gcc -fPIC -Wall -c pidgin_awn.c -o pidgin_awn.o -DVERSION=\"`date "+%Y%m-%d_%R"`\" `pkg-config --cflags gtk+-2.0 pidgin purple atk cairo pango glib-2.0 dbus-1`
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package pidgin was not found in the pkg-config search path.
Perhaps you should add the directory containing `pidgin.pc'
to the PKG_CONFIG_PATH environment variable
No package 'pidgin' found
Package purple was not found in the pkg-config search path.
Perhaps you should add the directory containing `purple.pc'
to the PKG_CONFIG_PATH environment variable
No package 'purple' found
Package atk was not found in the pkg-config search path.
Perhaps you should add the directory containing `atk.pc'
to the PKG_CONFIG_PATH environment variable
No package 'atk' found
Package cairo was not found in the pkg-config search path.
Perhaps you should add the directory containing `cairo.pc'
to the PKG_CONFIG_PATH environment variable
No package 'cairo' found
Package pango was not found in the pkg-config search path.
Perhaps you should add the directory containing `pango.pc'
to the PKG_CONFIG_PATH environment variable
No package 'pango' found
Package glib-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `glib-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'glib-2.0' found
pidgin_awn.c:36:26: error: conversation.h: No such file or directory
pidgin_awn.c:37:19: error: debug.h: No such file or directory
pidgin_awn.c:38:20: error: plugin.h: No such file or directory
pidgin_awn.c:39:19: error: prefs.h: No such file or directory
pidgin_awn.c:40:21: error: signals.h: No such file or directory
pidgin_awn.c:41:19: error: sound.h: No such file or directory
pidgin_awn.c:42:21: error: version.h: No such file or directory
pidgin_awn.c:44:24: error: gtkaccount.h: No such file or directory
pidgin_awn.c:45:22: error: gtkblist.h: No such file or directory
pidgin_awn.c:46:21: error: gtkconv.h: No such file or directory
pidgin_awn.c:47:23: error: gtkplugin.h: No such file or directory
pidgin_awn.c:48:22: error: gtkprefs.h: No such file or directory
pidgin_awn.c:49:30: error: gtksavedstatuses.h: No such file or directory
pidgin_awn.c:50:22: error: gtksound.h: No such file or directory
pidgin_awn.c:51:22: error: gtkutils.h: No such file or directory
pidgin_awn.c:52:25: error: pidginstock.h: No such file or directory
pidgin_awn.c:53:24: error: gtkdocklet.h: No such file or directory
pidgin_awn.c:54:24: error: gtkdialogs.h: No such file or directory
pidgin_awn.c:56:20: error: stdlib.h: No such file or directory
pidgin_awn.c:57:18: error: glib.h: No such file or directory
pidgin_awn.c:58:28: error: dbus/dbus-glib.h: No such file or directory
pidgin_awn.c:59:37: error: dbus/dbus-glib-bindings.h: No such file or directory
In file included from pidgin_awn.c:61:
pidgin_awn.h:56: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
pidgin_awn.h:57: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;awn_update_status&#8217;
pidgin_awn.h:58: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;plugin_load&#8217;
pidgin_awn.h:59: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;plugin_unload&#8217;
pidgin_awn.c:65: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;info&#8217;
pidgin_awn.c: In function &#8216;setAwnIcon&#8217;:
pidgin_awn.c:95: error: &#8216;DBusGConnection&#8217; undeclared (first use in this function)
pidgin_awn.c:95: error: (Each undeclared identifier is reported only once
pidgin_awn.c:95: error: for each function it appears in.)
pidgin_awn.c:95: error: &#8216;connection&#8217; undeclared (first use in this function)
pidgin_awn.c:96: error: &#8216;DBusGProxy&#8217; undeclared (first use in this function)
pidgin_awn.c:96: error: &#8216;proxy&#8217; undeclared (first use in this function)
pidgin_awn.c:97: error: &#8216;GError&#8217; undeclared (first use in this function)
pidgin_awn.c:97: error: &#8216;error&#8217; undeclared (first use in this function)
pidgin_awn.c:99: warning: implicit declaration of function &#8216;g_type_init&#8217;
pidgin_awn.c:101: error: &#8216;NULL&#8217; undeclared (first use in this function)
pidgin_awn.c:102: warning: implicit declaration of function &#8216;dbus_g_bus_get&#8217;
pidgin_awn.c:102: error: &#8216;DBUS_BUS_SESSION&#8217; undeclared (first use in this function)
pidgin_awn.c:106: warning: implicit declaration of function &#8216;dbus_g_proxy_new_for_name&#8217;
pidgin_awn.c:112: warning: implicit declaration of function &#8216;dbus_g_proxy_call&#8217;
pidgin_awn.c:112: error: &#8216;G_TYPE_STRING&#8217; undeclared (first use in this function)
pidgin_awn.c:113: error: &#8216;G_TYPE_INVALID&#8217; undeclared (first use in this function)
pidgin_awn.c: In function &#8216;unsetAwnIcon&#8217;:
pidgin_awn.c:118: error: &#8216;DBusGConnection&#8217; undeclared (first use in this function)
pidgin_awn.c:118: error: &#8216;connection&#8217; undeclared (first use in this function)
pidgin_awn.c:119: error: &#8216;DBusGProxy&#8217; undeclared (first use in this function)
pidgin_awn.c:119: error: &#8216;proxy&#8217; undeclared (first use in this function)
pidgin_awn.c:120: error: &#8216;GError&#8217; undeclared (first use in this function)
pidgin_awn.c:120: error: &#8216;error&#8217; undeclared (first use in this function)
pidgin_awn.c:124: error: &#8216;NULL&#8217; undeclared (first use in this function)
pidgin_awn.c:125: error: &#8216;DBUS_BUS_SESSION&#8217; undeclared (first use in this function)
pidgin_awn.c:136: error: &#8216;G_TYPE_STRING&#8217; undeclared (first use in this function)
pidgin_awn.c:136: error: &#8216;G_TYPE_INVALID&#8217; undeclared (first use in this function)
pidgin_awn.c: In function &#8216;setAwnInfo&#8217;:
pidgin_awn.c:141: error: &#8216;DBusGConnection&#8217; undeclared (first use in this function)
pidgin_awn.c:141: error: &#8216;connection&#8217; undeclared (first use in this function)
pidgin_awn.c:142: error: &#8216;DBusGProxy&#8217; undeclared (first use in this function)
pidgin_awn.c:142: error: &#8216;proxy&#8217; undeclared (first use in this function)
pidgin_awn.c:143: error: &#8216;GError&#8217; undeclared (first use in this function)
pidgin_awn.c:143: error: &#8216;error&#8217; undeclared (first use in this function)
pidgin_awn.c:147: error: &#8216;NULL&#8217; undeclared (first use in this function)
pidgin_awn.c:148: error: &#8216;DBUS_BUS_SESSION&#8217; undeclared (first use in this function)
pidgin_awn.c:158: error: &#8216;G_TYPE_STRING&#8217; undeclared (first use in this function)
pidgin_awn.c:159: error: &#8216;G_TYPE_INVALID&#8217; undeclared (first use in this function)
pidgin_awn.c: At top level:
pidgin_awn.c:163: error: expected &#8216;)&#8217; before &#8216;xid&#8217;
pidgin_awn.c: In function &#8216;unsetAwnInfo&#8217;:
pidgin_awn.c:187: error: &#8216;DBusGConnection&#8217; undeclared (first use in this function)
pidgin_awn.c:187: error: &#8216;connection&#8217; undeclared (first use in this function)
pidgin_awn.c:188: error: &#8216;DBusGProxy&#8217; undeclared (first use in this function)
pidgin_awn.c:188: error: &#8216;proxy&#8217; undeclared (first use in this function)
pidgin_awn.c:189: error: &#8216;GError&#8217; undeclared (first use in this function)
pidgin_awn.c:189: error: &#8216;error&#8217; undeclared (first use in this function)
pidgin_awn.c:193: error: &#8216;NULL&#8217; undeclared (first use in this function)
pidgin_awn.c:194: error: &#8216;DBUS_BUS_SESSION&#8217; undeclared (first use in this function)
pidgin_awn.c:204: error: &#8216;G_TYPE_STRING&#8217; undeclared (first use in this function)
pidgin_awn.c:205: error: &#8216;G_TYPE_INVALID&#8217; undeclared (first use in this function)
pidgin_awn.c: At top level:
pidgin_awn.c:231: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
pidgin_awn.c:254: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;awn_update_status&#8217;
pidgin_awn.c: In function &#8216;awn_update_status_cb&#8217;:
pidgin_awn.c:342: warning: implicit declaration of function &#8216;awn_update_status&#8217;
pidgin_awn.c: At top level:
pidgin_awn.c:345: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
pidgin_awn.c:351: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
pidgin_awn.c:356: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
pidgin_awn.c:361: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
pidgin_awn.c:365: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
pidgin_awn.c:369: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
pidgin_awn.c:373: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;plugin_load&#8217;
pidgin_awn.c:407: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;plugin_unload&#8217;
pidgin_awn.c:413: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
pidgin_awn.c:416: warning: return type defaults to &#8216;int&#8217;
pidgin_awn.c: In function &#8216;PURPLE_INIT_PLUGIN&#8217;:
pidgin_awn.c:416: error: expected &#8216;{&#8217; at end of input
make: *** [pidgin_awn.o] Error 1

```

I did a make and sudo make install with it earlier, with a different install of pidgin. (For that pidgin install I downloaded and comiled the source from the pidgin homepage) That install used the wrong path (according to the rest of the apps that interface with pidgin) and the awn plug gave me an error that the folder didn't exist. Is there anything I can do about this?

Thank you

---

### Post by overlord_david on 2007-10-24
Gah... I tried installing that deb. When I got to "About" in my current pidgin it says I have ver 2.0.2 but when I tried the deb it said I already have a newer version of pidgin. >_>;

---

### Post by hyperair on 2007-10-24
How about checking the version of Pidgin in Apt?
```
apt-cache policy pidgin
```

---

### Post by overlord_david on 2007-10-24
Okay, so because one of the pidgin things only half installed. I accedentally uninstalled my pidgin 2.0.0  

Now I was able to get this deb in. But it has HORRIBLE sound. Is this normal?? Cause before Pidgin had sound for comming/going list people  and for when you send and recieve a messege, each of which were nice and obvious. 

Now all it's doing is a crappy little console beep I really can barely hear.
How do I get the sound back in my pidgin?

---

