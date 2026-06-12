---
title: "help with ubuntu-6.06.1-server-i386.iso"
date: 2006-11-12
forum: Installation &amp; Upgrades
---

### Post by Cotsuma on 2006-11-12
I don't know if this would qualify to fit in here but i need some help with ubuntu-6.06.1-server-i386.iso I am wanting to turn my other computer which is Ubuntu 5.04 and i am wanting to turn it into a server - not a real big and fancy one and i wanted to use ubuntu-6.06.1-server-i386.iso but i am having a little of a hard time. I do the smart install and it works well untill it gets to this: 

> You are running a kernel(version 2.6.10-5-386) and attemping to remove the same version. This is a potentialy desatrous action. ... Remove the running kernel image (not recomended) [No]? 

I then answer no and it gives me this pop-up:

> Error:
The following problems were found on your system:
E:linux-image-2.6.10-5-386: subprocess pre-removal script returned error exit satus 1

Then i have to click ok and it exits me out of the install and says:

> Failed to apply all changes! Scroll in the terminal buffer to see what went wrong.

My intention is to turn it into a small server and be able to host and IRCd and maybe my own forums.
Is there any way i can do this or is it best for me just to use ubuntu desktop 6.06?

---

### Post by dcstar on 2006-11-14
> **Cotsuma said:**
> I don't know if this would qualify to fit in here but i need some help with ubuntu-6.06.1-server-i386.iso I am wanting to turn my other computer which is Ubuntu 5.04 and i am wanting to turn it into a server - not a real big and fancy one and i wanted to use ubuntu-6.06.1-server-i386.iso but i am having a little of a hard time. I do the smart install and it works well untill it gets to this: 



I then answer no and it gives me this pop-up:



Then i have to click ok and it exits me out of the install and says:



My intention is to turn it into a small server and be able to host and IRCd and maybe my own forums.
Is there any way i can do this or is it best for me just to use ubuntu desktop 6.06?

Quite possibly it just thinks that the current kernel is being replaced with the same, and it is just confused.

The easiest thing to do may be to install a 686 kernel on the current system, then reboot and remove the 386 kernel that the install is complaining about.

The install should install a 386 kernel by default, so it may not make any difference in the end if you remove it.

---

