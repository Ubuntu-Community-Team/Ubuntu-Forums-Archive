---
title: "Video Crashes After Enabling Dual-Monitor in 9.04 Beta"
date: 2009-04-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by acconrad on 2009-04-13
I currently have the latest version of 9.04 will all of the updates as of today. It is running on a 1.6GHz HP Pavilion dv1000. I have a 19'' Dell external monitor (LCD).

Steps: 
1. Plug in external monitor to blue VGA monitor plug
2. System > Preferences > Display
3. Enable 2nd monitor, sign out and sign in
4. Click on a .avi file (defaults to opening Movie Player/Totem)
5. Totem opens, as soon as it reads data from the movie file, it closes down
6. Repeat ad nauseum

I tried running it via command line and got this:

[FONT="Courier New"]/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 85 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)[/FONT]

I tried again with the --sync option enabled and it didn't reveal any new information, in fact it said "Error: Location not found" and spit out the exact same debug code to the console. I disabled the external monitor, unplugged it and rebooted to see if the previous state would be acceptable.

Nope. Exact same error.

So now I can't watch any video on my home machine.

I tried to download an alternate player such as VLC and its associated plugins...still crashes with a Bad alloc/X Window error. Anytime I try to play video now the program will crash.

Any ideas?

---

