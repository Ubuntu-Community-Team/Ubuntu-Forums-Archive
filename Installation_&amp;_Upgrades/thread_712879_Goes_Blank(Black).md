---
title: "Goes Blank(Black)"
date: 2008-03-02
forum: Installation &amp; Upgrades
---

### Post by xylon89del on 2008-03-02
My problem is that after i select to boot the ubuntu,everything just goes blank in black.

i post this problem earlier,and i get advice to make the partition with vista partitioner and the partitions shouldnt be left (unallocated)

i have reformat my vista and done all the the things above.

But,the result comes out is still the same.

someone please help me.I have spent my whole day working on it but still cannot figure wat is wrong.
Is it the problem of vista home basic or the problem of my comp?:confused:I am using dell laptop.

---

### Post by erginemr on 2008-03-02
Hi,

Please refer to this howto to check if your symptoms match the ones I have written there:
[http://ubuntuforums.org/showthread.php?t=700673](http://ubuntuforums.org/showthread.php?t=700673)

---

### Post by xylon89del on 2008-03-02
My problem is slightly different.

after the screen goes blank,it just stays blank foreve,no matter how long i wait..

---

### Post by zvacet on 2008-03-02
Boot in recovery mode and type 

```
dpkg-reconfigure xserver-xorg
```

when you come to the drivers stage select **vesa** and continue to the end.After rstart you should have basic graphic.

---

### Post by erginemr on 2008-03-02
> **zvacet said:**
> Boot in recovery mode and type 

```
dpkg-reconfigure xserver-xorg
```

when you come to the drivers stage select **vesa** and continue to the end.After rstart you should have basic graphic.

I second to that. If this is a graphics driver/resolution problem, this is the way to go...

---

### Post by qwertyyouup on 2008-03-02
I was about to post with this problem also. When I boot, I only have a blank screen. If I boot into recovery mode, I can init 5 and I'm presented with the login screen, and GUI, so I don't think this is a drivers problem. I've downloaded and installed all updates, and it doesn't help this issue. 

I'm running the x64 version. 
My hardware is as follows:
EVGA nForce 680i motherboard
EVGA GeForce 8800GTS 320MB
Intel Core 2 Duo E6750
2 GB Crucial DDR2 800

What would be the difference between booting into regular mode, vs recovery then going to runlevel 5? Is there a way for me to enable on screen information during boot, so I can see where things are going awry?

If you need more information, let me know.

---

### Post by erginemr on 2008-03-02
To view the on screen information, you can either press Alt+F3 when you see the Ubuntu logo,
--or--
you can select the grub entry you use for normal boot, enter the edit mode with "e", find the line with "kernel", press "e" again, remove "splash" and "quiet" and press "b" to boot (do not press Esc).

---

### Post by qwertyyouup on 2008-03-02
Come to think of it, I've never seen a splash screen for Ubuntu on any of my computers when booting. Never the less, Erginemr, thank you for the support. I tested removing the splash, and quiet options from the grub menu, then went on to take them out of the grub configuration file, and I'm able to boot straight into the gui now.

So, would anybody have any idea why the splash screen / quiet option prevented me from booting all the way? That seems like a pretty weird thing, that the splash screen would cause a failure like that.

---

### Post by erginemr on 2008-03-02
Great but I have a strong impression that this is a usplash issue as in:
[http://ubuntuforums.org/showthread.php?t=700673](http://ubuntuforums.org/showthread.php?t=700673)

You should follow the steps therein to get the Ubuntu splash screen back.

---

