---
title: "Installation hangs while &quot;Starting Hotplug Subsystem&quot;"
date: 2006-03-29
forum: Installation &amp; Upgrades
---

### Post by Cacique on 2006-03-29
While trying to load Ubuntu and then Fedora Core 3 onto a desktop
computer previously running XP, the installation of FC3 hangs while
displaying the following text:

"USB Universal Host Controller Interface Driver v. 2.2"

With Ubuntu, it hangs while displaying, "Starting Hotplug Subsystem".
Just hangs there indefinitely, as does the Ubuntu Live CD.

The box is made by AOne and its got 6 USB ports on the back and two at
the front.

No PCI USB cards that I see.

What's the best way to get a successful Linux installation onto this
box?  I'd rather not disable the USB ports.

Cheers.

---

### Post by meborc on 2006-03-29
i have heard that there are problems with installing linux on machines with multiple USB ports and multi-card readers...

the common way to do it is to disable the device... install linux... and plug it in again :D ... to *fool* the system...

you might try it, but if you prefer to not to mess with your hardware, i guess you just have to try a different distro...

if you really want to live on the edge (meaning a re-install of your box is not a prob) then i suggest you give Dapper a try... ;)

---

### Post by Cacique on 2006-03-29
I have disabled the USB controller in the BIOS but the installation still hangs at the "starting hotplug subsystem" stage.

---

### Post by mauvegrail on 2006-04-01
I have just installed breezy badger on my machine. Iam able to send this mail because i also have XP on the machine.

This mail will not help you, but it it might help others to help, because i need help too. My machine also locks up at "starting hotplug subsys". I tried the system in the recover mode, and got the following:


[4294689.192000] <0> Kernel panic - not syncing: FATAL EXCEPTION IN INTERRUPT.

There was an approximately 6 line dump before this. If I could have copied the dump, I would have posted that too.

help!

---

### Post by Cacique on 2006-04-16
I downloaded Breezy Badger (5.10) and got the same result -  system hangs while "starting hotplug subsystem".  I hunted around the forums a while and noticed that several people who had this problem were using Nvidia video cards.  I am using an Nvida FX 5200 myself, and decided to switch over to the system's onboard video.  The installation went smoothly!  No hang up at the "starting hotplug subsystem" stage and i'm now running Breezy on that system.  

To the other people having this problem - are you using Nvidia cards?

---

### Post by todoporron on 2006-04-16
Well, I have EXACTLY the same problem as Cacique, I also have an Nvidia fx5200 but when I enable it, the system hangs on Starting Hotplug subsystem line... it boots ok when using the onboard graphics. Any suggenstions? Thanks a lot.

---

### Post by todoporron on 2006-04-19
HOLLY COW !!!!! IT WORKS !!! I think I discovered the answer:

I had this issue with my Nvidia card. I just added the following to the etc/hotplug/blacklist:

intel_agp

Now it boots Ok and works with my NVidia. =D>

---

### Post by ajb on 2006-04-30
todoporron:

Will you please please clarify what you did?  I have the same problem as you but I've never used linux before.  How did you add a line to a linux file when linux wasn't working?  Did you go through windows?

Will you post a step by step guide on how to do this?  I would be eternally greatful!

Thanks!

---

### Post by ajb on 2006-04-30
Well not exactly the same.  but somewhat similar.

---

### Post by westvleteren on 2006-05-02
I do not have an Nvidia card in my laptop, but I have this problem as well, with the freeze at Hotplug Subsystem on startup.
 Although I was able to boot up. You can boot up if you hit "Ctrl C" fast enough before the Hotplug Subsystem process starts. I can log into Ubuntu fine after that, but cant connect to the internet. I was hoping that I could do some updates to fix this problem, but since I cant connect to the internet I cant do anything.
 I tried to Edit the /etc/hotplug/blacklist.d/alsa-base file but was unable to, since the setup never issued me a root user and password like other distros do. 
 I have Ubuntu running on My Toshiba laptop fine but can not get it to run properly on my Asus Laptop.
This hotplug subsystem problem is a pain in the arse!

---

