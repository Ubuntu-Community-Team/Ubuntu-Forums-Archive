---
title: "Cant install or run Live (7.04)"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by ByggareBob on 2007-04-19
Just downloaded Desktop 7.04, burned it on a cd (verification OK).

Now... Booting the cd and choosing "live" manually or selecting "start or install" just gives me :

"/bin/sh: Can't access tty; Job control turned off

ata 3.00 : failed to set xfermode"

What is wrong? Thanks in advance!

---

### Post by Teamgeist on 2007-04-19
What kind of machine are you trying this on?

Try hitting F6 at the install screen an add acpi=off to the bootline of the Kernel. See if that helps.

---

### Post by ByggareBob on 2007-04-19
Thank you!

Adding acpi=off helped me!

Actually... I am writing this in Firefox running on the Ubuntu Live CD.

---

### Post by BackwardsDown on 2007-04-19
Thanks Teamgeist, this has helped me too:)

---

### Post by lnogueir on 2007-04-19
On my notebook LG S1  I always get the messenger "Failed to start the x-server". 

C2D - 7200
Ati Mobility Radeon x1600!

Help! Please!

---

### Post by oyvinst on 2007-04-19
I'm getting a black screen after the 7.04 livecd has been booting for a while. Nothing works except Ctrl+Alt+Del. 

My hardware (short):
Thinkpad Z61m 
Radeon Mobile ATI X1400 128MB
2GB RAM

Tried all of the following:
noquiet nosplash : doesn't help
apci=off noquiet nosplash: doesn't help
noapic nolapic noquiet nosplash: doesn't help
acpi=off noapic nolapic noquiet nosplash: doesn't help

I don't think I can disable ACPI on this machine, because when off, lots of hardware fails to configure properly, including SATA/PATA controller.

I can't see any error messages after screen goes black, Alt+Fn is a no-go. I am suspecting that my ATI X1400 is causing problems. However, both Dapper(!) and Edgy livecds worked fine on this very same laptop before.

*Sigh* perhaps it's time for alternate-install-CD text-only installation mode ? 

Øyvind

---

### Post by infinite84 on 2007-04-19
I think i´ve got the same problem as you Inogueir...
Cannot start the x-server :( Not even on the live-cd.

Fatal server error:
Caught signal 11. Server aborting

XIO: fatal IO error 104 (Connection reset by peer) on X server ":0,0" after 0 requests (0 known processed) with 0 events remaining.

I´ve got an Asus F3Ja with ATI x1600.

Here is some "screens" of the error log:
[http://www.nascom.se/pettersson/e1.jpg](http://www.nascom.se/pettersson/e1.jpg)
[http://www.nascom.se/pettersson/e2.jpg](http://www.nascom.se/pettersson/e2.jpg)

---

### Post by infinite84 on 2007-04-19
Found a solution after some hours@google ;)



"I'll keep this quick, even though it's cost me several sleepless nights. The "ati" driver supplied on the Ubuntu CD doesn't support many of the new ATI video cards, namely the Radeon X* series. This is how you get around it:

   1. Boot from the CD and wait for the X server to crash.
   2. Press CTRL+ALT+F1 to switch to the console.
   3. Type sudo apt-get install xorg-driver-fglrx to download the official drivers.
   4. Run dpkg-reconfigure xserver-xorg, keep the defaults, but select "fglrx" instead of "ati" when it asks you what driver to use.
   5. Run startx and enjoy the LiveCD as everyone else sees it.

I hope this helps someone. "

Enjoy! :D

---

### Post by oyvinst on 2007-04-20
Ctrl+Alt+Fn was broken for me after the installation crash. So I installed Feisty via alternative text-mode only install, plugged in fglrx, and everything was fine.

---

### Post by BackwardsDown on 2007-04-20
I have installed ubuntu.

But now my system boot's really slow, it hangs for a few minutes on the first pixel of the loading bar. When I did ctrl-alt-f1 I saw that it gave me this error again, and a few times. After displaying this error a few times it went on booting and everything seems normal.

How to solve this long boottime? In the grub boot options acpi=off is already there.

---

### Post by tanari on 2007-04-20
I run liveCD choose "start or install" and after that I see only black screen :(. 
Don't know what to do.

---

