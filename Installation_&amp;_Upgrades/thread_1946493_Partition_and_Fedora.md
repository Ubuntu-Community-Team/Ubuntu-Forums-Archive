---
title: "Partition and Fedora"
date: 2012-03-24
forum: Installation &amp; Upgrades
---

### Post by UltimateCat on 2012-03-24
Hi:p
I opened a terminal to check what my partition is formatted as using:
```
sudo fdisk -1

```
And the output looked something like this:

b<size> (512,1024,2048, or 4096)
Give sizes in sectors instead of cylinders
C Specify # of cylinders
H Specify # of heads
S Specify # of sectors per track

Didn't really understand this output.  I am just trying to look at my partition that is a dual boot: Ubuntu 10.04 along with Windows XP to see if I have 10GB available to install Fedora.

I went to [www.fedoraproject.org](www.fedoraproject.org) and it all looks good just not sure what or how to work with my partition first.

What do you recommend to prepare for and start the install process?

Help is always greatly appreciated:popcorn:Thanks in advance!

---

### Post by Old_Grey_Wolf on 2012-03-25
The fdisk command ends with the letter l and not the number 1.

---

### Post by UltimateCat on 2012-03-27
Thought it was a number 1 no wonder it looks like another language-

Thank You

---

### Post by Old_Grey_Wolf on 2012-03-29
It happens all the time :) The -l (letter l) means "**l**ist partition tables".

---

### Post by QIII on 2012-03-29
Just as an aside and slightly off topic, but...

Wow!  10GB for Fedora?  Tight fit if you plan to do much with it.

---

### Post by Old_Grey_Wolf on 2012-03-29
> **QIII said:**
> Just as an aside and slightly off topic, but...

Wow!  10GB for Fedora?  Tight fit if you plan to do much with it.

I think the OP is following the minimum requirements from the fedoraproject page linked to in the first post. 

Yes. It is a tight fit :)

If the OP uses YUM to install anything it will probably not work due to lack of disk space.

Sometimes the best lessons are learned the hard way :)

---

### Post by UltimateCat on 2012-04-03
I'm not looking forward to shrink/resize the Windows XP partition as I need like above:
```
765MB : 10GB for hard drive

```In the process of installation(Fedora) I might just delete Windows but my best friend might not like that; LOL

Fedora is available for USB but...I'm not the queen of formatting a usb; have to learn how to-  Now, Fedora is offered online w/o the install as a OS but I just can't seem to decide so I'm going to give this careful consideration with the use of good practices ( backup) before I make another move.

I'm only installing to complete the exercises in the Linux Certification textbook...if I like Fedora I might just keep it-

---

### Post by UltimateCat on 2012-04-11
I'm having trouble deciding on which approach to install Fedora.

I found that I could use PackageKit or Yum for formatting a USB

Don't know that much about Yum. 

Is Yum an application/program?

---

