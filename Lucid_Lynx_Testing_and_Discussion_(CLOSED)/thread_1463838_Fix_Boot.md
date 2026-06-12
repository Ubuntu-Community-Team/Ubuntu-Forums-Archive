---
title: "Fix Boot ?"
date: 2010-04-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Hambombj on 2010-04-27
Hi peeps!

I have replaced one of the hard drives in my pc, and now ubuntu wont boot by itself.

It was installed on the 2cnd drive as at the time i had win xp pro on the ist drive.

I had since removed windows entirely as I'm so impressed with ubuntu 10.04!!

How do I get the grub loader to come back ?

At the moment i'm using super grub disk to boot into lucid, but thats a bit of a pain to keep doing.

also how do I upgrade it to the rc? or is it doing it bit by bit with the updates?


any ideas?
:(

---

### Post by VMC on 2010-04-27
Not sure how you were booting beofre. Hopfully you weren't using Wubi, as you need Windows.

Were you booting with grub or through Windows boot manager?

One thing , depending on your experience level, is [chroot]("http://ubuntuforums.org/showpost.php?p=8883297&postcount=3") using a livecd and install grub that way.

---

### Post by Hambombj on 2010-04-27
i installed ubuntu when windows was active, so maybe i was using wubi.

I used to get a screen come up giving me the option to boot into ubuntu.
with a series of ubuntu kernals listed, it had win xp at the bottom of the list.
allthough I had re-formatted the entire drive that had windows on it.

so I assume it was using grub. it had grub ver at the top

Experience wise I'm a newbi to ubuntu :-)

so the option for "Dummies" is probably best!

---

### Post by kansasnoob on 2010-04-27
It would be immensely helpful to see the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by limey_rick on 2010-04-27
So if you took away the windows disk, you likely took away the disk that had GRUB installed on the MBR. Windows tends to like to be installed on the disk that the BIOS boots first and so this may also have been where GRUB installed on the MBR. Now this disk is gone, you will need to re-install GRUB on the other disk. 

See this on how you can do this. You will need a Live CD.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by Bobhuber on 2010-04-27
> **Hambombj said:**
> Hi peeps!

I have replaced one of the hard drives in my pc, and now ubuntu wont boot by itself.

It was installed on the 2cnd drive as at the time i had win xp pro on the ist drive.

I had since removed windows entirely as I'm so impressed with ubuntu 10.04!!

How do I get the grub loader to come back ?

At the moment i'm using super grub disk to boot into lucid, but thats a bit of a pain to keep doing.

also how do I upgrade it to the rc? or is it doing it bit by bit with the updates?

any ideas?
:(
Follow these instructions.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Hambombj on 2010-04-28
Thanks everyone, but I have got it to work!

I installed the rc onto the first drive, thus giving me option to boot into the other drive :)

So now I have the 10.04 RC on the primary drive
and 10.04 beta 2 on the secondary drive.

oh and in my opinion ubuntu "Lucid Lynx" :guitar:

---

