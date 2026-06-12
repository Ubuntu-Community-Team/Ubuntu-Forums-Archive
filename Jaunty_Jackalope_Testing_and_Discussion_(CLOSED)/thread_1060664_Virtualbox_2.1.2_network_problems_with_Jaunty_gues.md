---
title: "Virtualbox 2.1.2 network problems with Jaunty guest?"
date: 2009-02-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jblackhall on 2009-02-05
Hi, I've tried installing Jaunty (32-bit) in the latest VirtualBox (2.1.2) Intrepid Host.  I'm getting nowhere, and I'm not sure what the problem is.  Normally networking is just "automatic".  I've even tried deleting the entire VM and hard disk and starting over, but it's no use.  I also tried changing the adapter type in VirtualBox as well, and even re-installing Virtualbox.

Any suggestions or is anyone else having this problem?

---

### Post by novafluxx on 2009-02-05
I can't offer anything besides the usual "its an alpha" so maybe wait for the next official alpha release, maybe even today

---

### Post by prshah on 2009-02-05
> **jblackhall said:**
> Normally networking is just "automatic".

With Windows clients, I find that I'm not able to use networking (among other things) until I have installed the specific "Guest OS extensions". However, this does not exist for some platforms. Maybe Jaunty's extensions are not yet created?

---

### Post by jmmL on 2009-02-05
It worked fine for me from the first time I tried it - alpha 1.
I've just checked, and I am running 2.1.2. Networking is working fine, I've just pulled the latest updates from the jaunty repos.

Sorry I can't be of any more help!

EDIT: Oh, and I didn't need to install any extensions or anything like that.
EDIT2: To clarify: I'm running jaunty as the guest, intrepid as the host.

---

### Post by linux6994 on 2009-02-05
I am running Jaunty fully updated as of this morning along with Virtualbox 2.1.2 and all is well. 

From Alpha1 to Alpha3 there was a kernel change and sometimes you need to have it recomplied to have the drivers run right.

Go to [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) and reinstall.I always do this after a kernel change. Its pretty quick and will save you headaches like this.

Good Luck!

---

### Post by prshah on 2009-02-05
> **linux6994 said:**
> I am running Jaunty fully updated as of this morning along with Virtualbox 2.1.2 and all is well. 


He wants to run Jaunty as a "guest" OS, not as the host (as in your screenshot, which shows an Ubuntu host and a XP guest).

---

### Post by linux6994 on 2009-02-05
OOPs not enough coffee yet.

---

### Post by jblackhall on 2009-02-05
Hi guys.  Thanks for the input.  To be clear, I have no problem with networking on a VM of Crunchbang Linux or Window 7.  Only Jaunty.  I'd chalk it up to it being an alpha, but I seem to recall installing alpha3 when it first came out and I had no problem with networking.  But now, even after re-installing alpha3 and creating a new VM, I can't get networking to work from the get-go.  This makes me think it has something to do with updating VirtualBox from 2.1.0 to 2.1.2, but I can't figure out what it would be or how to fix it.

Anyway, I guess I'll try out the newly released alpha4 and see if that makes any difference.  

Please let me know if you have any other suggestions!

---

### Post by jblackhall on 2009-02-05
Darn, same situation on alpha 4 :-/

---

### Post by jblackhall on 2009-02-05
So this is weird.  In the Jaunty guest, I can PING google.com and traceroute google.com (from inside Network Tools) but I can't connect to it via Firefox.  I also can't connect to the update servers to download any updates.

Going to try installing an Intrepid guest in a moment to see what that looks like.

---

### Post by prshah on 2009-02-05
> **jblackhall said:**
> This makes me think it has something to do with updating VirtualBox from 2.1.0 to 2.1.2, but I can't figure out what it would be or how to fix it.

Make sure you have the dkms (Dynamic Kernel Management System) package (a Dell contribition?) installed in the Jaunty guest.

This will automatically rebuild the vboxdrv kernel module when the kernel changes.

---

### Post by caspar_wrede on 2009-02-09
Same problem here. 

DNS resolution works, but no ping packets get through. What's going on

---

