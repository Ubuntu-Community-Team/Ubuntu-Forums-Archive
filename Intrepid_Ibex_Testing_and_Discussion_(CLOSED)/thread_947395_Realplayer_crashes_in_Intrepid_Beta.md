---
title: "Realplayer crashes in Intrepid Beta"
date: 2008-10-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by alvarez_saez on 2008-10-14
Realplayer crashes when I try to play videos in the rmbv format.
I get this message in the terminal:

The program 'realplay.bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 34 error_code 8 request_code 140 minor_code 13)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

I tried Realplayer 10 and 11 and the problem occurs in both. Both used to work fine in Ubuntu Gutsy and Hardy.

---

### Post by adam on 2008-10-16
In RealPlayer, go to:
Tools > Preferences

Go to the Hardware tab, and uncheck "Use XVideo".

---

