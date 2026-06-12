---
title: "100 CPU usage after Edgy upgrade"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by ggv6 on 2006-10-31
Hi,

I upgraded using the recommended method to edgy eft from dapper drake. My system boots ok but once it starts it seems very slow. The CPU usage is 100% when I look at system monitor but can't see any process taking more than 5%. I also tried top but get same results.

Has anyone had the same problem? Any suggestions?

Thanks

---

### Post by Dinerty on 2006-10-31
Are you sure nautilus isnt using it?

---

### Post by ggv6 on 2006-10-31
yes I am running nothing at all. Its only the desktop

---

### Post by towsonu2003 on 2006-10-31
> **ggv6 said:**
> The CPU usage is 100% when I look at system monitor but can't see any process taking more than 5%.
make sure you check the View>All Processes option.

---

### Post by jgcamp99 on 2006-10-31
> **towsonu2003 said:**
> make sure you check the View>All Processes option.

I have a very similar issue and yes, all processes is checked off and displayed. The panel graphical display fluctuates wildly between 8 and 100%, yet when the window is opened to the desktop, nothing (no single process) spikes over 14-15%. There are really only three processes that show activity, 2 of which are system monitor related processes gnome system monitor and multiload-applet-2, the other is Xorg, even while internet surfing and predominantly posting to Ubuntu forum threads like this response.

---

### Post by reubano on 2006-11-03
> **ggv6 said:**
> Hi,

I upgraded using the recommended method to edgy eft from dapper drake. My system boots ok but once it starts it seems very slow. The CPU usage is 100% when I look at system monitor but can't see any process taking more than 5%. I also tried top but get same results.

Has anyone had the same problem? Any suggestions?

Thanks
same thing here. the sys monitor processes add up to less than 20% yet the resource graph constantly shows 100% usage. I did a clean install rather than an upgrade also.

reub

---

### Post by towsonu2003 on 2006-11-03
when you suspect you're getting 100% cpu usage, issue this and analyze the output:
```
ps aux
```

---

### Post by gerkin on 2006-11-03
I´m having the same issue with banshee using up to 100% CPU at times??

---

### Post by reubano on 2006-11-03
> **reubano said:**
> same thing here. the sys monitor processes add up to less than 20% yet the resource graph constantly shows 100% usage. I did a clean install rather than an upgrade also.

reub

Fixed it! It turned out to be acroread. I simply killed the process and I have been back to normal since. I also read in a few other threads and there seems to be a bug in the beagled deamon. So check that too if neone is still having problems. If that is the cause, be sure to disable the beagled startup program in the sessions menu in addition to killing the process.

---

### Post by ggv6 on 2006-11-05
Hi

I tried
ps aux

When I add up it should only take about 10% but the CPU shows 100% and the computer is very slow even moving the mouse. I cannot see any processes that would cause the problem.

I am using an intel 3Ghz p4 with 512 Ram and Nvidia 5500.

I read somewhere that may have to install the 686 kernel. Would this be appropriate. Any ideas?

---

### Post by towsonu2003 on 2006-11-05
> **ggv6 said:**
> Hi

I tried
ps aux

When I add up it should only take about 10% but the CPU shows 100% and the computer is very slow even moving the mouse. I cannot see any processes that would cause the problem.

I am using an intel 3Ghz p4 with 512 Ram and Nvidia 5500.

I read somewhere that may have to install the 686 kernel. Would this be appropriate. Any ideas?

I doubt 686 will fix it, but you can try :)

can you post the output of ps aux just when you get the %100 cpu? 

also, if you have time, check out conky. it is a great way to monitor what your computer is doing. I am attaching my own configuration file for conky, in case you wanna try. See this post for a conky howto: [http://www.ubuntuforums.org/showthread.php?t=205865&highlight=conky+howto](http://www.ubuntuforums.org/showthread.php?t=205865&highlight=conky+howto)

in there, skip the first 2 steps and do ```
sudo apt-get install conky
``` instead. you can use the file I attached for the step 4. 

Let me also attach what it looks like on my desktop. 

It may or maynot be able to show you (in real time) what is causing the 100% cpu usage.

---

