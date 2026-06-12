---
title: "Anyone able to get Firefox 2 running in Karmic?"
date: 2009-09-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by khughitt on 2009-09-16
I have not had any luck getting so FF2 working in Karmic so far. The first error I ran into, was a dependency on libstdc++.so.5:

```

./firefox
./firefox-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```

Since Karmic [no longer has libstdc++5]("http://ubuntuforums.org/showthread.php?t=1265204") in the repos, I downloaded the library manually from [http://packages.ubuntu.com/jaunty/libstdc++5](http://packages.ubuntu.com/jaunty/libstdc++5).

The next error I've run into is a little less clear:

```

./firefox

Gdk-ERROR **: The program 'firefox-bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 1608 error_code 3 request_code 20 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
aborting...
Trace/breakpoint trap (core dumped)

```

Although it's not essential, it would be nice to be able to use Firefox 2 for testing purposes.

Has anyone else had any luck?

---

### Post by VMC on 2009-09-16
I don't know what FF2 is. Is it version2? Why not use version 5?

Here is my FF that works.

I use Chrome for almost all my browsing.

---

### Post by khughitt on 2009-09-16
Okay, I was able to get FF2 running. It turns out that the Gdk-ERROR is not related to Firefox 2, but rather to the profile manager: Whenever I run *any* version of firefox with the "-ProfileManager" switch, the program crashes after selecting a profile to use.

If I manually specify the profile (firefox -p myprofile), it works fine.

---

### Post by faPmasteRslaM on 2009-09-16
ff2?

[img]http://finalfantasytwo.files.wordpress.com/2008/09/final_fantasy_2_snes1.jpg[/img]

---

### Post by scottuss on 2009-09-16
Firefox 2 is no longer supported and should probably not be used due to security issues.

Is there any particular reason you don't want to use Firefox 3?

Edit: OK so it's for testing.. fair enough.

But still, I'd advise anyone you know against using version 2

---

### Post by khughitt on 2009-09-16
Thanks VMC,

"FF2" = "Firefox 2". 3.5 is great, and much faster, but in order to test web sites on older browsers, it's always good to have several different versions of Firefox, etc :)

---

### Post by khughitt on 2009-09-16
> **faPmasteRslaM said:**
> ff2?

[img]http://finalfantasytwo.files.wordpress.com/2008/09/final_fantasy_2_snes1.jpg[/img]

If only testing "ff2" could be that much fun :)

---

