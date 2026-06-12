---
title: "eject button not working perperly"
date: 2009-07-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by terry_gardener on 2009-07-30
i seem to have problem with the eject button. 

i insert a disc and when finished press the eject button on the drive and nothing happens. so i goto computer and right the drive and select eject then get prompted for password and then it ejects. 

but when i close the drive and try to reopen it by pressing the eject button on the drive nothing happens and when i try to right click the drive and select eject get message unable to eject no media to eject, i have to logout and log back in to insert another disc. 

it works ok in jaunty.

any ideas to fix this fault. 


thanks

---

### Post by dlmarti on 2009-07-30
On some drives the disk won't eject if the drive is still mounted, unmount the drive.

This is not a fault, but a reasonable protection.

---

### Post by terry_gardener on 2009-08-02
thanks that seems to work much better

---

### Post by phenest on 2009-08-02
> **dlmarti said:**
> On some drives the disk won't eject if the drive is still mounted, unmount the drive.

This is not a fault, but a reasonable protection.

I seem to remember this behaviour for several Ubuntu releases now. I get the same when using Ubuntu in a virtual machine. If I eject the media from outside the VM, nothing happens. But I can unmount it from inside.

I agree, that this is intended behaviour.

As for not being able to open the drive when there's no media in it... file a bug?

---

