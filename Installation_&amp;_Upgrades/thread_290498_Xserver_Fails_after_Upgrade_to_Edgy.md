---
title: "Xserver Fails after Upgrade to Edgy"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by eighthate on 2006-11-01
Hey, I recently upgraded to Edgy eft but right after ubuntu sign shows that all is loaded well, xserver wont go on, i read this thread ---- [http://www.ubuntuforums.org/showthread.php?t=187177](http://www.ubuntuforums.org/showthread.php?t=187177) but i dont know how to start in recovery mode, there is no Grub menu in my computer, at least
 thats what my noobism tend to let me think. Some1 help me please!!

---

### Post by thoolihan on 2006-11-01
Can you get to a regular terminal?  (Ctrl - Alt - F1)
If so, try looking at the X log (/var/log/Xorg...)
or at least post the contents here.

---

### Post by eighthate on 2006-11-01
how can i look at the x logs from a terminal? I'm actually in recovery mode on my linux computer.

---

### Post by kulashaker on 2006-11-01
Hi,

I have the same problem and I get this errormessage:

mkdtemp: private socket dir: permission denied.

My guess is that this is a related problems, since this appeared one reboot after the update.

/Kula

---

### Post by thoolihan on 2006-11-01
> **eighthate said:**
> how can i look at the x logs from a terminal? I'm actually in recovery mode on my linux computer.

cd /var/log
ls X*log
nano Xorg.0.log

or, try 

cat Xorg.0.log | grep "EE"

---

### Post by thornmastr on 2006-11-01
I had the same or an equivalent problem. After a number of bad attempts at resolution, I found that the following should have worked.

sudo dpkg-reconfigure -p high xserver-org

Unfortunately the first time I tried this I was told that either xserver-org was  broken or not completely installed. I reinstalled it doing 
sudo apt-get install xserver-xorg which seemed to reinstall the little devil with no back talk whatsoever. 

Then, repeating the sudo dpkg-reconfigure -p high xserver-org command worked just fine and lo and behold xserver was/is  happily doing its thing and all is rosy in the land of Ubuntu once again.

---

