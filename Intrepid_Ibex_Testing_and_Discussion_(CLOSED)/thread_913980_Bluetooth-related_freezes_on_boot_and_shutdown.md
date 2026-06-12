---
title: "Bluetooth-related freezes on boot and shutdown"
date: 2008-09-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Game_boy on 2008-09-08
On my computer, both booting and shutting down with the liveCD freeze on "Starting/Stopping Bluetooth" (nothing displayed where [OK] should be on the console). I have no Bluetooth-related devices or chipsets on the computer.

This is Intrepid Alpha 5, but I haven't tried previous alphas to see if the new kernel is at fault.

How can I fix it and/or circumvent it to load a desktop?

---

### Post by beartard on 2008-09-08
Out of curiosity, do you have any tv devices?

---

### Post by Gina on 2008-09-08
I had that with kernel 27-1 but 27-2 fixed it - I do have Bluetooth.

---

### Post by kol on 2008-09-08
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by BanjoBoy on 2008-09-23
> **beartard said:**
> Out of curiosity, do you have any tv devices?

I also have this problem with Intrepid Ibex linux-2.6.27-4-generic (and previous 2.6.27 kernels, 2.6.26 where working and still is if I boot this kernel) and but only when I have my Hauppauge WinTV USB2 device attached (which are using v4l and pvrusb2 kernel modules), then the boot hang at "Starting bluetooth".

And also, the TV device does not work if I attach it after the boot has finished!.

---

### Post by Nullack on 2008-09-23
Please consider helping make Intrepid better by contributing the bug process as explained in the contributing link in my sig.

---

### Post by BanjoBoy on 2008-09-24
> **Nullack said:**
> Please consider helping make Intrepid better by contributing the bug process as explained in the contributing link in my sig.

I have already created a bug report, but no ones take notice despite one more report the same problem to my bug report. So no help here and I hope to have better luck at this forum!

---

### Post by Nullack on 2008-09-24
Then please put a link to the bug number in your posts here. If you give the number Ill look at it.

Also there was a recent change to revert some kernel bluetooth functionality so can you synch to the repos and retest please.

---

### Post by BanjoBoy on 2008-09-24
> **Nullack said:**
> Then please put a link to the bug number in your posts here. If you give the number Ill look at it.

Also there was a recent change to revert some kernel bluetooth functionality so can you synch to the repos and retest please.

This link is: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/262927]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/262927"), just added little more after testing.

---

### Post by Nullack on 2008-09-25
Just to confirm, do you get this when you try:

nullack@PPP:~$ sudo apt-cache policy linux-image-2.6.27-4-generic
linux-image-2.6.27-4-generic:
  Installed: 2.6.27-4.6
  Candidate: 2.6.27-4.6
  Version table:
 *** 2.6.27-4.6 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages
        100 /var/lib/dpkg/status


So here when you can see that bluetooth was tried to be fixed:

[http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-intrepid.git;a=summary](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-intrepid.git;a=summary)

---

### Post by BanjoBoy on 2008-09-27
> **Nullack said:**
> Just to confirm, do you get this when you try:

nullack@PPP:~$ sudo apt-cache policy linux-image-2.6.27-4-generic
linux-image-2.6.27-4-generic:
  Installed: 2.6.27-4.6
  Candidate: 2.6.27-4.6
  Version table:
 *** 2.6.27-4.6 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages
        100 /var/lib/dpkg/status


So here when you can see that bluetooth was tried to be fixed:

[http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-intrepid.git;a=summary](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-intrepid.git;a=summary)

After I have done more testing, I don't think it's a bug relates to bluetooth, but may be a usbcore problem. If I boot without the WinTV USB2 device, then connect it, it then loads firmware to the device through usb and it automaticaly disconnect from the usb and then should re-connect again, but the usb are "dead". I cannot connect or disconnect any usb devices (usb-stick, usb HDD, usb dvd-rw or usb keyboard/mouse). Connected devices still works (like my usb keyboard/mouse).

---

