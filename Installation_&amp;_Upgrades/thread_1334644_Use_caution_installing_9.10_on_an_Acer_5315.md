---
title: "Use caution installing 9.10 on an Acer 5315"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by Stew2 on 2009-11-22
Hello all,
Actually, I'm not sure about an install as I was using the Live CD to check it out. I was impressed, it had sound and the wireless worked out of the box. However, something that didn't work was the cooling fan on the Acer. Not too sure if there is a thread on this or anything but my laptop overheated bad enough to shut itself down then wouldn't boot back to Windows. I tried to boot back to the live cd to get the comp shut down properly but it overheated again as soon as I got to the desktop. My solution to get it to boot was to go into the bios and set the boot sequence back to the HDD. I don't think I will muck around with this for fear of toasting my laptop, but just wanted to post a warning for others that might try Ubuntu 9.10 on the Aspire 5315. I know it's Acer's fault and not Ubuntu's but might save someone some grief. 9.10 looked cool what I saw of it though!

---

### Post by MrGreen on 2009-11-30
I have the same problem, everything seemed to work but after a while it would just switch off. While running noticed it was getting hot and no fan....

Did you solve the problem or just go back too 9.04?

MrG

---

### Post by crank_it_up on 2009-12-03
Anyone who has this problem, there are 2 fixes in the thread below:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451337)

(1) Use recomplied kernel provided by Andy Whitcroft
(2) Flash your bios using ISO file provided by Angel Garcia

Either will work perfectly. The second fix is better as it means you can install updates to the kernel

---

### Post by MrGreen on 2009-12-03
I have loaded up crunchbang 9.04 which solved the issue.... needed to confirm if it was laptop ['hardware] or ubuntu 9.10 [software]

Maybe as kernel gets updated the issue will be solved ....

Thanks for the heads up

MrG

---

### Post by Stew2 on 2009-12-07
> **MrGreen said:**
> I have the same problem, everything seemed to work but after a while it would just switch off. While running noticed it was getting hot and no fan....

Did you solve the problem or just go back too 9.04?

MrG

Actually, on this one I just went back to Vista... Don't hate me :). 9.10 was an awesome test drive though, wireless and sound worked out of the box for me. A first! I have Ubuntu on my desktop though and it works nicely, I might update it to 9.10 though.

---

