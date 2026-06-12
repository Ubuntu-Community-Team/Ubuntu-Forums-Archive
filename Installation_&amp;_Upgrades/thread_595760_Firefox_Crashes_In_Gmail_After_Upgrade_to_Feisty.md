---
title: "Firefox Crashes In Gmail After Upgrade to Feisty"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by coolboarderguy on 2007-10-29
Hi All,

I've just done an upgrade to feisty from dapper via edgy. From the moment the first stage was complete, Firefox crashes upon signing in to gmail. Anyone experienced this? I don't see any references in /var/log/messages or syslog for it.

---

### Post by ofb on 2007-10-29
I just had a quick look through a whole lot of related threads.
[http://www.google.com/search?hl=en&client=opera&rls=en&hs=XeO&q=+site:ubuntuforums.org+Firefox+crashes+gmail+ubuntu](http://www.google.com/search?hl=en&client=opera&rls=en&hs=XeO&q=+site:ubuntuforums.org+Firefox+crashes+gmail+ubuntu)

What's odd is the variety of fixes that do and don't work for people. Since you'd probably just like to get your mail, I suggest you try a few while keeping track of what you're doing, and keeping an eye to find out what the core problem really is.

You might try starting Firefox from the termial to see if there's useful output from the crash too.

(And of course you can install Opera to get your mail while you work on this.)

---

### Post by Doomguy0505 on 2007-10-29
I get the same problem with chatzilla, when I try to chat in it, it instantly crashes

EDIT: Upgrade firefox and it works

---

### Post by sahilsapre on 2007-10-29
i think it's got something to do with gmail chat...log in from another browser, and use the gmail view: standard without chat...now if you log back in from firefox, it shouldn't crash..it didn't for me, at least..

---

### Post by coolboarderguy on 2007-10-29
Hi All,

anyone on here got a clue?

firefox
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 120 error_code 8 request_code 144 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
marks@akito:~$ firefox --sync
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 120 error_code 8 request_code 144 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by coolboarderguy on 2007-10-29
Updating flash player solved this issue. Damn Ubuntu upgrades messing with my settings.

---

