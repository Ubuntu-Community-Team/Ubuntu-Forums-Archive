---
title: "xchat-gnome not working..."
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by spotdog14 on 2008-11-18
I upgraded to 8.10 and since then i cannot get xchat-gnome to work, when I try to launch it from terminal I get:

```
spotdog14@HP-1040us:~$ xchat-gnome
The program 'xchat-gnome' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadImplementation (server does not implement operation)'.
  (Details: serial 518 error_code 17 request_code 145 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
spotdog14@HP-1040us:~$ 

```

I have tried uninstalling it, and reinstalling it. xchat works fine, any ideas?

Thanks!

---

### Post by JDuc on 2009-01-01
I'm running into this same problem.  I installed it and was able to connect to a channel at first.  

It seems that once I selected to use a transparent background it shut down and won't start back up for me.

I saw another thread where the user said that removing the ~/.xchat2 directory solved the probelm but when I try and do that via the terminal, I get a warning that it can't do that because the directory isn't empty.

Anyone find a solution to this issue?  It worked fine under 8.04 (Hardy)

---

### Post by snova on 2009-01-01
> **JDuc said:**
> I saw another thread where the user said that removing the ~/.xchat2 directory solved the probelm but when I try and do that via the terminal, I get a warning that it can't do that because the directory isn't empty.

The rm command will not remove directories, and rmdir will not remove files. Nor will rmdir remove directories that are not empty.

Instead, try:

```
rm -r ~/.xchat2
```

---

