---
title: "Startup-Manager can break your nvidia drivers."
date: 2011-08-03
forum: Installation &amp; Upgrades
---

### Post by Duncan Williams on 2011-08-03
Using Startup-Manager to change your startup screens,etc. can leave you with no gui on next boot:

[http://peppermintos.net/viewtopic.php?f=9&t=3936](http://peppermintos.net/viewtopic.php?f=9&t=3936)

---

### Post by FormatSeize on 2011-08-03
What Nvidia drivers are you using (I'm going to try to see if mine break)?

---

### Post by Duncan Williams on 2011-08-03
nvidia current (have geforce 6200) from additional drivers.

---

### Post by FormatSeize on 2011-08-03
I couldn't replicate it because I didn't get startup manager to start. I didn't have it at first (I'm not sure exactly what it is), so I installed it. When I tried to run it, I got a bunch of errors, and then a segmentation fault.

I have Nvida GeForce 210 PCIE, and I have the proprietary drivers installed. I'm not sure whether it's the drivers that are causing me to not be able to run startup-manager or it its an operator error on my part. I'll do some searching around to see if I can find anything.

---

### Post by Duncan Williams on 2011-08-03
any info and stuff here:
[http://www.google.com/search?q=startup-manager%20linux](http://www.google.com/search?q=startup-manager%20linux)
should be in `software manager'

---

### Post by Duncan Williams on 2011-08-03
Actually if you read the thread in my first post.
Startup-Manager breaks your grub when you are using nvidia proprietory drivers. I should have made the title a bit more descriptive. can't now (no title edit)

---

### Post by FormatSeize on 2011-08-03
> **Duncan Williams said:**
> Actually if you read the thread in my first post.
Startup-Manager breaks your grub when you are using nvidia proprietory drivers. I should have made the title a bit more descriptive. can't now (no title edit)

Perhaps you should have been. You know why?

***Because now my Nvidia drivers are broken!!***

I get home. It's a long day because my car got stolen earlier this week and I had to take cabs back and forth to work. Then I had to walk (it's quite hot in this area) to the grocery store. I get home, cut on my computer, and take my dog out for a walk. I come back in, and see a command prompt. I log in. Still a command prompt. I try to start the DE, and nothing. One of the messages even mentioned that something "refuses". 

So yeah. Your statement is pretty accurate. Has this been reported as a bug already?

---

### Post by Duncan Williams on 2011-08-04
basically this is the solution (**please test it**)
(edit grub file in > /etc/default/grub)

this is how my grub file looked after the startup-manager problem:

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" vga=769"

delete the " comments " (in 2 lines) and change to:

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""

in terminal enter:
sudo update-grub

Hey presto - everything is fine!

[I]* the grub file needs to be edited and saved in root mode.
* to get to gui after grub broken - info in thread in 1st post.[/I]

---

