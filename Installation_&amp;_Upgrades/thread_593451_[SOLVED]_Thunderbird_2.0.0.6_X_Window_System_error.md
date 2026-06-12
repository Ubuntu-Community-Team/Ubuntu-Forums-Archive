---
title: "[SOLVED] Thunderbird 2.0.0.6: X Window System error (U7.10)"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by Lucky LIX on 2007-10-27
I've recently upgraded to Ubuntu 7.10 and am a happy user.
However there are still some minor problems...
After installing Thunderbird 2.0.0.6 I've sometimes noticed the following error:
Thunderbird fails to start after choosing a profile (2 users, so we use the profile manager) but not always :/ sometimes it just works as it should, while 2 seconds before it refused to...

When executing TB from the terminal and choosing a profile the console echoes the following code (when TB just works, nothing 's printed)
```
The program 'thunderbird-bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 1497 error_code 3 request_code 20 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

Hope someone can help me since my father might start complaining Window$ was better 'cause it just worked :x
(which it didn't, but still... you get the point)

Thanks in advance!


PS: if I should get this message to Launchpad or some other place, do tell me

---

### Post by Lucky LIX on 2007-10-30
?

---

### Post by Lucky LIX on 2007-11-03
No one? :(

---

### Post by It_Was_Luck on 2007-11-03
Try this in your terminal:

```
sudo apt-get install thunderbird thunderbird-gnome-support
```

Now if that doesn't work or you get a bunch of errors run this code below instead:

```
sudo apt-get update && sudo apt-get install mozilla-thunderbird
```


Hope that helped

---

### Post by Lucky LIX on 2007-11-05
Alright, thunderbird-gnome-support seems to have fixed it :)
Thank you very much It_Was_Luck !

---

