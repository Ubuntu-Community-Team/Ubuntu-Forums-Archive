---
title: "Installing IES4Linux"
date: 2011-08-31
forum: Installation &amp; Upgrades
---

### Post by bandito40 on 2011-08-31
I tried install IES4Linux from this site -> [http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu]("http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu"). During installation I get this error: 

> IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).


When I run the command ```
~$ wine --version
``` it tells me I have version wine-1.2.3 installed.  Anyone know how to bypass this error or what causes it?

---

### Post by Mark Phelps on 2011-09-01
If you're doing that so you can then install Internet Explorer version 8 or 9 -- you're wasting your time.  Other folks have tried that and have been unable to get either version to work. The most current version of IE that does appear to work is version 7.

---

### Post by bandito40 on 2011-09-01
Actually I am trying to install version 5-7 but always get the wrong wine version error and I also get this error 

```
The program 'ies4linux-gtk.py' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 3631 error_code 1 request_code 0 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

When I run ./ies4linux --sync it prints:

```
IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).

Error: unknown option "--sync"
run "./ies4linux --help" for more info

```

Any suggestions on how to surpass this error?

---

