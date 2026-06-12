---
title: "Login blocked after systemd update"
date: 2022-01-13
forum: Installation &amp; Upgrades
---

### Post by joehack on 2022-01-13
Ununtu distributed a systemd update today. As always, the system crashed when applying the systemd update.

After restart, I am no longer able to login with my user.
Strangely enough, the Unifi controller software works fine, but Pi.hole fails to start.

Any idea how to fix this?

---

### Post by MAFoElffen on 2022-01-14
What kind of machine is this?

What Flavor, version, and edition of Ubuntu is this?

It a Desktop Edition, does it display the splash  and go to the Graphical Logon Manager? Which manager is it? Does it display the password replacment characters? If you press <Cntrl><Alt><F4> does it switch over to a VTTY session where can try to login from?

If it does not display the splash and/or graphical logon manager, if at the Grub menu, if you press <E> for edit, go down to the line starting with "linux", delete the words "quiet splash", add the words "verbose debug", and then press <Cntrl><X>, does it display system message showing any errors of note?

If you go to the advance menu > Rescue > Root prompt... Does it go to a root prompt? If so, can you use dmesg from there to look for errors?

To fix what may be wrong, first we need to know where it fails... and what kind of messages it is throwing... It is doesn't boot.that's one thing.If it is actually erroring on a login, then that is another... Some diagnostics of that can be seen if you boot from a LiveCd and scan the system log file for what errors it is throwing...

---

### Post by joehack on 2022-01-14
Ah sorry!
It's a Ubuntu Server 20.04 without a graphical UI.

On the console, it already replies with an error after entering the my user.
As far as I can see it, the system boots without errors. Obviously, I can't check the logs.

I will boot with a live CD on the weekend.

---

### Post by LuddDjur on 2022-01-14
you might also enter the grub menu and edit the linux cmdline to add a ```
init=/bin/bash
``` at the end - this would result in a root shell and you can investigate within the system logs.

---

### Post by MAFoElffen on 2022-01-14
Or like I said... At the Grub Menu, select Advanced, Then Rescue menu, then Root Prompt, to use dmesg to scan the sys log for errors... 

Or boot from an Ubuntu LiveCd to look the the sys logs on the installed system. If you look at the 3rd post of my Graphics Resolution sticky in my signature line, you can mount the system from an Ubuntu LiveCd, then investigate and repair from there.

There are many options.

---

