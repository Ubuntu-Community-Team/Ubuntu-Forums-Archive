---
title: "Do you use Me-TV with ATSC, if so it could use testing for Jaunty"
date: 2009-02-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by metvfan on 2009-02-10
Hi.

I am a fan of Me-TV.  I live in the US which uses ATSC.  But the current releases of Me-TV do not contain ATSC support because there were not enough ATSC users for testing and debugging.  So I started my own branch to help the Me-TV author get ATSC back in the fold.  But as of right now I am the only ATSC user helping out and that is simply not enough.  I am looking for other ATSC users who use or might use Me-TV to help test and debug ATSC support in Me-TV.  The Me-TV author will be very soon hoping to upload a new release of Me-TV to Debian experimental and request a sync with Jaunty.  This is going to happen real quick so if you would like to see ATSC support for Jaunty, you need to get cracking.

Here's the branch:
[https://code.launchpad.net/~me-tv-fan/me-tv/metvfan-atsc](https://code.launchpad.net/~me-tv-fan/me-tv/metvfan-atsc)
Do note that Launchpad seems to occasionally change the branch status to merge, just ignore it as I am working to figure out why and solve it.

As for myself I don't really care if it gets into Jaunty or not as I am content to always build from source, but I will be submitting my ATSC report to the Me-TV author tonight or on Wed.  Please help me out or if you know someone who would like to participate please let them know about this.  Thank you.

[https://launchpad.net/me-tv](https://launchpad.net/me-tv)

---

### Post by LavianoTS386 on 2009-02-10
I switched to VLC so I could have 16:9 to 16:10 conversion. Does the new iterations of me-tv have that?

---

### Post by metvfan on 2009-02-10
> **LavianoTS386 said:**
> I switched to VLC so I could have 16:9 to 16:10 conversion. Does the new iterations of me-tv have that?
I don't know, you would have to ask the author.  Check the contact page or try irc at #me-tv on FreeNode.

---

### Post by Salane on 2009-02-10
Count me in for testing. I have an HVR-1800 and use K/Ubuntu just because it is easy to install/use the 0.5.33 because of the ATSC support. It would be nice to use the later versions.

---

### Post by Salane on 2009-02-10
Since I am not on the mailing list yet. I will post this bug here.


~/metvfan-atsc/src$ ./me-tv -v
Me TV 0.7.14
02/10/2009 17:14:53: Scanning DVB devices ...
02/10/2009 17:14:53: Opening frontend device: /dev/dvb/adapter0/frontend0
02/10/2009 17:14:54: Frontend not supported
02/10/2009 17:14:54: Exception: There are no available DVB tuner devices

---

### Post by metvfan on 2009-02-10
> **Salane said:**
> Since I am not on the mailing list yet. I will post this bug here.


~/metvfan-atsc/src$ ./me-tv -v
Me TV 0.7.14
02/10/2009 17:14:53: Scanning DVB devices ...
02/10/2009 17:14:53: Opening frontend device: /dev/dvb/adapter0/frontend0
02/10/2009 17:14:54: Frontend not supported
02/10/2009 17:14:54: Exception: There are no available DVB tuner devices
It probably does not help that I did not commit the change!#-o
The change is now committed, please re-download the code.

---

### Post by Salane on 2009-02-10
Ok I built the new ME-TV. I imported my channel.conf in from working 0.5.33 and now getting hard locks of my computer. I let it hang for a while and got a unhandled error message. I will try again tomorrow with a clean system and let it scan in its own file.

---

### Post by metvfan on 2009-02-10
> **Salane said:**
> Ok I built the new ME-TV. I imported my channel.conf in from working 0.5.33 and now getting hard locks of my computer. I let it hang for a while and got a unhandled error message. I will try again tomorrow with a clean system and let it scan in its own file.
EDIT:  The channels.conf scan has been fixed, please update your src.  Auto scanning still does not work but importing an existing channels.conf now works where before it gave an error.  So you still need dvb-utils.

Original post.
Me-TV does not support scanning at the moment.  You have to use the scan command provided by the dvb-utils package.  Please read the file README.scan at /usr/share/doc/dvb-utils.  Example below but there are many ATSC files to choose from.

```
$scan /usr/share/doc/dvb-utils/examples/scan/atsc/us-NTSC-center-frequencies-8VSB | tee channels.conf
```

---

### Post by Salane on 2009-02-11
> **metvfan said:**
> EDIT:  The channels.conf scan has been fixed, please update your src.  Auto scanning still does not work but importing an existing channels.conf now works where before it gave an error.  So you still need dvb-utils.

Original post.
Me-TV does not support scanning at the moment.  You have to use the scan command provided by the dvb-utils package.  Please read the file README.scan at /usr/share/doc/dvb-utils.  Example below but there are many ATSC files to choose from.

```
$scan /usr/share/doc/dvb-utils/examples/scan/atsc/us-NTSC-center-frequencies-8VSB | tee channels.conf
```

I am not familiar with bzr and the help wasn't helpful. How do I update? is that bzr merge inside the dir? I guess I was right.
I merge and make. ./me-tv still scrambles the x window but at least ctrl-alt del got me out of it. I will try it with another user this afternoon.

---

### Post by Salane on 2009-02-11
Works well in Gnome, in KDE not so well. Still scrambles the display window. I predominantly use KDE so I will gladly help diagnose that if you want.

---

