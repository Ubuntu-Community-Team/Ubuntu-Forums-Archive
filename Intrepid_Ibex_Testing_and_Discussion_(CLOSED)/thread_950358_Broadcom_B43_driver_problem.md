---
title: "Broadcom B43 driver problem?"
date: 2008-10-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Zlatan on 2008-10-17
Hi,

currently trying Kubuntu Intrepid Ibex on my Lenovo 3000 N100. Everything works fine, except that in section Hardware Drivers there are 2 drivers:
Broadcom B43 wireless driver (installed, but could not activate it)
wl (activated)

wl does not work with my wireless card, and the problem is, that I would like to activate B43 driver. But it does not work:)

Has anyone solved this?

Thank you

---

### Post by Ewingo401 on 2008-10-17
I don't know what the exact steps would be for doing this in Kubuntu, but I was able to fix this issue in Ubuntu by going into the synaptic package manager and marking b43-fwcutter for re installation. After I did that it asked me if I wanted to extract the firmware, I did and from then on the driver worked with no issues.  I know its not Kubuntu, but I hope it helps.

---

### Post by Zlatan on 2008-10-17
> **Ewingo401 said:**
> I don't know what the exact steps would be for doing this in Kubuntu, but I was able to fix this issue in Ubuntu by going into the synaptic package manager and marking b43-fwcutter for re installation. After I did that it asked me if I wanted to extract the firmware, I did and from then on the driver worked with no issues.  I know its not Kubuntu, but I hope it helps.

I also have this idea, that after installation issue could be solved in easy way. Thank you for your answer.

---

### Post by inportb on 2008-10-17
It should be the same on Kubuntu, except you would not use Synaptic. Also, you might be able to get it working on a live session with a bit of cleverness.

---

### Post by Zlatan on 2008-10-17
> **inportb said:**
> ...Also, you might be able to get it working on a live session with a bit of cleverness.

Explain please.

---

### Post by rondackcpu on 2008-10-17
There's a great howto post by "mazza558".  Works every time from hardy and intrepid.  Try this link, or search on "mazza558".  He posts a lot, so it's a ways down the search return.  Date of post is March 2008.

<http://ubuntuforums.org/showthread.php?t=734003&highlight=mazza558>

CRS

---

### Post by Zlatan on 2008-10-17
> **rondackcpu said:**
> There's a great howto post by "mazza558".  Works every time from hardy and intrepid.  Try this link, or search on "mazza558".  He posts a lot, so it's a ways down the search return.  Date of post is March 2008.

<http://ubuntuforums.org/showthread.php?t=734003&highlight=mazza558>

CRS

yeah, the post is great, but in Hardy wireless works directly after enabling restricted driver in GUI

---

### Post by lowlymarine on 2008-10-17
Try running this command in a terminal:
```
sudo dpkg-reconfigure b43-fwcutter
```
Should present you with the dialogue to set it up, after which you can enable the b43 driver without issue.   At least it worked on my Gateway 7422GX with BCM4308 wireless.

---

### Post by Zlatan on 2008-10-17
> **lowlymarine said:**
> Try running this command in a terminal:
```
sudo dpkg-reconfigure b43-fwcutter
```
Should present you with the dialogue to set it up, after which you can enable the b43 driver without issue.   At least it worked on my Gateway 7422GX with BCM4308 wireless.

Than you, will try that if it will be needed after install. Have a nice weekend:)

---

### Post by crazyness003 on 2008-10-17
I had the same problem (only i was using Ubuntu instead of Kubuntu...and i was in 64bit) with Intrepid. I also reinstalled/reconfigured repeatedly but nothing seemed to work. 
I actually got it up and running by using network manager itself. 
What i did was disable wireless. Restart then enabled it. and Bam, i got wireless. I know weird.
I dont know how Kubuntu would fare in the endeavor.

---

