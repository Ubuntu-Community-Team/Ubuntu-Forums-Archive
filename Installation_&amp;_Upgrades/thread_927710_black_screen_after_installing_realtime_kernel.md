---
title: "black screen after installing realtime kernel"
date: 2008-09-23
forum: Installation &amp; Upgrades
---

### Post by zansiball on 2008-09-23
i got the latest ubuntu desktop version installed. i tryed to install the realtime kernel but when i try to boot it the screen just turns black.

i read somewhere that it has something to do with the nvidia drivers.

how can i solve this problem? i really want the realtime kernel. nvidia drivers isnt that important but should be great if they worked.

---

### Post by pretzelboy on 2008-09-27
> **zansiball said:**
> i got the latest ubuntu desktop version installed. i tryed to install the realtime kernel but when i try to boot it the screen just turns black.

i read somewhere that it has something to do with the nvidia drivers.

how can i solve this problem? i really want the realtime kernel. nvidia drivers isnt that important but should be great if they worked.

I have the exact same problem.....
My generic kernel uses the Nvidia restricted driver and it boots fine from the grub menu.

I installed the RT kernel (to use Ardour etc) and now when I boot that kernel I get kicked back to a CLI with errors related to the Nvidia driver.

I *can* get the system to boot by editing xorg.conf to use nv instead of nvidia, but now my dual monitors don't work.

I installed the RT kernel from the ubuntu repository via synaptic.

Like I said, my generic stock kernel boots fine from grub menu.

So how do i fix this, and more importantly, fix it without screwing up my working kernel.

TIA!

---

### Post by tistria on 2008-10-02
I have a similar problem.  I found [this]("http://meandubuntu.wordpress.com/2008/07/17/install-nvidia-17713-drivers-on-realtime-kernel/") page, with instructions to install the drivers again.  I'll give it a shot and get back to you.

---

