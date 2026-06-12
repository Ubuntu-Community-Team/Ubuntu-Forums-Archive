---
title: "trying to go back to 9.10 from 10.4"
date: 2010-04-11
forum: Installation &amp; Upgrades
---

### Post by bboyreason on 2010-04-11
i tried out the beta of 10.4, but i am having issues i think because i installed wicd but changed a repository source incorrectly because i have seen a few "k" programs/processes and i am using gtk;
so now i want a fresh 9.10 install, i dont even care about data being wiped or losing settings at all;
i plugged up a usb and booted and it gets as far as "choose your language" then there is a splash screen and it goes quickly(like 1 second) to 10.4 login screen;
i could grab a HD camera and try to analyze the splash screen as it is too fast to read;
but i thought i would see if i am doing something obviously wrong;
the initial install, btw, was ubuntu netbook remix on an asus eee 1.6 atom, i stopped netbook remix and maximus window manager from startup, then it gets a little gray as i am not sure if i did anything else before upgrading to 10.4;
btw again, the splash screen says something about "... cant be overwritten" i think

---

### Post by drpjkurian on 2010-04-11
> **bboyreason said:**
> i tried out the beta of 10.4, but i am having issues i think because i installed wicd but changed a repository source incorrectly because i have seen a few "k" programs/processes and i am using gtk;
so now i want a fresh 9.10 install, i dont even care about data being wiped or losing settings at all;
i plugged up a usb and booted and it gets as far as "choose your language" then there is a splash screen and it goes quickly(like 1 second) to 10.4 login screen;
i could grab a HD camera and try to analyze the splash screen as it is too fast to read;
but i thought i would see if i am doing something obviously wrong;
the initial install, btw, was ubuntu netbook remix on an asus eee 1.6 atom, i stopped netbook remix and maximus window manager from startup, then it gets a little gray as i am not sure if i did anything else before upgrading to 10.4;
btw again, the splash screen says something about "... cant be overwritten" i think

Hi
If you do not mind data loss, then I would suggest you to format the hard disk with partition editor which is available in live session.

So when you boot from USB, select the first option which says "Run ubuntu without any change to HD" something like that

Navigate to System>Prefernce or administration>partition editor.

Select format the drive and wipe everything

And then do a fresh install of karmic

---

### Post by bboyreason on 2010-04-11
thanks doc;
yes, i forgot to mention it does give me the option to do: live, permanent, test, etc;
i do also have the machine currently working with 10.4, it is just janky;
i tried to format from the 10.4 regular desktop with an administrative tool(forget which) but was told the drive was in use! (obviously, but i would think the program would be prepared for this)
do i need to specifically format from a live cd/usb?
or can i format in 10.4 desktop/gtk or with the command line?

edit: i just wanted to add, 10.4 seems great so far; 
i think i just messed it up by changing around network-manager for wicd before i understood the process;
btw, should average users try to report problems/bugs?

---

