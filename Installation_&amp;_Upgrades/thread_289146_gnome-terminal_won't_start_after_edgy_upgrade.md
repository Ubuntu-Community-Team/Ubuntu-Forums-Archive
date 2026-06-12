---
title: "gnome-terminal won't start after edgy upgrade"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by sillygit on 2006-10-30
Hey All,
After doing a `sudo apt-get dist-upgrade` (my bad, I didn't realise the update-manager handled this) my gnome-terminal won't start.  If I use the icon an entry appears in the task bar with "starting terminal" but after a few seconds it disappears.  If I attempt to start it from within 'konsole' (which runs incredibly slow) I get the following error:
[INDENT]
wasdan@dev05:~$ gnome-terminal
The program 'gnome-terminal' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 105 error_code 2 request_code 78 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
[/INDENT]

Any clues?

Cheers,
Dan

---

### Post by sillygit on 2006-10-30
I think it may have something to do with my xorg.xml.  I have two screens attached (and man was that annoying to set up).

---

### Post by sillygit on 2006-10-30
This thread is a duplicate of
[http://ubuntuforums.org/showthread.php?t=288624](http://ubuntuforums.org/showthread.php?t=288624)

---

