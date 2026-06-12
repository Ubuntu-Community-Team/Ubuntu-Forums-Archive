---
title: "Can anyone run jack? :S"
date: 2009-04-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by olskar on 2009-04-19
Hi,

I tried running jack trough qjackctl today in Jaunty to record some songs and realized I couldn't :( Can anyone check if they are able to run jack?

Just install qjackctl, run it and press start.

I get:
```
22:03:50.206 Statistics reset.
22:03:50.233 ALSA connection graph change.
22:03:50.429 ALSA connection change.
22:03:52.110 Startup script...
22:03:52.111 artsshell -q terminate
sh: artsshell: not found
22:03:52.519 Startup script terminated with exit status=32512.
22:03:52.520 JACK is starting...
22:03:52.521 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2
22:03:52.528 JACK was started with PID=9184.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -699230480, from thread -699230480] (1: Operation not permitted)
cannot create engine
22:03:52.572 JACK was stopped successfully.
22:03:52.573 Post-shutdown script...
22:03:52.574 killall jackd
jackd: no process killed
22:03:52.998 Post-shutdown script terminated with exit status=256.
22:03:54.702 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```


Edit 1: It works when running as root but I guess that is not adviceable? (And wasn't needed before)

---

### Post by markbuntu on 2009-04-19
Jack works for me but the rt kernel does not boot so no rt for me. Did you install jack over ubuntu?

---

### Post by olskar on 2009-04-19
> **markbuntu said:**
> Jack works for me but the rt kernel does not boot so no rt for me. Did you install jack over ubuntu?

Yes, without rt kernel just generic, same problem on two different computers

---

### Post by zenithdave on 2009-04-19
Confirmed ! as it was reporting FIFO buffer problems i checked  Force 16bit and it started working, try that.
But sadly Jack has been shelved. On the very few times i did get it to work by tweaking the GUI it was a fast as ASIO !

---

### Post by olskar on 2009-04-20
> **zenithdave said:**
> Confirmed ! as it was reporting FIFO buffer problems i checked  Force 16bit and it started working, try that.
But sadly Jack has been shelved. On the very few times i did get it to work by tweaking the GUI it was a fast as ASIO !

That and unchecking realtime made it start for me :) Perhaps it's worth a try installing the realtime kernel again, I had no success with that in Intrepid

---

### Post by eric71 on 2009-04-20
Don't forget to update the etc/security/limits.conf file (search google with "limits" and "rtprio" and you'll find suggestions). You also need to create an "audio" group and put yourself in it to take advantage of these limits.conf changes. It doesn't seem that Jaunty comes with this as default. Once you restart after making these changes, Jack will start in RT mode. 

One problem I had in with the jackd included with Jaunty was getting disconnected from from jack too often. This was using Reaper with wineasio, and may have been a wineasio problem. But increasing "Timeout" setting in QJackCtl to 8500 ms solved that problem, a useful tip from one of the helpful people at the reaper forum.

Edit: I was too lazy to search for  the limits.conf information myself, but felt guilty after posting :) So here is the information from Ubuntustudio:

"Real-Time Support

After you've got the kernel you still need to set up real-time access for your applications.

All you have to do for this is give your audio group permissions to access the rtprio, nice, and memlock limits. To do this, you just need to run these commands, which will add some lines to the file /etc/security/limits.conf:

 sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'
 sudo su -c 'echo @audio - nice -19 >> /etc/security/limits.conf'
 sudo su -c 'echo @audio - memlock unlimited >> /etc/security/limits.conf'

These value are suggested by [http://jackaudio.org/faq](http://jackaudio.org/faq). The memlock line determines how much of your memory can be locked by audio processes. Some recommend setting this as half of your total memory (RAM, in KB). See Florian Paul Schmidt's page.

In Intrepid and Januty Beta, you have to create a user group named "audio" and add your user name (and other users of the workstation if needed) to this group. You can do that very simply in "System / Administration / User Group".

Restart the workstation and it is ok."

---

### Post by barisurum on 2009-04-20
Thanks eric71 for your very useful tips. JACK indeed works with the generic kernel! It works with my usb-audio fluently at 5ms latency. I will try with ardour soon. :D

---

### Post by PC_load_letter on 2009-04-20
Jack has been shelved!!!!!!!? So is there a replacement in sight, or is this it for Linux audio w/ minimum latency?

---

### Post by PC_load_letter on 2009-04-20
I couldn't find anything that says development of Jack has stopped, or that the project was abandoned. On the contrary, it seems that the devs are developing the next version Jack2, and the latest release has been just released last month. Read it all here: [http://jackaudio.org/](http://jackaudio.org/)

---

