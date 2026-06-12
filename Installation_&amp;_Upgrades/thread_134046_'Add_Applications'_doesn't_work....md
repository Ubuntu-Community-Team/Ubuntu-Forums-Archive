---
title: "'Add Applications' doesn't work..."
date: 2006-02-21
forum: Installation &amp; Upgrades
---

### Post by 3ntity on 2006-02-21
Hello,
I re-installed Ubuntu recently and i cannot install applications through 'Add Applications' (as in clicking on Applications -> 'Add Applications' causes nothing to happen)... I've set myself as a sudoer, tho maybe not correctly, you never know (and should that cause problems?). Anyone got any ideas?
Thanks :)

---

### Post by Greg2 on 2006-02-21
[QUOTE=3ntity](as in clicking on Applications -> 'Add Applications' causes nothing to happen)[/QUOTE]
Use your terminal to try to open it and post the error for us to check. In terminal do:```
/usr/bin/gksudo /usr/bin/gnome-app-install
```

---

### Post by 3ntity on 2006-02-22
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 41, in ?
    from AppInstall import AppInstall
  File "/usr/lib/gnome-app-install/AppInstall.py", line 30, in ?
    import gtkmozembed
ImportError: libgtkembedmoz.so: cannot open shared object file: No such file or directory

That's the error
(Ps. im running this on a 'standard' ubuntu 5.10 install)

---

### Post by Greg2 on 2006-02-22
[QUOTE=3ntity]ImportError: libgtkembedmoz.so: cannot open shared object file: No such file or directory[/QUOTE]
That (libgtkembedmoz.so) should be in the /usr/lib/mozilla-firefox directory? Close firefox and try to open the package manager? :-k

---

### Post by 3ntity on 2006-02-24
Hey,
Closing firefox didnt help at all. I've tried running 'Add Applications' several times just after startup, to no avail. And that file does not appear to be present on my system :S. What can I do??? :P
Thanks for any help,
Inti

---

### Post by Greg2 on 2006-02-24
[QUOTE=3ntity]that file does not appear to be present on my system :S. What can I do?[/QUOTE]
In your terminal do:```
locate libgtkembedmoz.so
```The output should look like this:```

greg@halfway:~$ locate libgtkembedmoz.so
/usr/lib/mozilla-firefox/libgtkembedmoz.so
```If it doesn't, then something happened when you re-installed Ubuntu? If you fine it somewhere else, you could symlink it... let us know?

FWIW, if you do a search for 'libgtkembedmoz.so' on the forum, you will find 26 threads... without an answer to your problem? :???:

---

### Post by jackfjack on 2006-02-25
I seem to have a problem very similar to 3ntity. I am new to linux and ubuntu. I have had a very difficult time finding a distro that I could install (to an external HD), and was finally able to install ubuntu that way last night. I began playing  around (with browser, email package, etc) and realized that I wanted/needed to add some applications (like smb4k, I think its called). So I gave 'add applications' a try. But, like 3ntity, when I clicked it nothing seemed to happen. There seemed to be a kind of flicker on the screen, but no go. And the 'show updates', 'install updates', 'package manager', and 'update package list now' also didn't seem to do anything when clicked, although when I log on I get a message up in the right hand corner that tells me I have 60 updates or so waiting for me.

So that problem brought me to this thread, and I followed the suggestions herein. I put ```
/usr/bin/gksudo /usr/bin/gnome-app-install
``` in a terminal, as suggested, and I got no error - just another line with a prompt on it. But clicking applications then still didn't do anything. I closed FF and clicked on it, but still no go. The libgtkembedmoz.so is present on my system where you say it should be:
 
```
jack@ubuntu:~$ locate libgtkembedmoz.so
/usr/lib/mozilla-firefox/libgtkembedmoz.so

```

Please tell me what I might try now. What is *supposed* to happen when I click on Add Applications? I tried changing some of the properties in its launcher - for example, 'run in terminal', but all that happens then is a terminal window flickers  on the screen and then disappears, but nothing apparently happens.

---

### Post by jackfjack on 2006-02-25
Okay. I see. Although I am still not able to get anything by clicking on 'add applications' I can get into 'add-remove programs' at the Terminal this way:
```
root@ubuntu:/home/jack# gksudo /usr/bin/gnome-app-install
```

---

### Post by fistfullofroses on 2006-02-26
you can always use apt.
go to the terminal and type in 
apt-get update
apt-get install _______
whre ______ is the package name.

---

### Post by 3ntity on 2006-02-27
inti@Inti:~$ gksudo /usr/bin/gnome-app-install
  File "/usr/bin/gnome-app-install", line 41, in ?
    from AppInstall import AppInstall
  File "/usr/lib/gnome-app-install/AppInstall.py", line 30, in ?
    import gtkmozembed
ImportError: libgtkembedmoz.so: cannot open shared object file: No such file or directory

Ive tried locate libgtkemdebmoz.so but to no avail... I think i might have removed, the previous version of mozilla's folder before/after installing 1.5 ... How can i recover this file?

---

### Post by Greg2 on 2006-02-27
[QUOTE=3ntity]Ive tried locate libgtkemdebmoz.so but to no avail... I think i might have removed, the previous version of mozilla's folder before/after installing 1.5 ... How can i recover this file?[/QUOTE]
This is what you posted earlier in this thread:> Ps. im running this on a 'standard' ubuntu 5.10 installbut now I find out that’s not true?

So please read this thread:
[http://ubuntuforums.org/showthread.php?t=96595](http://ubuntuforums.org/showthread.php?t=96595)
You will find that many programs depend on these libs in Breezy... So I would suggest that you remove firefox 1.5 and reinstall firefox 1.0.7.

If you must have firefox 1.5, you could install that to a ‘separate’ location ‘after’ you’ve reinstalled firefox 1.0.7.

---

