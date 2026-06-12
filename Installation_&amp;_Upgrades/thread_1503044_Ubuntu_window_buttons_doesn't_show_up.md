---
title: "Ubuntu window buttons doesn't show up"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by dineshbabumm on 2010-06-06
Hello everyone,

I just upgraded to 10.04 from 9.10 and I ran into few issues. My laptop is Dell Vostro 1520. I am using 64 bit ubuntu. I never had any of the following issue with 9.10. 

<EDIT> I had few issues resolved after posting this. This is the only one left unsolved <END EDIT>
3. There is some issue with wifi too. It connects to the internet properly and shows connection established. But I am not getting any response when I ping and hence not able to browse. But I was able to get response when I use ethernet (wired connection) and I am able to browse. No issues with wifi card as my wifi is working properly from Windows.

<EDIT> The following issues got resolved after I posted them <END EDIT>> 
1. The 'close, minimize, maximize' buttons are not showing up altogether (no they are not in left hand side). 

2. Also they don't show up in the task bar below. So I am not able to close the application in traditional way. I close them using ctrl+q or ctrl+w etc.


4. And the workspace, I am not able to edit the preference and set it to 4 or the number of workspace I want. It says it failed to load or some similar error. 

5. When I click on 'show desktop' icon, it says it is not configured or some thing similar. 
 
Any suggestions how to get rid of this problem is highly appreciated. Thanks a lot for patiently reading till this and hope that I can get some help in resolving this. :)

---

### Post by dineshbabumm on 2010-06-06
> **dineshbabumm said:**
> Hello everyone,
1. The 'close, minimize, maximize' buttons are not showing up altogether (no they are not in left hand side). 

2. Also they don't show up in the task bar below. So I am not able to close the application in traditional way. I close them using ctrl+q or ctrl+w etc. 

4. And the workspace, I am not able to edit the preference and set it to 4 or the number of workspace I want. It says it failed to load or some similar error. 

5. When I click on 'show desktop' icon, it says it is not configured or some thing similar. 

Okay guys, after posting this issue I tried some thing my friend suggested. He suggested to change settings in compiz. I just typed compiz in the terminal and it didn't loaded. But all the above problems got resolved! I hardly have any idea how. But it leaves me with one unsolved problem. 
> 
3. There is some issue with wifi too. It connects to the internet properly and shows connection established. But I am not getting any response when I ping and hence not able to browse. But I was able to get response when I use ethernet (wired connection) and I am able to browse. No issues with wifi card as my wifi is working properly from Windows.

I am yet to fix the wifi problem. Some one please help me fixing it. Had to come to windows again to post it :(

---

### Post by dineshbabumm on 2010-06-06
Okay one more update:

compiz seems to be a temporary solution. When I restarted, it went back to the same old state. I had to type compiz to restore the normal state. And while typing compiz & in terminal, I get the following error message:

"dinesh@dinesh-laptop:~$ WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
Starting gtk-window-decorator
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!"

Also compiz doesn't get invoked.

The wifi problem still persists :(

ifconfig output if that will help:

> dinesh@dinesh-laptop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:24:e8:dd:f2:c7  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:e8ff:fedd:f2c7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22050 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15674 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29890171 (29.8 MB)  TX bytes:1679630 (1.6 MB)
          Interrupt:30 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 0c:60:76:09:29:6e  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e60:76ff:fe09:296e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:47 errors:0 dropped:0 overruns:0 frame:12160
          TX packets:60 errors:8 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15104 (15.1 KB)  TX bytes:10512 (10.5 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1696 (1.6 KB)  TX bytes:1696 (1.6 KB)



---

