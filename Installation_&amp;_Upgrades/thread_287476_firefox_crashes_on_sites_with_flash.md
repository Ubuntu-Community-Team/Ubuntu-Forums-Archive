---
title: "firefox crashes on sites with flash"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by bigbhai on 2006-10-28
Firefox crashes while trying to open a site with flash. I started firefox from the command line, and I putting the output I get here.

$firefox
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
  (Details: serial 118 error_code 8 request_code 146 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by bigbhai on 2006-10-28
This started happening after I upgraded to edgy eft.

---

### Post by bschuteker on 2006-10-28
Try this it just worked for me.

[http://www.ubuntuforums.org/showthread.php?t=286069](http://www.ubuntuforums.org/showthread.php?t=286069)

---

### Post by bschuteker on 2006-10-28
Also you have to restart Firefox for it to work.

---

### Post by bigbhai on 2006-10-28
> **bschuteker said:**
> Try this it just worked for me.

[http://www.ubuntuforums.org/showthread.php?t=286069](http://www.ubuntuforums.org/showthread.php?t=286069)

It WORKED! Thanks!:mrgreen: :mrgreen: :-D :-D

---

### Post by roachk71 on 2006-11-02
Not the only browser with this problem, either. Both Mozilla 1.7 and Epiphany Browser crash on flash sites, as does Swiftfox...

Perhaps this is a shared library issue. :evil:

And the fixes mentioned here didn't work at all for me. Besides, I need 16bpp graphics for my emulators to work correctly (especially Gens.)

Kind of a shame, but, I'll keep Flashblock enabled until the specific problem's been identified and fixed by the devs. I've had to live without Flash before (it was actually *more* enjoyable back in the days of having no 'net access...Go figure.) 8)

---

