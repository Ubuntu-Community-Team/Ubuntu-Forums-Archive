---
title: "Problems installing Gnomad2"
date: 2008-08-20
forum: Installation &amp; Upgrades
---

### Post by I[AM]SMRT on 2008-08-20
I'm trying to install Gnomad2 for my Creative Zen X-Fi. I got the latest source, untarred and ./configure but when I try to "make", I get some errors:

```
brian@brian-laptop:~/Desktop/gnomad2-2.9.2$ sudo make
Making all in src
make[1]: Entering directory `/home/brian/Desktop/gnomad2-2.9.2/src'
gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.9.2\" -DPACKAGE_STRING=\"gnomad2\ 2.9.2\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" -DPACKAGE=\"gnomad2\" -DVERSION=\"2.9.2\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIBMTP=1 -DHAVE_DBUSGLIB=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_CODESET=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DENABLE_NLS=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_CHDIR=1 -I. -pthread -I/usr/local/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1 -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -DPREFIX=\"/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMAPSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT jukebox.o -MD -MP -MF .deps/jukebox.Tpo -c -o jukebox.o jukebox.c
jukebox.c: In function &#8216;hd2jb_thread&#8217;:
jukebox.c:2183: error: &#8216;LIBMTP_track_t&#8217; has no member named &#8216;storage_id&#8217;
jukebox.c:2187: error: too few arguments to function &#8216;LIBMTP_Send_Track_From_File&#8217;
jukebox.c: In function &#8216;hd2jb_data_thread&#8217;:
jukebox.c:2354: error: too few arguments to function &#8216;LIBMTP_Send_File_From_File&#8217;
jukebox.c: In function &#8216;jukebox_create_playlist&#8217;:
jukebox.c:2752: error: &#8216;LIBMTP_playlist_t&#8217; has no member named &#8216;parent_id&#8217;
jukebox.c:2753: error: &#8216;LIBMTP_playlist_t&#8217; has no member named &#8216;storage_id&#8217;
jukebox.c:2755: error: too few arguments to function &#8216;LIBMTP_Create_New_Playlist&#8217;
jukebox.c: In function &#8216;jukebox_create_folder&#8217;:
jukebox.c:3617: error: too many arguments to function &#8216;LIBMTP_Create_Folder&#8217;
make[1]: *** [jukebox.o] Error 1
make[1]: Leaving directory `/home/brian/Desktop/gnomad2-2.9.2/src'
make: *** [all-recursive] Error 1

```

Is there anything I'm doing wrong?

Maybe it's because there's something wrong with my libnjb install?

```
Making all in doc
make[2]: Entering directory `/home/brian/Desktop/libnjb-2.2.6/doc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/brian/Desktop/libnjb-2.2.6/doc'
make[2]: Entering directory `/home/brian/Desktop/libnjb-2.2.6'
make[2]: Leaving directory `/home/brian/Desktop/libnjb-2.2.6'
make[1]: Leaving directory `/home/brian/Desktop/libnjb-2.2.6'
Making install in src
make[1]: Entering directory `/home/brian/Desktop/libnjb-2.2.6/src'
make[2]: Entering directory `/home/brian/Desktop/libnjb-2.2.6/src'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'libnjb.la' '/usr/local/lib/libnjb.la'
/usr/bin/install -c .libs/libnjb.so.5.1.0 /usr/local/lib/libnjb.so.5.1.0
/usr/bin/install: cannot remove `/usr/local/lib/libnjb.so.5.1.0': Permission denied
make[2]: *** [install-libLTLIBRARIES] Error 1
make[2]: Leaving directory `/home/brian/Desktop/libnjb-2.2.6/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/brian/Desktop/libnjb-2.2.6/src'
make: *** [install-recursive] Error 1

```

---

### Post by Partyboi2 on 2008-08-21
Do you need to compile it? Or can you use the one in the ubuntu repo's?
```
sudo apt-get install gnomad2
```
[B]
[/B]

---

### Post by Themaister on 2008-09-06
I have the same issue with 2.9.2 .. However, 2.9.1 compiles just fine for some reason.

---

### Post by kaniza on 2008-09-08
I'm getting the exact same output. I would reinstall from the repo, but my system won't load Gnomad2 for whatever reason, so I thought I would compile from the source with the latest version.

Of course, Sourceforge now only offers 2.9.2.... :(

Has anyone been able to come up with possible solutions for this? I have all the require dependencies already installed. Not sure where to even go from here.

---

### Post by Partyboi2 on 2008-09-08
This is how I got gnomad2-2.9.2 compiled.
```
 sudo apt-get build-dep gnomad2
```
then proceeded with
./configure
make
sudo make install

---

### Post by Zaopunk on 2008-12-17
Ok, well here's my probably more simple problem. I am trying the line:

sudo apt-get install gnomad2

and getting the response:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gnomad2

how do I update the repositories or the "list" it speaks of. Sorry ahead of time, I haven't used ubuntu in almost half a year and my brain got filled with electronic engineering mumbo jumbo.

---

### Post by Partyboi2 on 2008-12-17
Open up Software Sources (System>Admin>Software Sources) on the first tab make sure that universe is ticked. Then close Software Sources and try installing it again. Or from the terminal you can open up /etc/apt/sources.list 
```
sudo nano /etc/apt/sources.list
``` and remove the # from in front of the universe repo and save. (Ctrl+o enter Ctrl+x)Then back in the terminal
```
sudo apt-get update && sudo apt-get install gnomad2
```

---

