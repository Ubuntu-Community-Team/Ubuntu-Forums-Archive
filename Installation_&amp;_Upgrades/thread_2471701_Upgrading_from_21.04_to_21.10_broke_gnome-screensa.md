---
title: "Upgrading from 21.04 to 21.10 broke gnome-screensaver, why? (Details below)"
date: 2022-02-07
forum: Installation &amp; Upgrades
---

### Post by tomtefar2 on 2022-02-07
I ran a more or less stock Ubuntu 21.04 on my desktop computer, which I recently upgraded to 21.10 (via **do-release-upgrade**, nothing else touched). When I did, something that relates to the screensaver broke. I use gnome, lightdm and Xorg (not Wayland).

(Formatting comment: I use bold text where I would have used inline code tags, if I could find them...)

_Before upgrading_, I started **gnome-screensaver** as my login user (perhaps not the most elegant way, but it worked: A file in **~/.config/autostart** that contained **Exec=/usr/bin/bash -c "screen -ls | grep -F 'gnome-screensaver' > /dev/null || screen -dmS gnome-screensaver /usr/bin/gnome-screensaver"**, i.e., started gnome-screensaver in a screen session), and I could then use **gnome-screensaver-command -l** to lock (and unlock) my screen from an SSH session (and I could use the dedicated lock key on my Logitech MX Keys keyboard)

_After upgrading_, I can lock the screen by going to the top-right corner system meny and choosing "Lock", but I cannot get the screen to lock via **gnome-screensaver-command -l**, and my physical lock key on my keyboard does not lock the screen (but the lock key itself works as before in Windows virtual machines running under Ubuntu, and I get some valid-looking inputs from an **xev** window, so it does not appear to be a keyboard driver issue). I also tried **xfce4-screensaver** instead of the gnome one, and while I got the **xfce4-screensaver-command -l** to work rightaway, it did not work with the lock key on my keyboard. Hence, I need to use gnome-screensaver.


*_ So something broke gnome-screensaver when I upgraded. I'd like to know what and why._* I have a very ugly workaround that I can put in a script during login, but I'd prefer to know why it broke in the first place.


[B]Symptoms:
[/B]
After logging in, my usually-present screensaver screen session is not there. When typing **gnome-screensaver** in a terminal, I get:
> ** (gnome-screensaver:2997311): WARNING **: 00:33:58.852: screensaver already running in this session

**gnome-screensaver-command -q** returned:
> (gnome-screensaver-command:12377): GLib-CRITICAL **: 00:41:13.936: the GVariant format string '(b)' has a type of '(b)' but the given value has a type of '(s)'
(gnome-screensaver-command:12377): GLib-CRITICAL **: 00:41:13.936: g_variant_get: assertion 'valid_format_string (format_string, TRUE, value)' failed
The screensaver is inactive

**ps -ef | grep -i saver** returned the following:
> USERNAME         919174    8129  0 11:15 ?        00:00:00 /usr/bin/gjs /usr/share/gnome-shell/org.gnome.ScreenSaver
USERNAME         935208  934918  0 11:39 pts/6    00:00:00 grep --color=auto -i saver

In other words, the /usr/bin/gjs binary program (actually a symlink to **gjs-console**) seems to try to start the screensaver, and the system "thinks" it has started the screensaver, but it fails somewhere. 
A look in the system log (**journalctl -b | grep -i saver | sed "s/$MYSYSTEMNAME/MYSYSTEMNAME/g"**) returned:
> Feb 05 00:37:09 MYSYSTEMNAME gnome-session[8414]: gnome-session-binary[8414]: WARNING: Could not parse desktop file xscreensaver.desktop or it references a not found TryExec binary
Feb 05 00:37:09 MYSYSTEMNAME gnome-session-binary[8414]: WARNING: Could not parse desktop file xscreensaver.desktop or it references a not found TryExec binary
Feb 05 00:37:10 MYSYSTEMNAME systemd[8129]: Starting GNOME FreeDesktop screensaver service...
Feb 05 00:37:10 MYSYSTEMNAME systemd[8129]: Started GNOME FreeDesktop screensaver service.
Feb 05 00:37:10 MYSYSTEMNAME systemd[8129]: Reached target GNOME FreeDesktop screensaver target.
Feb 05 00:37:10 MYSYSTEMNAME dbus-daemon[8148]: [session uid=1000 pid=8148] Activating service name='org.gnome.ScreenSaver' requested by ':1.77' (uid=1000 pid=8825 comm="/usr/libexec/gsd-power " label="unconfined")
Feb 05 00:37:10 MYSYSTEMNAME dbus-daemon[8148]: [session uid=1000 pid=8148] Successfully activated service 'org.gnome.ScreenSaver'
Feb 05 00:37:10 MYSYSTEMNAME gnome-session[8414]: gnome-session-binary[8414]: WARNING: Could not retrieve current screensaver active state: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.Shell.ScreenShield was not provided by any .service files
Feb 05 00:37:10 MYSYSTEMNAME gnome-session-binary[8414]: WARNING: Could not retrieve current screensaver active state: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.Shell.ScreenShield was not provided by any .service files



**A very ugly workaround is as follows:**

```
kill $(ps -ef | grep -i "/usr/share/gnome-shell/org.gnome.ScreenSaver" | grep -v grep | awk '{ print $2; }')
gnome-screensaver
```

(Yes, there probably should be some error-checking and tests for multiple PID matches, but that worked when I tested it right now.) After this, **gnome-screensaver-command** and my physical lock key work as before - But note that I cannot type gnome-screensaver-command before starting the gnome-screensaver itself, because that will somehow spawn a new "gjs" process.

---

### Post by MAFoElffen on 2022-02-07
Inline CODE TAGS are added like this (using a noparse tag so you can see how to add them):
[noparse]```
 add_output_or_commands_here 
```[/noparse]

So it looks to me as if the command changed with the versions or it can't find a file (where it says it cannot find a binary). 

Is that what I am seeing?

---

### Post by tomtefar2 on 2022-02-08
Re: The screensaver issue:
The problem is that Ubuntu "thinks" it has started a screensaver, as evidenced by "Feb 05 00:37:10 MYSYSTEMNAME dbus-daemon[8148]: [session uid=1000  pid=8148] Successfully activated service 'org.gnome.ScreenSaver'". But it does not work, that's the problem. And I only noticed this after upgrading from Ubuntu 21.04 to Ubuntu 21.10.

But I did notice something else by starting **journalctl -f** and trying to see anything useful in the **dbus-monitor** output (too much text too fast): It appears that the lock key on my keyboard casues **gsd-media-keys** to activate, which will start the invalid screensaver (as will some periodic polls from other programs) - There will then be an error message "Couldn't lock screen: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.Shell.ScreenShield was not provided by any .service files".

So the keyword seems to be "***org.gnome.Shell.ScreenShield***", but I don't know enough about dbus or low-level gnome utilities to fix the root cause. I did not find any filename under /etc, /var or /usr that contained "ScreenShield", but I did find (e.g.) /usr/share/gnome-shell/org.gnome.ScreenSaver, so it seems something is missing. Or a bug.



So if anyone knows why this happened, if there was a related change in the 21.04->21.10 upgrade, I'd like to know.


But I have made this workaround script, which I run every time I login:
```

#!/bin/bash

# https://ubuntuforums.org/showthread.php?t=2471701

# /usr/bin/gjs /usr/share/gnome-shell/org.gnome.ScreenSaver

DEBUGPRINTOUTS=true
DEBUGPRINTOUTS=false

CORRECT_SCREENSAVER="gnome-screensaver"
CORRECT_SCREENSAVER_FULL_COMMAND="/usr/bin/$CORRECT_SCREENSAVER &"

# Note that starting the screensaver will (probably) cause it to block, so nothing will be written to the log. Use "&"


NO_INVALID_SAVERS=$(ps -ef | awk '{ print $8 " " $9 };' | grep "/usr/bin/gjs /usr/share/gnome-shell/org.gnome.ScreenSaver" | wc -l)
NO_GNOME_SAVERS=$(ps -ef | awk '{ print $8; }' | grep "$CORRECT_SCREENSAVER" | wc -l)


if $DEBUGPRINTOUTS; then echo -e "\t\t[DEBUG] Before any screensaver action: $NO_GNOME_SAVERS correct ones and $NO_INVALID_SAVERS invalid ones are running"; fi


if [ "1" == "$NO_GNOME_SAVERS" ] && [ "0" == "$NO_INVALID_SAVERS" ]; then
        # All is well, already running
        logger -t "SCREENSAVER" -p user.notice "No change, one (correct) $CORRECT_SCREENSAVER process was already running"
        exit 0
elif [ "0" == "$NO_GNOME_SAVERS" ] && [ "1" == "$NO_INVALID_SAVERS" ]; then
        # Seems the incorrect screensaver was running - Kill it and start the correct one
        kill $(ps -ef | awk '{ print $2 " " $8 " " $9 };' | grep "/usr/bin/gjs /usr/share/gnome-shell/org.gnome.ScreenSaver" | grep -v grep | awk '{ print $1; }')
        if $DEBUGPRINTOUTS; then echo -e "\t\t[DEBUG] Trying to start $CORRECT_SCREENSAVER_FULL_COMMAND"; fi
        eval "$CORRECT_SCREENSAVER_FULL_COMMAND"
        if $DEBUGPRINTOUTS; then echo -e "\t\t[DEBUG] Started $CORRECT_SCREENSAVER_FULL_COMMAND"; fi
        # Confirm that the correct screensaver is running
        NO_INVALID_SAVERS=$(ps -ef | awk '{ print $8 " " $9 };' | grep "/usr/bin/gjs /usr/share/gnome-shell/org.gnome.ScreenSaver" | wc -l)
        NO_GNOME_SAVERS=$(ps -ef | awk '{ print $8; }' | grep "$CORRECT_SCREENSAVER" | wc -l)
        if [ "1" == "$NO_GNOME_SAVERS" ] && [ "0" == "$NO_INVALID_SAVERS" ]; then
                logger -t "SCREENSAVER" -p user.notice "Killed the invalid screensaver and started the (correct) $CORRECT_SCREENSAVER"
                exit 0
        else
                logger -t "SCREENSAVER" -p user.err "Tried to kill the invalid and start the correct screensaver, but failed: $NO_GNOME_SAVERS correct ones and $NO_INVALID_SAVERS invalid ones are running"
                exit 1
        fi
elif [ "0" == "$NO_GNOME_SAVERS" ] && [ "0" == "$NO_INVALID_SAVERS" ]; then
        # Something might have closed down, because no screensaveer of any kind was running
        if $DEBUGPRINTOUTS; then echo -e "\t\t[DEBUG] Trying to start $CORRECT_SCREENSAVER_FULL_COMMAND"; fi
        eval "$CORRECT_SCREENSAVER_FULL_COMMAND"
        if $DEBUGPRINTOUTS; then echo -e "\t\t[DEBUG] Started $CORRECT_SCREENSAVER_FULL_COMMAND"; fi
        # Confirm that the correct screensaver is running
        NO_INVALID_SAVERS=$(ps -ef | awk '{ print $8 " " $9 };' | grep "/usr/bin/gjs /usr/share/gnome-shell/org.gnome.ScreenSaver" | wc -l)
        NO_GNOME_SAVERS=$(ps -ef | awk '{ print $8; }' | grep "$CORRECT_SCREENSAVER" | wc -l)
        if [ "1" == "$NO_GNOME_SAVERS" ] && [ "0" == "$NO_INVALID_SAVERS" ]; then
                logger -t "SCREENSAVER" -p user.notice "No screensaver whatsoever was running, started the (correct) $CORRECT_SCREENSAVER"
                exit 0
        else
                logger -t "SCREENSAVER" -p user.err "No screensaver was running, tried to start the correct one, but failed: $NO_GNOME_SAVERS correct ones and $NO_INVALID_SAVERS invalid ones are running"
                exit 1
        fi
else
        logger -t "SCREENSAVER" -p user.err "Unexpected number of screensaver processes found, will not to anything: $NO_GNOME_SAVERS correct ones and $NO_INVALID_SAVERS invalid ones are running"
        exit 1
fi


```



Re: Formatting: Thanks, but to me, the code part appears in a bounded box, not flowing with the text in the same paragraph:
Like this, from here to the end of this post is the same paragraph: Here, ```
I put some inline code
``` in the middle of a sentence.

---

### Post by MAFoElffen on 2022-02-08
Yes... not exactly "inline"... It does push it down to it's own. But does respect BB code tags.

When I was a Moderator here, I was supposed to tell everyone to ensure they only posted commands and/or raw output within tags. If not, besides filling pages and being hard to read, it sometimes wreaks havoc on the Forums System software... Moderators have enough to do here. Them having to edit User's posts adds extra work for them. I try to kindly tell people to go back and edit their posts to inform them. Keeps the peace.  

*** 
I have to say, I looked through your code in your work-around. My compliments. I like your "coding style". I don't tell many people that, and I have had 32 years of experience, so... It is easy to read and follow. I am impressed in your understanding of the problem, and how you approached it. Your code follows your previous explanation, checking the conditions of, and being able to react to those conditions... Having been a maintenance programmer for a time, I really appreciate that you comment your code with your own thoughts, to help "tell the story of how it should be working..." LOL I do that in my code, to jog my own memory, and as a courtesy to others that read my code later on.

The correct, best action from here, would be to file a Bug Report, using 
```

ubuntu-bug gnome-screensaver

```
To report it to Launchpad, so that they can investigate the problem, and get changes made through the upstream channels to correct it. I'm active on Launchpad. That is what I would do, so that it gets fixed and works for everyone. (In Linux as a whole. Not just in Ubuntu.) I invite you to create a User Account there, so that it gets the attention it needs, and that you can follow it to the end.

---

### Post by schragge on 2022-02-08
Could it have something to do with GNOME issue [#4100]("https://gitlab.gnome.org/GNOME/gnome-shell/-/issues/4100")? Looks like this won't be fixed on the GNOME side anytime soon, as it was closed and labelled "[highlight]Expected Behavior[/highlight]".

[Here]("https://discourse.ubuntubudgie.org/t/5394") is the relevant discussion on Ubuntu Budgie forum.

And some nitpicking ;)

> **tomtefar2 said:**
> **A very ugly workaround is as follows:**

```
kill $(ps -ef | grep -i "/usr/share/gnome-shell/org.gnome.ScreenSaver" | grep -v grep | awk '{ print $2; }')
```
This is what [pkill]("https://manpages.debian.org/unstable/procps/pkill.1.en.html") and [killall]("https://manpages.debian.org/unstable/psmisc/killall.1.en.html") are for.
```
pkill -9 -f '/usr/bin/gjs /usr/share/gnome-shell/org.gnome.ScreenSaver'
```

> **tomtefar2 said:**
> ```
NO_INVALID_SAVERS=$(ps -ef | awk '{ print $8 " " $9 };' | grep "/usr/bin/gjs /usr/share/gnome-shell/org.gnome.ScreenSaver" | wc -l)
NO_GNOME_SAVERS=$(ps -ef | awk '{ print $8; }' | grep "$CORRECT_SCREENSAVER" | wc -l)
```
How about
```
NO_INVALID_SAVERS=$(pgrep -cf '/usr/bin/gjs /usr/share/gnome-shell/org.gnome.ScreenSaver')
NO_GNOME_SAVERS==$(pgrep -c "$CORRECT_SCREENSAVER")
```:?:

---

### Post by MAFoElffen on 2022-02-08
That issue you linked to was opened and closed 9 months ago. 

I think/feel that if a 'new' Bug Report was opened in Ubuntu Launchpad, with the OP's data that he has collected on it, it would be triaged and confirmed by Launchpad, which would give it validity to upstream Gnome as a valid issue that needs to be corrected.

I do not see an recent Bug Reports like this filed on gnome-screensaver on Launchpad.

---

### Post by schragge on 2022-02-08
Well, here is the relevant Launchpad bug: LP#[lpbug]1930104[/lpbug].

See also [Keyboard shortcut for lock screen no longer works even when set to something else (21.10)]("https://askubuntu.com/questions/1387638") @ Ask Ubuntu. So, reinstalling **ubuntu-desktop** may help.

LP#[lpbug]1901109[/lpbug] provides an interesting script to test working of the lock key. Here is my version of it
```
#!/bin/sh
result='/tmp/result'
rm -rf "$result"
service='org.gnome.ScreenSaver'
cnt=60
while [ 0 -lt "$((cnt=cnt-1))" ]
do
  echo "$cnt" >>"$result"
  dbus-send --print-reply --dest="$service" \
    /org/gnome/ScreenSaver "$service".GetActive >>"$result"
  loginctl session-status|sed '1{s/ .*//;q}'|
    xargs -r loginctl -pLockedHint --value show-session >>"$result"
  echo >>"$result"
  sleep 1
done
```
It is supposed to be autostarted on login with
```
[Desktop Entry]
Name=ScreenStatusMonitor
Comment=Monitor Screen lock status
Terminal=false
Type=Application
Exec=/tmp/test.sh
```

---

### Post by Claus7 on 2022-02-08
Hello,

just to mention that trying to fix some issues of lock/login screen of ubuntu, I came across the gnome-screensaver package. In its description it was stated more or less that it was a package that was no longer required. I do not know if the OP fell in-between those versions that gnome-screensaver was no longer supported as it used to.
Under ubuntu development version it states: Screensaver and screen lock formerly used in GNOME.
I think an alternative would be xscreensaver

Regards!

---

### Post by schragge on 2022-02-08
A quote from [XScreenSaver FAQ]("https://www.jwz.org/xscreensaver/faq.html#gnome-screensaver") (by its author, [Jamie Zawinski](https://en.wikipedia.org/wiki/Jamie_Zawinski)):
> 21. **I'm running GNOME or KDE, and everything's broken!  What's wrong?**

[indent] Probably you are not running XScreenSaver at all, but are running "gnome-screensaver" or "kscreensaver" instead. You should stop.

XScreenSaver is secure, stable, and mature; whereas gnome-screensaver is bug-ridden, unreliable, and an ongoing security disaster (for all the reasons outlined in the [On Toolkits](https://www.jwz.org/xscreensaver/toolkits.html) page).[/indent]

---

### Post by tomtefar2 on 2022-02-09
> **MAFoElffen said:**
> 
I have to say, I looked through your code in your work-around. My compliments. I like your "coding style". I don't tell many people that, and I have had 32 years of experience, so... It is easy to read and follow. I am impressed in your understanding of the problem, and how you approached it. Your code follows your previous explanation, checking the conditions of, and being able to react to those conditions... Having been a maintenance programmer for a time, I really appreciate that you comment your code with your own thoughts, to help "tell the story of how it should be working..." LOL I do that in my code, to jog my own memory, and as a courtesy to others that read my code later on.


Thanks - And coding isn't even my day job. :-) But I think that keeping comments in the code, and prioritizing readability over compact code, means that I don't have to remember what I've done. The less I have to reverse-engineer my own code *x* months or years later, the better.

> **MAFoElffen said:**
> 
The correct, best action from here, would be to file a Bug Report, using 
```

ubuntu-bug gnome-screensaver

```
To report it to Launchpad, so that they can investigate the problem, and get changes made through the upstream channels to correct it. I'm active on Launchpad. That is what I would do, so that it gets fixed and works for everyone. (In Linux as a whole. Not just in Ubuntu.) I invite you to create a User Account there, so that it gets the attention it needs, and that you can follow it to the end.

I might just do that, haven't reported bugs before except for creating questions at Github.

---

### Post by tomtefar2 on 2022-02-09
> **schragge said:**
> Could it have something to do with GNOME issue [#4100]("https://gitlab.gnome.org/GNOME/gnome-shell/-/issues/4100")? Looks like this won't be fixed on the GNOME side anytime soon, as it was closed and labelled "[highlight]Expected Behavior[/highlight]".

[Here]("https://discourse.ubuntubudgie.org/t/5394") is the relevant discussion on Ubuntu Budgie forum.

And some nitpicking ;)

This is what [pkill]("https://manpages.debian.org/unstable/procps/pkill.1.en.html") and [killall]("https://manpages.debian.org/unstable/psmisc/killall.1.en.html") are for.
```
pkill -9 -f '/usr/bin/gjs /usr/share/gnome-shell/org.gnome.ScreenSaver'
```


How about
```
NO_INVALID_SAVERS=$(pgrep -cf '/usr/bin/gjs /usr/share/gnome-shell/org.gnome.ScreenSaver')
NO_GNOME_SAVERS==$(pgrep -c "$CORRECT_SCREENSAVER")
```:?:

The problems from that Budgie thread seem very similar yes, but I have never tried Budgie. Their solution looked  very similar to mine too.
I have run a "deployment script" I originally created for installing Ubuntu on a Raspberry Pi, and on the RPi I changed the configuration to use slickgreeter, lightdm and xfce4, for performance reasons. So I do have xfce4-screensaver installed on my system, but I don't use it. But there might be some residual config somewhere that caused similar symptoms for me as in the Budgie case.

Regarding code nitpicking: Thanks for the tips. And I am sure there are many ways to create more compact code, there usually are lots of more or less well-known options to many commands... 
But: I usually tend to use commands whose syntax I can remember without looking it up, and since I don't process huge datasets (especially not in this case), performance is not an issue (i.e., I don't care that every pipe spawns another process). I think it is easier, for me at least, to interpret  long strings of commands and syntax I know by heart, instead of looking up man pages or help screens for (admittedly more optimized) commands I rarely use.

---

### Post by schragge on 2022-02-09
I'm with **Claus7** on this. Just purge **gnome-screensaver** and use **xscreensaver** instead.

---

### Post by tomtefar2 on 2022-02-09
> **Claus7 said:**
> just to mention that trying to fix some issues of lock/login screen of ubuntu, I came across the gnome-screensaver package. In its description it was stated more or less that it was a package that was no longer required. I do not know if the OP fell in-between those versions that gnome-screensaver was no longer supported as it used to.
Under ubuntu development version it states: Screensaver and screen lock formerly used in GNOME.
I think an alternative would be xscreensaver

Regards!

The problem appeared when upgrading 21.04 -> 21.10, so that is possible... But when gnome-screensaver was ***not*** running, no screensaver (or lock key) worked. xfce4-screensaver worked from the commandline as before, but that did not catch the lock key on my keyboard.

I have not tried to reinstall the entire desktop package.

---

### Post by tomtefar2 on 2022-02-09
> **schragge said:**
> A quote from [XScreenSaver FAQ]("https://www.jwz.org/xscreensaver/faq.html#gnome-screensaver") (by its author, [Jamie Zawinski]("https://en.wikipedia.org/wiki/Jamie_Zawinski")):

I'm not really in a position to evaluate the author's claims regarding security, but I did note that his original words are from 2004 and I assume that something has happened to fix security holes in gnome-screensaver since then.


But the main reason I will *probably* not switch to that package, and especially not if my keyboard lock key and command line locking/unlocking do not work, is this: The reason for my screensaver is to prevent my child from doing stuff on my home computer. The purpose of the screensaver is not to protect nuclear launch codes in a public environment. As long as the screensaver does not present a remote vulnerability that traverses both computer software firewall and my router, my current setup is secure enough (or more precisely, vulnerabilities are likely to exist outside of the screensaver).

---

