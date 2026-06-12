---
title: "Can i delete windows files after installing windows?"
date: 2012-05-25
forum: Installation &amp; Upgrades
---

### Post by gogobaba on 2012-05-25
Hello im currently installing ubuntu on my windows PC and i was wondering can i delete the windows files(folders)(windows,program files etc etc.) from my C drive.And if i do a clean install witn CD or USB flashdrive can i keep all the files from My D: pertiotion or i  havet to back them up on the internet?

---

### Post by roelforg on 2012-05-25
Yes, you could.
Just have the livecd overwrite the windows C: partition for the installation.
The D: will be untouched
Just make sure you pick the right one and you moved all stuff you want to keep to D:

---

### Post by gogobaba on 2012-05-25
So if i download the disc image and install ubuntu on the pc with the cd it will give me option to install it on my OLD C: pertiotion of windows and format only the C: ? 

I would love a fast reply  because i installed it  with the windows installer and its not that good and  i want to do a clean install with the cd 

Thank you

---

### Post by roelforg on 2012-05-25
Well, the <character>: naming is windows style.
Linux uses /dev/sd<character><number_representing_partition>.
But yes, if you find out which one of the partitions is C: (the installer has a good gui for this), you tell it to use the old C: and it'll wipe C and install ubuntu on it.

EDIT: I just noticed: 1000'th bean!

---

### Post by gogobaba on 2012-05-25
Well thank you for the fast reply again i downloaded and im buring the image right now.Hopefully everything will be fine :P

---

### Post by roelforg on 2012-05-25
> **gogobaba said:**
> Well thank you for the fast reply again i downloaded and im buring the image right now.Hopefully everything will be fine :P
Let us know if it worked or if you have any remaining questions.
Ah, just drop a post about the result anyway.

---

### Post by gogobaba on 2012-05-25
OK  im stuck on the pertiotion screen of the install i have selected my old C: but when i click on Install now it says "no root files system is defined.please correct this from the pertiotioning menu".Im trying to install it on /dev/sda2 ntfs and when i click on it the only option it gives me it to change delete or rever..

Would love some help now

---

### Post by gogobaba on 2012-05-25
Ive done its up and running :P

---

