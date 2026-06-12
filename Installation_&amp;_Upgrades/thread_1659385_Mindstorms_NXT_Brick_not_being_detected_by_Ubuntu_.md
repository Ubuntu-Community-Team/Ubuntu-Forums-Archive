---
title: "Mindstorms NXT Brick not being detected by Ubuntu Laptop via USB"
date: 2011-01-04
forum: Installation &amp; Upgrades
---

### Post by abcde13 on 2011-01-04
Alright guys, I have come to all you experts on Ubuntu as a last resort because I have exhausted all other attempts at my problem.

This is under *Installation & Upgrades* because I think I might need to install some missing packages or something...

I am trying to run NXT ROS on my Ubuntu 10.10 laptop, with the NXT Brick connected via USB. I go through this process: [http://www.ros.org/wiki/nxt/Installation](http://www.ros.org/wiki/nxt/Installation). I go through all the installation and rosmakes and all correctly, because it says that all the packages are built with 0 failures. However, when I run **rosrun nxt_python touch_sensor_test.py**, the 
**nxt.locator.BrickNotFoundError** is raised. Typical, the NXT ROS documentation says. Just make sure you configuration settings are right. Which I have checked multiple times. They are.

Now for the hardcore checking. I realize my NXT Brick hasn't popped up on the desktop. I have PyUSB installed, and I know it detects some connection because my terminal doesn't print **"No USB or Bluetooth connection detected"** I run the lsusb and I see the list of USB devices. I see my thumb drive by **Hewlett Packard**, which I put in as a test to check it wasn't my USB ports that were the problem. However, I do not see anything remotely close to **Mindstorms NXT** by the **LEGO Group**
So now I think it either a) doesn't know what the connection is or b) doesn't know there is a connection. I don't think(or don't like) b) because of before; it doesn't print that error statement. 

I also tried manual mounting; didn't work either.

I know this was a flurry of information, and I am sorry. I love Ubuntu 10.10, and I don't want this little mishap to get in the way. If you think I ran any of the commands in the wrong order or way, or think I misinterpreted the output, I will gladly run and post them again.

I am not next to my Ubuntu Laptop however, as I am actually doing homework. However, when I get the time, I will give the laptop model and settings if asked, but be patient with me, my responses might be slow. And for the same reason, I wasn't able to copy and paste those initial code i/o results. But any help, whether or not it fixes my problem, that increases my skills as a Ubuntu user, is greatly appreciated. Thanks

---

