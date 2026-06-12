---
title: "Installation Trouble...."
date: 2006-12-26
forum: Installation &amp; Upgrades
---

### Post by nu2lin on 2006-12-26
Hi everyone,  I am new to Linux and Ubuntu, I've used the LiveCD without any problems but when I tried to do a dual-boot (xp/ubuntu) I get an error message and now I cannot load Ubuntu or WIN??

My current config Intel 3.4Ghz, 2 74gig (raid0), and back up 250gig.

When I installed Ubuntu I loaded on the 250 drive, I thought it would be safer because it has more room and wouldn't have to worry about the raided drives.

But when I reboot it shows that it tries to load the Grub, but then I get an "Error 21"

I am still able to use the LiveCD. Now I am lost. Any help is appreciated..

---

### Post by foolsh on 2006-12-26
thats a tough one

it sounds like grub was installed on the boot partition of the raid array and cant find /boot
you could change the boot priority to the 250gb drive and reinstall ubuntu over itself this may fix the issue with both win and ubuntu im not sure

---

### Post by nu2lin on 2006-12-26
Thanks, I'll give that a try.

BTW I went into the BIOS and tried to change the boot priority to the 250gig but still no luck. Still comes up with the same error code. I even made other attempts to isolate the drives by disable in BIOS. No Luck.

---

