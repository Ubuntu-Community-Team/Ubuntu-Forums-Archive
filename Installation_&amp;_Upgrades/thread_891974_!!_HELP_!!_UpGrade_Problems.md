---
title: "!! HELP !! UpGrade Problems"
date: 2008-08-16
forum: Installation &amp; Upgrades
---

### Post by 4-PackDad on 2008-08-16
Hey;

I tried to go to 8.0.4 from 7.10...

Upgrade 'froze-up'.
Last message was ...
Generating locals
     en.au.utf-8...

Sat at this point for hours.
Did not see any HD activity.

Good or Bad, I rebooted.

Got the Message...
Failed to Initiate HAL!

I get a blank screen.

I can get to my PC thru Failsafe Gnome

Can Not get to the internet.

Proxy server can not be found.

System
  Admin
    Network
The configuration could not be loaded.
You are not allowed to access the system configuration

...
Now What...?
I'm still New to Ubuntu...

Thnx,
Bill

---

### Post by Pumalite on 2008-08-16
Try rebooting and going into an earlier kernel in Recovery Mode.
There:
dpkg --configure -a
That might get you through.

---

### Post by 4-PackDad on 2008-08-16
OK;

I'll give it a shot if you tell me how.
I've only been usung Ubuntu for not quite a year.
Haven't had a change to delve under the hood.

Login Screen
    Options
       Select Sessions
           ??Failsafe Ternimal??   (is what I need)??

Then What???

Other options are:

Last Session
run Xclient Script
Gnome
Secure Rmnote Connection
Failsafe Gnome
Failsfe Terminal

Thnx,
Bill

---

### Post by Pumalite on 2008-08-16
Can you see Grub? There, go to the OS you are upgrading, choose a previous kernel and instead of booting the kernel itsel, choose what comes below it: Recovery Mode

---

### Post by 4-PackDad on 2008-08-16
Hey;

No Grub,,, or any other kind of bug...

In Failsafe Terminal Session...

I got to the following prompt.

grub>

Now what...?

Thnx,
Bill

---

### Post by 4-PackDad on 2008-08-16
OK;

Sorta,,, figured out the "Kernel" thing...

What 'kernel' do I need.
Presume going back to 7.10.

Command options are...

kernel [-no-mem-option] [-type=type]

Need some explaining on this.

Thnx,
Bill

---

### Post by Pumalite on 2008-08-16
If you hyave no Grub; use:
Ctrl+Alt+F1 (2, 3, 4, 5, 6) to get a CLI
Then:
sudo dpkg --configure -a

---

### Post by 4-PackDad on 2008-08-18
> **ubuntal said:**
> The moment the install freezes, run the terminal (Start menu - Accessories - Terminal). A window should pop up showing something like this ```
ubuntal@machine:~$
```

Enter "top" and press Enter (this step is optional, just for you to see what's going on inside the box).

```
ubuntal@machine:~$ top
```

You should see a localedef process at the top, consuming the CPU at about 99%. You should kill it.

To quit the top list, just click the "q" button. Now you need to find out the localedef's id.

In the terminal window enter ```
ubuntal@machine:~$ ps -fe | grep locale
```

You should see something like this ```
ubuntal@machine:~$ ps -fe | grep locale

root      17061  15634  0 11:21 ?     00:01:14 localedef some-options-here...
root      15634  1      1 11:20 ?     00:02:29 locale-gen some-options-here...


```

This means that the upgrade is executing locale-gen, and locale-gen is executing localedef. To kill the bad process, enter (note: in your case the number will be different, just enter your number instead of 15634)

```
ubuntal@machine:~$ sudo kill -9 15634
```

The update should now continue. If it freezes again, kill locale-gen again (the number will again be different).

Then after the upgrade and restart, open a terminal window and enter

```
ubuntal@machine:~$ sudo localedef --no-archive -i en_AU -c -f UTF-8 en_AU.UTF-8
```

In your case it's probably en_US instead of en_AU. To check it's been fixed, go

```
ubuntal@machine:~$ locale
LANG=en_AU.UTF-8
LC_CTYPE="en_AU.UTF-8"
LC_NUMERIC="en_AU.UTF-8"
LC_TIME="en_AU.UTF-8"
LC_COLLATE="en_AU.UTF-8"
LC_MONETARY="en_AU.UTF-8"
LC_MESSAGES="en_AU.UTF-8"
LC_PAPER="en_AU.UTF-8"
LC_NAME="en_AU.UTF-8"
LC_ADDRESS="en_AU.UTF-8"
LC_TELEPHONE="en_AU.UTF-8"
LC_MEASUREMENT="en_AU.UTF-8"
LC_IDENTIFICATION="en_AU.UTF-8"
LC_ALL=

ubuntal@machine:~$ exit

```

Hope this makes sense.

Hey;

Finally got it all figured out......
Should have done more searching first before posting a new thread.
**RE:Hardy 8.04 update freezes on generating locals**

---

