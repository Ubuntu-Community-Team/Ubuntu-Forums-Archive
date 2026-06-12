---
title: "Doesn't turn off pc after shut down!!"
date: 2008-10-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by janko on 2008-10-15
Ok, one of some problems: if I do shut down (using any button available for the job) the system does everything right until it ends its "shutting down tasks" but then doesn't turn off my notebook.
Any ideas?? So far I press my power button for 4 seconds to cut off power but doesn't seem too safe to me!

---

### Post by Polygon on 2008-10-15
how old is your laptop?

my old computer that has a 400 mhz cpu doesnt shut off after i turn off the computer, it turns off the hard drive and everything but i have to press the power button to actually turn it off. this is the equiviliant of 'it is safe to turn off your computer now" message in windows 95

---

### Post by janko on 2008-10-16
No my laptop has about 2 years, and shut down always worked well in Ubuntu until this beta!
I'm so sad :(

---

### Post by Gina on 2008-10-16
I get this very occasionally with my computers - including desktops.

---

### Post by mejy on 2008-10-16
It's probably an issue between the new kernel and the ACPI hardware of your laptop - the best thing you can do at this stage is probably to file a bug report on launchpad with a detailed list of its hardware.

---

### Post by davidsrsb on 2008-10-16
I have this on my home network, but normal quick shutdown in the office. It does actually turn off after about 3 minutes.
Error messages appear about acpid, dhcp-client and removing routes from eth0.
I sniffed my office connection and Intrepid sends several DNS and MDNS packets during shutdown. 3 minutes is the standard TCPIP timeout
Try unplugging your network cable to see if shutdown happens quicker

---

### Post by Hatfield on 2008-10-18
I've got the same problem.  The last 2 nights I've shutdown my homegrown computer running 64-bit Ibex, it takes me to a blank screen with only a mouse cursor and just sits there.  After waiting for a few minutes(15min last night), I press the power switch and the "Kubuntu" shutdown logo finally pops up, cycles through from light to dark, and the computer shuts down properly.

---

### Post by inportb on 2008-10-18
Sounds sort of familiar... what video chipset and driver are you using?

---

### Post by Hatfield on 2008-10-20
7600GT and proprietary Nvidia accelerated graphics driver (version 177("recommended")).

But the problem seems to have resolved itself.  My computer is now shutting down properly.

---

### Post by drs305 on 2008-10-21
> **Hatfield said:**
> 7600GT and proprietary Nvidia accelerated graphics driver (version 177("recommended")).

But the problem seems to have resolved itself.  My computer is now shutting down properly.

I have the same setup and when I choose the 'Shutdown' text from the lower left corner of the screen it only goes into suspend. Any movement of the mouse resumes to the login page.

---

### Post by davidsrsb on 2008-10-24
I still have this. I used wireshark to trace the traffic and found repeated

Standard query AAAA localhost               to the DSL router
Standard query response, Server failure     from the router

The first line in /etc/hosts is
127.0.0.1 localhost
so I don't know why the PC is trying to lookup

After a few minutes the blinking cursor is replaced by acpid: exit and the PC shuts down

---

### Post by 4Orbs on 2008-10-24
This has fixed the shutdown problem for me, and for some other people on this forum.

Edit the /etc/modules as root with your text editor. Add this line at the bottom of the list.

Save the file, then reboot. Shutdown might work now for you.

```
apm power_off=1
```

Important: Reboot before trying shutdown.

---

### Post by davidsrsb on 2008-10-24
Sorry this did not work,and I did reboot first.
Removing and reconnecting the network cable does cause a quicker shutdown, with error messages nm-dispatcher signal 15

Can somebody post a clean install hosts file, this PC is an upgrade and hosts was modified in the past because of a sudo bug

---

### Post by jongkind on 2008-10-25
These problems are probably related to this bug:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995")

The solution that worked for me was written by:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995/comments/33]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995/comments/33")

(in that solution wlan0 can be substituted by e.g. eth0, depending on your network interface)

---

### Post by hikaricore on 2008-10-26
> **jongkind said:**
> These problems are probably related to this bug:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995")

The solution that worked for me was written by:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995/comments/33]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274995/comments/33")

(in that solution wlan0 can be substituted by e.g. eth0, depending on your network interface)

Didn't fix it for me on either of my systems.

---

