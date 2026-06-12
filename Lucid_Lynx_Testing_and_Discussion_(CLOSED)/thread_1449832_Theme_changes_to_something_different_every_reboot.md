---
title: "Theme changes to something different every reboot"
date: 2010-04-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by JDShu on 2010-04-08
Hey! Ever since I upgraded (straight upgrade through upgrade manager) to Lucid and used the Ambiance theme, the theme changes to something ugly every time I restart. Going to Preferences->Appearance changes it back to Ambiance without even choosing a theme. Is this a common problem? Thanks!

---

### Post by ankspo71 on 2010-04-08
It's not happening to me, but to me it sounds like it might be gnome-settings-daemon crashing on startup. I haven't upgraded though, this is a fresh install.

If you run
```
killall gnome-settings-daemon 
```
does it give you the ugly theme your were talking about?

```
gnome-settings-daemon
```
will apply the theme again.

After a reboot, and when your theme doesn't start, check inside your home folder in a hidden file called ".xsession-errors". Look for any error messages in there for gnome-settings-daemon. Also copy any errors that the terminal gives for gnome-settings-daemon. The "Log File Viewer" might have info on gnome-settings-daemon crashing too.

Once you know what the problem is, report it by running 
```
ubuntu-bug <package-name>
```
in the terminal.

A temporary fix might be adding a startup application entry for gnome-settings-daemon

---

### Post by JDShu on 2010-04-08
Looks like you were exactly right! Following your directions, I filed a bug report [here]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/558611").

---

### Post by ankspo71 on 2010-04-08
Here is a similar bug report, but it is for one version older of Ubuntu.
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/521766](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/521766)

It looks like your bug report got an automated response and it got closed due to lack of collected information from the bug reporting application (apport). 

Do you happen to see any crash reports popping up like this? 
[https://wiki.ubuntu.com/Apport?action=AttachFile&do=get&target=apport-gtk-desktopfile.png](https://wiki.ubuntu.com/Apport?action=AttachFile&do=get&target=apport-gtk-desktopfile.png)
[https://wiki.ubuntu.com/Apport?action=AttachFile&do=get&target=apport-async-crash.png](https://wiki.ubuntu.com/Apport?action=AttachFile&do=get&target=apport-async-crash.png)

I ask because according to [https://wiki.ubuntu.com/Apport#How%20to%20enable%20apport](https://wiki.ubuntu.com/Apport#How%20to%20enable%20apport)
it says that apport (the bug reporting application) is not enabled by default on stable releases, which is what you upgraded from, so you might have to check to see if apport is enabled.

An easy way to do it is to go to the terminal (or press Alt+F2) and type:
```
gksudo gedit /etc/default/apport
```
(enter password)
and look at the line that says... "enabled=0" or "enabled=1"
If it says 0, replace the 0 with 1 so that it is enabled.
Save the file, then close the text editor, then reboot enough times to see if it will catch the gnome-settings daemon crashing. If the file  already says "1" then apport is not finding the problem for some reason.

---

### Post by JDShu on 2010-04-08
Apport seems to be enabled. I get a crash that looks like your second image. When I click on it it says that gvfs-gdu-volume-monitor closed unexpectedly, though that sounds like a separate issue right?

---

### Post by JDShu on 2010-04-08
Actually its might not be a separate issue, I just looked at .xsession-errors again.

```

(gnome-settings-daemon:1154): GdkPixbuf-CRITICAL **: gdk_pixbuf_format_get_name: assertion `format != NULL' failed

```

```
(gnome-settings-daemon:1154): GVFS-RemoteVolumeMonitor-WARNING **: invoking IsSupported() failed for remote volume monitor with dbus n$
The program 'gnome-settings-daemon' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 1015 error_code 8 request_code 3 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```so confused hahaha

---

### Post by JDShu on 2010-04-12
bump.. any idea what I should do? I don't even know how to file a bug report properly :(

---

