---
title: "Have I done this right?"
date: 2015-08-22
forum: Installation &amp; Upgrades
---

### Post by thetexan on 2015-08-22
Anticipating installing Ubuntu I used paragon to set up three partitions dedicated to Ubuntu. This is on an Intel machine that already has windows 7 on it.

---

### Post by thetexan on 2015-08-22
Anticipating installing Ubuntu I used paragon to set up three partitions dedicated to Ubuntu. This is on an Intel machine that already has windows 7 on it. 

Mine partition is 30g for the root (/). Another is 18g for a swap disk (I have 8g of ram). And a third is about 50g for /home for various stuff. 

Now...do I install Ubuntu and assign each of these to there respective mounts during installation?

I am an absolute noob. Please help. 

Tex

---

### Post by howefield on 2015-08-22
Wow, too much information....

How can anyone give you a decent answer with the paucity of detail that you have provided ?

---

### Post by matt_symes on 2015-08-22
Hi

To expand on howfield's comment, more information is required such as the size of the partitions and the size of the drive.

Always supply as much information as you can, as consicely as possible for the best support.

Edit: were threads merged here ?

Kind regards

---

### Post by TheFu on 2015-08-22
All those partitions are a little big.
/ - 25G
swap - either 4G if you don't hibernate or 8.1G if you do. Anything more is a waste. The old rules of thumb don't apply any more.
/home - 50G seems like WAY too much. I suppose if you are a java dev, that could be fine.

I'm a perl webapp dev and have 15G total for my development machine - that's /home, /, and swap.  I always keep media files elsewhere - never /home - usually on the network somewhere. Keeping them separate makes nightly, versioned, backups much more efficient. Media files don't change often and don't need to be versioned. OTOH, my libreoffice designs or emails or diagrams do need to be versioned. Plus having all the settings for the different programs I run on the system versioned in daily backups means if something bad happens, I can easily role the ~/.config/ back 1 day or 3 weeks or 2 months - until everything works again. Since I've settled on one environment, that hasn't been necessary, but most people like to try multiple different DEs to pick the one they prefer.

If you are happy, keep the / and /home as it is, but definitely reduce swap. By the time any desktop uses 8G of swap, the system will be painfully slow.  However, 4G is really the minimum swap these days, just because modern browsers will easily each 2G.

Just so you see I'm not making these number up:
```
$ uptime
 18:09:23 up 7 days, 11:13,  3 users,  load average: 6.17, 6.69, 6.73

$ free -m
             total       used       free     shared    buffers     cached
Mem:          7975       7857        117          0          9       6685
-/+ buffers/cache:       1162       6813
Swap:         6579       1430       5149
```
The box has been up for a week and isn't using 1.5G of swap.

And a smaller machine (my main desktop/dev box):
```
$ uptime
 18:10:48 up 7 days, 11:42,  6 users,  load average: 0.16, 0.17, 0.17

$ free -m
             total       used       free     shared    buffers     cached
Mem:          3053       2804        249          8        395        793
-/+ buffers/cache:       1615       1438
Swap:         3003        200       2803
```

And a bigger machine:
```
$ uptime
 18:13:29 up 21 days,  6:33,  2 users,  load average: 0.62, 0.63, 0.75

$ free -m
             total       used       free     shared    buffers     cached
Mem:         16040      13292       2747          3       2059       1514
-/+ buffers/cache:       9718       6321
Swap:        11632       2802       8830

```
See the swap use on each?  2G isn't enough, so 4G is a conservative amount for most people. Of course, there are workloads where more swap would be needed and if you don't have enough swap, it can be bad - like the machine will lock up.
Why show the uptime?  Just so you know these aren't freshly rebooted machines that haven't been running tasks for a week or 3.  

Actually, I have some performance graphs for swap for all these machines for the last year. I'll take a look at those.
* There is a clear pattern for swap use on the 16G machine (which is also the backup server here) - every night when backups run, the swap jumps to 4.9G. The rest of the time, it sits around 4.43G.
* On the 8G RAM machine, peak swap use this month was 1.4G.

Too much swap is a waste. That's the synopsis.

---

### Post by howefield on 2015-08-22
Threads merged.

---

### Post by thetexan on 2015-08-22
Ok I'll adjust those numbers. 
my main question is have I done the partitioning correctly?  Specifically....I just assign those during installation?

---

### Post by TheFu on 2015-08-22
> **thetexan said:**
> Ok I'll adjust those numbers. 
my main question is have I done the partitioning correctly?  Specifically....I just assign those during installation?

There isn't just 1 way to partition stuff.  Linux is extremely flexible and that goes to partitioning or even just laying out a disk.  For someone new, **it is probably fine. **  If the disk is GPT, you get a little more flexibility. If it is MBR/MSDOS formated, there are some caveats and important limitation to consider.

As you gain expertise, you might want to use LVM which is like having dynamic partitions that don't require reboots to change. There are other features that LVM supports, but with these extra capabilities there are extra complexities.

Boot into a live-CD environment (*Try Ubuntu*), and please post the output from **sudo parted -l**, then we can probably provide better advice.

---

### Post by yancek on 2015-08-23
The size and number of partitions is basically up to the user, what s/he wants and the drive space available.  You can create the partitions in windows but you will need to format them with a Linux filesystem during the install and you will see that option if you pay attention.  A default windows system is incapable of formatting with a Linux filesystem.  If you want to create a separate /home partition during the install, I believe you will need to select the Manual Installation Type which is called "Something Else" in Ubuntu.  I've never actually used the Install Alongside option so I'm not sure, maybe you can select partitions.  You can definitely do it with the Something Else option.

---

