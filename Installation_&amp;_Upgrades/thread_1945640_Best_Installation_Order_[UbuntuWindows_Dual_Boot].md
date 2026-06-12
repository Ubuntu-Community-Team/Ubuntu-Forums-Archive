---
title: "Best Installation Order? [Ubuntu/Windows Dual Boot]"
date: 2012-03-23
forum: Installation &amp; Upgrades
---

### Post by alexgeek on 2012-03-23
I'm currently using Windows 7 64 Bit, but it's getting too slow so I want to switch to dual booting Ubuntu and Windows 7 (reinstalling Windows 7 as my current one is bit clogged). 
Planning to split my 1TB drive into 2 500GB partitions with Ubuntu on one, Windows on the other.
Before I do just checking which is better, installing Windows first then Ubuntu or Ubuntu then Windows?
Cheers

Side note, would anyone recommend Xubuntu over Ubuntu? Seems like Xubuntu is designed for lightweight systems but mine is pretty powerful.

---

### Post by snowpine on 2012-03-23
It is easier to install Windows first and then Ubuntu second, but both methods will work, as you can read here:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

I would describe Xubuntu not so much as "Ubuntu designed for lightweight systems" but rather as "Ubuntu with the Xfce Desktop Environment (which happens to be lightweight)." If you prefer Unity then install Ubuntu; if you prefer Xfce then install Xubuntu; if you can't decide, it is easy to install Xfce as an add-on to Ubuntu (or Unity as an add-on to Xubuntu)! :)

---

### Post by alexgeek on 2012-03-23
Thanks, I'll go with Ubuntu since I already have the ISO then.

---

### Post by snowpine on 2012-03-23
You're welcome. If you decide to try Xfce at a future date, this will help:

[http://www.psychocats.net/ubuntu/xfce](http://www.psychocats.net/ubuntu/xfce)

---

### Post by rjs987 on 2012-03-23
Just as an alternate thought. I like installing Ubuntu on the whole partition, and then installing Windows 7 in a VB virtual machine. Then I can have both running at the same time. I have this setup at work (they "tollerate" me doing it even though there are some at work who are ms brainwashed). I run the vm in seamless mode all the time and can drag/drop or cut/paste between Windows 7 and Ubuntu. I altenate working in documents in Libre Office in Ubuntu or in ms office in Windows 7 constantly with no issues. I can choose what I feel is the best of both.

BTW- one of my co-workers decided to try a VB virtual machine running on his Windows 7 install (backwards from how I have it) and the vm just does NOT run well that way. The problem is as I have always told them... Windows just doesn't know how to do local virtual machines very well at all compared to Linux. Last year I was 'allowed' to have a vm of my Ubuntu on my mandatory Windows 7 box and it just didn't run anywhere as well as a native install of Ubuntu with a Windows 7 vm.

---

### Post by ranger1021994 on 2012-03-23
> **alexgeek said:**
> I'm currently using Windows 7 64 Bit, but it's getting too slow so I want to switch to dual booting Ubuntu and Windows 7 (reinstalling Windows 7 as my current one is bit clogged). 
Planning to split my 1TB drive into 2 500GB partitions with Ubuntu on one, Windows on the other.
Before I do just checking which is better, installing Windows first then Ubuntu or Ubuntu then Windows?
Cheers

Side note, would anyone recommend Xubuntu over Ubuntu? Seems like Xubuntu is designed for lightweight systems but mine is pretty powerful.


I reccomend u install Windows first and then Ubuntu because doing this otherwise would result in loss of GRUB loader which can detect both Windows and Linux based systems...
U have nice config. Enjoy Ubuntu :) :)

---

