---
title: "Ubuntu 8.10 - Can't connect to internet"
date: 2008-10-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by fificam on 2008-10-11
Hey all,

I've recently installed Ubuntu 8.10 (downloaded it on Thursday) on my computer, alongside Windows.

However, my internet connection has not worked out of the box. Both my network devices...

- ASUSTek Computer RTL8111/8168B
- Realtek RTL-8139/8139C/8139C+

...are greyed out on the dropdown menu from the Network Connections icon on the top bar. The internet connection on my Windows partition works flawlessly.

I have never used a Linux distribution before, so I don't have a clue about where to start troubleshooting. If someone could hold my hand through the process, I would be very grateful.

Thanks in advance.

---

### Post by Perfect Storm on 2008-10-11
Moved to Intrepid Ibex Testing and Discussion.


> I have never used a Linux distribution before, so I don't have a clue about where to start troubleshooting. If someone could hold my hand through the process, I would be very grateful.

Perhaps trying 8.04 instead as 8.10 is still in testing/development phase.

---

### Post by jblackhall on 2008-10-11
> **fificam said:**
> Hey all,

I've recently installed Ubuntu 8.10 (downloaded it on Thursday) on my computer, alongside Windows.

However, my internet connection has not worked out of the box. Both my network devices...

- ASUSTek Computer RTL8111/8168B
- Realtek RTL-8139/8139C/8139C+

...are greyed out on the dropdown menu from the Network Connections icon on the top bar. The internet connection on my Windows partition works flawlessly.

I have never used a Linux distribution before, so I don't have a clue about where to start troubleshooting. If someone could hold my hand through the process, I would be very grateful.

Thanks in advance.

Are these hardwire (ethernet) connections or wireless ones?  If they're hardwire, it's a known bug.  You actually should have internet, it's just not displayed correctly on Network Manager (the icon in the system tray).  For example, if you check for updates (System -> Administration -> Update Manager) you'll find that your internet connection is just fine.  If you can't get Firefox to load correctly, go to File -> and uncheck 'Work Offline' and you should be good to go (although at this point you have to do this every time you load Firefox, it's part of the bug).  They're working on getting this solved though.  

[https://bugs.launchpad.net/ubuntu/hardy/+source/network-manager/+bug/191889](https://bugs.launchpad.net/ubuntu/hardy/+source/network-manager/+bug/191889)

If it's wireless, then I'm not sure what the problem is.

---

### Post by fificam on 2008-10-11
Thanks for the reply Jblack.

The connection is wired, not wireless. I tried going to System -> Administration -> Update Manager, but it only returned a long list of 'W: Failed to fetch so-and-so'.

I assume that means I'm still not connected to the internet.

---

### Post by jblackhall on 2008-10-11
ah, this is gonna sound weird.  I read again that you're running a dual boot on Windows (that right?).  I had a problem like this before on another computer where Windows would disable the network cards on shut down.  So I know it sounds weird, but try shutting down and then physically unplugging your computer for about 30 seconds.  This should reset the NIC and you should be able to use it.  If that works, there (hopefully) is an option in your BIOS to disable that feature so Windows can't lock you out of your NICs anymore.

If that doesn't work, then I'm not sure what the issue could be.  Perhaps file a bug report?  [http://bugs.launchpad.net/ubuntu/intrepid](http://bugs.launchpad.net/ubuntu/intrepid)

---

### Post by fificam on 2008-10-12
Thanks for another reply :-)

> **jblackhall said:**
> you're running a dual boot on Windows (that right?)
Correct.

> **jblackhall said:**
> try shutting down and then physically unplugging your computer for about 30 seconds.  This should reset the NIC and you should be able to use it.
It didn't work unfortunately :(

Anyway, I recently wiped my hard drive and installed 8.04. I'm still getting the same problem, but I'm hoping I might get more help if I'm on the supported version. You can see my new thread [here](http://ubuntuforums.org/showthread.php?t=945328).

Thanks for your efforts all the same, Jblack.

---

### Post by ShirishAg75 on 2008-10-12
It actually might be [lpbug] 279262 [/lpbug] but that's in 8.10, dunno about 8.04

---

