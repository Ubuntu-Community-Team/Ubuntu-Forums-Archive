---
title: "Instal won't let me 'Forward'"
date: 2011-01-02
forum: Installation &amp; Upgrades
---

### Post by raysa on 2011-01-02
Trying to instal Ubuntu 10.10 on a new Acer laptop, alongside the pre-installed Windows 7. After allocating the vast majority of the hdd to Ubuntu (because I shall rarely use Windows), the instal gets as far as "Who are you?". I duly complete the user name etc and get green arrows to show the form likes what I've done, and all fields are filled in correctly. 
Then after a load of file-copying the progress bar says "Ready when you are..." but the Forward button is greyed out and I can't get any further.
I downloaded the iso again and burnt a new disc - on a different machine - just in case the first one was corrupt, but same result - grey Forward and no way to progress.
My other two computers both run Ubuntu 10.04 and I want the new one to be a Ubuntu machine as well ... how can I get the installation to, er, instal?

Thanks, Ray

---

### Post by Quackers on 2011-01-02
The username cannot start or end with a capital letter, that is usually the problem here.
However, a word of warning to you.
With the 10.10 installer the "install alongside" option has been known to over-write existing operating systems!
I would cancel that installation and select the "specify manually" option at the partitioning stage and create my own Ubuntu partitions from the unallocated space on the disc. If you don't have any unallocated space, you should first make some.

---

### Post by Rubi1200 on 2011-01-02
Just want to add something to what Quackers has already said.

When you start the LiveCD, before you proceed with the installation process, go to the terminal and post the output of this command:
```
sudo parted -l
```
(lowercase L not 1)

Once we know what your setup looks like, we can advise you further.

But, as already said, do NOT use the "install alongside" option. In this case, manual partitioning is the safest route to take.

---

### Post by raysa on 2011-01-02
Thanks both. It was the username initial capital that was the problem - it would be useful if the need to avoid them was mentioned on the form itself!

And your warnings about the 'install alongside' option came too late - I had of course already tried the installation when I posted my problem. So I now discover that the Ubuntu installation has wiped Windows from my brand new laptop. 

Having an 'install alongside' option which does nothing of the sort but wipes the 'alongside' OS partition instead is one hell of a bug!!

---

### Post by Quackers on 2011-01-02
Oh dear. I'll add you to the growing list of Ubiquity victims.

---

### Post by SEisch on 2011-01-21
And your warnings about the 'install alongside' option came too late - I had of course already tried the installation when I posted my problem. So I now discover that the Ubuntu installation has wiped Windows from my brand new laptop.

Having an 'install alongside' option which does nothing of the sort but wipes the 'alongside' OS partition instead is one hell of a bug!![/QUOTE]


I wish I had read some of these discussions before doing the exact same thing last week.  I selected the "install alongside" option.  My previous version of Ubuntu worked fine using this option, so I had no reason to suspect it wouldn't work this time.  I was wrong.  I'm just glad I had nothing important left on the windows side of the partition.  In all honesty I would have probably removed Windows eventually anyways.  It just happened a little sooner that expected.  Live and learn I guess.:)

---

### Post by Rubi1200 on 2011-01-21
I'm sorry to hear that this caused you to lose your Windows install (whether you planned on removing it eventually is immaterial).

You can help yourself, and those of us working to try and get the developers to fix this, by adding your name and a description of what went wrong here: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

---

### Post by SEisch on 2011-01-24
I will do that. Thanks Rubi1200.

---

### Post by Quackers on 2011-01-24
Most unfortunate.
There will be changes made to the 11.04 installer, but, sadly, not to the 10.10 installer.

---

### Post by dirghrabadia on 2011-01-24
I would say its a blessing in disguise for people like me who find it difficult (initially) to switch from Windows to Linux. jk ;)

---

### Post by Quackers on 2011-01-24
> **dirghrabadia said:**
> I would say its a blessing in disguise for people like me who find it difficult (initially) to switch from Windows to Linux. jk ;)

Lol, it's not the ideal way to do it, but it certainly forces your hand :wink:

---

