---
title: "libjpeg.so.8: cannot open shared object file"
date: 2012-08-11
forum: Installation &amp; Upgrades
---

### Post by Eelbuntu on 2012-08-11
On my 12.04, 64bit server I try to get PHP5 GD running to enable captcha images . But it gives an error:

```
~$ php -v
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626/gd.so' - libjpeg.so.8: cannot open shared object file: No such file or directory in Unknown on line 0
PHP 5.3.10-1ubuntu3.2 with Suhosin-Patch (cli) (built: Jun 13 2012 17:19:58) 

```

When I look at the shared libraries, I see libjpeg.so.8 (and libfontconfig.so.1) is indeed missing:

```
 ldd /usr/lib/php5/20090626/gd.so 
	linux-vdso.so.1 =>  (0x00007fff98bff000)
	libgd.so.2 => /usr/lib/x86_64-linux-gnu/libgd.so.2 (0x00007f0cd8700000)
	libt1.so.5 => /usr/lib/libt1.so.5 (0x00007f0cd84a2000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f0cd80e4000)
	libXpm.so.4 => /usr/lib/x86_64-linux-gnu/libXpm.so.4 (0x00007f0cd7ed3000)
	libjpeg.so.8 => not found
	libfontconfig.so.1 => not found
	libfreetype.so.6 => /usr/lib/x86_64-linux-gnu/libfreetype.so.6 (0x00007f0cd7c36000)

```

Now my simple question is, how do I get these libs installed? Because  whatever I try, I don't get any libjpeg.so.8 installed. This doesn't help for example.

```
sudo apt-get install libjpeg8
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libjpeg8 is already the newest version.

```

What am I missing here? Any help very much appreciated.

---

### Post by spjackson on 2012-08-11
The packages needed are libjpeg-turbo8 and libfontconfig1. I used apt-file to find this out.

---

### Post by Eelbuntu on 2012-08-14
Thanks, and it sounded like the solution. With apt-file it does say that these are the packages to install:

```
$apt-file search libjpeg.so.8
libjpeg-turbo8: /usr/lib/x86_64-linux-gnu/libjpeg.so.8
libjpeg-turbo8: /usr/lib/x86_64-linux-gnu/libjpeg.so.8.0.2
libjpeg-turbo8-dbg: /usr/lib/debug/usr/lib/x86_64-linux-gnu/libjpeg.so.8.0.2

~$ apt-file search libfontconfig.so.1
libfontconfig1: /usr/lib/x86_64-linux-gnu/libfontconfig.so.1
libfontconfig1: /usr/lib/x86_64-linux-gnu/libfontconfig.so.1.4.4
libfontconfig1-dbg: /usr/lib/debug/usr/lib/libfontconfig.so.1.4.4
libfontconfig1-dbg: /usr/lib/debug/usr/lib/x86_64-linux-gnu/libfontconfig.so.1.4.4

```

But installing these packages didn't solve it:

```
libjpeg-turbo8 is already the newest version.
libfontconfig1 is already the newest version.

```

So my problem persists:

```
 ldd /usr/lib/php5/20090626/gd.so
	linux-vdso.so.1 =>  (0x00007fffa91ff000)
	libgd.so.2 => /usr/lib/x86_64-linux-gnu/libgd.so.2 (0x00007f2ff48c4000)
	libt1.so.5 => /usr/lib/libt1.so.5 (0x00007f2ff4666000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f2ff42a8000)
	libXpm.so.4 => /usr/lib/x86_64-linux-gnu/libXpm.so.4 (0x00007f2ff4097000)
	libjpeg.so.8 => not found
	libfontconfig.so.1 => not found

```

Anybody any more ideas? Why don these libraries install?

---

### Post by Eelbuntu on 2012-08-14
It's solved!

I thought there just was some inconsistenty, so I decided to remove the two mentioned packages that should have resolved my problem, but didnt solve it. So I removed them

```
sudo apt-get remove libjpeg-turbo8
sudo apt-get remove libfontconfig1

```

Then it turned out that PHP5-gd was gone as well. Visible because /usr/lib/php5/20090626/gd.so did not exist any more.

Then after installing everything again:

```
sudo apt-get install libjpeg-turbo8
sudo apt-get install libfontconfig1
sudo apt-get install php5-gd

```

there was no problem any more. Thanks spjackson for pointing me to the right direction.

---

### Post by modevel on 2012-09-13
Sorry, it does not work!

- Ubuntu 12.04 LTS -


# ldd /usr/lib/php5/20090626/gd.so
        linux-vdso.so.1 =>  (0x00007fffe6600000)
        libgd.so.2 => /usr/lib/x86_64-linux-gnu/libgd.so.2 (0x00007fc0f5c70000)
        libt1.so.5 => /usr/lib/libt1.so.5 (0x00007fc0f5a10000)
        libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fc0f5650000)
        libXpm.so.4 => /usr/lib/x86_64-linux-gnu/libXpm.so.4 (0x00007fc0f5438000)
       [B] libjpeg.so.8 => /usr/lib/x86_64-linux-gnu/libjpeg.so.8 (0x00007fc0f51e8000)
        libfontconfig.so.1 => /usr/lib/x86_64-linux-gnu/libfontconfig.so.1 (0x00007fc0f4fb0000)[/B]
        libfreetype.so.6 => /usr/lib/x86_64-linux-gnu/libfreetype.so.6 (0x00007fc0f4d10000)
        libpng12.so.0 => /lib/x86_64-linux-gnu/libpng12.so.0 (0x00007fc0f4ae8000)
        libz.so.1 => /lib/x86_64-linux-gnu/libz.so.1 (0x00007fc0f48d0000)
        libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007fc0f45d0000)
        /lib64/ld-linux-x86-64.so.2 (0x00007fc0f60e0000)
        libX11.so.6 => /usr/lib/x86_64-linux-gnu/libX11.so.6 (0x00007fc0f4298000)
        libexpat.so.1 => /lib/x86_64-linux-gnu/libexpat.so.1 (0x00007fc0f4068000)
        libxcb.so.1 => /usr/lib/x86_64-linux-gnu/libxcb.so.1 (0x00007fc0f3e48000)
        libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007fc0f3c40000)
        libXau.so.6 => /usr/lib/x86_64-linux-gnu/libXau.so.6 (0x00007fc0f3a38000)
        libXdmcp.so.6 => /usr/lib/x86_64-linux-gnu/libXdmcp.so.6 (0x00007fc0f3830000)

# la libj*
lrwxrwxrwx 1 root root     18 Jan 11  2012 libjasper.so.1 -> libjasper.so.1.0.0
-rw-r--r-- 1 root root 325880 Jan 11  2012 libjasper.so.1.0.0
lrwxrwxrwx 1 root root     17 Okt 13  2011 libjpeg.so.62 -> libjpeg.so.62.0.0
-rw-r--r-- 1 root root 150144 Okt 13  2011 libjpeg.so.62.0.0
[B]lrwxrwxrwx 1 root root     16 Jul 13 01:31 libjpeg.so.8 -> libjpeg.so.8.0.2
-rw-r--r-- 1 root root 260872 Jul 13 01:31 libjpeg.so.8.0.2[/B]


**My try:**

sudo apt-get remove libjpeg-turbo8
sudo apt-get remove libjpeg8
sudo apt-get remove libjpeg62
sudo apt-get remove libfontconfig1

sudo apt-get install libjpeg-turbo8
sudo apt-get install libfontconfig1
sudo apt-get install php5-gd

service apache2 restart

After that ... php_info

**gd**
  GD Support enabled
GD Version 2.0
FreeType Support enabled
FreeType Linkage with freetype
FreeType Version 2.4.8
T1Lib Support enabled
GIF Read Support enabled
GIF Create Support enabled
JPEG Support enabled [B]
libJPEG Version [/B][B]unknown
[/B]PNG Support enabled  libPNG
Version 1.2.46
WBMP Support enabled 


What can I do, now?

---

### Post by cjhabs on 2012-09-13
I can't help you but I have an app that needs the same library and I have it installed the exact same way as you - same folder, same file size, same link - and that resolved by dependency problem. 
The only thing I can think of is that your app is looking for a 32-bit library instead of 64-bit?

---

