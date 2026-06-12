---
title: "Installing NVIDIA Driver from Command Line"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by user0182 on 2007-09-28
Hi,

I have just installed Ubuntu from the alternate CD to my laptop, but now that I have, Xserver won't start. When I boot up my computer, I just get the command line. I thought that this could be due to a driver problem, therefore I am currently downloading a Linux nVidia GeForce 8400M GT GPU driver, using my Windows partition.

My question is: once I have downloaded the driver to my Windows partition, how would I install the driver using the Ubuntu command line. Am I able to use a flash drive or sould I use a CD?

btw - When I boot up my laptop, the first error message I recieve is "[0.444086] PCI: Failed to allocate mem resource #6:20000@e0000000 for 0000:01:00.0" could someone please explain this error message to me.


Thank You (in advance),

user0182

---

### Post by charles.g.moore on 2007-09-28
What kind of lappy is it?

---

### Post by Pumalite on 2007-09-28
Can you get to the Desktop or not? Do you end up with a blank screen?

---

### Post by user0182 on 2007-09-28
No, I cannot get to the desktop. I just get an error message stating the Xserver cannot run and then I am sent straight to the command line.

btw - It's a Sony AR Series laptop.

---

### Post by Pumalite on 2007-09-28
At the command line:
sudo dpkg-reconfigure xserver-xorg, accept most defaults, choose 'vesa' as the driver, then: startx

---

### Post by user0182 on 2007-09-28
Thanx Pumalite, that was awesome. Ubuntu is running perfectly, for now :-).

---

### Post by Pumalite on 2007-09-29
You are welcome. Happy Ubuntuing!

---

