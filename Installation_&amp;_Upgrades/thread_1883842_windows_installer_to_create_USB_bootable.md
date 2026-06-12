---
title: "windows installer to create USB bootable"
date: 2011-11-20
forum: Installation &amp; Upgrades
---

### Post by uhuru53 on 2011-11-20
Is it possible to create a bootable USB pen drive using windows installer wubi?
How ?
Thanks.

---

### Post by uhuru53 on 2011-11-20
error on permanent pen drive USB ubuntu 11.10
whenevere i reboot i get:

/init: line 7: can't open /dev/sr0: No medium found

and I have to format again the pendrive!!!

any solution?

thanks

---

### Post by oldfred on 2011-11-20
Threads merged.

Did you use the instructions on the Ubuntu site?

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

You should be able to use Windows or wubi to create a bootable USB flash drive. Some have had issues with certain brands of flash drives.

Others suggest using unetbootin:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by uhuru53 on 2011-11-20
> **oldfred said:**
> Threads merged.

Did you use the instructions on the Ubuntu site?

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

You should be able to use Windows or wubi to create a bootable USB flash drive. Some have had issues with certain brands of flash drives.

Others suggest using unetbootin:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Yes I did follow the instructions.
But error on permanent pen drive USB ubuntu 11.10
whenevere i reboot i get:

/init: line 7: can't open /dev/sr0: No medium found

Then?

---

### Post by oldfred on 2011-11-20
For what ever reason it is trying to load the cd sr0?

Have you tried any of the other ways to create the USB flash drive?

Do you have a foppy drive? And if not do you have one enabled in BIOS.

[https://bugs.launchpad.net/ubuntu/+bug/500822](https://bugs.launchpad.net/ubuntu/+bug/500822)

---

### Post by uhuru53 on 2011-11-20
For what ever reason it is trying to load the cd sr0?

I do not know.

Have you tried any of the other ways to create the USB flash drive?

Yes, I did, same error.

Do you have a foppy drive?

No.

 And if not do you have one enabled in BIOS.

No, I disabled in the BIOS.


I read all thread:
[https://bugs.launchpad.net/ubuntu/+bug/500822](https://bugs.launchpad.net/ubuntu/+bug/500822)

but it has no solution for this bug, yet.

---

