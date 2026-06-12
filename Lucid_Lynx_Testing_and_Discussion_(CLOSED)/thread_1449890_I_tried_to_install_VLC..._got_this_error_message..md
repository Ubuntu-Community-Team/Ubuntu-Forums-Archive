---
title: "I tried to install VLC... got this error message."
date: 2010-04-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Ric_NYC on 2010-04-08
~$ sudo apt-get install vlc  vlc-nox vlc-data
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  [B]vlc-nox: Depends: libass3 (>= 0.9.6-1) but it is not installable
           Depends: libiso9660-5 but it is not installable[/B]
E: Broken packages




VLC was uninstalled after the upgrade to Lucid.

---

### Post by oldos2er on 2010-04-08
Do you have the universe repository enabled?

---

### Post by cariboo on 2010-04-08
I've got libiso9660-7 installed, are your package lists up-to-date, and pointing to the right place?

---

### Post by ankspo71 on 2010-04-08
I just installed 'vlc' and 'mozilla-plugin-vlc' about 1.5 hours ago, and they also included 'vlc-data' and 'vlc-nox' as dependencies. You might have tried to install the packages as they were updating them.

Do you get the same error when trying to install vlc by itself? It should automatically include vlc-nox and vlc data.

---

### Post by bsmith1051 on 2010-04-08
which repository are you using?  Have you tried installing it through the Ubuntu Software Center?

---

### Post by Ric_NYC on 2010-04-08
> **oldos2er said:**
> Do you have the universe repository enabled?


Yes. It is enabled.

---

### Post by Ric_NYC on 2010-04-08
> **cariboo907 said:**
> I've got libiso9660-7 installed, are your package lists up-to-date, and pointing to the right place?


I didn't change any settings.

---

### Post by Ric_NYC on 2010-04-08
> **bsmith1051 said:**
> which repository are you using?  **Have you tried installing it through the Ubuntu Software Center?**


Yes. I got this message:

> **Package dependencies cannot be resolved** 

This error could be caused by required additional software packages which are missing or not installable. Futhermore there could be a conflict between software packages which are not allowed to be installed at the same time.

---

### Post by vredley on 2010-04-08
Is your /etc/apt/sources.list pointing to the Karmic repos? This is what I get on Lucid:

```
~$ sudo apt-get install vlc vlc-nox vlc-data
...
The following NEW packages will be installed:
liba52-0.7.4 libass4 libdca0 libdvbpsi5 libdvdnav4 libebml0 libfaad2 libiso9660-7 libmatroska0 libmpeg2-4 libsdl-image1.2 libtar libtwolame0 libupnp3 libvcdinfo0 libvlc2 libvlccore2 libxcb-keysyms1 vlc vlc-data vlc-nox
```

As you can see, vlc depends on libass4 and libiso9660-7, not libass3 and libiso9660-5.

---

### Post by ranch hand on 2010-04-08
Both of those files are in the repo.  I just checked synaptic.

Either your repo info is out of date or you just need to install them.

You could try a different mirror if they are not listed for you.

---

### Post by wkulecz on 2010-04-08
I just uninstalled all the vlc packages as I couldn't get "Open Capture Device" to work.  Locked up my capture card (SAA1734) until I rebooted.

TVtime works fine.  Zapping TV Viewer pops up error dialogs on startup and then doesn't do anything useful.


This simple gstreamer pipeline works fine once I've set the source input with TVtime:

gst-launch v4l2src ! video/x-raw-yuv, framerate=\(fraction\)30000/1001 ! xvimagesink

so I think there be problems with vlc and ZappingTV.

---

### Post by QLee on 2010-04-08
> **cariboo907 said:**
> I've got libiso9660-7 installed, are your package lists up-to-date, and pointing to the right place?

Ric, the above quote was a very good hint.

> **Ric_NYC said:**
> I didn't change any settings.

That is not the point people are trying to make to you, when it was suggested, I imagine cariboo907 wanted you to check your installation. If your sources list is correct the next thing suggested will probably be a reload of the packages files (or "check" on update manager). Your system is not trying to install the correct package. I've given no new information, it's all here in the thread, I've just rephrased a bit.

Edit: Oops, I see you prefer apt-get, one I left out, you will want an apt-get update to get the new packages files.

---

### Post by Ric_NYC on 2010-04-13
Thanks for all help.

I changed some software sources. 
VLC was installed, but it doesn't start.

This is the error message:

> vlc: error while loading shared libraries: libvlc.so.2: cannot open shared object file: No such file or directory


---

