---
title: "[SOLVED] Windows installation killed my Ubuntu"
date: 2008-10-24
forum: Installation &amp; Upgrades
---

### Post by balagosa on 2008-10-24
Before anyone comments, I needed Windows because of MatLab. I know there is SciLab to counter MatLab but my teacher is strict that we should use MatLab because he will check our codes. VMware wouldnt do because it was too slow. Wine was just not working for me.

I know there are threads like this all around the forums, but I have no time. My schedule is just hectic now that it is finals week.

So I installed windows. The problem is Windows killed my **Grub Boot Loader**, resulting that I can not load my Ubuntu anymore. When I start up my PC, it directly goes to Winblows.

So can anyone help?

As a last resort, after passing the project I will load the LiveCD and delete the windows partition.

---

### Post by balagosa on 2008-10-24
I found this thread, I hope this works

[link]("http://ubuntuforums.org/showthread.php?t=755782")

---

### Post by rsambuca on 2008-10-24
All you have to do is re-install grub to the MBR using a liveCD.  It should detect both Ubuntu and Windows and then give you an option at bootup which to start.

---

### Post by balagosa on 2008-10-24
> **rsambuca said:**
> re-install grub to the MBR


Exaclty how do you do that?

---

### Post by rsambuca on 2008-10-24
Boot up from an Ubuntu live CD.  Open a terminal.  At the prompt, enter```
sudo grub
```Then at the grub> prompt, enter ```
find /boot/grub/stage2
```It will give you a location of your Ubuntu grub in the form of (hdX,Y), where X and Y will be numbers specific to your installation.  Use this info to setup grub by entering```
root (hdX,Y)
```, replacing the X and Y with your specific numbers.  Then write the grub to the MBR by entering ```
setup (hd0)
```Then get out of grub by entering ```
quit
```

---

### Post by balagosa on 2008-10-24
That worked and it is a better solution to the link that I found.

---

### Post by jpkotta on 2008-10-24
Matlab does run on Linux.  The student version (I will assume that's what you have) has all three of Windows, Mac, and Linux versions on the CD.

Also, take a look at Octave.  It generally considers incompatibilities with Matlab as bugs, and with some experience you can write code that will run on both.

---

### Post by balagosa on 2008-10-24
OK, there is a new problem.

Now I can not load Windows, it has been wiped off the Grub options. How do I put it in?

-----------------------------------------------------------------------------

Solved it. Windows is on /dev/sda2 so I edit /boot/grub/menu.lst

and added

```
title Windows XP
root (hd0,1)
makeactive
chainloader +1
```

root (hd0,1) // This is 1 because Windows is located on sda2

---

