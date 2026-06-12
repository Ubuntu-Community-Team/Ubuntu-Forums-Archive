---
title: "Nvidia-crashes"
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by eGelor on 2010-05-18
Hello everyone,
I upgrade my system to lucid lynx 10.4
but the upgrade doesn't fix my problem with my nvidia drivers.
i got this problem since 2.6.31.14 now um running 2.6.32.22
my card is
> 01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 9200M GS] (rev a1)
 
i reinstall nvidia-current,nvidia-common as other Threads says but nothing.
Black screen on start up.
> predator@Terminal:~$ cat /var/log/Xorg.0.log |grep EE
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
(II) XKB: reuse xkmfile /var/lib/xkb/server-D378AD8F86E560F712A83EE36E4E5E92C595B9BD.xkm

Pls Help.:confused:

---

### Post by 2hot6ft2 on 2010-05-18
For 32 bit you need to install to the 2.6.32-21 kernel which came with it.
Then it should work fine I have a 8200M

For 64 bit you have to install to the 2.6.32-21 kernel first. Then it gets more complicated.
We have tried pretty much every fix we could find and this one is looking like the best one yet.

So here's the fix.
[http://ultimateeditionoz.com/forum/viewtopic.php?f=69&t=1112](http://ultimateeditionoz.com/forum/viewtopic.php?f=69&t=1112)

Replace the 2.6.32-22 kernel with the server kernel
```
sudo apt-get purge linux-headers-2.6.32-22 linux-image-2.6.32-22-generic
```
when that finishes install the server kernel per Blackwolfs's instructions
```
sudo apt-get install linux-headers-server linux-image-server linux-server
```
You will have to reboot after it finishes.
That's it.
Let us know if it works or not for you, so far we're getting good results and we want this bug squashed.
:guitar:

---

### Post by eGelor on 2010-05-19
I want this bug dead too.
I delete all nvidia driver : and install
 nvidia-current, nvidia-current-modaliases, nvidia-common, nvidia-settings.
I remove all old linux-images 
and add 2.6.32.22 and 2.6.32.21
nvidia drivers in my synaptic tool
i test 2.6.32.22 pae  and generic with nvidia drivers . Nada.(i delete this image) from synactic (linux-image)
i test 2.6.32.21 pae (nvidia crash into a black screen) and generic(gives green screen flashing) . nada.

---

### Post by eGelor on 2010-05-21
Anybodyyyyyyyy...

---

