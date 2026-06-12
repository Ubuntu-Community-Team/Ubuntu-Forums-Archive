---
title: "reinstalling curiosity"
date: 2010-09-11
forum: Installation &amp; Upgrades
---

### Post by producer on 2010-09-11
Hi,
I have been having dome troubles with what I *think* is a piece of malware deliberately targeted at my system.  Be that as it may, I had repartitioned my 500 GB harddrive and now the install partitioner and G-Perted all see only 250 GB on the drive.  Part of my desire to reinstall is to once again access all 500 GB. Does anyone know how I may do this?) ):P

---

### Post by producer on 2010-09-11
By the way it's 10.04.

---

### Post by 23dornot23d on 2010-09-11
What have you tried to do so far ......

This is where I would start - do a quick check and just look at the disk ...... 
post a screenshot if you would .... too ...... just so we can see what it shows you.

apt-get install gparted

gparted

There is a useful thing called [_bootchart_]("http://www.bootchart.org/") too ..... when that is installed it notes all the hidden process's running at boot if you think
something is running that should not be ..... you may be able to see it on here ...... 
(apt-get install bootchart)
and lists them for you to see on a chart ....... that it writes to the var/log/bootchart/     directory as a .png file
might also be useful if you think you have a problem with malaware .....
______________________________________
If there are problems with the disk structure this can help to fix it .......

apt-get install testdisk

testdisk

**[COLOR=Red]Just have a quick look at the layout of the disk first ...... but do not alter anything .......[/COLOR]**

The program allows you to Analyze the disk ...... but do not alter it until you are sure that all is well.

cut and paste the results of that here too ..... if you would please.

It also allows you to backup and makes a copy of the partition table ...... (might be worth doing that too)

Just post the results so that others can see ......

---

### Post by producer on 2010-09-11
I think this is the photo that I am attaching  it's called screenshot.  I hope I did that correctly.

---

### Post by 23dornot23d on 2010-09-11
You did that just great ......

What makes you think its 500 Gig ?

here is a link to the model name .. that appears on the gparted 
**WD2500AAKS** capacity 232.88 Gig

... I just [_searched for and the one I found is 250 Gig_]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136161")

There are others though ..... [Here's a 500 Gig ..... ]("http://www.wdc.com/en/products/products.asp?driveid=301")

its code is **WD5000AAKS**

So I would say yours is 250 Gig ......

---

### Post by producer on 2010-09-11
Maybe I'm getting old, I just saw that too, but I've always thought I had a 500 GB drive,  Maybe the salesperson told me that.  OK I'm going to get another one as a secondary.  Wait a minute,  I did have an external drive that was 500 GB and maybe I did a mind transference thing thinking this one was also.  <sigh>
Sorry if I wasted your time.  You've been most kind... I wonder whatever happened to that external drive... it must be around here somewhere.
Thanks.

---

### Post by 23dornot23d on 2010-09-11
Ok your welcome ..... I hope you find it ...... ):P

---

