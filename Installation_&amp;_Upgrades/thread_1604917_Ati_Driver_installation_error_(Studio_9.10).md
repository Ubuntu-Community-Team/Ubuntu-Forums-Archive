---
title: "Ati Driver installation error (Studio 9.10)"
date: 2010-10-24
forum: Installation &amp; Upgrades
---

### Post by crazyhorse54 on 2010-10-24
About 3 weeks ago the system did an update and I started having problems scrolling and moving windows, very jerky!  After looking around I came to the decision it was video driver related.  So after fighting with it for a couple of weeks I've finally gotten the basic ATI driver working and the problem is gone.  So I know it was associated with the driver.

At this point I've also tried installing ATI Crystal packages 10.6, 10.9, 10.9 hotfix and 10.10 several times.  I've been very careful to follow the instructions carefully but in every case I get:

Creating symlink /var/lib/dkms/fglrx/8.783/source ->
                 /usr/src/fglrx-8.783

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
cd /var/lib/dkms/fglrx/8.783/build; sh make.sh --nohints --uname_r=2.6.31-9-rt --norootcheck.....(bad exit status: 1)
0
0
[Error] Kernel Module : Failed to build fglrx-8.783 with DKMS
[Error] Kernel Module : Removing fglrx-8.783 from DKMS

------------------------------
Deleting module version: 8.783
completely from the DKMS tree.
------------------------------
Done.
[Message] Kernel Module : update initramfs not required

I've checked required packages back and forth but still the same.  I've found several solutions on the forum but none have helped so if someone out there has any ideas I'm open!

---

### Post by crazyhorse54 on 2010-10-24
About 3 weeks ago the system did an update and I started having problems scrolling and moving windows, very jerky!  After looking around I came to the decision it was video driver related.  So after fighting with it for a couple of weeks I've finally gotten the basic ATI driver working and the problem is gone.  So I know it was associated with the driver.

At this point I've also tried installing ATI Crystal packages 10.6, 10.9, 10.9 hotfix and 10.10 several times.  I've been very careful to follow the instructions carefully but in every case I get:

Creating symlink /var/lib/dkms/fglrx/8.783/source ->
                 /usr/src/fglrx-8.783

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
cd /var/lib/dkms/fglrx/8.783/build; sh make.sh --nohints --uname_r=2.6.31-9-rt --norootcheck.....(bad exit status: 1)
0
0
[Error] Kernel Module : Failed to build fglrx-8.783 with DKMS
[Error] Kernel Module : Removing fglrx-8.783 from DKMS

------------------------------
Deleting module version: 8.783
completely from the DKMS tree.
------------------------------
Done.
[Message] Kernel Module : update initramfs not required

I've checked required packages back and forth but still the same.  I've found several solutions on the forum but none have helped so if someone out there has any ideas I'm open!

---

### Post by howefield on 2010-10-24
Please only create one thread per issue.

Threads merged.

---

