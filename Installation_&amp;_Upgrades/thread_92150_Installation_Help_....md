---
title: "Installation Help ..."
date: 2005-11-18
forum: Installation &amp; Upgrades
---

### Post by A.I. BOT on 2005-11-18
I have used Ubuntu and Kubuntu for a while now and I like them very much. I have been wanting really baddly to try xubuntu.

My problem is annoying:
I put in my Ubuntu Breezy Badger PPC CD.
Then I type "server"
Then I go through the install etc etc.
When I get to the consol i log in.
Then I type "sudo su" to login as root.
I then type "nano /etc/apt/sources.list" and edit and save.
I then type "apt-get update"
Then I type "apt-get install xubuntu-desktop gdm".

Everything installs fyne so I say "reboot" and when it reboots, it goes ot the ubuntu boot screen where it checks all the modules, sounds, clock things etc. It gets to the last task "Starting perodic [[something]] ... " and say OK. I wait, I wait, nothing happens, the screen is still there. Then it goes to a non-gui of the boot screen and i still continue ot wait and wait. NOTHING HAPPENS :(


Why??

Thank you.

---

### Post by taurus on 2005-11-18
Why don't you just hit the return key to install a desktop instead of a server at the boot prompt!!!  ;)

---

### Post by A.I. BOT on 2005-11-18
Wont that install regualar Ubuntu with Gnome?

---

### Post by desquer on 2005-11-18
Yes, it will install Gnome. I did just that and then made sure my wireless network was working. I then made the changes you describe and successfully downloaded the XCFE 4.2 stuff (Xubuntu).

I have XCFE 4.2 running (as Xubuntu) and can boot to Gnome or XCFE. There is a link with the instructions, but it sounds like you have that stuff already.

Dave

---

### Post by A.I. BOT on 2005-11-18
Ok i opned synaptic and said for it to install xubuntu-desktop. It gets 1/2 way through the "applying changes" and stops saying "E: /var/cache/apt/archives/ubuntu-docs_5.10-6_all.deb: trying to overwrite `/usr/share/ubuntu-artwork/home/index.html', which is also in package ubuntu-artwork"

:S any ideas on what i can do?

---

### Post by A.I. BOT on 2005-11-19
bump :) any ideas??

---

### Post by A.I. BOT on 2005-11-19
Good news and bad news:

I did a different install instructions, and this time im kinda happy. I rebooted and ejected my CDROM then it goes through a non-gui boot screen then checks clock and dependances, fonts etc then it goes to a gui screen saying that X window system can not start up or was not configured right or something :S

anything i can do?

---

### Post by taurus on 2005-11-19
[QUOTE=A.I. BOT]Good news and bad news:
anything i can do?[/QUOTE]
Yeah.  What video card and monitor do you have???

---

### Post by A.I. BOT on 2005-11-19
I have a mac mini: [http://www.apple.com/macmini/specs.html](http://www.apple.com/macmini/specs.html)
ATI Radeon 9200

I have a Dell monitor (vga).

Tnx

---

### Post by A.I. BOT on 2005-11-19
>.< I reconfigured xserver and it works now :D tnx so much guys

---

