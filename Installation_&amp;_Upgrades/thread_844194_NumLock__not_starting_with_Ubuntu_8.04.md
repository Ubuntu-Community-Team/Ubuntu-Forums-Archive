---
title: "NumLock  not starting with Ubuntu 8.04"
date: 2008-06-29
forum: Installation &amp; Upgrades
---

### Post by rats54 on 2008-06-29
Hi,

I know there a lot of different versions of this thread already on the forum, but none of them that I have seen have a solution to my problem.

I want the NumLock key to automatically come on when Ubuntu is at the logon screen and stay on when the desktop opens. Not an unusual request, but one that Hardy does not seem to be able to do.

I have numlock turned on in the BIOS.  I have edited /etc/gdm/Init/Default.  The Mouse Keys are off in System/Preferences/Assistive Technologies/Keyboard Accessibility. I have pressed the F6 key twice.  I have circled the computer chanting.  I have done everything I can find in the forums. Yet, the NumLock must be manually activated.

I have this problem on three computers running Hardy.

When the computer starts to boot, while the branded startup screen is showing the lights on the keyboard flash and the NumLock light stays on.  During Grub the light stays on.  Once Ubuntu starts to load the light goes off and stays off until it is manually turned on.

If I turn on NumLock at the logon screen it will stay on until I manually turn it off or the screen goes black while Hardy is shutting down.

There is something in Grub or Boot that turns off (over rides) NumLock's being turned on by the BIOS.

Does someone have a solution for this problem or am I to continue manually turning on NumLock for ever?

I know that compared to other problems Hardy has this is not major, but it is a real PINTA.

Thanks for your help.

---

### Post by ajgreeny on 2008-06-29
Here is the info that seems to work for me, though interestingly, I haven't had to do it in Hardy and my numlock is always on when I boot.  Perhaps you didn't install numlockx.

** Enabling NUM LOCK at boot **

 The Default behavior is for the NUM LOCK key to be off; if you are on a desktop and have a keypad though, entering digits from it can be much quicker and you may wish to have it enabled for entering login password, etc. Here's how: 
 
[LIST]
[*]From Synaptic, download and install "numlockx," or, from the command line;
[/LIST]
   sudo apt-get install numlockx

[LIST]
[*]To get it working, you now have to edit the appropriate startup file.  First, make sure you have a working backup of the file:
[/LIST]
   sudo cp /etc/gdm/Init/Default /etc/gdm/Init/Default.bak

[LIST]
[*]Next, modify the gdm/Init file.  In terminal:
[/LIST]
   gksudo gedit /etc/gdm/Init/Default

[LIST]
[*]Scroll down to the end of the file, and above the line that says "exit 0" add the following:
[/LIST]
   if [ -x /usr/bin/numlockx ]; then
  /usr/bin/numlockx on 
  fi

[LIST]
[*]Next time you reboot, your NUM LOCK should default to "on."
[/LIST]
Just seen this as well.
Go to System>>Preferences>>Keyboard and then to the Mouse Keys tab and make sure there is no check mark in the "Allow to control the pointer using keyboard"

---

### Post by rats54 on 2008-06-30
Thanks for the reply AJ.  But I had also seen both of the solutions you suggest.  In fact, I have been there, done that with both and still have the problem. neither of them fixed the problem.

On one of the machines with the problem I have downloaded a new version of Hardy, burned the .iso CD and done a complete new install; then used the numlockx solution and nothing changed.  I then tried the other solution and that did not fix the problem.

I have been able to turn on the NumLock and have it work the way I want it to work before I installed Hardy.  It worked on Ubuntu 7.10, after I did the numlockx thing.  It worked with Windows XP Pro on all three computers without a problem.  It is just since I have installed Hardy that I have had the problem.

I do not think I mentioned that all three computers had their HDD wiped clean and reformatted before I did a new install of Hardy.  These are not machines that have been upgraded to Hardy, they have a clean new installation of Hardy.

Thanks again.

---

### Post by gettinoriginal on 2008-07-02
I also was having the same problem, but the solutions here worked great, and now my numlock is auto on.  Thanks for the turorial.

---

### Post by wpshooter on 2008-07-02
I would report these type of things as bugs so they can get fixed and not just try to juryrig some type of workaround !!!

---

### Post by rats54 on 2008-07-05
Thanks gettinoriginal and wpshooter for the reply.

Gettin, which tutorial were to referring to that fixed your problem?

Shooter, I will try reporting the bug, but judging from all the lookers on all of the postings I looked at, There are a lot of people with the same problem.  There is even a thread where they were trying to fix this bug, but it just died out.

Thanks again,

---

### Post by wajje on 2008-07-11
This is not working for me. I tried the workaround you gave me, and the "numlock" button turns on while in login-screen for Ubuntu, but the second i login, it goes "off"..

The biggest issue for me here, is that my real numlock key is broken, so I always have to force myself around that, and activate it in the OS.

i tried downloading numlockx and editing that last line: and now it looks like this
(the last lines)
```

      fi
    fi
  fi
fi
if [ -x /usr/bin/numlockx ]; then
/usr/bin/numlockx on
fi
exit 0

```

Is there anyway for me to "force" on the numlock key?

---

### Post by Za5od on 2009-02-08
> **wajje said:**
> This is not working for me. I tried the workaround you gave me, and the "numlock" button turns on while in login-screen for Ubuntu, but the second i login, it goes "off"..

The biggest issue for me here, is that my real numlock key is broken, so I always have to force myself around that, and activate it in the OS.

i tried downloading numlockx and editing that last line: and now it looks like this
(the last lines)
```

      fi
    fi
  fi
fi
if [ -x /usr/bin/numlockx ]; then
/usr/bin/numlockx on
fi
exit 0

```

Is there anyway for me to "force" on the numlock key?

FYI, I'm running hardy, and I've installed numlockx, which works for GDM, but not AFTER gdm apparently.

That said, I think the "numlock" issue might be keyboard related.  The keyboard that I've got, Logitech DiNovo Keyboard for laptops, doesn't have a dedicated Numlock key like other keyboards.  On it, I have to press/hold CapsLock and then press the "clear" key that's on the number pad to turn on numlock.  I'm thinking about running a test with another keyboard to make sure.  However, as a quick work around, you can always just add "/usr/bin/numlockx on" to  your .bashrc/.profile/.kshrc/.whatever.  I did that, and now my numlock key is "on", even after login.

If you're not sure numlockx works on your system, there's an easy way to test:  start  a terminal, try hitting some number keys on the keypad.  press return; type in /usr/bin/numlockx on, press return, then hit some number keys again.

If you get number, it works, if you don't, then something else is wrong.  If you get numbers, but numlock doesn't work in GDM, then you've most likely mis-placed the lines to turn it on.  To keep it simple, they should be placed right before the "exit 0" line of /etc/gdm/Init/Default.

---

### Post by ucsdrake on 2009-05-03
where can I find the ".bashrc/.profile/.kshrc/.whatever." file?

I have the same problem with the keyboard and its just a simple keyboard I'd like to get working

---

### Post by chk9 on 2009-07-22
> **rats54 said:**
> Gettin, which tutorial were to referring to that fixed your problem?


What ajgreeny wrote is a tutorial or 'how-to', and it worked for me too!

Thanks a lot! =D>
HaveFun.

---

### Post by ggallozz on 2010-01-20
Ubuntu makers, pleeeeease,
would you integrate the NumLock ON in ubuntu once 4 ever ?!
Should you stop pushing us, beginners like me, to mess-up in X CONF files just to do something that nowadays must be a default in modern OS's.
Really. i'm following you (with Ubuntu I means) since v.8.04. testing it. re-installing , and so on. and I do desagree this editing back X Config file every times.

In my mind this is one of the MUST that will bring Ubuntu (and linux's) on the top of the scene for end-users; don't forget that in front of us is still standing M$oft. playing with such "user-friendly" facilities...... 
;-)

tnx a lot for your attention

---

### Post by steveneddy on 2010-01-20
> **ggallozz said:**
> Ubuntu makers, pleeeeease,
would you integrate the NumLock ON in ubuntu once 4 ever ?!
Should you stop pushing us, beginners like me, to mess-up in X CONF files just to do something that nowadays must be a default in modern OS's.
Really. i'm following you (with Ubuntu I means) since v.8.04. testing it. re-installing , and so on. and I do desagree this editing back X Config file every times.

In my mind this is one of the MUST that will bring Ubuntu (and linux's) on the top of the scene for end-users; don't forget that in front of us is still standing M$oft. playing with such "user-friendly" facilities...... 
;-)

tnx a lot for your attention

The developers of Ubuntu do not read these forums.

You need to file a bug report.

What about laptop users? Should numlockx be automatically turned on just for desktop users?

If the numlockx isn't repairing your issue, file a bug report or go over the instructions in ajgreeny's post.

I haven't heard of numlock issues since Edgy, actually.

I recently installed 8.04 on an old desktop at home and the numlock is always on for me, didn't have to enable numlockx.

---

### Post by windspirit219 on 2010-02-08
I am anabsolute newby at Linux, running Karmic Koala( Ubuntu 9.1).  The following post by [ajgreeny]("http://ubuntuforums.org/member.php?u=27747") worked perfectly for me.  Many thanks for this great forum with its wealth of knowledge.
[B]
Enabling NUM LOCK at boot [/B]

 The Default behavior is for the NUM LOCK key to be off; if you are on a desktop and have a keypad though, entering digits from it can be much quicker and you may wish to have it enabled for entering login password, etc. Here's how: 
 
[LIST]
[*]From Synaptic, download and install "numlockx," or, from the command line;
[/LIST]
   sudo apt-get install numlockx

[LIST]
[*]To get it working, you now have to edit the appropriate startup file.  First, make sure you have a working backup of the file:
[/LIST]
   sudo cp /etc/gdm/Init/Default /etc/gdm/Init/Default.bak

[LIST]
[*]Next, modify the gdm/Init file.  In terminal:
[/LIST]
   gksudo gedit /etc/gdm/Init/Default

[LIST]
[*]Scroll down to the end of the file, and above the line that says "exit 0" add the following:
[/LIST]
   if [ -x /usr/bin/numlockx ]; then
  /usr/bin/numlockx on 
  fi

[LIST]
[*]Next time you reboot, your NUM LOCK should default to "on."
[/LIST]

---

### Post by Pelgar on 2010-02-08
I just wanted to add my thanks to ajgreeny for this fix. Numlock has been bugging me in 9.10, my first and only Ubuntu so far. Numlocks is set to ON in my bios and sometimes comes on when Ubuntu boots and sometimes not. I found this rather odd! 
I just went through the steps ajgreeny suggested and rebooted. Numlocks did come on but only time will tell if it comes on every time.

Thanks ajgreeny!!!

---

### Post by bro brian on 2010-12-31
Thanks, ajgreeny. It worked for me too.

---

### Post by presence1960 on 2010-12-31
Not to minimize anyone's pain, but is pressing the NumLock key to activate it that big of an issue? Come on, out of all the things to gripe about this is really trifling!

---

### Post by bro brian on 2011-01-03
> **presence1960 said:**
> Not to minimize anyone's pain, but is pressing the NumLock key to activate it that big of an issue? Come on, out of all the things to gripe about this is really trifling!
Good day, pres.
  It looks like you've been on these forums for a very long time, and I respect your longevity. I also get what you're saying, and it really isn't a big deal to many out there. For others - such as myself, it can be a real problem. I, for one, am running 2 older desktops, and a screaming System76 laptop (Ubuntu factory installed).
  Imagine the ongoing annoyance of remembering which computer I have to hit the Num Lock key on when logging in. It's a real pain. When I forget to press the Num Lock key, and enter all the login info, I get the "password incorrect" BS.
  It's much easier not having to deal with such a nuisance. Much more convenient not having to deal with the Num Lock issue. Having said, you are correct. Not too big an issue - just annoying enough to become an issue.

---

### Post by presence1960 on 2011-01-03
> **bro brian said:**
> Good day, pres.
  It looks like you've been on these forums for a very long time, and I respect your longevity. I also get what you're saying, and it really isn't a big deal to many out there. For others - such as myself, it can be a real problem. I, for one, am running 2 older desktops, and a screaming System76 laptop (Ubuntu factory installed).
  Imagine the ongoing annoyance of remembering which computer I have to hit the Num Lock key on when logging in. It's a real pain. When I forget to press the Num Lock key, and enter all the login info, I get the "password incorrect" BS.
  It's much easier not having to deal with such a nuisance. Much more convenient not having to deal with the Num Lock issue. Having said, you are correct. Not too big an issue - just annoying enough to become an issue.

Like I said "not trying to minimize anyone's pain", but if you can look to see if your num lock light is lit you can avoid keying in the password when num lock is inactive. A split second to take a peek at it saves you 3 more seconds to retype your password again. Sounds like a good trade off, especially since we are talking about "only a few seconds here."

I know it can be a slight nuisance, as my num lock is not active on booting 10.10. But once I trained myself to look at my num lock indicator light my angst has left.

---

