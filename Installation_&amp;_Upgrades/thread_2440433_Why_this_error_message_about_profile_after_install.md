---
title: "Why this error message about profile after install?"
date: 2020-04-10
forum: Installation &amp; Upgrades
---

### Post by davepool on 2020-04-10
Still rather new to Ubuntu (and Linux), more or less "coming and going." My first exchange with you all was with Ubuntu Budgie but, this time around, I've decided that the best Ubuntu for me is Ubuntu Mate and the best of my devices to use it on is my little Acer Aspire One 722.

The installations (I did it twice to see if a second attempt would get this message to go away but no such luck) went very smoothly, no hiccups at all. However, on the required post-install restart, once I got past the login screen, I got (and continue to get) this message: 

[B]Error found when loading /home/dave/.profile:

/home/dave/.profile: line 1: /usr/share/defaults/etc/profile: No such file or directory

As a result the session will not be configured correctly. You should fix the problem as soon as feasible.[/B]

I never got that message with my installs of Ubuntu Budgie (though that was on a ThinkPad, not this Acer) and I've noted that whatever it's advising me of has not stopped me from pressing on with first steps, installation of packages, etc.  Still, I'm ready to "fix the problem." I just need to know what it is!  Thanks!

---

### Post by Holger_Gehrke on 2020-04-10
'.profile' is one of the hidden start-up files of the shell. Seems like it's trying to include another file from /usr/share/defaults/etc/profile but that file does not exist. You can either just remove the offending line in an editor or replace it with
```

test -f /usr/share/defaults/etc/profile && source /usr/share/defaults/etc/profile

```
which will test whether the file exists and include it if it does.

Holger

---

### Post by davepool on 2020-04-10
@Holger thanks for the reply. The strange thing is: when I run ls in the terminal for /home/dave that apparently hidden file .profile does not show up. And, as a result, a text editor isn't finding it to open up.

Wait.... ls -a is the command.  I knew that.

The actual "offending line" in .profile (and there's only one line to offend) is: 

source /usr/share/defaults/etc/profile

I'll try replacing it with your line.

Annnnd...it worked!  No error message!  Thanks again!

---

