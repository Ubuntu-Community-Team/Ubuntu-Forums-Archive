---
title: "Any way to globally disable IPv6 Jaunty?"
date: 2009-04-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by skymera on 2009-04-09
Yeah, i see IPv6 is built into the kernel so blacklisting IPv6 is useless.

I don't really feel like compiling my own damn kernel every time so I can have decent download speeds (I'm getting less than half speed 80KB/s!)

Considering Ubuntu targets user friendliness, this isn't a good start to 9.04

Any way around this? Or am i having to pack my bags back to Windows

---

### Post by overdrank on 2009-04-09
Moved to  Jaunty Jackalope Testing and Discussion

---

### Post by Polygon on 2009-04-09
does having ipv6 enabled really hurt download speeds that much?

---

### Post by ihatetryingtopickaloginna on 2009-04-09
Yes it does slow it down. I had to turn it off in 7.04, 7.10, and now 8.04. It would sometimes take up to a minute to even start showing a webpage with ipv6 enabled. And then it was worse than dialup when it finally started drawing the page. I even dumped my first attempt at Ubuntu for a few weeks because I didn't know it could be blacklisted.

---

### Post by skymera on 2009-04-09
Yes im getting barely a third of my download speed.

I choose not to install the masses of updates because i don't have time.
Time to ignore Ubuntu and go Fedora it seems.

---

### Post by Polygon on 2009-04-09
um.....worksforme?

---

### Post by olskar on 2009-04-09
Check [http://ubuntuforums.org/showthread.php?t=1065469](http://ubuntuforums.org/showthread.php?t=1065469)

---

### Post by Polygon on 2009-04-09
best way to fix it IMHO:

> **MacUntu said:**
> Maybe the preferred fix is to talk to your ISP. IPv6 is no geek thing, they better should get ready for it.

---

### Post by skymera on 2009-04-09
^^^

I understand that.

Previous to Ubuntu 9.04 disabling IPv6 allowed me to actually use the internet.
Now it's a nightmare. Step backwards it seems.

---

### Post by Polygon on 2009-04-09
well as it seems that the bug has not been fixed yet...aside of compiling your own kernel...your best bet until they fix it is to phone up your ISP and tell them to get their rear in gear =)

---

### Post by ronacc on 2009-04-09
> **Polygon said:**
> well as it seems that the bug has not been fixed yet...aside of compiling your own kernel...your best bet until they fix it is to phone up your ISP and tell them to get their rear in gear =)

you obviously never talked to my ISP :lolflag:

---

### Post by skymera on 2009-04-10
Nor mine, i use Virgin Media, they suck and cap speeds. So i doubt they'll listen to me.

---

### Post by The Cog on 2009-04-10
Why does having IPv6 slow you down, I wonder? It doesn't do so for me, so I wonder what the difference is. I have either wireless or ethernet to a local IPv4-only router. What's your setup?

Do you have an IPv6 default route? What's your output from **route -n**? If you hve a default IPv6 route, have you tried deleting it?

---

### Post by skymera on 2009-04-10
Here's my route -n

```
 scott@scott-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 wlan0
scott@scott-desktop:~$ 

``` Thanks

---

### Post by 67GTA on 2009-04-10
This is actually a bug in the kernel. There is a patch for it. [http://patchwork.ozlabs.org/patch/24127/](http://patchwork.ozlabs.org/patch/24127/)

---

### Post by Reiger on 2009-04-10
> **The Cog said:**
> Why does having IPv6 slow you down, I wonder? It doesn't do so for me, so I wonder what the difference is. I have either wireless or ethernet to a local IPv4-only router. What's your setup?

Do you have an IPv6 default route? What's your output from **route -n**? If you hve a default IPv6 route, have you tried deleting it?

Because of the fact that the entire Internet is glued together using `suitable' **timeouts**. Any packet which is sent with an IPv6 first policy (and that includes the highly important ACK packets which are vital to the workings of TCP), and a fall back of IPv4 will incur a performance hit if the network somewhere in the middle decides to say "Please stop hurting me, please no more IPv6, please don't hurt me...!". See? For every packet you send you get a performance penalty; however for any download the number of packets you send is about equal to the number of packets you receive (because you have to ACK each and every one until you have collected the entire `file'). So that kind of kills perfomance.

---

### Post by The Cog on 2009-04-11
That explanation doesn't ring true to me. Once a connection has been established using TCP/IPv4, I reckon it will confinue to use IPv4. You can't switch TCP between protocols mid-connection.

I can see that establishing a new connection could be delayed if the PC tries TCP/IPv6 first - if the IPv6 doesn't arrive then the connection attempt will eventually time out and then it will try IPv4. Do every new connection will be delayed by the IPv6 connection failure timeout time. That's why I asked about the IPv6 default route. Since skymera seems not to have a default route for IPv6, I don't see how even that delay can occur - the IPv6 connection attempt should fail immediately with a "no route to host" or similar. So I don't know what's going on. I'd love to see the output from **sudo tcpdump -i eth0** while you try to make one of those delayed connections. I can't try it here because I don't have the problem.

---

### Post by ronacc on 2009-04-11
I can't tell you why the slowdown occurs , but I can assure you it does .and that in kernels prior to 2.6.28-4 setting ipv6 to off in /etc/modprobe.d/aliases fixed it .

---

### Post by skymera on 2009-04-11
> **ronacc said:**
> I can't tell you why the slowdown occurs , but I can assure you it does .and that in kernels prior to 2.6.28-4 setting ipv6 to off in /etc/modprobe.d/aliases fixed it .

Yes , i dont know either. All i know is, it worked for LOTS of people

I always thought a connection was made with IPv6 first which then if it timed out, IPv4 was used.

---

### Post by ronacc on 2009-04-11
the problem is not ipv6 . the problem is that those people who do have a problem with it either due to a router that does not recognise ipv6 ( like mine ) or to an ISP who has not implemented ipv6  yet , can no longer disable it . I solved my problem by buying a new router but throwing money at a problem is not a desireable solution for many and if the problem is with your ISP you may be stuck if there is only one in your area .

---

### Post by skymera on 2009-04-11
If i need to spend money on hardware Ubuntu is hardly "free".

I might aswell buy Windows where i am able to keep my router for all my family and disable IPv6 using that..

To be fair i DO NOT CARE what the problem is, all i care about is it getting fixed. The method people used to fix it, no longer works.
We're lost, waiitng for an answer.

---

### Post by The Cog on 2009-04-12
If I knew whtat the problem was, maybe I could figure out something that might work for you. But information about the problem is proving hard to come by.

It's interesting that the make of router has an effect. Perhaps the router is advertising itself as an IPv6 router? If so, something like this, blocking all IPv6 from the router, might help. You might try adding this to the end of /etc/rc.local:
> ip6tables -A INPUT -j DROP

---

### Post by resergent on 2009-04-12
I have tried 8.04 32bit, 8.10 32bit and 64bit and 9.04 64bit (I believe).  And all versions seem to have the same problem. When I ping [www.yahoo.com](www.yahoo.com) the pings show they are fast, but it takes a few seconds for each reply to come back (IPv6). If I ping [www.yahoo.com](www.yahoo.com) using the IP address, response is normal. Resolving the name (which I believe is IPv6 and DNS working together as default for Ubuntu) does not work very well to the level of other linux distro's and dare I say Microsoft. Telling me to push my ISP or buy a new router (I have linux firewall/router) is not the solution. Maybe the solution is providing a way to make a IPv6 to IPv4 gateway on the desktop machine or a way to disable IPv6. Who can help?

---

### Post by Sarvatt on 2009-04-12
if you have a sufficiently recent kernel you can set 
/proc/sys/net/ipv6/disable_ipv6 to TRUE, or just add ipv6.disable=1 to your grub kernel command line.

---

### Post by jfernyhough on 2009-04-12
> **Sarvatt said:**
> just add ipv6.disable=1 to your grub kernel command line.Bloody brilliant. It works perfectly. How come it's taken months for you to post this? :P You, sir, are a :KS

---

### Post by mamamia88 on 2009-04-12
excuse me but how do you edit kernel command line?

---

### Post by Polygon on 2009-04-12
use your favorite text editor and edit /boot/grub/menu.lst

so...

gksudo gedit /boot/grub/menu.lst

and then scroll down and you should find all the entries for ubuntu

there is a line that says kernel and a bunch of options, just at the end of that line put ipv6.disable=1

---

### Post by mamamia88 on 2009-04-12
so do you add it after "quiet"?  i can't find the exact section you are talking about and i really don't want to screw anything up

---

### Post by jfernyhough on 2009-04-12
Something like this will do:

```
title		Ubuntu jaunty (development branch), kernel 2.6.29-02062901-generic
uuid		7e92add6-8b76-42a0-95d8-731df33519ad
kernel		/boot/vmlinuz-2.6.29-02062901-generic root=UUID=7e92add6-8b76-42a0-95d8-731df33519ad ro ipv6.disable=1 quiet splash 
initrd		/boot/initrd.img-2.6.29-02062901-generic
quiet
```Note I added the section before quiet splash simply as I often delete those two to observe the boot process - the order is unimportant.

---

### Post by mamamia88 on 2009-04-12
ok just did that and rebooted and it said unknown boot option ignoring was that supposed to happen?   

changed it to 

uuid	7b22552b-80e5-42dd-a7a5-dcc3d59920b7
title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic
uuid		7b22552b-80e5-42dd-a7a5-dcc3d59920b7
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7b22552b-80e5-42dd-a7a5-dcc3d59920b7 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic   ipv6.disable=1
quiet 

seems to boot up fine now ill let you know if i get any more severe internet slow downs

---

### Post by jfernyhough on 2009-04-12
Look again at where the option is placed: at the end of the kernel line, not the end of the initrd line! :wink:

---

### Post by mamamia88 on 2009-04-12
so....?

uuid 7b22552b-80e5-42dd-a7a5-dcc3d59920b7
title Ubuntu jaunty (development branch), kernel 2.6.28-11-generic 
uuid 7b22552b-80e5-42dd-a7a5-dcc3d59920b7
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=7b22552b-80e5-42dd-a7a5-dcc3d59920b7 ro quiet splash 
initrd /boot/initrd.img-2.6.28-11-generic ipv6.disable=1
quiet

---

### Post by skymera on 2009-04-12
> **Sarvatt said:**
> if you have a sufficiently recent kernel you can set 
/proc/sys/net/ipv6/disable_ipv6 to TRUE, or just add ipv6.disable=1 to your grub kernel command line.

Many thanks, hugs  +  kisses ):P

---

### Post by ronacc on 2009-04-12
I'm running the 2.6.29 rc6  kernel and when I add the ipv6.disable=1  I get " unknown option 'ipv6.disabe' ignoring " as soon as the boot begins . and yes I do have it in the kernel line .

---

### Post by Sarvatt on 2009-04-14
> **ronacc said:**
> I'm running the 2.6.29 rc6  kernel and when I add the ipv6.disable=1  I get " unknown option 'ipv6.disabe' ignoring " as soon as the boot begins . and yes I do have it in the kernel line .

rc6 isn't new enough, 2.6.29 or 2.6.29.1 can do it though :D It was added mid 2.6.29-rc7. The patch that adds the option should apply fine to the jaunty kernel if you want to rebuild it and stick with an older kernel though.

[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=fe7ca2e1e847b65c12d245cbf402af89da96888a](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=fe7ca2e1e847b65c12d245cbf402af89da96888a)

---

