---
title: "Feisty on HP dv2310us Laptop Troubles"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by hipnerd on 2007-04-25
So after getting Ubuntu going fantastically on my desktop, I thouht I'd try for Feisty on my new laptop -- and that hasn't gone as smoothly.

[LIST=1]
[*]I cannot get the wireless drivers to work. I've uninstalled and reinstalled ndiswrapper a dozen times. I've followed four or five guides. No dice. Right now, it's worse off then when I started, as it can't even see the wireless adapter anymore.
[*]I don't have any sound.
[*]If I turn on desktop effects, the menu bars disappear on all the windows.
[/LIST]

I was a little disappointed, actually. Ubuntu had worked so well at hardware detection on my desktop. It isn't doing so well on the laptop. The lack of wireless connectivity especially is a dealbreaker. I suspect I could fix the other problems, but Ive just spent five hours not getting the wireless network to function, and I'm a little fried.

Any help would be appreciated.

---

### Post by 0MG on 2007-04-30
Just picked up the same laptop. I'm also having problems with the sound and the wireless. The Desktop effects work great for me though - maybe you need to install the restricted nvidia driver?

Wireless is a bit of a pain so far - I can get it to connect to the access point (at least that's what iwconfig says) but I can't get it to pass traffic. Can't pull DHCP, and can't ping the access point when I manually set an IP. I'll keep messing with it and reply to this thread when I get it working.

I haven't started with the sound yet.

---

### Post by hipnerd on 2007-04-30
After doing all sorts of unholy things to the laptop, I got wireless to work...sometimes, and sometimes the PC refuses to boot.

I'm going to reformat and start over.

---

### Post by 0MG on 2007-04-30
Reinstalled Feisty. Sound works out of the box. Got wireless working with the following help: (quick n dirty howto)

Remove current ndiswrapper
Install newest ndiswrapper from [here]("http://sourceforge.net/project/showfiles.php?group_id=93482")
Download windows driver from [here]("ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe")
Install a package called cabextract and use it to extract the files from the above download
blacklist bcm43xx in /etc/modprobe.d/blacklist
good idea to reboot here
ndiswrapper -i bcmwl5.inf;
ndiswrapper -l;
depmod -a;
modprobe ndiswrapper;

You should now be in business.

---

