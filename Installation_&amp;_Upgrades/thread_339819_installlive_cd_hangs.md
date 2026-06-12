---
title: "install/live cd hangs"
date: 2007-01-16
forum: Installation &amp; Upgrades
---

### Post by coakley on 2007-01-16
I have wandered these forums for the last several days to no avail.

I am attempting to install Dapper (either Ubuntu or Kubuntu) on a Dell Optiplex 320N. After the system boots the installation kernel from the initial splash screen and goes to "Mount the root partition" (which at this stage would be a ramdisk, I believe) and everything stops for about a minute and then the system dies. 

This same disk was used to install 6 Dell systems a few months ago and I used it to install on a BYO system with a Shuttle mainboard yesterday, so I know it works. I tried to install SuSE 10.1 which was a little more informative. It said that it could not locate the install disk. It says this after booting from that self-same disk. I also unsuccessfully tried to install Xandros.

Obviously there is a problem between the kernel and the IDE/SATA/PATA setup on the Dell mainboard. I have seen many, many other posts in this forum that revolve around this same issue - not necessarily with a Dell but with recent motherboard configurations.

While this failure may well be the fault of whoever built the mainboard for Dell, I think it is a Linux problem now. Is there a workaround? A bug fix? An update in progress?

---

### Post by derby007 on 2007-01-17
Thismightn't be your problem, but Dell's come with 3 primary partitions, so your 4th will have to be an extended partition & then Ubuntu put on a logical partition.....ignore this if it doesnt apply...

---

### Post by coakley on 2007-01-19
Actually, this Dell Optiplex is a 320N so the drive comes totally unformatted. After several hours with Dell tech support and a bit of time with SuSE/Novell, I had in hand over 20 boot options to try. Many of them changed the problem, but none solved the problem.

In the long run, I could mount either the hard drive or the CD/DVD-RW but never both at the same time. It seems that the IDE/SATA/PATA controller chips on the mainboard do not get along with the Linux or BSD kernels. In fact, you also could not use both with the FreeDOS that Dell shipped with the computers.

Dell finally admitted that they shipped computers with no pre-loaded operating system onto which no functional operating system could be loaded. I have returned the machines for credit.

This problem is not unique to these Dell Optiplex machines. In trying to find a solution on this and other forums, I saw posts about many other machines with this same problem. Most of those posters are relatively new to Linux and will likely end up running Vista out of desperation. (Windows can see both drives. Both work but both seem to run slower.)

As for me, I'm calling eracks.com.

---

### Post by sonam on 2008-04-14
"Dell finally admitted that they shipped computers with no pre-loaded operating system onto which no functional operating system could be loaded. I have returned the machines for credit."

Oh no! I just bought the same system and facing the same problem. 

"This problem is not unique to these Dell Optiplex machines. In trying to find a solution on this and other forums, I saw posts about many other machines with this same problem. Most of those posters are relatively new to Linux and will likely end up running Vista out of desperation. (Windows can see both drives. Both work but both seem to run slower.)"

I am one of them... I am  on the  verge of throwing DELL  out the window or throw Ubuntu CDs and use vista. 

the issue with Linux is if it works it works perfectly....  if you have a problem you get stuck for a long long time and still no solution........

---

