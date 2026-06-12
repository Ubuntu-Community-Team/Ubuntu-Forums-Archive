---
title: "Lenovo IdeaPad Z570-1024D9U - Laptop (Login Trouble)"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by zdeuyo on 2012-04-28
Hello Forum,


The problem I am having is with my Lenovo IdeaPad Z570-1024D9U - Laptop. After upgrading to 12.04 everything worked great. The problem now is that I cannot login. The screen showing username and password shows up. I enter password and click enter and it says Logging In...then it hangs.
Here are the specs.


Description:	

IdeaPad Z570 Laptop - 1024D9U - Gunmetal Grey: Weekly Deal	

Processor:	2nd generation Intel Core i7-2670QM Processor( 
2.2GHz 1333MHz 6MB)	

Operating system:	Genuine Windows 7 Home Premium 64	

Graphics:	Intel Integrated HD Graphics 3000	

Memory:	8.0GB PC3-10600 DDR3 SDRAM 1333 MHz	

Display:	15.6" HD Glare with integrated camera 1366x768	

Pointing device:	Industry Standard Touchpad	

Hard Drive:	500GB 7200	

Optical Drive:	DVD Recordable	

Battery:	6 Cell Lithium-Ion	

Network Card:	Intel 1000 BGN Wireless	

Bluetooth:	Bluetooth Version 2.1 + EDR	

Warranty:	One Year	

Camera:	Integrated 2.0MP Camera	

HDMI:	HDMI (Out)



Please help.

---

### Post by poonjabi on 2012-04-28
Have you tried changing to the Ubuntu 2D session and then trying to login? Click the gear icon to change your session at the login prompt.

---

### Post by zdeuyo on 2012-04-28
This works and allows me to login, but why does 3d not work?

---

### Post by zdeuyo on 2012-04-28
Hey,

After getting into 2D mode I ran

Update manager...done

```


sudo apt-get update
sudo apt-get upgrade


```

Restarted, then 3D allowed me in. SOLVED

---

### Post by zdeuyo on 2012-04-28
Well....its back again...2D and 3D does not work to login...it just hangs

---

### Post by zdeuyo on 2012-04-28
It allowed me to login by terminal. When arriving at GUI login, I pressed Alt+Tab+F6 and went to terminal and it worked...no GUI....this is weird...any ideas?

---

### Post by poonjabi on 2012-04-28
> **zdeuyo said:**
> It allowed me to login by terminal. When arriving at GUI login, I pressed Alt+Tab+F6 and went to terminal and it worked...no GUI....this is weird...any ideas?

You are going to have to drop back to Ubuntu 2D and wait this out. There is a bug report for this issue. You may want to submit your own as well.  Hang in there. It just got released yesturday so....

---

### Post by zdeuyo on 2012-04-28
> **poonjabi said:**
> You are going to have to drop back to Ubuntu 2D and wait this out. There is a bug report for this issue. You may want to submit your own as well.  Hang in there. It just got released yesturday so....

I cannot login to either 2D or 3D though...

---

### Post by poonjabi on 2012-04-28
> **zdeuyo said:**
> I cannot login to either 2D or 3D though...

Then you need to drop to the recovery mode during bootup and remove the video driver you installed manually from the command line. You will need to research a bit how to do this.

---

### Post by oldfred on 2012-04-28
Even with nVidia I had to drop back to 2D. And that seems to be working well for me.

For Intel:
The Open-Source Linux Graphics Card Showdown
[http://www.phoronix.com/scan.php?page=article&item=intel_ivy_gpushow&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_ivy_gpushow&num=1)

---

### Post by zdeuyo on 2012-04-28
The thing is both worked for an entire day with 12.04. Then only 2D worked, then neither of them work. Any ideas?

---

### Post by zdeuyo on 2012-04-29
Hello,


Well now I am writing this followup in Windows....as I mentioned 2D and 3D do not work....what do I do?

---

### Post by oldfred on 2012-04-29
Can you boot to command line from recovery mode?

I would from that see if any updates help. Otherwise I would search for specific issues with your model Lenovo and Ubuntu. Do you have one of those Optimus dual video things that has issues?

---

### Post by zdeuyo on 2012-04-29
> **oldfred said:**
> Can you boot to command line from recovery mode?

I would from that see if any updates help. Otherwise I would search for specific issues with your model Lenovo and Ubuntu. Do you have one of those Optimus dual video things that has issues?

Hello Oldfred,


I am actually using it on the linux side now. I just reinstalled from Usb and started clean. This seems to have fixed it. It must have been a corrupted file and or package.

Idk if I should mark this thread as solved. Should this count as a solution?

---

### Post by oldfred on 2012-04-29
I suppose, if another user with exactly your model computer searches they will find it does work, eventually. :)

---

### Post by zdeuyo on 2012-04-29
> **oldfred said:**
> I suppose, if another user with exactly your model computer searches they will find it does work, eventually. :)



solved :)

---

