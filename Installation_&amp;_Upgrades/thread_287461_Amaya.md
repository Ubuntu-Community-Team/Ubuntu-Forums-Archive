---
title: "Amaya"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by marcadams on 2006-10-28
Hi;

Just installed Edgy, and wanted to test out Amaya (part of standard repositories). 

However, after installed, when launched it waits a few seconds - the GUi flashes up, then disappears. 

Any advice on getting this running?

Many Thanks
Marc

---

### Post by marcadams on 2006-10-30
Hi there - the problem resolved itself.
Initially I had just restarted the desktop after installing Amaya.
However after re-booting the system, Amaya starts correctly.

Thanks
Marc

---

### Post by Zdravko on 2006-10-30
What is "Amaya "?

---

### Post by pzonik on 2006-11-02
> **marcadams said:**
> Hi there - the problem resolved itself.
Initially I had just restarted the desktop after installing Amaya.
However after re-booting the system, Amaya starts correctly.

Thanks
Marc

Amaya is a special web browser for web designers (full W3C support).

I also have problem with Amaya 9.51 under Ubuntu 6.10. When I started Amaya form console, I recieved this massage:

schopenhauer@aristotle:~$ amaya
11:53:10: Deleted stale lock file '/home/schopenhauer/.amaya-schopenhauer'.

(amaya:5140): Gtk-CRITICAL **: gtk_widget_set_colormap: assertion `!GTK_WIDGET_REALIZED (widget)' failed
The program 'amaya' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 5354 error_code 8 request_code 142 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
schopenhauer@aristotle:~$ 

Than I try higher version (current realise is 9.52; in Edgy repositories is 9.51) form [http://www.w3.org/Amaya/](http://www.w3.org/Amaya/) (.deb package is available), and without results. I see:

schopenhauer@aristotle:~$ amaya
12:07:44: Deleted stale lock file '/home/schopenhauer/.amaya-schopenhauer'.
The program 'amaya' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 305 error_code 8 request_code 143 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
schopenhauer@aristotle:~$ 

Please help.

---

### Post by n3Cre0 on 2006-12-05
I just did "sudo aptitude install amaya"

But I get this output
> 
n3Cre0@EdgyEft:~$ amaya
09:00:35 PM: Deleted stale lock file '/home/n3Cre0/.amaya-n3Cre0'.
09:00:35 PM: Warning: Mailcap file /etc/mailcap, line 39: incomplete entry ignored.
09:00:35 PM: Warning: Mailcap file /etc/mailcap, line 40: incomplete entry ignored.

(amaya:17116): Gtk-CRITICAL **: gtk_widget_set_colormap: assertion `!GTK_WIDGET_REALIZED (widget)' failed
The program 'amaya' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 5354 error_code 8 request_code 142 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

Haven't yet rebooted though..

---

