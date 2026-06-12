---
title: "shutdown crashes with 2.6.27 kernels"
date: 2008-09-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by scradock on 2008-09-13
Is anyone else having this problem?

My laptop shuts down normally with Hardy, or Intrepid using the 2.6.26 kernels. Trying to shut down Intrepid using any of the 2.6.27 kernels leads to a crash; the screen fills with a trace, but there is no way to scroll the screen to see more lines of the trace, or to continue to shut down. SysRq-REISUB reboots, or Power Off turns the machine off. Nothing else works.

I get this behavior however I try to shut down: System | Shutdown; Reboot or Shotdown from the new user switcher; even "sudo shutdown -r now" in a terminal.

None of the logs I have checked refers to anything after the shutdown call (15).

I have filed a bug report - complete silence for over a week.

Any confirmation? Any ideas?

---

### Post by ronacc on 2008-09-13
I'm not getting that here with 64bit intrepid and I haven't seen any other posts mentioning it perhaps somehow something got mis configed on your system. check synaptic for broken packages and maybe run sudo apt-get dist-upgrade if you have just been going the standard upgrade route , I know I've had to dist-upgrade a couple of times to get some packages to install that were held back for no reason I could see .

---

### Post by Nullack on 2008-09-13
Whats the bug number?

Remember, improving your bug report and generally managing it yourself as it moves through the lifecycle is possible and encouraged.

The only issue I have on shutdown is that NM 0.7 doesnt end clean.

---

### Post by Trespasser on 2008-09-13
> **Nullack said:**
> 

The only issue I have on shutdown is that NM 0.7 doesnt end clean.

Same problem here, as well. I'm sure it will be mended soon. Ibex is starting to smooth out, except for needing firestarter to surf the internet (no biggie on that point). :).

---

### Post by Nullack on 2008-09-13
To be honest Im not convinced NM 0.7 will be mended in time given how tight the gnome schedule for 2.24 now is.

---

### Post by scradock on 2008-09-14
OK, glad to hear no-one else sees the same problem.

I see the NM closing down messages; the screen-full of crash trace has a line about usplash, so both those packages might be responsible. Trouble is that to give more information for the bug report I would like more information about the crash, and nothing seems to be being logged.

Any idea of how I can trap and post the crash trace from the final screen, short of copying it by hand?

The bug# is 264571. I don't know what I can do to progress it, without some feedback from those who know more than I do about what might be going on.

I suspected a mis-configuration, so I did a clean install of alpha-5, but the same thing happened. I now have two fully up-to-date Intrepid installs, (one continuously upgraded from alpha-2, the other newly installed at alpha-5 and upgraded from there) with no unmet dependencies hanging things up; the one with kernel 2.6.26-5 shuts down fine, and the one with 2.6.27-3 hangs as I described. Using any 2.6.27 kernel on either of them causes the crash on shutdown.......

On the same machine, Hardy shuts down fine.

---

### Post by Nullack on 2008-09-14
Ive responded to your bug.

---

### Post by scradock on 2008-09-14
> **Nullack said:**
> Ive responded to your bug.

Thanks, Nullack. I posted the output for both installs. Both look just like yours did.

---

### Post by scradock on 2008-10-16
Argghhhh! The usplash crash on shutdown is back! It hasn't been a problem for several weeks, but after I did the huge update yesterday (October 15th) I'm getting the crash dump and frozen machine on shutdown again.

I thought it might be usplash, which was updated from 0.5.24 to 0.5.25, but it doesn't seem to be that, after checking logs and downgrading to 0.5.24.

Work-around is to use nosplash in the boot stanza, but that isn't ideal. Usplash isn't working, and I don't know why.

Nullack suggested that the problem was with uvesafb originally, but it went away after a few days, and I thought someone had stopped calling usplash during shut-down - the splash screen never appeared, and the crash didn't happen. Now it's back...........

---

