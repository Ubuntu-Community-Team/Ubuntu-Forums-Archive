---
title: "USB Installation Issue on Netbook"
date: 2011-03-02
forum: Installation &amp; Upgrades
---

### Post by drioddude on 2011-03-02
I have been attempting to install Ubuntu 10.10 on my Acer Aspire One for a few days now. Its current OS is Win7 Starter, if that even matters.

-I made a USB drive and Ubuntu boots and runs just fine. 
-I hit the "install Ubuntu" icon and it has me choose my language, then I hit forward. 
-It asks if I want to install updates and/or third party apps, I check the boxes and hit forward - and then it just sits there with the cursor spinning like its trying to do something, but it never does. The longest I have let it sit there was four hours, and still nothing happened.
**[_This _]("http://www.ubuntu.com/sites/default/files/active/maverick/install_02_medium.jpg")is the step it always stops on. 

Could the problem be that I am trying to install the desktop version instead of the netbook version? I tried the netbook version and I just don't like it as much.

What do you think is keeping Ubuntu from installing?

---

### Post by swapnilnarendra on 2011-03-03
First of all, Ubuntu says that it needs at least 2.6GB space but believe me the minimum is 10GB (okay that was a little bit out of context).

But about your problem, even if the desktop edition is not for the netbook, it should not just freeze there. Though I havent heard/read anywhere that you cant desktop edition on a netbook, but still I think it should not be done. Even I have tried running the desktop edition on my netbook and it worked fine but I never installed it and so dont know. You said that you tried the Netbook version, so I am hoping that you installed it. 

Maybe this IS a problem with the desktop version being installed in a netbook.

---

### Post by drioddude on 2011-03-03
> **swapnilnarendra said:**
> First of all, Ubuntu says that it needs at least 2.6GB space but believe me the minimum is 10GB (okay that was a little bit out of context).

But about your problem, even if the desktop edition is not for the netbook, it should not just freeze there. Though I havent heard/read anywhere that you cant desktop edition on a netbook, but still I think it should not be done. Even I have tried running the desktop edition on my netbook and it worked fine but I never installed it and so dont know. You said that you tried the Netbook version, so I am hoping that you installed it. 

Maybe this IS a problem with the desktop version being installed in a netbook.

The same problem occurs when I try to install Netbook edition as well. 

I tried to install the desktop version on my dad's laptop-a totally different machine-, and the install halted at the same place.

I probably should have mentioned this in my first post but when I get to the problem point, it gives me an error message saying the program "parted_server" closed unexpectedly. I'm not sure really what that means. My best guess is that Win7 doesn't want me to install Ubuntu? But if that's the case, how do I get around that problem?:confused:

---

### Post by drioddude on 2011-03-10
Bump.

Anyone have any ideas? I have continued trying with no luck.

---

### Post by Hedgehog1 on 2011-03-10
One thing I have seen cause this is when all 4 primary partitions are already taken on the disk.

drioddude, could you do this from the LiveUSB in 'TRY' mode:

In the Terminal (Menu to: Applications >> Accessories >> Terminal), please run this command:  (the -'l' is a lower case 'L')
```
sudo fdisk -l
```
Then copy the text from the output and paste it into your next post.

***The Hedge***

:KS

---

