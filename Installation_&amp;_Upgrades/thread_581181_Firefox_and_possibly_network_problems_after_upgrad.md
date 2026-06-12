---
title: "Firefox and possibly network problems after upgrading to 7.10"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by mkaz on 2007-10-19
After upgrading 7.04 to 7.10 I am having problems accessing the internet with Firefox.
Firefox starts up and displays the local, default Ubuntu start page. When I try to access any external website, Firefox tries for quite a while and then fails.
I can access my local website with Firefox, which seems to indicate that Firefox itself works. I deleted the local cache but this did not help.

I am writing this from my Windows machine and I can access the website of the Ubuntu machine from the Windows machine. Seems like networking does work, at least in my local net.

I can ping outside sites from the Ubuntu machine.

Any ideas how to fix the Firefox issue? How to proceed and how and what to check?

Thanks,
Michael

---

### Post by phonixor on 2007-10-19
i am having similar problems,

though when i fetched the DNS address of my router and added it to my wireless .... (which wasnt required before) it started working again... though very very sluggish...

---

### Post by Original Brownster on 2007-10-19
Hi,

```
I can ping outside sites from the Ubuntu machine.
```

By name ie
ping [www.bbc.co.uk](www.bbc.co.uk)
does this work?

Many people are experiencing a slow connection with firefox, have you tried disabling ipv6 within firefox?

---

### Post by steviemc on 2007-10-19
Hi,
I had exactly the same problem...I found this in the Help...

3.2.7.&#8195;IPv6 Not Supported

   1. IPv6 is supported by default in Ubuntu and can sometimes cause problems.
   2. To disable it, open a Terminal (Applications &#9656; Accessories &#9656; Terminal) and type the command: gksudo gedit /etc/modprobe.d/aliases.
   3. Find the line alias net-pf-10 ipv6 and change it to read alias net-pf-10 off.
   4. Reboot Ubuntu.

This solved my problems.

Cheers

---

### Post by Em-Buntu on 2007-10-19
I had the same problem.
Upgrading to Firefox 3.0 seems to have fixed it.
I upgraded using The Synaptic Package Manager

---

