---
title: "X misconfigured after upgrade to 10,04"
date: 2010-07-01
forum: Installation &amp; Upgrades
---

### Post by Farhad_Gulemov on 2010-07-01
Hi,

My problem is with a Dell Inspiron 8200 with a GeForce4 440Go card.

I have recently gone through all the steps to upgrade from 8.04LTS to 10.04LTS (upgrading each intermedia stage from 8.04->8.10->9.04->9.10->10.04) with no problems until 10.04.  When at the end of the upgrade I rebooted, my graphics card and monitor were not recognized and all X could do was  1024x768 with ugly (blurred looking) fonts. 

The weird thing is that when I used a Xubuntu 10.04 live-CD I would get a very nice looking 1400x1050 resolution :confused:

In such cases what I usually do is mount the / partition and copy the xorg.conf file from /etc/X11 to /media/rootdisk/etc/X11 and reboot.  Except, this time, there was no xorg.conf.

I tried to create one by doing "sudo Xorg -configure :1" [no my idea, a suggestion from the Ubuntu IRC] and this did create /root/xorg.conf.new which I promptly copied to /media/rootdisk/etc/X11 and renamed xorg.conf.  Alas, on reboot, I got a message telling me that Ubuntu was using a low-res mode and then I was right back to my ugly 1024x768.:confused:

When I tried to change the resolution from my HD install of Ubuntu 10.04 I was offered the option to use the Nvidia driver.  I was told to run sudo nvidia-config and reboot, but that only got me a black screen with no working X.  The amazing thing is that the live-CD of Xubuntu 10.04 give me the very nice 1400x1050 resolution *without* using the Nvidia diver :confused:

To the best of my ability to guess what is going on I would say that Ubuntu 10.04 re-configures X on each bootup and it gets it wrong, whereas for some weird reason the Xubuntu live-CD gets it right.

So what do I do now?  Should I simply install Xubuntu 10.04 over my / partition?  I would loose lots of configurations and apps and what guarantees me that for some weird reason Xubuntu would not start doing the same crap as Ubuntu does?

Can I create a valid xorg.conf file in Xubuntu, copy it to /etc/X11 and somehow FORCE Ubuntu read it (and not bypass it) on bootup?

Can I manually edit whatever file 10.04 uses instead of xorg.conf?

I am rather clueless and I would very much appreciate any help.

Thanks!!

FG

---

