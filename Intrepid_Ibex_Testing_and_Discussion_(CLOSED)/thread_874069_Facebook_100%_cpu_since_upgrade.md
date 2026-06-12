---
title: "Facebook 100% cpu since upgrade"
date: 2008-07-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by LittleKoy on 2008-07-29
Hello, I went abroad for 2 weeks, and when I came back I did a massive upgrade (about 350mb). Since then, facebook became very very slow, it kills my cpu (both old and new), just looking at the homepage gets my cpu crazy... I used both FireFox3 and Opera, with same result

---

### Post by psyke83 on 2008-07-29
> **LittleKoy said:**
> Hello, I went abroad for 2 weeks, and when I came back I did a massive upgrade (about 350mb). Since then, facebook became very very slow, it kills my cpu (both old and new), just looking at the homepage gets my cpu crazy... I used both FireFox3 and Opera, with same result

It's most likely a Flash problem. Since beta 2, CPU usage is quite high for some flash content (but not all). A workaround is to downgrade to beta 1 of Flash 10.

Download this archive, then copy to "/var/cache/flashplugin-nonfree/": [http://www.megaupload.com/?d=6EXVWL10](http://www.megaupload.com/?d=6EXVWL10)

Then, download and install the beta 1 deb (i386): [http://launchpadlibrarian.net/14629821/flashplugin-nonfree_10.0.1.218ubuntu1_i386.deb](http://launchpadlibrarian.net/14629821/flashplugin-nonfree_10.0.1.218ubuntu1_i386.deb)

Restart Firefox for changes to take place. You should also hold back the flashplugin-nonfree package for upgrades, otherwise you'll get beta 2 again.

---

### Post by klange on 2008-07-29
Facebook is not normally Flash heavy, but it is very slow (I have had the same problems for quite a while, even back in Hardy).

Can't provide any insight, though.

---

### Post by BwackNinja on 2008-07-29
Turn off javascript. Edit > Preferences > Content and uncheck it. Either a problem with javascript or a problem with facebook's use of it.

---

### Post by thedevnull on 2008-07-29
> **LittleKoy said:**
> Hello, I went abroad for 2 weeks, and when I came back I did a massive upgrade (about 350mb). Since then, facebook became very very slow, it kills my cpu (both old and new), just looking at the homepage gets my cpu crazy... I used both FireFox3 and Opera, with same result

Does it happen at any other time?  On any other website?  Have you taken a look at the two Firefox Add-on: AD Block Pro (blocks ads) and NoScript (blocks java/javascript and flash)?  This will block all the crap from the social networking sites you don't need or want to run in your browser.  You then can will great granularity select which sites or parts of sites that you trust to have content run in your browser.  Check em out...

Let me know how it goes...

---

### Post by BwackNinja on 2008-07-29
[www.megaupload.com](www.megaupload.com) has the same problem and turning off javascript fixes that too, so I'd expect that something is going screwy with javascript.

---

### Post by psyke83 on 2008-07-29
> **BwackNinja said:**
> [www.megaupload.com](www.megaupload.com) has the same problem and turning off javascript fixes that too, so I'd expect that something is going screwy with javascript.

Are you sure about it? Perhaps turning off javascript caused those *huge* flash animations to also get disabled. I'm 99% sure this issue is with flash, as I said earlier. Using beta 2, some flash content now seems to use bilinear filtering, and that causes extreme slowdown, of which megaupload.com is one of these offenders.

Try beta 1 and see if it helps.

---

### Post by psyke83 on 2008-07-29
> **WindowsSucks said:**
> Facebook is not normally Flash heavy, but it is very slow (I have had the same problems for quite a while, even back in Hardy).

Can't provide any insight, though.

Unfortunately I don't have a Facebook account. Can anyone verify if it uses flash content for the interface or advertisements? For the latter, ensure you have adblock plus/noscript disabled in order to see the unmodified version of the site.

---

### Post by Lem on 2008-07-30
Are you getting a fairly high cpu load (50-60%) at other times? What chip/chipset are you using? I'm getting something very similar to this but the with a new build on very recent hardware, so it may/may not be related.

---

### Post by gjoellee on 2008-07-30
it might help to use flash 10beta which works better in Hardy then flash 9 take a look here: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by gjoellee on 2008-07-30
this tweak might help to: (for firefox)
1.Type &#8220;about:config&#8221; into the address bar and hit return. Scroll down and look for the following entries:
 network.http.pipelining network.http.proxy.pipelining network.http.pipelining.maxrequests
 Normally the browser will make one request to a web page at a time. When you enable pipelining it will make several at once, which really speeds up page loading.
 2. Alter the entries as follows:
 Set &#8220;network.http.pipelining&#8221; to &#8220;true&#8221;
 Set &#8220;network.http.proxy.pipelining&#8221; to &#8220;true&#8221;
 Set &#8220;network.http.pipelining.maxrequests&#8221; to some number like 30. This means it will make 30 requests at once.
 3. Lastly right-click anywhere and select New-> Integer. Name it &#8220;nglayout.initialpaint.delay&#8221; and set its value to &#8220;0&#8243;. This value is the amount of time the browser waits before it acts on information it receives.

---

### Post by LittleKoy on 2008-07-30
Wow, thank you :D

Well, turning off Javascript indeed fixes (I use noScript), but a lot of features are missing... And if it's a flash problem, JS solves it just indirectly...
Unfortunately the tweak in FF config didn't work :(

I'm not a fan of downgrade, and even if it's a flash issue, I'd prefer to wait for it to be fixed... But FB became really impossible to use, so I'll make an exception :D
I'll let you know how it goes.

PS: since someone was talking abnout MegaUpload doing the same joke.. I went there to download what psyke, and it really does. Furthermore, it doesn't load the buttons and the girls photo it usually shows, but the right animation about Visitor Exchanges or toolbar yes. Also, when I change tab, the cpu overload stops and goes very low, so it's probably an issue in visualization, which strenghten flash option...

---

### Post by LittleKoy on 2008-07-30
Yes, downgrading as psyke suggested fixed. Thank you so much :)

BTW, are they going to fix it? Because someone said that this is caused by usage of bilinear filter. Is this a final choice or just a temp issue?

---

### Post by psyke83 on 2008-07-30
Edit: you tested beta 1, cool.

I certainly hope it gets fixed :). You should keep an eye on [http://labs.adobe.com](http://labs.adobe.com) and [http://blogs.adobe.com/penguin.swf/](http://blogs.adobe.com/penguin.swf/) for status updates on Flash.

Also note that Firefox has a serious bug when you use beta 2 (causes Firefox to crash on many sites). Beta 1 doesn't seem to have this problem, but newer versions definitely will. Hopefully the next release of Firefox will include the fix; otherwise, see: [http://ubuntuforums.org/showpost.php?p=5472028&postcount=33](http://ubuntuforums.org/showpost.php?p=5472028&postcount=33)

---

### Post by LittleKoy on 2008-07-30
Yes, I noticed that ff crashed every 2 youtube videos... actually, it crashed before updating too, but much less... Let's see now ;)

---

### Post by Gourgi on 2008-07-30
i'm gettind this messages from firefox while various untitled little windows popup when i visit this page [http://www.contra.gr/](http://www.contra.gr/) .
i doesn't happens anytime but about 3 out of 10 times for sure.
i already use firefox's flashblock plugin

here is some log
```

$firefox
GCJ PLUGIN: thread 0x695220: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x695220: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x695220: NP_GetValue
GCJ PLUGIN: thread 0x695220: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x695220: NP_GetValue return
GCJ PLUGIN: thread 0x695220: NP_GetValue
GCJ PLUGIN: thread 0x695220: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x695220: NP_GetValue return
GCJ PLUGIN: thread 0x695220: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x695220: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x695220: NP_GetValue
GCJ PLUGIN: thread 0x695220: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x695220: NP_GetValue return
GCJ PLUGIN: thread 0x695220: NP_GetValue
GCJ PLUGIN: thread 0x695220: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x695220: NP_GetValue return
*** NSPlugin Viewer  *** WARNING: unhandled variable 17 in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: Unimplemented function g_NPN_SetValue at line 920
/usr/share/themes/NewHuman/gtk-2.0/gtkrc:79: error: unexpected identifier `colorize_scrollbar', expected character `}'
Fontconfig warning: "/etc/fonts/conf.d/53-monospace-lcd-filter.conf", line 17: invalid constant used : lcdlegacy

(npviewer.bin:13724): Gdk-WARNING **: GdkWindow 0x5a00020 unexpectedly destroyed
The program 'npviewer.bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadDrawable (invalid Pixmap or Window parameter)'.
  (Details: serial 236 error_code 9 request_code 55 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
*** NSPlugin Wrapper *** ERROR: NPP_Destroy() wait for reply: Connection closed
*** NSPlugin Wrapper *** ERROR: NPClass::Invalidate() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NP_Shutdown() invoke: Connection closed
*** NSPlugin Viewer  *** WARNING: unhandled variable 17 in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: Unimplemented function g_NPN_SetValue at line 920
/usr/share/themes/NewHuman/gtk-2.0/gtkrc:79: error: unexpected identifier `colorize_scrollbar', expected character `}'
Fontconfig warning: "/etc/fonts/conf.d/53-monospace-lcd-filter.conf", line 17: invalid constant used : lcdlegacy

(npviewer.bin:13740): Gdk-WARNING **: GdkWindow 0x5a00020 unexpectedly destroyed

(npviewer.bin:13740): Gdk-WARNING **: GdkWindow 0x5a0001f unexpectedly destroyed

(npviewer.bin:13740): Gdk-WARNING **: GdkWindow 0x5a0001e unexpectedly destroyed

(npviewer.bin:13740): Gdk-WARNING **: GdkWindow 0x5a00003 unexpectedly destroyed

(npviewer.bin:13740): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed
The program 'npviewer.bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 237 error_code 3 request_code 18 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
*** NSPlugin Wrapper *** ERROR: NPP_GetValue() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_GetValue() invoke: Connection closed
*** NSPlugin Wrapper *** WARNING: unhandled variable 11 in NPP_GetValue()
*** NSPlugin Wrapper *** ERROR: NPP_SetWindow() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_Destroy() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPClass::Invalidate() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NPP_Destroy() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NP_Shutdown() invoke: Connection closed
*** NSPlugin Viewer  *** WARNING: unhandled variable 17 in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: Unimplemented function g_NPN_SetValue at line 920
/usr/share/themes/NewHuman/gtk-2.0/gtkrc:79: error: unexpected identifier `colorize_scrollbar', expected character `}'

(npviewer.bin:13755): Gdk-WARNING **: GdkWindow 0x5a00020 unexpectedly destroyed

(npviewer.bin:13755): Gdk-WARNING **: GdkWindow 0x5a0001f unexpectedly destroyed

(npviewer.bin:13755): Gdk-WARNING **: GdkWindow 0x5a0001e unexpectedly destroyed

(npviewer.bin:13755): Gdk-WARNING **: GdkWindow 0x5a00003 unexpectedly destroyed

(npviewer.bin:13755): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed
The program 'npviewer.bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 237 error_code 3 request_code 18 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
*** NSPlugin Wrapper *** ERROR: NPP_Destroy() invoke: Connection reset by peer
*** NSPlugin Wrapper *** ERROR: NPClass::Invalidate() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NP_Shutdown() invoke: Connection closed
*** NSPlugin Viewer  *** WARNING: unhandled variable 17 in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: Unimplemented function g_NPN_SetValue at line 920
/usr/share/themes/NewHuman/gtk-2.0/gtkrc:79: error: unexpected identifier `colorize_scrollbar', expected character `}'
Fontconfig warning: "/etc/fonts/conf.d/53-monospace-lcd-filter.conf", line 17: invalid constant used : lcdlegacy

(npviewer.bin:13910): Gdk-WARNING **: GdkWindow 0x5a00020 unexpectedly destroyed
The program 'npviewer.bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadDrawable (invalid Pixmap or Window parameter)'.
  (Details: serial 236 error_code 9 request_code 55 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
*** NSPlugin Wrapper *** ERROR: NPP_Destroy() wait for reply: Connection closed
*** NSPlugin Wrapper *** ERROR: NPClass::Invalidate() invoke: Connection closed
*** NSPlugin Wrapper *** ERROR: NP_Shutdown() invoke: Connection closed
/usr/share/themes/NewHuman/gtk-2.0/gtkrc:79: error: unexpected identifier `colorize_scrollbar', expected character `}'

(npviewer.bin:13927): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:13927): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

```

has anyone seen something like this ?
is there already a bug report for my problem? cause i can't find it in launchpad

---

### Post by MaX on 2008-07-30
Try [http://www.new.facebook.com](http://www.new.facebook.com) and see if their new layout helps

---

### Post by Choad on 2008-09-25
> **BwackNinja said:**
> Turn off javascript. Edit > Preferences > Content and uncheck it. Either a problem with javascript or a problem with facebook's use of it.

best. fix. ever.



(note: facebook presents you with a blank page with js disabled. certainly solves the cpu usage problem)

---

### Post by c1rcu17 on 2008-09-26
I have the exact same problem. When I downgraded to flash 9, facebook and other sites that slowed fixed itself. With me, Xorg would take anywhere from 50 - 100% cpu usage. After the downgrade, everything worked fine.

---

### Post by syko21 on 2008-09-26
Just out of curiosity, what parts of facebook use javascript? Basically what functionality do I lose to disabling JS?

---

### Post by BwackNinja on 2008-09-26
The problem is in flash, some stuff won't work with facebook without javascript (though I haven't checked in a while). I'd actually recommend upgrading flash via this: [https://launchpad.net/~psyke83/+archive](https://launchpad.net/~psyke83/+archive) ppa (psyke83's) I'd just download the .deb so you don't mess with other stuff.

---

### Post by wakingrufus on 2008-09-27
i had the same problem.  adblocking "http://www.new.facebook.com/swf/SoundPlayer.swf" fixed it without disabling any features that i can see.

---

### Post by UbuWu on 2008-09-27
Here is the corresponding bug report: [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/251700](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/251700)

---

### Post by psyke83 on 2008-09-27
Please, stop the madness. This is **not** a Facebook issue, **not** a Javascript issue, and **not** a Firefox issue - it **is** a Flash issue. 

The version of Flash in Intrepid (10.0.1.218+10.0.0.525ubuntu1, actually 10.0.0.525, which is Flash 10 beta 2) has a major performance regression from previous versions. For some inexplicable reason, some Flash content appears to have a bilinear filter applied, which causes *extreme* CPU usage, and Facebook is an example of this.

The solution is to upgrade Flash (which is taking some time due to complexity for 64 bit users). I have marked those bug reports as a duplicate of the FFe for Flash 10 RC2 (which solves the performance issues).

As I said before, if you're really impatient and want to try the new version now, check my PPA.

---

### Post by stewacide on 2008-09-27
Thanks for the explanation. Hope this gets fixed soon.

edit -- *****, I just remembered the reason I upgraded to Flash 10 in the first place: Flash9s PulseAudio bugs causing Firefox to crash!!!

Is there any version of Flash 9/10 that doesn't crash constantly and doesn't consume 100% of CPU? Deb link plz??

---

