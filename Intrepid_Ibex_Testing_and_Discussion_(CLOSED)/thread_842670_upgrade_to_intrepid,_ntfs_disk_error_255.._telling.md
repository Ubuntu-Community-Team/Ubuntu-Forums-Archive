---
title: "upgrade to intrepid, ntfs disk error 255.. telling me to run chkdsk -f ??"
date: 2008-06-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by puccaso on 2008-06-27
ok so i am upgrading my system to intrepid... cos im using the hpmini note and its the new kernel supposedly supports the wifi card.. 

but now im getting an error telling me its due to inconsistancy on the ntfs drive.. and i should run chkdsk -r... 

ive done that
i still get the error.. 

what do i do?:guitar:

ok, so an edit to the first post

the actuall error message reads


could not mount the partition d/ev/disk/by-uuid/xxx this could also happen if the file system is not clean because of an operating sytem cash, an interrupted boot process, an imporer shutdown, or unplugging of a removable device without first unmounting or ejecting it. to fix this simply reboot into windows, let itt fully start, lgo in, run chkdsk /r, then gravefully shutdown and reboot bck into windows. 
after this you should be able to reboot again and resume the installation...

then it goes into initramfs.

the problem seems to accure with the 2.6.26-2-generic kernel, however i do not get this error with the previous hardy kernel.

---

### Post by ago on 2008-06-30
Did you upgrade from wubi 7.04? That is not supported. You will have to do a fresh installation of 8.04[.1]

---

### Post by puccaso on 2008-06-30
i had installed 8.04
i then upgraded that to 8.10 alpha 1.. 
that is when i get the ntfs 255 error..
but i only get that error with the new 2.6.26 kernel release, if i use the hardy kernel, i get no errors

what could this be?

---

### Post by ago on 2008-06-30
sorry misread, alpha 1 is still in early stages to be supported I am afraid, it would be good though if you could find out more and post relevant bugs in launchpad :)

---

### Post by puccaso on 2008-06-30
ok sounds like a plan

does the hardy kernel and the intrepid kernel have METHODS OF accessing hardware? like a newer hal that makes a big difference etc..?

cos as stated, intrepid works fine if booted with the HARDY kernel, 
but the harddrive is not able to located using the intrepid kernel.. 
the harddrives/partitions are all in UUID in fstab and both are identicle for hardy and intrepid kernels.. 


how do i go about documenting bugs to post to launchpad?

---

### Post by ago on 2008-06-30
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

