---
title: "[SOLVED] XWindows error from FireFox after Gutsy upgrade"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by ag65151 on 2007-10-23
This is a weird error I am getting. It only happens on certain websites. (i.e., [this one]("http://www.baptistpress.com"), or [another one]("http://www.firstbaptistraytown.com")) But it will happen on both of those websites. FireFox just disappears with no error messages whatsoever. I executed it from CLI and below is what happened.
```

:/var/log$ firefox
The program 'gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 119 error_code 8 request_code 146 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

Anybody have a suggestion? I have been playing with xorg.conf all day long with no luck.

---

### Post by ag65151 on 2007-10-23
I poked around some more and found that if you are running with the screen set to 16 in xorg.conf, the flash plugin takes out Firefox. I changed it to 24 and restarted X. Now I have no problems. It is solved!

I am starting to like 7.10 more and more.

---

