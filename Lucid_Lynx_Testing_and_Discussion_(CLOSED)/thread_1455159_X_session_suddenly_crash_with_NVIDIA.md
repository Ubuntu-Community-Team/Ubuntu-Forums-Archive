---
title: "X session suddenly crash with NVIDIA"
date: 2010-04-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by stek79 on 2010-04-15
Hi guys,

I have an nvidia-based laptop.

A nasty bug is present in Lucid: every now and then, the session suddenly crashes and I'm taken back to the login!

Is there anyone else that is affected by this problem?

I've opened this bug:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/557572](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/557572)

Thanks

---

### Post by Crunchy the Headcrab on 2010-04-15
No problems here.  Nvidia 9800M GS 512MB.

What model number do you have?  I should specify that I didn't use the restricted hardware installer to install my nvidia drivers.  I used:

> sudo aptitude install nvidia-current


---

### Post by stek79 on 2010-04-15
> **Crunchy the Headcrab said:**
> No problems here.  Nvidia 9800M GS 512MB.

What model number do you have?  I should specify that I didn't use the restricted hardware installer to install my nvidia drivers.  I used:


Hi Crunchy, thanks for the reply.

Mine is:

01:00.0 VGA compatible controller: nVidia Corporation NV17 [**GeForce4 420 Go**] (rev a3)

---

### Post by Ibidem on 2010-04-15
Looks like its "GeForce4 420 Go"
(see lspci output in Launchpad)

EDIT:OK, you posted while I was writing...

---

### Post by Aries K on 2010-04-15
Yes, I am having this problem too. Here are the links to the thread I made and the bug I filed.

[http://ubuntuforums.org/showthread.php?t=1451351](http://ubuntuforums.org/showthread.php?t=1451351)

[https://bugs.launchpad.net/ubuntu/+bug/562565](https://bugs.launchpad.net/ubuntu/+bug/562565)

---

### Post by eco2geek on 2010-04-16
I have exactly the same problem. It occurs every time I boot, and reinstalling "nvidia-current" does not make the problem go away. Until there's a fix, I'm back to using the "nv" driver.

---

### Post by stek79 on 2010-04-17
> **eco2geek said:**
> I have exactly the same problem. It occurs every time I boot, and reinstalling "nvidia-current" does not make the problem go away. Until there's a fix, I'm back to using the "nv" driver.

Great, would you all subscribe to my bug as affected people?

Hopefully we can increase the probability that it will be looked into.

Aries, your bug report seems totally unrelated to this problem!

Perhaps the one I opened is more suited, since Ubuntu X chief (Bryce Harrington) has already marked it as Confirmed.

Let's subscribe to it then!

You can find it in my first post, then click on the button "affects me too".

We'll see how it goes.

---

### Post by Aries K on 2010-04-17
> **stek79 said:**
> Great, would you all subscribe to my bug as affected people?

Hopefully we can increase the probability that it will be looked into.

Aries, your bug report seems totally unrelated to this problem!

Perhaps the one I opened is more suited, since Ubuntu X chief (Bryce Harrington) has already marked it as Confirmed.

Let's subscribe to it then!

You can find it in my first post, then click on the button "affects me too".

We'll see how it goes.

I see now, your bug crashes while in a session vs. mine during bootup. I apologize for the misunderstanding. Good luck getting your problem solved! :guitar:

---

### Post by zekopeko on 2010-04-17
> **stek79 said:**
> Hi guys,

I have an nvidia-based laptop.

A nasty bug is present in Lucid: every now and then, the session suddenly crashes and I'm taken back to the login!

Is there anyone else that is affected by this problem?

I've opened this bug:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/557572](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/557572)

Thanks

I'm getting something similar but with the restricted nvidia driver.

---

### Post by regomodo on 2010-04-17
I'm not crashing with my 8800gt but I cannot get my system to run with the nvidia driver when trying to enable the visual effects. It just falls back to what I assume is the nv driver.

---

