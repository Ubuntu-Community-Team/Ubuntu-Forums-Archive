---
title: "Installation Nightmare"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by RickSimnett on 2010-02-26
Hello,
I recently purchased an intel atom d510 mobo + 4gigs of ram to build a small web server out of. I am, and have been a loyal ubuntu user since version 6, and have been able to tackle most problems head on via google and a bit of persistance, however, I have run straight into a wall with my current problem.

I am trying to install ubuntu 8.04 LTS onto the new machine. Everything goes fine, except for the fact that it DOES NOT find or detect the network card in the machine (realtek 8111DL). So I get the red warning screen during install, and really havent been able to progress further. I found a driver from realtek, that I think will work, except I cannot get it to compile due to missing modules.

The driver i found is here:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)

I have downloaded it, installed make, as well as build-essentials but it is still missing a module at /lib/modules/linux-2.6 < yada yada>

My question is this can someone explain to me either A) to get the driver to work for the NIC without compiling, or B) someone explain to me how to get the missing files so I can build the driver myself.

Any help anyone can lend is greatly appreciated.

Thanks,
Rick

---

### Post by RickSimnett on 2010-02-26
I have also applied the new bios from intel, as I found another thread on here saying that it was needed. There was no change when I applied it, and my bios was already current.

---

### Post by pbpersson on 2010-02-26
I know this is the wrong answer but I feel life is too short and my patience too non-existent to spend hours or days on these sorts of things so I grab another NIC card from my parts bin and.....problem solved.

---

### Post by zcrafts on 2010-02-26
Hello,

I am also struggling to get it installed and test it on my local machine..Searching for a helping hand :(

---

### Post by RickSimnett on 2010-02-26
Ok guys. Well so far no dice. I have finally successfully built the driver, ubuntu loads it, but refuses to grab an ip from DHCP. If i statically set the ip, it wont connect. The key to getting the realtek driver to build was to install:

apt-get install linux-headers-$(uname -r)[B]

and then to just run the autorun.sh file included with it.

So I guess now I have a driver, but still no luck getting it to work.

I would post the lshw -C net, and lspci output, but since I cannot copy and paste, it seems like a bit too much work at the moment. For the record, both do report finding the proper driver now.

Thanks,
Rick
[/B]

---

### Post by snowpine on 2010-02-26
Hi Rick, I would recommend trying a Live CD of the current Ubuntu release (9.10) to see if it supports your card out of the box. As you probably know, the atom d510 is a brand new chipset that did not exist in April 2008 when Hardy was released. Therefore, it is temorially impossible for 8.04 to fully support your hardware. :) I understand you may have your reasons for using 8.04 but it is worth at least experimenting with the current version if 8.04 is a "nightmare" for you, do you agree?

---

### Post by RickSimnett on 2010-02-26
SUCCESS!

I got it to work guys. The problem is simple when you get right down to it. In 8.04, for whatever reason it forces the r8169 driver onto the card (it doesnt work). So the solution is this:

1. Go to realtek and download the driver:[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)

2. extract the file from realtek.

3. install all the dependencies: apt-get install build-essential linux-headers-$(uname -r)[B]

4. navigate into the directory for the new realtek driver, and run autorun.sh

5. upon successful completion of the driver build reboot, and then log back in

6. run the following to make sure you see the two drivers r8168 and r8169: lsmod | grep r816

7. now you have to disable the r8169 driver, so go to /etc/modprobe.d

8. [/B]sudo touch blacklist-network

9. nano blacklist-network and  add "blacklist r8169" to the file, save the file

10. make the removal permanent (so it survives reboots) sudo update-initramfs -u 

11. reboot

12. VOILA! When the system reboots, the network card seems to start working again.


I hope this helps someone else out there, this little task took me the better part of 2 days to figure out, but it works!

Thanks,
Rick

---

### Post by Sef on 2010-02-26
Thank you Rick typing the solution up in way that is easy for others to follow.

---

### Post by kazooless on 2011-01-22
Not sure if anyone will see this so much later than the original "Success!" post, but...

How are you running apt-get and downloading the driver if your network card doesn't work? Isn't this sort of the chicken and the egg?

kazooless

---

### Post by kazooless on 2011-01-22
For anyone searching for this (like I did), here is the answer to my question:

The server install CD actually has the build-essential and linux-headers... we need to compile the driver. 

> apt-cdrom add

Then use aptitude instead of apt-get (this worked for me. Maybe apt-get still works)

---

