---
title: "problems with serial mouse and edgy install"
date: 2007-09-15
forum: Installation &amp; Upgrades
---

### Post by jamesr on 2007-09-15
Hi, 
I am additional problems with the Edgy install . The installation worked when I used the alt cd. All completed but the mouse is not active which makes the rather difficult to do anything. I seen this problem before but I cannot find any notes on the fix. The mouse is a serial 3 button.

---

### Post by jamesr on 2007-09-15
hi,

The problem was solved, for completeness I will post the information ie fix from the fixed system later. So I suppose I change keep Ubuntu 6.10 user in my signature.

---

### Post by jamesr on 2007-09-17
Hi,

How the problem was solved. I assume many others are solved the problem the same way.

Boot to user / password page
select sessions
select failsafe terminal
```
sudo /etc/X11/xorg.conf
``` Then change lines in file 
```
 Option          "Device"                "/dev/ttyS0"
Option          "Protocol"              "Microsoft"

```  NB that it is ttyS0 if com1 or ttyS1 if com2 and that it is S not s.
 Save file and exit :-
 Cntrl X, Yes, return.

Reboot and all is well.

On a general point. I know that the newer kernels do not automatically find serial mice but it seems to me at least short sighted to remove a very basic feature that even Microsoft still supports. If there was not a alternative CD ie non graphics I would have been screwed.

Now back to where I was 2 days to upgrade to Feisty (7.04)

---

### Post by debianchick on 2007-09-17
> **jamesr said:**
> 
On a general point. I know that the newer kernels do not automatically find serial mice but it seems to me at least short sighted to remove a very basic feature that even Microsoft still supports. If there was not a alternative CD ie non graphics I would have been screwed.

Now back to where I was 2 days to upgrade to Feisty (7.04)



The new kernels do have serial support. It is just Ubuntu and few other distros that disable it because they think no one uses serial mice or external modems any more.

---

### Post by jamesr on 2007-09-17
Hi, 
I know they have support but my point was about automatically finding the information. But I do take your point about some distros needing help on that front. I also hope that I will remember about the serial modems on another system that I am going use as a fax machine.

---

