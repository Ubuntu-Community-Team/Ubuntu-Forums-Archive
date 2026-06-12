---
title: "Nvidia Driver activated but not in use"
date: 2010-03-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Dobbie03 on 2010-03-19
I just upgraded to the beta of Lucid and I have been having to manually set my visual effects.  I checked to see if my nvidia driver was activated and it is but it is saying this:

> This driver is activated but not currently in use

What do I do to get my nvidia card to start at boot up?

---

### Post by dino99 on 2010-03-19
so what other driver do you use ?

---

### Post by quadproc on 2010-03-19
> **MattDobson said:**
> I just upgraded to the beta of Lucid and I have been having to manually set my visual effects.  I checked to see if my nvidia driver was activated and it is but it is saying this:
...

I suspect that you used the "hardware drivers" feature in system administration to see if the driver is activated.  If so, that utility may be reporting incorrectly.  I found a very similar problem here in that that utility (which is named jockey-gtk) reports "no proprietary drivers are in use on this system" even though I am running the ATI driver for my video cards and it is functioning correctly.

To find out what your system is really running, look in the /etc/X11/xorg.conf file and see what it shows in the "Device" section for "Driver".  If that is the nvidia driver then you should be OK as-is.  If not, then you can change the driver to whatever is appropriate after first making sure that you have installed the correct driver and you have made a backup copy of your running xorg.conf file (just in case you have to go back).  In case of trouble you can change the driver to vesa to get running again temporarily; vesa doesn't do many things but at least it is a simple and robust fallback.

You might also be able to learn something from the Xorg.0.log file in /var/log if the preceeding doesn't help.

Hope this helps.

quadproc

---

### Post by whoop on 2010-03-19
[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/539997](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/539997)

---

### Post by cecilpierce on 2010-03-19
I found this thread form google search >>>

Old  January 20th, 2010   	   #4
chrismine
A Carafe of Ubuntu
 
Join Date: Jun 2006
Location: GEORGE ZA
Beans: 100
Ubuntu Development Release
	
Re: Nvidia driver activated but not currently in use ??
I had the same problem. I removed all nvidia drivers with Synaptic. Then I installed again from command line - sudo apt-get install nvidia-current and ran sudo nvidia-xconfig and it worked.

Hope it helps.
__________________
Intel E7400 2.8 GHz Core2Duo CPU, Asus P5K mobo, 2 GB DDR800 mem, 256 MB POV Nvidia8600GTS GPU, 250 GB Seagate HDD, LG 22x DVD Rewriter, 23" Acer H233H LCD @ 1920 x 1080 Ubuntu User # 17508

---

### Post by dinamic1 on 2010-03-19
same here
[http://i43.tinypic.com/w0hl5w.png](http://i43.tinypic.com/w0hl5w.png)

---

### Post by Dobbie03 on 2010-03-20
Thanks everyone for your help but I will just waut for the official release.

---

### Post by ronacc on 2010-03-20
I also had this problem , installed driver from Nvidia with cmd line , it still says not in use but it is infact in use , compiz works and nvidia settings shows it as being active . also extra effects do not show enabled but also work just fine .

---

### Post by edkmho on 2010-03-21
Hi guys, 

I have similar issue and i could not enable the desktop effect with the new driver. with 195.36.08, i am able to enable the desktop effect without any problem.

Could anyone help me. Many thanks.

---

