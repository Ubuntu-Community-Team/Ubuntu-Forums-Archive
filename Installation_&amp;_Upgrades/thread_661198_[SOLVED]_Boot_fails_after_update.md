---
title: "[SOLVED] Boot fails after update"
date: 2008-01-07
forum: Installation &amp; Upgrades
---

### Post by OpenSourceFuture on 2008-01-07
A power outage during an update occured.
Boot up now fails at start up, I tried reinstalling graphical interfaces in recovery mode, now i get up to a X.org error, it says it has to be manually configured and returns me to command prompt login, which also fails.

More details can be provided upon request, sometime during the boot I get two red [Failed] in the status box in the list of processes starting.

Any help would be greatly appreciated, thank you.

---

### Post by Pumalite on 2008-01-07
'returns me to command prompt login, which also fails.'

Give more details and exact errors.

---

### Post by OpenSourceFuture on 2008-01-07
The actual [failed] components happen too fast for me to see them, is there a way to scroll?
The X.org error I will be able to get as soon as a reboot...

---

### Post by OpenSourceFuture on 2008-01-07
heres what I get:
> displayconfig.gtk is not installed.
Without that tool you must manually configure x.org

---

### Post by OpenSourceFuture on 2008-01-07
bump

---

### Post by Pumalite on 2008-01-07
Try:

sudo dpkg-reconfigure xserver-xorg

Use vesa as the driver.
If that doesn't work, edit your xorg.conf file

---

### Post by Avendoor on 2008-01-07
i am having trouble installing ubuntu (latest version and would be grateful if someone could help, i have the following;

7800GS SLI
2x 80 GB HDD
1x 200GB HDD
KN8 SLI deluxe MB
3500 AMD 64 CPU
1250 PSU
4GB dual RAM running 128 - bit

i get a blank screen after the splash screen. I am a windoze user and looking to convert.

Please assist. 

I have tried;

deleting the two //'s that are present at the normal advanced options path and uninstalling the SLI AND trying all the above with SAFE graphics installed. i am no noob user i am a total noob user of Ubuntu. I see this as the OS that i would like to operate but am not happy that it doesnt work on my hardware. Can someone please help in any way?

Many thanks in advance.

---

### Post by OpenSourceFuture on 2008-01-07
> **Pumalite said:**
> Try:

sudo dpkg-reconfigure xserver-xorg

Use vesa as the driver.
If that doesn't work, edit your xorg.conf file

Pumalite, thanks alot, I'll let you know if it works.

---

### Post by OpenSourceFuture on 2008-01-07
Nope, i get the same message, only now I cannot access my keyboard or mouse once x.org starts.

One of the [Failed] messages I did manage to get though:

/etc/rcS.d/S85/urandom: 63: cannot create /proc/sys/kernel/random/poolsize: permission denied.

:( I'd just reinstall it but I have 3 OSes and 10 partitions on this computer, maybe I could resize the ubuntu filesystem, double check to make sure its the right partition, then drop hardy heron on the resized partition, otherwise I don't know any 100% safe way to do this without accidentally taking out a home partition or something.

Any help/suggestions are appreciated.

---

### Post by OpenSourceFuture on 2008-01-07
bump

---

### Post by OpenSourceFuture on 2008-01-07
*Rebumps in a final attempt to obtain help*

---

### Post by Pumalite on 2008-01-08
It looks to me like a reinstall, unless someone comes up with a better idea.

---

### Post by OpenSourceFuture on 2008-01-08
It was suggested that I try fsck from a live cd. Trying that now...

---

### Post by OpenSourceFuture on 2008-01-08
> **OpenSourceFuture said:**
> It was suggested that I try fsck from a live cd. Trying that now...

No luck, partition is clean.

---

### Post by OpenSourceFuture on 2008-01-08
> **Pumalite said:**
> It looks to me like a reinstall, unless someone comes up with a better idea.

Is there a way to recover my Firefox bookmarks and plug ins from a live boot environment?

---

### Post by Pumalite on 2008-01-08
I don't remember if the Live CD comes with a burner, but LinuxMint 4.0 Live CD comes with k3b

---

### Post by OpenSourceFuture on 2008-01-08
I don't need a burner, I'm on a live USB (Back Track Linux 2) and am backing up to an external HD. 

I was just curious to know where Firefox in Ubuntu stores it's bookmarks file.
I'd like to back it up.

---

### Post by Pumalite on 2008-01-08
I always keep my bookmarks in my /home, but you might want to look in Places<Home/username>Check 'Hidden Files'>./firefox

---

### Post by OpenSourceFuture on 2008-01-08
> **Pumalite said:**
> I always keep my bookmarks in my /home, but you might want to look in Places<Home/username>Check 'Hidden Files'>./firefox

Thank you very much, thats all I needed to know. My home is a seperate partition, and I'm backing it up just in case something goes wrong. Thanks alot, I should be fine from this point.

---

### Post by Pumalite on 2008-01-08
You are welcome. Good luck.

---

### Post by OpenSourceFuture on 2008-01-08
I'm going to mark it as solved as soon as I find it in my backup of my /home.

Thanks again.

---

### Post by OpenSourceFuture on 2008-01-08
Its actually located in ./mozilla/firefox/ and is successfully backed up.

---

