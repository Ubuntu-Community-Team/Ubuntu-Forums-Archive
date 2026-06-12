---
title: "Graphics driver acting up"
date: 2010-12-20
forum: Installation &amp; Upgrades
---

### Post by esser on 2010-12-20
Hello
I just updated alot of stuff in ubuntu including the kernel. Now it will only run in low-graphics mode. I have tried reconfiguring, but got no result.
I read somewhere that it helps reinstalling the driver, but i cant do it through ubuntus build-in driver-updater, since it claims that its working and up-to-date.
The real question is, how to use the .run file that i downloaded from nvidia. What is the terminal command?

---

### Post by iosuna86 on 2010-12-20
I have been having trouble with NVIDIA graphics cards too.

I found a solution for Ubuntu to run smoothly with NVIDIA's website drivers.

Here is what I did:

1. I downloaded the driver from NVIDIA's website (NVIDIA-Linux-x86-260.19.29.run)

2. Then, I opened a terminal

        ```
sudo apt-get --purge remove xserver-xorg-video-nouveau 
```

3. Then I hit CTRL+ALT+F1 in order to switch to command-line.

4. Typed: 
     
     ```
sudo init 3 
```
     
     ```
sudo stop gdm 
```

5. Then I installed the drivers manually.

I went to the folder in which I had downloaded the drivers, which was Downloads

     ```
cd /home/--username--/Downloads 
```

Then I run the package

     ```
sudo sh NVIDIA-Linux-x86-260.19.29.run 
```

or if you don't have any other .run files in that folder
     
     ```
sudo sh *.run 
```

6. The NVIDIA driver installation will start, you will have to  accept the license, then say Yes to something regarding the X server. It  will also try to purge your conflicting/previous NVIDIA drivers.

---

