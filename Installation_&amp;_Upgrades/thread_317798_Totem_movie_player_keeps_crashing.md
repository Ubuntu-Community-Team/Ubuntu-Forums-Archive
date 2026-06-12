---
title: "Totem movie player keeps crashing"
date: 2006-12-13
forum: Installation &amp; Upgrades
---

### Post by vivin_west on 2006-12-13
I installed Totem-Xine player through Synaptic in order to play .wmv files. Now the movie player crashes all the time.It doesnt open at all. Even after reinstallation it doesnt work.

---

### Post by 23meg on 2006-12-13
Do you get any error messages when you type "totem" in a terminal?

---

### Post by vivin_west on 2006-12-13
I am not using the terminal. When I click Applications>>Sound & Video>> Movie player it opens and then suddenly disappears from the screen. I donot know how to use linux command window.

---

### Post by vivin_west on 2006-12-13
Here is what I get in the terminal window when I type totem.

(totem:10730): Gdk-WARNING **: locale not supported by Xlib

(totem:10730): Gdk-WARNING **: cannot set locale modifiers
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 69 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
vivin@vivin-desktop:~$

---

### Post by 23meg on 2006-12-13
Did you install totem-xine just to be able to play WMV files? You can play WMV files just fine with the Gstreamer backend after installing w32codecs; did you install it?. I suggest you reinstall totem-gstreamer and [install w32codecs]("https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5").

---

### Post by vivin_west on 2006-12-13
I have installed w32codecs.Still Totem did not play the .wmv files.Then I found that I had to install Totem-Xine in one forum discussion.When I marked Totem-xine for installation, it told me that in order to install Totem-Xine I have to remove gstreamer.I clicked Ok and proceeded.This is the current status

Totem-Xine is installed
Totem gstreamer is uninstalled

Should I reverse the things?

---

### Post by 23meg on 2006-12-13
I think so, especially since totem-xine seems to be causing crashes. You should also install pitfdll and refresh your codec registry. Do the following:```
sudo apt-get install totem-gstreamer gstreamer0.10-pitfdll
rm -rf ~/.gstreamer-0.10
gst-inspect-0.10
```

---

### Post by vivin_west on 2006-12-13
Previous status
Totem-Xine-installed
Totem installed
Totem-gstreamer-uninstalled forcibly ie I cant install totem-xine if totem gstreamer is installed
Will play .wmv file when I go to the directory and click on it
When I run totem it will crash


When I typed your following code and gstreamer0.10-pitfdll got installed

Current stauts
w32codecs-installed
Totem-installed
totem gstreamer-installed
gstreamer pitfdll-installed

Cannot play .wmv file.Message appears that you donot have the right decoder installed.

---

