---
title: "Help making an USB &quot;live disk&quot; to upgrade"
date: 2011-11-22
forum: Installation &amp; Upgrades
---

### Post by jlh68 on 2011-11-22
I made a USB flash drive using the "Startup Disk Creator" and I have tried six time to install Ubuntu 11.10 on my netbook.  All tries were unsuccessful.  At first I was getting a message about grub_xputs not found, then I repartitioned my hard drive and tried to a clean install, still no go.

It is frustrating that I had a perfectly good OS (Ubuntu 10.04LTS) on my notebook.  I had not tried to install Unity on it because when I used the live 11.04 and 11.10B it crashed a lot, so I did not want to go with it yet.

Would one of you Linux Guru's provide me with some instructions on this.  It is not like I haven't upgraded before as I started with 6.06 and have upgraded several computers, it is that this  time nothing works in upgrading.

---

### Post by darkod on 2011-11-22
If the live mode was not loading you can expect problems after upgrading/installing too. That's why it's better not to upgrade/install until you find what the issue is and the solution.

You seem to have nvidia card, usually the problem with them is they require the nomodeset parameter.

Since your system is already upgraded, boot it but in the grub menu press 'e' to edit the boot commands (not Enter to select it and boot it).

In the line starting with linux, add nomodeset in front of quiet splash. Press Ctrl + B to boot.

If that worked, I'm not sure if only installing a driver will help, or you need to make the nomodeset permanent.
First see if it worked.

---

### Post by jlh68 on 2011-11-24
I formatted my USB flash drive and used "Startup Disk Creator" again just to make sure I had a good USB boot stick.  I also formatted my partitions so they would be "clean" also.

I was able to install 11.10 and I got it to work.  

Still not sure about Unity.  AI added Cairo-dock which gives me a more traditional desktop operation.

---

