---
title: "Annoyed again, naturally."
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by Bob63 on 2010-04-30
So, my experience with the upgrade...

Going from 9.10 64-bit to 10.4 64-bit.

Tried to be a decent, sharing sort and downloaded the LiveCD for 64-bit from torrent. No problem.

Didn´t have any blank CDs handy, but I had a 1GB USB thumb drive that I have used to install other distros that I wanted to test, so used unetbootin to make my installation on. No problem.

LiveCD tried to run, but hung with a black screen; no blinking cursor, nothing. Problem.

Restart, go back to my functioning system, and re-create the LiveCD on the thumb drive using USB Startup Disc Creator. No problem.

Reboot. Monitor went into standby and never came out. Problem.

Decided to give up on the LiveCD. Downloaded the alternate-install CD for 64-bit and put it on the thumb drive. No problem.

Installation went fine. No major hang-ups at this point. Had the grub_puts problem, even though I specified the correct place, and so had to reinstall grub, which fixed that.

Although it is still early in the process for me, my main (relatively minor) gripe is the same one I always have: Although Linux seems to be able to tell a lot about the hardware (through what I assume is either ¨asking¨ the hardware about it capabilities or getting info from the BIOS, perhaps), why can it not tell that ***my*** keyboard numlock key is ***supposed*** to be ON? My BIOS is set to turn it on at boot. My username and password both have numbers in them, and it is convenient for me to have the numlock on at boot and remain on.

I fully realize that there are many users of notebooks/netbooks that having this setting ON for default is a problem. I don´t want it ON as default. I want a simple way to change the setting. I´ve seen complaints and questions about this since at least Edgy (there may be older postings, but I haven´t needed to research back). System>Preferences>Keyboard can let me do so many things with my keyboard - except this, apparently.

Maybe it is just me, but it doesn´t seem right that one of the first things I have to do after installation is modify a configuration file...

---

### Post by eltonw on 2010-04-30
Just a "heads up" did you verify the MD5SUMS before burning the downloaded ISO?

---

### Post by Slim Odds on 2010-04-30
Just another "heads up", you don't upgrade with a LiveCD. It's does not have upgrade capability. So it's best to understand what you're doing to save yourself some trouble. Upgrades are either over the net or using the alternate install CD.

---

### Post by Bob63 on 2010-04-30
> **eltonw said:**
> Just a "heads up" did you verify the MD5SUMS before burning the downloaded ISO?

Yeah, did that and thanks. Unfortunately, even though the md5sums checked, it just wouldn't run. I wasn't shocked by that, I've had that issue before. 

> **Slim Odds said:**
> Just another "heads up", you don't upgrade with a LiveCD. It's does not  have upgrade capability. So it's best to understand what you're doing to  save yourself some trouble. Upgrades are either over the net or using  the alternate install CD.     You are correct. I misspoke. When I said "upgrade" I meant moving from 9.10 -> 10.4. I'm not sure what the "official" term is when the distro moves to the next release. I had hoped to do a fresh install over the 9.10 since I finally got smart enough to move my /home directory to a separate partition, which allows me to mangle the /root one to my hearts content.:)

---

### Post by Slim Odds on 2010-05-01
> **Bob63 said:**
> ...
You are correct. I misspoke. When I said "upgrade" I meant moving from 9.10 -> 10.4. I'm not sure what the "official" term is when the distro moves to the next release. I had hoped to do a fresh install over the 9.10 since I finally got smart enough to move my /home directory to a separate partition, which allows me to mangle the /root one to my hearts content.:)

The "official" term for upgrading from one release to the next is "upgrade".
The "official" term for installing a fresh release where you don't care what was on the machine is "install".

Not really "official", just common sense I think.

Having /home on a separate partition is definitely a good move.

---

