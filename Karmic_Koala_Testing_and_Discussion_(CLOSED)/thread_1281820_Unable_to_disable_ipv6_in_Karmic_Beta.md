---
title: "Unable to disable ipv6 in Karmic Beta"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tr4nce on 2009-10-03
I made a clean install of Karmic Koala and suddenly found out that it's impossible to disable ipv6 so internet is reeeeeeeeeeeeeeeeeeeallllllyyyyyyyyyyyy slow . First of all, I looked up in the whole Ubuntu related sites for solutions, besides the one for Firefox (in about:config, Oh...that made the trick but only for firefox!) and no one seems to be working (for example the "ipv6.disable=1" on /boot/grub/grub.cfg isn't working)

The problem is that I have extremely long delays with internet related commands such as ping, apt-get update, or whatever you can imagine

I have the same problem in old versions of ubuntu, but using the forums i was able to turn off ipv6 support (for example modifying /etc/modprobe/aliases)... Now I can't figure out what to do :( Is there any way to disable ipv6 or I will have to reinstall Jaunty and wait for Karmic's final release to see if there where any solution to my problem?

I'm an owner of HP Compaq 6720s and these are the related specifications:

> # Processor: Intel Core 2 Duo Processor T5470 1.60GHz , 2MB L2 cache, 800MHz FSB
# Wireless: Intel Wireless LAN 802,11a/b/g

Thanks in advance.

---

### Post by psyke83 on 2009-10-03
Sorry for not answering your question properly, but...

Have you looked for firmware updates for your router? That may fix your slow IPv6 problems.

---

### Post by pressureman on 2009-10-03
Try adding/editing the following into your /etc/default/grub.cfg:

```
GRUB_CMDLINE_LINUX="disable_ipv6=1"
```

then run update-grub

---

### Post by tr4nce on 2009-10-03
> **pressureman said:**
> Try adding/editing the following into your /etc/default/grub.cfg:

```
GRUB_CMDLINE_LINUX="disable_ipv6=1"
```

then run update-grub

Nope, not working :( but thanks!

---

### Post by zika on 2009-10-03
> **pressureman said:**
> Try adding/editing the following into your /etc/default/grub.cfg:
```
GRUB_CMDLINE_LINUX="disable_ipv6=1"
```then run update-grubIs it disable_ipv6=1 or ipv6.disable=1. I think it is latter ... It worked for me.

---

### Post by shafin on 2009-10-03
You can try recompiling your kernel without ipv6, if you really need it.
[http://ubuntuforums.org/showpost.php?p=7033690&postcount=9](http://ubuntuforums.org/showpost.php?p=7033690&postcount=9)

---

### Post by tr4nce on 2009-10-03
It might be a good idea if no other way

---

### Post by suplero on 2009-10-04
Did you edit the grub.cfg file manually, or use the update-grub command?

I used the update-grub command in kubuntu 9.10, and that seemed to speed firefox up, but I still have the long lag times in apt.

I edited /etc/default/grub and included the ipv6.disable=1 in the "quiet splash" quotes. 

and then I had to run update-grub to make the grub.cfg file.  

cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash ipv6.disable=1"**
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"

---

### Post by seanlano on 2009-10-04
You need to file a bug report for this, I think. 

I am having this problem as well, Thinkpad R61i with 32-bit Karmic Koala Beta, from a fresh install. Never had this problem before (i.e. with Jaunty, Intrepid etc.) 

Like you said, I can get Firefox to work, but nothing else can connect to the Internet, it hits a timeout before any progress is made. 

Interestingly, if I use Network Tools to ping a domain (e.g. mirror.internode.on.net, my local Ubuntu mirror) then I can access that domain. e.g. ping my mirror, then run Update Manager and it works temporarily, until I end the connection I guess. Not sure why that happens.

---

### Post by DutchKillerBee on 2009-10-04
> **seanlano said:**
> You need to file a bug report for this, I think. 

I am having this problem as well, Thinkpad R61i with 32-bit Karmic Koala Beta, from a fresh install. Never had this problem before (i.e. with Jaunty, Intrepid etc.) 

Like you said, I can get Firefox to work, but nothing else can connect to the Internet, it hits a timeout before any progress is made. 

Interestingly, if I use Network Tools to ping a domain (e.g. mirror.internode.on.net, my local Ubuntu mirror) then I can access that domain. e.g. ping my mirror, then run Update Manager and it works temporarily, until I end the connection I guess. Not sure why that happens.

+1 :(

I used a temporary solution by setting the opendns servers as name servers in the /etc/resolf.conf file instead of my router ip adress.
I changed the /etc/nsswitch.conf to files dns for the hosts part as well.
now karmic flies like an eagle 
KB

---

### Post by zika on 2009-10-04
> **tr4nce said:**
> Nope, not working :( but thanks!Did You try **ipv6.disable=1**? Check with ifconfig atrewards to see if it is turned off. 
**disable_ipv6=1** is used for the other way of disabling ipv6 ... not via kernel boot line.

---

### Post by suplero on 2009-10-04
I have long thought there was a problem with the DNS resolution in 9.10.  It's nice to see that DutchKillerBee found a solution in that direction.

I don't know why/how the DNS changed in 9.10, or if there are other factors involved either, but it also looks like the problem can be very hardware dependent.  I have qwest as my ISP, and for whatever reason they seem to have issues with 9.10, but not 9.04.  

Others have reported that 9.10 connects and runs without any problems.  This just adds more questions for me, and doesn't really point to a nice solution.

---

### Post by cariboo on 2009-10-04
Just to add a bit to this thread, I have the following line in dmesg:

```
[   26.042528] eth0: no IPv6 routers present
```

but have no problems with lag on any command. I'm running a wrt54gs router if it makes any difference.

---

### Post by seanlano on 2009-10-05
> temporary solution by setting the opendns servers as name servers in the /etc/resolf.conf file instead of my router ip adress.
I changed the /etc/nsswitch.conf to files dns for the hosts part as well.I'll give that a try. 

Has anyone filed a bug report? I would like to comment on the bug, so please provide a link.

---

### Post by todak on 2009-10-05
Try this: [http://ubuntuforums.org/showpost.php?p=8048347&postcount=7](http://ubuntuforums.org/showpost.php?p=8048347&postcount=7) **_FIRST MAKE A BACKUP COPY OF NSSWITCH.CONF!_**

---

### Post by seanlano on 2009-10-05
To clarify/simplify the workaround from DutchKillerBee, follow the **[instructions on the OpenDNS website]("https://www.opendns.com/start/device/ubuntu")**. 
Read all the way to the bottom, there are some commands to run in a terminal if the GUI method doesn't work. 

These steps worked for me, although I'm not sure if it was the GUI or the CLI steps that did it because I did them both. 


However, this is still not a solution (unless Ubuntu will use OpenDNS by default, which isn't going to be likely), so something is wrong still.

---

### Post by camper365 on 2009-10-18
I reported a bug on this a while ago:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/417757](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/417757)

---

### Post by tad1073 on 2009-10-18
to the best of my knowledge, Ipv6 is no longer modular, which means it is built into the kernel, so you would have to recompile a kernel to disable it.

off topic, but, IEEE needs to have all Ipv4 addresses converted  to Ipv6 and completely drop Ipv4.

---

### Post by seamuso on 2009-10-19
I was having similar slowdowns, thought it was IPV6, reality for me was I needed to edit nsswitch.conf

```

# hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
hosts:          files dns

```

prior to that change, pinging any of my local machines resulted in long waits for ping replies to return, etc. Once I made the change, all was as it should be.

See if it helps, your mileage may vary ..

---

### Post by the111dan on 2009-10-19
same problem here
I tried editing nsswitch.conf but it didn't work for me, the internet is still slow for me. I have static ip and manual DNS connection through NetworkManager.

---

### Post by Static- on 2009-10-19
i need to get this disabled,

---

### Post by tad1073 on 2009-10-19
[http://ubuntuforums.org/showpost.php?p=8126662&postcount=18](http://ubuntuforums.org/showpost.php?p=8126662&postcount=18)

---

### Post by seeker5528 on 2009-10-19
I just did:

```
sudo vim /etc/sysctl.conf
```

: and added the lines:

```

#Disable IPv6
net.ipv6.conf.all.disable_ipv6=1



```
: to the bottom of the file, then rebooted and:

```
cat /proc/net/if_inet6
```

: shows nothing, indicating IPv6 is disabled.

I haven't seen that it makes a difference if IPv6 is enabled or not on any of my machines over the last 4-5 years, however long it's been since IPv6 has been enabled by default, but obviously not true for everybody, so YMMV.

Later, Seeker

---

### Post by psyke83 on 2009-10-20
If you believe that IPv6 is slowing down your internet connection due to your ISP not supporting it, you may want to consider testing "miredo", available in the repository. Works perfectly here.

I notice slow DNS resolution on Ubuntu, and I've isolated the problem to the avahi daemon, not IPv6.

---

### Post by Static- on 2009-10-20
^^ good info

---

