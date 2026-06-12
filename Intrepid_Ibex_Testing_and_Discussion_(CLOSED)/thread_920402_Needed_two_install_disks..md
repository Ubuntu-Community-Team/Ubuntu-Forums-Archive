---
title: "Needed two install disks."
date: 2008-09-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by dawynn on 2008-09-15
I don't plan to open a bug on this, simply because I don't plan to keep reinstalling Intrepid to check if future releases fixed the issue.  But, thought I should at least pass this on for those that are wondering about the state of II.

I tried burning the II disk in K3B (Hardy).  It built it, but failed on the verification.  I then went to Windows and reburned in Nero.

I rebooted my system with one of the CD's in my boot drive.  I tried to verify the CD.  It could not -- because it could not figure out how to mount the CD that it was currently using!

I decided to go ahead with the install anyway.  Again, it got to a point of needing to mount the CD that it was using to install the system, and couldn't figure out how to do that!  But since I had a second copy of the disk, I stuck it in my other CD drive.  Voila!  I was able to complete the install with only one other issue (complained of not being able to write a Grub menu.lst after it had already written a Grub menu.lst).  The computer went ahead and booted anyway.  

(The computer had used the first disk when it needed to run part of its installation process, but had used the second disk when retrieving packages.)

So, someone should look into the installer and find out why it can't recognize a disk that it already has mounted and in use.  Unless we're expecting Shipit to send two copies along with each request, and hope that every computer has two CD drives...

---

