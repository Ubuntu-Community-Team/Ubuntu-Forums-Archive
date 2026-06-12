---
title: "Password Recover not working - here in LiveUSB"
date: 2014-07-24
forum: Installation &amp; Upgrades
---

### Post by Mark_in_Hollywood on 2014-07-24
I did a clean install of 12.04 today. All the updates. Next I did a distribution upgrade to 14.04. Entered a password, twice. Green check mark says they match.

Rebooted. Got to Login/password entry screen. Entered password (previously written on paper). OS would not accept pw.

Googled for "14.04" password recover.

Found some help, reading:

[http://linuxconfig.org/ubuntu-14-04-lost-password-recovery](http://linuxconfig.org/ubuntu-14-04-lost-password-recovery)

and a few others and all use the same methodology:

At GRUB, select "e" and add

init=/bin/bash to end of line starting with the word: Linux

next, F10

drop to a terminal like screen and type:

# mount -o remount,rw/
# passwd
-----here you enter a password, twice, on two separate line to confirm they match-----
Reboot

I tried this. I got to the place to add a password, I typed a new password. Twice.

I rebooted. But I did have to press the reset button on the computer case, as the following commands were not recognized:

quit, exit, reboot, sudo exit, sudo shutdown -r now and some others.

Does this problem mean the password change failed?

FYI the key combination Alt-SysRq-R-E-I-S-U-B-K did not work from that screen either.

What is the proper command to reboot?

At the password entry screen, the password would not work.

So, here I am, in LiveUSB (Precise ver. 12.04) asking what to do next.

---

### Post by kc1di on 2014-07-25
the Correct terminal command for reboot is ```
shutdown -r now
```
as for your password I can only assume that maybe your caplock key is on or something of that nature.

I've never had a problem with 12.04 not remembering the password.

---

### Post by Mark_in_Hollywood on 2014-07-25
As I have my /home on a separate partition, my work is "safe". I decided to re-install 12.04 and even it balked with Keyring problems. My guess is that some of the old or older packages, apps, and software my have been connected to the old password.

I would not have changed the password, but the installation of 14.04 broke and I was asked to send an error report which included my password. So I immediately changed my password. 

If I delete the Keyring's "login" will it automatically re-spawn it and show a place to enter a new password?

And believe me, I wrote the password down on paper, which I have in front of me. The caps lock isn't on. This is a serious serous problem with Ubuntu.

---

### Post by kc1di on 2014-07-25
I know you most likely don't want to here this , But if it were me I'd back up my important data and reinstall the whole thing formatting my /home partition as well.
it could be any number of things in those old config files that's causing the problem. 
good Luck :)

---

### Post by steeldriver on 2014-07-25
The instruction you followed

```

# mount -o remount,rw/
# passwd
-----here you enter a password, twice, on two separate line to confirm they match-----

```

sets the **root** password (and hence unlocks the root account) - not your **user's** password. You would need to do
```

# mount -o remount,rw/
# passwd [COLOR=#0000ff]***your_username***[/COLOR]
-----here you enter a password, twice, on two separate line to confirm they match-----

```

In any case, can you log in via one of the CLI virtual terminals (e.g. Ctrl-Alt-F1)? It may be a GUI session startup issue rather than a password issue, since you are so sure you were using the correct (written down) password.

---

