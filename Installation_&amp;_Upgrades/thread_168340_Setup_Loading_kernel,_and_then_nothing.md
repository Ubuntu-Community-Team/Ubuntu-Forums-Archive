---
title: "Setup: Loading kernel, and then nothing"
date: 2006-04-30
forum: Installation &amp; Upgrades
---

### Post by haris_led on 2006-04-30
Hello, 
I'm a new user of linux, and i have a problem when I try to install ubuntu 5.10 on my system.
I have an acer aspire 1692 wlmi laptop.
After the system reads the ubuntu cd, i press enter to continue installation and in the next screen I get: "Uncompressing Linux... OK, loading kernel."
After that nothing happens:-k :( 
Can anyone tell me what to do?
I have downloaded the iso again, and burned but also nothing.
The same happens with the live cd, and with the dvd version!](*,) ](*,) 
I am downloading right now the 6.06 version ([http://releases.ubuntu.com/6.06/ubuntu-6.06-beta2-live-i386.iso](http://releases.ubuntu.com/6.06/ubuntu-6.06-beta2-live-i386.iso)) to see if the problem will be solved:confused:

---

### Post by cilynx on 2006-04-30
Usually, this is a ACPI issue.  One of my laptops does the same thing unless I disable ACPI entirely.  

Trying another version of the install as you are doing is generally the easiest way to start troubleshooting.  I don't remember the boot menu on the install CD off hand, but if there is a "failsafe" or "no ACPI" method of booting, I'd give that a shot.

---

### Post by haris_led on 2006-04-30
[QUOTE=cilynx]Usually, this is a ACPI issue.  One of my laptops does the same thing unless I disable ACPI entirely.  

Trying another version of the install as you are doing is generally the easiest way to start troubleshooting.  I don't remember the boot menu on the install CD off hand, but if there is a "failsafe" or "no ACPI" method of booting, I'd give that a shot.[/QUOTE]
Thank you for your answer.
Indeed, i gave this: linux acpi=off (as stated in help menu) and the instalation began successfully:) 
Now I face another problem.
The instalation is done, and ubuntu loads after a restart, and then I hear a sound (probably the sound when ubuntu begins) and the screen goes off:(
P.S. I have an ati mobility x700 graphics card.:confused:
EDIT: that sound is like a drum! if, this helps! thanks again! :)

---

### Post by cilynx on 2006-04-30
The drum noise is the default GUI login noise, which means your system thinks it's working.  I'm betting your screen goes off because your graphics card is trying to run a resolution that your monitor doesn't support.

If you Ctrl+Alt+F1, do you get a text console?

---

