---
title: "Ubuntu 10.10 VirtualBox Client OS problems"
date: 2010-09-27
forum: Installation &amp; Upgrades
---

### Post by quutar on 2010-09-27
One of my computers is running VirtualBox and I use that to play around with build envs

I am able to install Ubuntu 10.04.1 with VirtualBox and then install the GuestOS extension, and everything works fine. I can re size the screen all I want, the clipboard sharing works... basically as a GuestOS 10.04.1 works great and the drivers work with it.

If i try to upgrade my GuestOS 10.04.1 installation to 10.10 beta, or if I install from the maveric ISO file... It works, sort of... The OS is able to run in the VirtualBox... but none of the GuestOS additions work. The screen is limited to 800x600 and the clipboard is no longer shared.

Even if i start from a working 10.04.1 with the GuestOS drivers loaded, upgrading to 10.10 kills it

Is there a new set of GuestOS drivers for Ubuntu 10.10 or is there a reason the 10.04.1 drivers are not working?

---

### Post by gordintoronto on 2010-09-27
Ubuntu 10.10 is beta (testing) software, you should expect it to break or be incomplete -- and to change every day or so.

---

### Post by lcn on 2010-10-11
Now that 10.10 0has been released, the above mentioned issue seems to still be there.
A solution is very much needed ....

---

### Post by josmith42 on 2010-10-13
VirtualBox 3.2.10 has just been released.  You might try downloading the new version to see if it fixes the problems you're experiencing.

---

