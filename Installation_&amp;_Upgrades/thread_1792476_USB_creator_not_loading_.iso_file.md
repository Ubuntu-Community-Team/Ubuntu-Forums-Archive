---
title: "USB creator not loading .iso file"
date: 2011-06-28
forum: Installation &amp; Upgrades
---

### Post by ktp.kti on 2011-06-28
I am trying to create a bootable usb flash drive for installing ubuntu 11.04. I have already downloaded the desktop i386.iso file. It contained the usb creator. When i tried to use it to create the bootable usb drive, i am unable to load the .iso file into it. What should i do?

---

### Post by mörgæs on 2011-06-28
Is the USB stick completely empty, or does it contain U3 or similar programs for booting?

Have you tried Unetbootin?

---

### Post by ktp.kti on 2011-06-28
The usb stick is completely empty (I had formatted it). The problem is not with the usb drive. It is getting loaded and is being shown in usb creator. But the .iso file is not getting loaded into the usb creator program.

I will try unetbootin and let you know.

My suggestion is, if i have to go for a 3rd party software anyway for this purpose why is the useless usb creator being bundled with the .iso file. It should be corrected if faulty or removed altogether.

---

### Post by mörgæs on 2011-06-28
**IF** we are dealing with a bug in Usb-creator:

Software bugs will only be corrected if you take your time to post a detailed and exact error report.

---

### Post by varunendra on 2011-06-28
> **ktp.kti said:**
> My suggestion is, if i have to go for a 3rd party software anyway for this purpose why is the useless usb creator being bundled with the .iso file. It should be corrected if faulty or removed altogether.
You won't complain like this if you realize how open source software works. If you want everything stable - stick with latest LTS versions. That too is not guaranteed to work with everything but is much more stable.

Besides, you get that stability because of people doing what mörgæs said above.

Having said this, try the one included in 10.04 if you have its CD. Else, unetbootin may be good for you.

---

### Post by ktp.kti on 2011-06-28
Sorry if i sounded rude! What i intended to convey is this. If some faulty piece of software is provided with ubuntu, first-time users might be disheartened to try it further when they find faults. This should be corrected soon, especially for an excellent software like ubuntu!

I am a staunch supporter of ubuntu and other open source softwares. That is why i am devoting my time to try and use ubuntu and spread it to my friends also.

Sorry once again, dear ubuntu!

---

### Post by varunendra on 2011-06-28
> **ktp.kti said:**
> Sorry if i sounded rude! What i intended to convey is this. If some faulty piece of software is provided with ubuntu, first-time users might be disheartened to try it further when they find faults. This should be corrected soon, especially for an excellent software like ubuntu!

It's all right, I didn't mean to offend you too.

It's just that a major part of the power of open source comes from its huge user base (combined with independent developers). They test - report bugs - developers release fixes - users retest - report - bugfix -.... and this cycle keeps going until a reasonably stable and reliable version is released. This level of testing can't be done in labs so quickly and effectively as it happens through independent groups/individuals. So this has to be done.

While being effective, the downside of this method is that when users who expect 'latest-must-be-best' are troubled by such initial releases. You may think "why not release such versions only among 'testers/developers' then?" "Let a normal user face only the matured version!!" But this user/tester/developer base is so huge that it simply isn't possible to distribute certain versions among certain individuals.

So what it needs is awareness among users, not a radical change in how open source operates.

[DISCLAIMER: I've myself not understood the whole FOSS thing properly so far, so please excuse me if I made stupid mistakes explaining above. ;)]

@ktp.kti
Just tell us if something worked for you, and what, if something actually did.

---

### Post by ktp.kti on 2011-06-28
Unetbootin worked without a glitch. It was quite faster than the Universal USB installer suggested by the ubuntu site! I am installing ubuntu with the flash drive now!

Thanks mörgæs and varun!

---

### Post by mörgæs on 2011-06-28
Good to hear! Have fun with Ubuntu.

The problem with a program like USB-creator is that it should work with an unlimited number of USB sticks, some of which are maybe only sold in a certain part of the world. It is impossible for the developers to test any given combination.


Here are the known bugs for USB-creator:
[https://bugs.launchpad.net/ubuntu/+source/usb-creator](https://bugs.launchpad.net/ubuntu/+source/usb-creator)

Would be great if you could confirm a bug report, if someone has found the same error as you.


Finally, if I may give you some advice: You will do yourself a favour by posting only a few times a day, when it is absolutely necessary. Too many posts give a bad impression. This is not meant as bitching, only for helping.

---

### Post by ktp.kti on 2011-06-28
Thanks for the kind advice mörgæs. (I am actually violating your advice by posting this, but i hope this will be my last post for today! I really cannot stop thanking you people who spend your valuable time for the problems we newbies face! Without such advice i would have never completed my ubuntu installation successfully today. Thanks again everybody!)

I also visited the bug page you suggested. There was a report on an exactly similar error. I added myself to the list.

---

### Post by mörgæs on 2011-06-28
You are welcome. 

This is just 'Ubuntu'. Some day it might be you answering questions here... :-)

---

