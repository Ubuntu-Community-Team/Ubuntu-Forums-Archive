---
title: "Songbird 1.1"
date: 2009-03-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jblackhall on 2009-03-11
I just read that [Songbird 1.1 was released]("http://blog.songbirdnest.com/2009/03/10/songbird-11-is-here/").  This project is *quickly* shaping up to be a fantastic project.  They now have automatic folder watching and they're working hard to decrease their memory footprint.

Upon reading that [Rhythmbox is on its way out]("http://ubuntuforums.org/showthread.php?t=1076064"), this looks to be a strong contender (along with Banshee) to replace it.

I've got 2 questions.  Will 1.1 make it into Jaunty?  And if not, is there a PPA available for Songbird with the latest release?

---

### Post by rtalcott on 2009-03-11
getdeb has songbird 1.1.1

---

### Post by rtalcott on 2009-03-11
that getdeb songbird is for 8.10....just noticed that.

---

### Post by jfernyhough on 2009-03-11
I've not yet found a package for Intrepid (certainly on GetDeb) that doesn't work on Jaunty.

Anyhow, you could always download from the official site and unzip to your user area. I have a load of binaries in /home/me/bin (FF 3.2a1pre, Netbeans 6.5, RSSOwl 0.9, Thunderbird 3.0b3pre, Seamonkey 2.0a1pre, Kerkythea2008, etc etc).

---

### Post by jblackhall on 2009-03-11
fta just got back to me.  This looks good: [https://bugs.launchpad.net/ubuntu/+bug/94494](https://bugs.launchpad.net/ubuntu/+bug/94494)  I was thinking of filing the same bug myself :)  But unfortunately it looks like zero chance of making it into Jaunty :(

---

### Post by afv on 2009-03-11
> **rtalcott said:**
> getdeb has songbird 1.1.1

Thanks :)

I was just searching, minutes ago, for some PPA with the new version... Came here now to check unread topics and this was the first on the list :lol:


> Preparing to replace songbird 1.0.0+0-0ubuntu1~fta6 (using .../songbird_1.1.1-1~getdeb1_i386.deb) ...

:popcorn:

---

### Post by cl333r on 2009-03-11
Tried installing from getdeb, Sonbird won't start, thought it's a package issue. Downloaded the official release from getsongbird.com, yet I get:

> fox@fox-desktop:~/apps/Songbird$ ./songbird
*** glibc detected *** ././songbird-bin: free(): invalid pointer: 0xb3215620 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7d29454]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb7d2b4b6]
/usr/lib/libvisual-0.4.so.0(visual_mem_free+0x21)[0xb3032141]
/usr/lib/libvisual-0.4.so.0[0xb3029407]
/usr/lib/libvisual-0.4.so.0(visual_plugin_get_list+0x73)[0xb30295e3]
/usr/lib/libvisual-0.4.so.0(visual_init+0x291)[0xb3038ec1]
/usr/lib/gstreamer-0.10/libgstlibvisual.so[0xb30921f4]
/home/fox/apps/Songbird/lib/libgstreamer-0.10.so[0xb3ea52f6]
/home/fox/apps/Songbird/lib/libgstreamer-0.10.so(gst_plugin_load_file+0x62f)[0xb3ea5bad]
/home/fox/apps/Songbird/lib/libgstreamer-0.10.so[0xb3eb0822]
/home/fox/apps/Songbird/lib/libgstreamer-0.10.so(gst_registry_scan_path+0x135)[0xb3eb09c7]
/home/fox/apps/Songbird/lib/libgstreamer-0.10.so[0xb3e60a44]
/home/fox/apps/Songbird/lib/libgstreamer-0.10.so[0xb3e60f30]
/home/fox/apps/Songbird/lib/libgstreamer-0.10.so[0xb3e61589]
/home/fox/apps/Songbird/lib/libgstreamer-0.10.so[0xb3e61b44]
/usr/lib/libglib-2.0.so.0(g_option_context_parse+0x5b3)[0xb6b1a7e3]
/home/fox/apps/Songbird/lib/libgstreamer-0.10.so(gst_init_check+0xf1)[0xb3e5fd1b]
/home/fox/apps/Songbird/lib/libgstreamer-0.10.so(gst_init+0x32)[0xb3e5fe25]
/home/fox/apps/Songbird/lib/sbGStreamerMediacore.so(_ZN18sbGStreamerService4InitEv+0x9ff)[0xb3d7a6a3]
/home/fox/apps/Songbird/lib/sbGStreamerMediacore.so[0xb3d82a05]
/home/fox/apps/Songbird/lib/sbGStreamerMediacore.so[0xb3d8bdb6]
/home/fox/apps/Songbird/xulrunner/libxul.so[0xb75d9a85]
/home/fox/apps/Songbird/xulrunner/libxul.so[0xb75d8f47]
/home/fox/apps/Songbird/lib/sbGStreamerMediacore.so[0xb3d88e83]
/home/fox/apps/Songbird/lib/sbGStreamerMediacore.so[0xb3d88ead]
/home/fox/apps/Songbird/lib/sbGStreamerMediacore.so[0xb3d88659]
/home/fox/apps/Songbird/lib/sbGStreamerMediacore.so[0xb3d81413]
/home/fox/apps/Songbird/lib/sbGStreamerMediacore.so(_ZN27sbGStreamerMediacoreFactory4InitEv+0x46)[0xb3d81be0]
/home/fox/apps/Songbird/lib/sbGStreamerMediacore.so[0xb3d82965]
/home/fox/apps/Songbird/lib/sbGStreamerMediacore.so[0xb3d8bdb6]
/home/fox/apps/Songbird/xulrunner/libxul.so[0xb75d9a85]
/home/fox/apps/Songbird/components/sbMediacoreManager.so[0xb4face29]
/home/fox/apps/Songbird/components/sbMediacoreManager.so[0xb4face56]
/home/fox/apps/Songbird/components/sbMediacoreManager.so[0xb4fac6f1]
/home/fox/apps/Songbird/components/sbMediacoreManager.so(_ZN8nsCOMPtrI19sbIMediacoreFactoryEC1ERK15nsCOMPtr_helper+0x2d)[0xb4f95705]
/home/fox/apps/Songbird/components/sbMediacoreManager.so(_ZN18sbMediacoreManager4InitEv+0x1b7)[0xb4f932d7]
/home/fox/apps/Songbird/components/sbMediacoreManager.so[0xb4f93654]
/home/fox/apps/Songbird/xulrunner/libxul.so[0xb75b6773]
/home/fox/apps/Songbird/xulrunner/libxul.so[0xb75b6d18]
/home/fox/apps/Songbird/xulrunner/libxul.so[0xb6e4abe0]
/home/fox/apps/Songbird/xulrunner/libxul.so(XRE_main+0x19af)[0xb6e488c1]
././songbird-bin[0x8048f40]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7cd0685]
././songbird-bin[0x8048bb1]
======= Memory map: ========
08048000-0804e000 r-xp 00000000 08:06 1145550    /home/fox/apps/Songbird/songbird-bin
0804e000-0804f000 rw-p 00006000 08:06 1145550    /home/fox/apps/Songbird/songbird-bin
081b3000-081d4000 rw-p 081b3000 00:00 0          [heap]
b3018000-b3054000 r-xp 00000000 08:11 88619      /usr/lib/libvisual-0.4.so.0.0.0
b3054000-b3055000 r--p 0003b000 08:11 88619      /usr/lib/libvisual-0.4.so.0.0.0
b3055000-b3056000 rw-p 0003c000 08:11 88619      /usr/lib/libvisual-0.4.so.0.0.0
b3061000-b3067000 rw-p b3061000 00:00 0 
b3067000-b3086000 r-xp 00000000 08:11 88295      /usr/lib/libjpeg.so.62.0.0
b3086000-b3087000 rw-p 0001e000 08:11 88295      /usr/lib/libjpeg.so.62.0.0
b3090000-b3096000 r-xp 00000000 08:11 95665      /usr/lib/gstreamer-0.10/libgstlibvisual.so
b3096000-b3097000 r--p 00005000 08:11 95665      /usr/lib/gstreamer-0.10/libgstlibvisual.so
b3097000-b3098000 rw-p 00006000 08:11 95665      /usr/lib/gstreamer-0.10/libgstlibvisual.so
b3098000-b30a5000 r-xp 00000000 08:11 95663      /usr/lib/gstreamer-0.10/libgstjpeg.so
b30a5000-b30a6000 r--p 0000c000 08:11 95663      /usr/lib/gstreamer-0.10/libgstjpeg.so
b30a6000-b30a7000 rw-p 0000d000 08:11 95663      /usr/lib/gstreamer-0.10/libgstjpeg.so
b30a7000-b30b7000 r-xp 00000000 08:11 88253      /usr/lib/libhal.so.1.0.0
b30b7000-b30b8000 r--p 0000f000 08:11 88253      /usr/lib/libhal.so.1.0.0
b30b8000-b30b9000 rw-p 00010000 08:11 88253      /usr/lib/libhal.so.1.0.0
b30be000-b30c8000 r-xp 00000000 08:11 95662      /usr/lib/gstreamer-0.10/libgstinterleave.so
b30c8000-b30c9000 r--p 00009000 08:11 95662      /usr/lib/gstreamer-0.10/libgstinterleave.so
b30c9000-b30ca000 rw-p 0000a000 08:11 95662      /usr/lib/gstreamer-0.10/libgstinterleave.so
b30ca000-b30d0000 r-xp 00000000 08:11 95658      /usr/lib/gstreamer-0.10/libgstgoom2k1.so
b30d0000-b30d1000 r--p 00005000 08:11 95658      /usr/lib/gstreamer-0.10/libgstgoom2k1.so
b30d1000-b30d2000 rw-p 00006000 08:11 95658      /usr/lib/gstreamer-0.10/libgstgoom2k1.so
b30d2000-b3112000 rw-p b30d2000 00:00 0 
b3112000-b311a000 r-xp 00000000 08:11 114709     /usr/lib/gnome-vfs-2.0/modules/libsftp.so
b311a000-b311b000 r--p 00007000 08:11 114709     /usr/lib/gnome-vfs-2.0/modules/libsftp.so
b311b000-b311c000 rw-p 00008000 08:11 114709     /usr/lib/gnome-vfs-2.0/modules/libsftp.so
b311c000-b3123000 r-xp 00000000 08:11 87976      /usr/lib/libfam.so.0.0.0
b3123000-b3124000 rw-p 00006000 08:11 87976      /usr/lib/libfam.so.0.0.0
b3124000-b312a000 r-xp 00000000 08:11 4458       /lib/libacl.so.1.1.0
b312a000-b312c000 rw-p 00005000 08:11 4458       /lib/libacl.so.1.1.0
b312c000-b3131000 r-xp 00000000 08:11 95659      /usr/lib/gstreamer-0.10/libgsthalelements.so
b3131000-b3132000 r--p 00004000 08:11 95659      /usr/lib/gstreamer-0.10/libgsthalelements.so
b3132000-b3133000 rw-p 00005000 08:11 95659      /usr/lib/gstreamer-0.10/libgsthalelements.so
b3133000-b313b000 r-xp 00000000 08:11 114702     /usr/lib/gnome-vfs-2.0/modules/libftp.so
b313b000-b313c000 r--p 00007000 08:11 114702     /usr/lib/gnome-vfs-2.0/modules/libftp.so
b313c000-b313d000 rw-p 00008000 08:11 114702     /usr/lib/gnome-vfs-2.0/modules/libftp.so
b313d000-b313f000 r-xp 00000000 08:11 4504       /lib/libkeyutils-1.2.so
b313f000-b3141000 rw-p 00001000 08:11 4504       /lib/libkeyutils-1.2.so
b3141000-b3148000 r-xp 00000000 08:11 88305      /usr/lib/libkrb5support.so.0.1
b3148000-b3149000 r--p 00006000 08:11 88305      /usr/lib/libkrb5support.so.0.1
b3149000-b314a000 rw-p 00007000 08:11 88305      /usr/lib/libkrb5support.so.0.1
b314a000-b316c000 r-xp 00000000 08:11 88297      /usr/lib/libk5crypto.so.3.1
b316c000-b316d000 r--p 00022000 08:11 88297      /usr/lib/libk5crypto.so.3.1
b316d000-b316e000 rw-p 00023000 08:11 88297      /usr/lib/libk5crypto.so.3.1
b316e000-b31fd000 r-xp 00000000 08:11 88303      /usr/lib/libkrb5.so.3.3
b31fd000-b31ff000 r--p 0008e000 08:11 88303      /usr/lib/libkrb5.so.3.3
b31ff000-b3200000 rw-p 00090000 08:11 88303      /usr/lib/libkrb5.so.3.3
b3200000-b3300000 rw-p b3200000 00:00 0 
b3301000-b3329000 r-xp 00000000 08:11 88160      /usr/lib/libgssapi_krb5.so.2.2
b3329000-b332a000 r--p 00028000 08:11 88160      /usr/lib/libgssapi_krb5.so.2.2
b332a000-b332b000 rw-p 00029000 08:11 88160      /usr/lib/libgssapi_krb5.so.2.2
b332b000-b3347000 r-xp 00000000 08:11 114704     /usr/lib/gnome-vfs-2.0/modules/libhttp.so
b3347000-b3348000 r--p 0001b000 08:11 114704     /usr/lib/gnome-vfs-2.0/modules/libhttp.so
b3348000-b3349000 rw-p 0001c000 08:11 114704     /usr/lib/gnome-vfs-2.0/modules/libhttp.so
b3349000-b3361000 r-xp 00000000 08:11 114869     /usr/lib/gio/modules/libgvfsdbus.so
b3361000-b3362000 r--p 00017000 08:11 114869     /usr/lib/gio/modules/libgvfsdbus.so
b3362000-b3363000 rw-p 00018000 08:11 114869     /usr/lib/gio/modules/libgvfsdbus.so
b3363000-b3370000 r-xp 00000000 08:11 87532      /usr/lib/libgvfscommon.so.0.0.0
b3370000-b3371000 r--p 0000d000 08:11 87532      /usr/lib/libgvfscommon.so.0.0.0
b3371000-b3372000 rw-p 0000e000 08:11 87532      /usr/lib/libgvfscommon.so.0.0.0
b3373000-b3376000 r-xp 00000000 08:11 4464       /lib/l


---

### Post by jfernyhough on 2009-03-11
Try with a clean profile?

From [http://getsatisfaction.com/songbird/topics/ubuntu_8_10_64bit_songbird_1_0_seg_faults_on_launch](http://getsatisfaction.com/songbird/topics/ubuntu_8_10_64bit_songbird_1_0_seg_faults_on_launch)

> You're not going to be able to use the same profile on your 32-bit and 64-bit linux installs. There are some binary bits in the profiles that just don't translate between 32- and 64-bit machines.

---

### Post by jblackhall on 2009-03-11
Also, forgot to mention that FTA is updating his PPA, so it should be easy enough to upgrade soon.

---

### Post by cl333r on 2009-03-11
> **jfernyhough said:**
> Try with a clean profile?

From [http://getsatisfaction.com/songbird/topics/ubuntu_8_10_64bit_songbird_1_0_seg_faults_on_launch](http://getsatisfaction.com/songbird/topics/ubuntu_8_10_64bit_songbird_1_0_seg_faults_on_launch)

I got 32 bit Ubuntu on 32 bit Pentium D.
Deleted ~/.songbird(32).. same issue persists

---

### Post by afv on 2009-03-13
Anyone experiencing Songbirg hanging (up to some minutes) when searching the library?

I'll try the fta package now… OK, same problem… It was OK on previous version.

---

### Post by wiebeest on 2009-03-19
> **cl333r said:**
> Tried installing from getdeb, Songbird won't start, thought it's a package issue. Downloaded the official release from getsongbird.com, yet I get:

I have the same problem in Ibex (32bit). Used the .deb from [http://www.getdeb.net/]("http://www.getdeb.net/") myself.
 
Funny thing is it used to work up till sunday, but now all of a sutton today it won't start anymore :-( Maybe an update FUBAR'd it? Re-install didn't fix it.

UPDATE: The workaround > sudo apt-get remove libvisual-0.4-plugins
seems to have fixed it. 

Maybe you guys could try that too as a sollution for the Songbird issues with Jaunty?

---

