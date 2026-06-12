---
title: "Fresh 12.04 install freezes"
date: 2012-05-05
forum: Installation &amp; Upgrades
---

### Post by GrindcoreVlad on 2012-05-05
Hi,

I have a fresh install of Ubuntu 12.04 but at least once a day I get a total freeze. Everything stops working and I get that annoying repetitive sound. 

This never happened to me before in 11.10 (on my first Ubuntu install).

I searched the internet for this problem but as close as I got, was a thread talking about how nVidia drivers may be the cause.

I'm a beginner at using Ubuntu so I don't know where to start detecting what causes this problem and how to solve it. Can someone please guide me? (BTW 5min ago just got another freeze #-o)

---

### Post by Mark S Bilk on 2012-05-06
"I have a fresh install of Ubuntu 12.04 but at least once a day I get a total freeze. 
Everything stops working and I get that annoying repetitive sound."

I am humble Suse user visiting, but I'm getting great assistance with details from friend
in chat who is running Ubuntu!

Your freeze is rather infrequent for computer operating at billions of instructions per second.
Could be bad memory.  Maybe didn't cause crash with previous OS because bad memory
location wasn't used for anything critical then.

Suggest at next freeze, see if  you can reach a text terminal by typing Ctrl-Alt-F3 and
logging in as yourself (not root).  If you can, have a look at kernel log:    /var/log/syslog
Use "less" command and look at end of that file -- see if any message is there indicating
cause of crash.   

If you can't reach text terminal after crash, look at that log file after you reboot.
Booting prints lots of messages in log, so look at message times and figure out
which entries (if any) came just before crash.

Also, run memory test program through one complete cycle, which may require ten hours or so.
Program is called memtest86+ and runs standalone -- not inside Linux.  You can get it
from here: [http://memtest.org/#downiso](http://memtest.org/#downiso)

Get bootable ISO file from exactly here:   [http://memtest.org/download/4.20/memtest86+-4.20.iso.zip](http://memtest.org/download/4.20/memtest86+-4.20.iso.zip)
Download that file and unzip it.  Resulting mt420.iso file is 1,839,104 bytes long.
Burn that onto a CD-R and then boot from it.
Should show text screen that indicates which of many tests it's running, and which area
of memory it's testing.  Let it cycle through all tests and all memory at least once.  
May take ten hours or so.

If you have bad memory -- and it does happen -- that test will tell you.
Good luck!

---

### Post by GrindcoreVlad on 2012-05-07
Thank you very much.

I will run the test memory program tomorrow while I'm at work so it can take as long as it's needed.
I will also check the logs file on my next freeze(this is exactly what I was looking for when I started the thread).

---

