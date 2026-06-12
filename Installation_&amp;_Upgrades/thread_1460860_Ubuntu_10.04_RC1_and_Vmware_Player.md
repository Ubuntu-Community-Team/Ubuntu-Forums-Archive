---
title: "Ubuntu 10.04 RC1 and Vmware Player"
date: 2010-04-23
forum: Installation &amp; Upgrades
---

### Post by stefan_ on 2010-04-23
Hi

I am using Ubuntu with VMWare Player for quite some time and without problems.
Recently I upgraded from 9.10 to 10.04 beta. I ran into the problem with the keyboard (no keyboard on login screen) and solved it.
Everything worked fine until today: I updated my system to RC1 by installing all the new packages.

Since then I can login and it works fine. However when I start a console the console hangs (no prompt shown) and soon after ubuntu hangs.
It does not respond to the mouse or keyboard. Even using Send Ctrl Alt Del from VM Menu in the Vmware player does nothing. I have to reset and start again.

I then downloaded the RC1 cd and created a new Virtual Machine. Installation finishes and I can login (strange thing is the keyboard still does not work on the login screen, I thought this was fixed, but I can use the screen keyboard).

I can use Ubuntu for some time but then it also shows the same locking behaviour.
It seems to be a gnome related problem but I am really not sure.

I did not activate any specific settings, its really a fresh install.
Only thing I installed manually is vpn client for cisco (network manager) and configured it.

I am using VMware Player 3.0.0 build-203739 on Windows Vista 64 bit

Any ideas?
Stefan

---

### Post by Jim_in_Omaha on 2010-04-27
Here is what I have done to get this to work on a Dell laptop with XP as host.

Step 1:
When you come to the login screen click on the "Universal Access Preferences" (It's the little guy in the circle) on the bottom toolbar to the left of the date and time. Then click on the pop-up that says "Universal Access Preferences". Then put a check mark next to "Use on-screen Keyboard". Reboot and you will have an on-screen keyboard that works. Once your in to your Gnome desktop the keyboard works fine.

Step 2:
Run "sudo dpkg-reconfigure console-setup" in a terminal console. I just selected the Dell laptop choice and ENTER through the rest of the selections.

Now it appears to be working. The only problem is I'm stuck with XP for a host on this laptop because of work. Would rather run Xp in VMWare with Ubuntu as the host....:lolflag:

---

### Post by Mike Beatty on 2010-04-30
Thanks for the tip Jim_in_Omaha. I did the same thing, chose the HP laptop and it works fine.:)

I did have to reboot after selecting the virtual keyboard in order to get it to show up.

Mike B.

---

### Post by tripwire45 on 2010-05-01
Thanks Jim_in_Omaha. You also solved my problem. As an aside, my name is Jim and I was born in Omaha. Greetings, brother. :)

---

