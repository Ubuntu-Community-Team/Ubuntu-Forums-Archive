---
title: "Ekiga 2.9 for test using Intrepid"
date: 2008-07-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by YannickDefais on 2008-07-19
Hello,

Ekiga is a free Voice over IP, IP Telephony and Video-Conferencing application for Linux and other Unices.

I'm building packages for Intrepid of the current SVN of Ekiga. Ekiga 3.0 should land in intrepid, thus I do it to test if our new Ekiga compile right on intrepid and also for testing purpose.

Ekiga 3.0 includes many, many new features.

Mainly:
- Contact status in the main window (offline, online, away, do not disturb) with custom messages,
- Much better video quality for a lower bandwidth,
- A bit easier setup Assistant (not finished yet...)
- Slightly different GUI (including a panel for calls)
- Many internal improvements.

Screenshot:
[https://help.ubuntu.com/community/Ekiga#Development%20snapshots](https://help.ubuntu.com/community/Ekiga#Development%20snapshots)

Please: **Do not report bug about this package to Ubuntu, report directly to upstream here: [http://bugzilla.gnome.org/enter_bug.cgi?product=ekiga](http://bugzilla.gnome.org/enter_bug.cgi?product=ekiga)**

If you have issue with installing the packages, you can report to me in this forum.

Here are the instructions:
[http://snapshots.ekiga.net/](http://snapshots.ekiga.net/)

Best regards,
Yannick

---

### Post by emid on 2008-07-19
I had been testing out the Ekiga snapshots on my 8.04 amd64 machine.  I've had some problems and had to go back to the regular Ekiga builds.  I recently decided to give the snapshot another try, but when I try to install it I get the following error:

```
E: /var/cache/apt/archives/libpt-snapshot-plugins-alsa_20080718v01hardy2_amd64.deb: trying to overwrite `/usr/lib/ptlib-snapshot/2.3-beta0/device/sound/alsa_pwplugin.so', which is also in package libpt-snapshot-ptrace
E: /var/cache/apt/archives/libpt-snapshot-plugins-v4l2_20080718v01hardy2_amd64.deb: trying to overwrite `/usr/lib/ptlib-snapshot/2.3-beta0/device/videoinput/v4l2_pwplugin.so', which is also in package libpt-snapshot-ptrace
```

I have been using the following repo:

```
deb http://snapshots.ekiga.net/snapshots/ubuntu/ hardy main

```

I know your post was about Intrepid testing, I hope I'm not too far off base posting here. :)

Any help would be appreciated.

---

### Post by YannickDefais on 2008-08-29
> **emid said:**
> I had been testing out the Ekiga snapshots on my 8.04 amd64 machine.  I've had some problems and had to go back to the regular Ekiga builds.  I recently decided to give the snapshot another try, but when I try to install it I get the following error:

```
E: /var/cache/apt/archives/libpt-snapshot-plugins-alsa_20080718v01hardy2_amd64.deb: trying to overwrite `/usr/lib/ptlib-snapshot/2.3-beta0/device/sound/alsa_pwplugin.so', which is also in package libpt-snapshot-ptrace
E: /var/cache/apt/archives/libpt-snapshot-plugins-v4l2_20080718v01hardy2_amd64.deb: trying to overwrite `/usr/lib/ptlib-snapshot/2.3-beta0/device/videoinput/v4l2_pwplugin.so', which is also in package libpt-snapshot-ptrace
```


Hello,

Sorry for the long delay.

The -ptrace version of opal and ptlib has been deprecated in my new build.

You should be able to upgrade now.

Best regards,
Yannick

---

### Post by freechelmi on 2008-09-19
Hi , i'm wondering , 

Does the latest interpid Alpha include Ekiga ? I don't see it in the packages intrepid pages.

---

### Post by mihai.ile on 2008-09-25
Well just checked today's daily build and the version is:
/pool/main/e/ekiga/ekiga_2.0.12-0ubuntu5_i386.deb

Too bad it will not come with the 3.0 version that was released...

---

### Post by Bou on 2008-10-14
Hi Yannick, I've got a couple questions about the version in your PPA:

-When the assistant first asks you to give your user and password, do you need to write "username" or "username@ekiga.net"?
-I seem to be unable to talk to any of my contacts, or even the echo test. When I try to call, I get a "no common codec" error message. Does this have a known cause?

---

### Post by forcecore on 2008-10-14
maybe they install Ekiga 3.0 in final i think, it should be in because it is more advanced than 2.0.

---

