---
title: "Video Card needed for virtualization?"
date: 2016-11-14
forum: MINT
---

### Post by JayKay3OOO on 2016-11-14
Hi Folks.

I have an I5 4690k with onboard graphics and a GTX 760 graphics card with Ubuntu mint.

I run several virtual machines including Windows 10, ubuntu server, (with terminal server), windows server2012 and test / server virtual machines. I sometimes edit video and play quake 2. I only use one 32inch screen.

Would I notice any video performance loss by taking the graphics card out? I always assumed the graphics card was being used for virtual machines, but now I'm not really sure. I would like to lower the power consumption of the pc and one way of doing it would be to sell this graphics card.

---

### Post by QIII on 2016-11-14
Moved to MINT.

Hello!

What software are you using for your virtualization?

---

### Post by JayKay3OOO on 2016-11-14
Virtualbox

---

### Post by wildmanne39 on 2016-11-14
What do you mean video card needed for virtualbox? the vm is going to use a generic video card driver so as far as I know it does not make much difference what card you have, it will use the card of your host and the driver from virtualbox.

I see I am sure the vm needs a video card might be an exception if they do not have a gui.

---

### Post by JayKay3OOO on 2016-11-14
Ok, so it will probably feel about the same using the cpu onboard graphics then?

---

### Post by wildmanne39 on 2016-11-14
See if this helps.
[http://www.idganswers.com/question/6660/do-you-still-need-a-video-card-if-you-don-t-use-your-pc-for-gaming](http://www.idganswers.com/question/6660/do-you-still-need-a-video-card-if-you-don-t-use-your-pc-for-gaming)

---

### Post by QIII on 2016-11-14
Be aware, however, that the virtual video card supplied by the hardware abstraction layer in VBox performs very poorly.  No matter the hardware GPU, graphics performance will be insufficient for graphics heavy software like games.

VBox does not, as yet, support pass-through.

---

### Post by JayKay3OOO on 2016-11-16
Ok - so not having my old gaming graphics card in won't harm virtual machine performance in any way is what I'm reading since vritualbox can't use it anyway.

Your answers clear up what I was hoping really. 

The power usage drops by nearly half not having it in as I have HDMI on the motherboard so no need for it.

Good stuff, thanks for clearing that up :)

---

