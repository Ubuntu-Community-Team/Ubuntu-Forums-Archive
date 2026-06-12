---
title: "Smaller partition size on Dapper Drake Install?"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by charles_d on 2006-06-02
Is it possible? I'm running Windows XP Pro Corp. ed on my 200gb sata hdd and I want to install Dapper Drake. When I load the DD cd and i double click the install icon on the desktop, everything is fine and dandy untill it shows my available hard drives to partition. It will show my 200gb sata drive just fine, but the smallest it will let me partition is 70GB and I definately do not want or need that much space. I guess the max I want is 20GB. How can I go about doing this? I am a Linux noob, and not good at all with the command line (DOS or Linux) but if I need too I guess I could try it. Any help is appreciated ! :)

---

### Post by az on 2006-06-02
Is that the size of your new or old partition?

Maybe it is telling you that you cannot shrink it more than that...

---

### Post by charles_d on 2006-06-02
I'm under the impression that the slider sets the percent of the original hard drive space to be partioned and used for Ubuntu. Am I under the wrong impression?

---

### Post by az on 2006-06-04
I just wanted to quote the correct thig:  I am doing an install now, ont a box which already hs a Window OS on it.

The partitioning step says:

"How do you want to partitoin your disks?"

With the defaul option being 

"Resize IDE1, master blablabla hda1 and use freed space"

and the slider says "new partition size".  Now that is a little misleading because what it means is "the new size of your old partition" as opposed to "the size of your new partition."

So the slider is the size of your old partition.  In your case, it cannot be shrunk any smaller than 70 gigs (cuz it's that full).

---

