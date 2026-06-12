---
title: "need help gnome won't load after getting updates"
date: 2007-05-17
forum: Installation &amp; Upgrades
---

### Post by juniorsonny on 2007-05-17
I installed fiesty and it went great but after I downloaded and installed the updates Gnome will not load up at start. I get a error box at start up saying it failed to load and will try at next start up.  Any ideas?

---

### Post by heimo on 2007-05-17
Possible workaround (which will lose your gnome settings), run this in virtual console (ctrl+alt+F2):
```
mv ~/.gnome2 ~/.gnome2_bak
```

---

### Post by juniorsonny on 2007-05-17
Sorry, I thought the error message said just Gnome, it actually said it could not start the Gnome Settings Daemon.  Would it help this too?

---

### Post by juniorsonny on 2007-05-18
Tried the work around but no success. The whole error message says.

There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.

Please help!! It takes 3 or so minutes for Gnome to load after log in.

---

### Post by heimo on 2007-05-18
Drop to virtual console (ctrl+alt+F2) and try pinging localhost
```
ping localhost
```

Does it work?

---

### Post by juniorsonny on 2007-05-18
when I typed in ping localhost all I got was.

ping localhost (127.0.0.1) 56(84) bytes of data

---

### Post by heimo on 2007-05-18
This is all just guessing - but I once had similar problem and doing something like this fixed the problem:
```
sudo ifup lo
sudo ifconfig lo 127.0.0.1
sudo route add 127.0.0.1 lo

```

---

### Post by juniorsonny on 2007-05-18
Thanks,   I do this in virtual console?

---

### Post by heimo on 2007-05-18
> **juniorsonny said:**
> Thanks,   I do this in virtual console?

Yeah. On command line.

---

### Post by juniorsonny on 2007-05-18
Still no luck.  When I entered - sudo ifup lo- it gave me this

Ignoring unknown interface lo=lo.

Even though this came up I still entered the other 2 lines but it didn't work.

---

### Post by heimo on 2007-05-18
Check that you have these lines in /etc/network/interfaces:
```
auto lo
iface lo inet loopback

```You can edit interfaces file with command:
```
sudo nano /etc/network/interfaces
```

It's possible that this has nothing to do with your problem, but it may be related.

---

### Post by juniorsonny on 2007-05-19
This is a silly question.  Trying to save in nano but can't get it to save.  How do you save in nano?  I usually use gedit but it's not pulling up the file.

---

### Post by heimo on 2007-05-19
Ctrl+O

or

Ctrl+X and then select Y to save before exiting.

---

### Post by juniorsonny on 2007-05-19
Thanks,  I edited the interfaces file and saved with your help.  Then I went to virtual console and reconfigured lo and everything is working Great!!!!!   Thanks a lot for all your help!!!  I also downloaded Envy to get my Nvidia Geforce 5200 video card working!!!

---

