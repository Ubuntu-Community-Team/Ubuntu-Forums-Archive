---
title: "Failed to start X server"
date: 2005-11-16
forum: Installation &amp; Upgrades
---

### Post by futz on 2005-11-16
Went to install Ubuntu 5.10 on a box here today. Everything went normally until the reboot. Then it errors out and says, "Failed to start X server". I can login to a normal text terminal from there, but don't know how to get X to go.

The machine is a generic older P4 that previously ran Fedora 4 and Mandriva with no problems. The video card is pretty vanilla too - Asus V7700 GeForce2.

Any ideas?

---

### Post by Kyral on 2005-11-16
Could you tell us the error that X is spitting out?

---

### Post by futz on 2005-11-16
Ok, here it is:

```
Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?
```

And here are some of the (most likely) pertinent parts of that output:

```
Using config file: "/etc/X11/xorg.conf"
```

It does something like this three times:

```
Skipping... "/usr/X11R^/lib/modules/extensions/libGLcore...
  No symbols found
```

And then the actual errors:

```
(EE) NV(0): No valid modes found
(EE) Screen(s) found, but none have a usable configuration

Fatal server error.
no screens found
```

---

### Post by invalid on 2005-11-16
Try
```
sudo dpkg-reconfigure xserver-xorg
```
to reconfigure your xorg.conf file.

If this does not work, maybe you could post the contents of /etc/X11/xorg.conf so that we can inspect it.

Cheers,
Cb

---

### Post by futz on 2005-11-16
I'll try that, but here's one more data point first. I stuck in a PCLinuxOS live-cd and had the exact same problem. The Ubuntu live-cd pukes too.

Now I'm going to try that reconfigure thing.

---

### Post by futz on 2005-11-16
> Now I'm going to try that reconfigure thing.

No go. Package xserver.xorg is not installed.

---

### Post by futz on 2005-11-16
> If this does not work, maybe you could post the contents of /etc/X11/xorg.conf so that we can inspect it.

Pretty tough to do. The text screen is screwed up too. There's no cursor and line wrap is all buggered up. I'm certainly not going to try to write it all on paper.

We're gonna slam in a different video card and see what happens.

What fun! First time I've seen the Ubuntu install puke.

---

### Post by Kyral on 2005-11-16
Did you type in "xserver-xorg" or "xserver.xorg" :P

---

### Post by futz on 2005-11-16
Ok, hold on. Don't waste any more time on this thread. 

I think it's a strange hardware problem. I forgot that this mainboard was flaky before, but it went away. Well now the flakiness is back and even worse. Possibly loose or broken RAM slot(s). Reseat and the problem either changes or goes away temporarily.

I'm pretty sure it's not Ubuntu's fault now.

---

### Post by Kyral on 2005-11-16
I don't know if that is a good thing or a bad thing.

I mean its cool that the problem isn't with Ubuntu, but it sucks that it may be your Motherboard

---

### Post by futz on 2005-11-16
> but it sucks that it may be your Motherboard

No big deal. It was a freeby, and a crappy RD-RAM freeby at that. One of many old klunkers here in the swamp. 

My Ubuntu (and PCLinuxOS) box (that I'm typing on right now) I found by a dumpster. The case was bent up from the previous owner chucking it in a rage (I assume). With a bit of work and some junkyard parts it runs better than any Celeron has a right to. It's one of my favorite older boxes now.

I have newer boxes too. It's not all klunkers here at Futz's Computer Emporium.

---

