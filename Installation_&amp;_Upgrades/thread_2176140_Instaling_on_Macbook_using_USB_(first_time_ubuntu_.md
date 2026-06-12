---
title: "Instaling on Macbook using USB (first time ubuntu user)"
date: 2013-09-23
forum: Installation &amp; Upgrades
---

### Post by thomas12 on 2013-09-23
Hi all.
I have an old Macbook (around 2005-2006) that i would like installing ubuntu on. Have a friend that's using [http://www.lubuntu.net/](http://www.lubuntu.net/) so i though I'd use that (but I'm up for suggestion).

My problem now is:
I'm following the instruction on how to create a bootable USB from here [https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick](https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick) all works fine untill i reboot and hold down Alt to boot from the USB. It isn't there on the list and when i restart in OSX it say that "The disk you inserted was not readable by this computer".

What could i have done wrong?
Can it be the iso (that was converted to img) that i got from lubuntu (lubuntu-13.04-desktop-i386.iso) that isn't compatible somehow?

Remember, I'm a total newb when it comes to this.

cheers,
Thomas

---

### Post by mörgæs on 2013-09-23
Hi, welcome to the fora.

Have you tried the USB stick in another computer?

---

### Post by MrXindeed on 2013-09-23
Make sure your USB disk is formatted as Mac OS Extended (Journaled) otherwise your Mac wont even look at it for booting.

---

### Post by Quackers on 2013-09-23
It's a bit more involved than usual but have a read here
[http://ubuntuforums.org/showthread.php?t=2174630]("http://ubuntuforums.org/showthread.php?t=2174630")

Also you should first check that your Mac can even boot from a USB device - some can't.

---

