---
title: "Asus Eee PC 1201N, error appears during boot"
date: 2010-08-24
forum: Installation &amp; Upgrades
---

### Post by arker on 2010-08-24
Recently I installed Ubuntu 10.04 in my Eee PC 1201n, dual boot with Win7. I got some error at booting, it says: nForce2_smbus 0000:00:03.2: Error probing SMB2. It not happened when I used 9.10, dual boot. After the error appearing, the system will stay still for around 20 seconds, then start to react to log in interface. Do any one meet the same problem, please show me some solutions. thanks a lot ;-)

---

### Post by Rubi1200 on 2010-08-24
Are you sharing files between Windows and Ubuntu?

---

### Post by arker on 2010-08-24
I don't know, probably not. Because it happened just after a fresh installation. byw, do you know how to prevent sharing things between win and ubuntu, that might cause problem, thanks

---

### Post by Rubi1200 on 2010-08-24
> **arker said:**
> I don't know, probably not. Because it happened just after a fresh installation. byw, do you know how to prevent sharing things between win and ubuntu, that might cause problem, thanks
If you are not sharing files and haven't enabled anything then there is nothing to worry about.

Ok, to your problem:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/575296](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/575296)

This bug report indicates that this is not a new issue (see the link to the report for Karmic).

You need to go through it and see if anyone has come up with a solution yet (or at least a workaround).

---

### Post by arker on 2010-08-27
I'd better wait for the 10.10; I checked the website, the only solution is edit something on grub; but.. the boot still delay, only the error message is gone, doesn't help. I hope 10.10 will fix this problem for Eee PC user. I don't have problem when I use Karmic, may I should back to that, then I need to fix the wireless, microphone, and wifi.... life is paradox. thanks for your answer, byw, another question, do you think the higher version cost more computer power, I feel 9.10 runs faster than 10.04 on my netbook, is that illusion or real? Once, my computer is doing nothing, only mouse can move, in 10.04, but it never happened in 9.10 and 9.10 runs much smooth. In summary, I think only certain version is fit certain laptop, not always update and upgrade, do you think so.. maybe I should stick  to 9.10 and try to fix all the problem, or waiting for the solutions. I am look forward to 10.10.. thanks again.

---

### Post by Rubi1200 on 2010-08-27
I see this happening again and again; one version works well and then suddenly the newer version seems to have problems on the same computer.

A lot of it comes down to hardware compatibility with newer kernels. The developers cannot take into account every computer make and hardware combination, so they try and find a solution that will work for as many people as they can. 

Inevitably, some people will experience difficulties and have to go back to an older version until bugs etc. are worked out.

I decided to stick with 9.10 for the moment, but each person makes their own decision.

Good luck whatever you decide; as long as it is Ubuntu :)

---

### Post by arker on 2010-08-29
thanks for your reply, I will stick to Ubuntu for sure. The way of find problem and get solution is also a way of life. I will learn a lot through this, thanks again for your answer. now I am feeling the power of the Ubuntu community!!

---

