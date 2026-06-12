---
title: "Firefox2 closes after 2 sec."
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by alberto666 on 2006-10-27
Hello.

After upgrading to Edgy, when I try to open firefox, it closes after about 2 sec.

I had a previous installation of firefox2 before upgrading in my home directory, but now I have both, and none of them works. 

Right now I'm using mozilla web browser...

No error messages, nothing, just closes.

---

### Post by pay on 2006-10-27
Can you run it in the terminal and see if an error message comes up? ```
firefox
```

---

### Post by alberto666 on 2006-10-27
Ok, after working on the problem, I have realised that the problem is because of the theme that Ubuntu install when I try to open a web with ¿JavaScript, or maybe Flash? 

I had [www.gmail.com](www.gmail.com) as my start page, I changed it before open it, and with ubuntuforums there is no problem.

I changed to the theme to NOIAXtreme and now there is no problem.

Anyway, if I open from the terminal, this is the problem:

```
** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 115 error_code 8 request_code 146 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Segmentation fault (core dumped)

```

---

### Post by alberto666 on 2006-10-27
Ok, it was not just like that.

When I open Firefox2 from the path that I installed in my home directory with another theme, it works fine, but if I open from the firefox2 that the system install even with the other theme, when I open [www.gmail.com](www.gmail.com) or [www.um.es](www.um.es) it hangs with the same error.

---

### Post by alberto666 on 2006-10-27
After fighting a lot with firefox, I have discovered the following:

The problem is FlashPlayer. It doesn't work properly.

I uninstall flashplayer from automatix, from apt-get and deleted the file in $HOME/.mozilla/plugins.

After that, everything works, except the flash plugin.

I have tried to install it again, but allways goes wrong (as soon as the page open, firefox close). I tried to install with the firefox installer, but it freezed again, also again with automatix, the same problem. I downloaded the program from the official page ([www.macromedia.com)](www.macromedia.com)), the same problem.

So I can't use flash :(

The only that I can do is install libflash-mozplugin, and after that it works, but no so good, some pages doesn't display really good, because it is not the official :(

What can I do?

Everything was OK before upgrading, and now even if I install the 1.5.0.7 version of Firefox it doesn't work with flash :(

---

### Post by Wight_Rhino on 2006-10-27
I had this problem, and read in another thread to change depth setting to 24 (mine was on 16) in xorg.conf.

It fixed it for me, might be worth a shot!

---

### Post by pay on 2006-10-28
"sudo nano /etc/X11/xorg.conf" then change it from there.

---

### Post by orsula on 2006-11-05
I erased flashplayer.xpt  and libflashplayer.so from:

```
~/.mozilla/plugins
```
This means I don't have flash for now, but Ff2 doesn't crash. 
Any one knows how to solve the flash problem?

---

### Post by alberto666 on 2006-11-05
As they said before, just change to 24bits colors.

But is not a good way :(

---

