---
title: "Udevd eats 100% CPU on Jaunty Alpha 6 Upgrade"
date: 2009-03-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by vidgc on 2009-03-22
Hey all,
I recently upgraded to Jaunty alpha 6.  However, boot now takes longer than ever, and upon logging in, about 4 seperate udevd processes now hog up 100% cpu.

I did a search and found the evms related solution, but I don't have evms installed.

killall udevd solves it, but obviously that's not exactly an ideal solution :-P

In syslog:
```
Mar 22 02:31:27 UbuntuLaptopD udevd[6487]: root privileges required 
Mar 22 02:31:31 UbuntuLaptopD udevd[6491]: bind failed: Address already in use 
Mar 22 02:31:31 UbuntuLaptopD udevd[6491]: error binding control socket, seems udevd is already running 
Mar 22 02:31:36 UbuntuLaptopD udevd[6495]: bind failed: Address already in use 
Mar 22 02:31:36 UbuntuLaptopD udevd[6495]: error binding control socket, seems udevd is already running 
Mar 22 02:31:43 UbuntuLaptopD udevd[6499]: bind failed: Address already in use 
Mar 22 02:31:43 UbuntuLaptopD udevd[6499]: error binding control socket, seems udevd is already running 
Mar 22 02:31:51 UbuntuLaptopD udevd[6503]: bind failed: Address already in use 
Mar 22 02:31:51 UbuntuLaptopD udevd[6503]: error binding control socket, seems udevd is already running 
Mar 22 02:31:53 UbuntuLaptopD udevd[6507]: bind failed: Address already in use 
Mar 22 02:31:53 UbuntuLaptopD udevd[6507]: error binding control socket, seems udevd is already running 
Mar 22 02:31:55 UbuntuLaptopD udevd[6508]: bind failed: Address already in use 
Mar 22 02:31:55 UbuntuLaptopD udevd[6508]: error binding control socket, seems udevd is already running 
```
Why would it be starting that many times?

I've attached my bootchart image if it's any help.

Thanks!

---

### Post by Rocket2DMn on 2009-03-22
Moved to Jaunty Jackalope Testing and Discussion.

---

