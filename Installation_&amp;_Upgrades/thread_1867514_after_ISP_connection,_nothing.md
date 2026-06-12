---
title: "after ISP connection, nothing"
date: 2011-10-23
forum: Installation &amp; Upgrades
---

### Post by kflorek on 2011-10-23
I installed oneiric fresh (from the alternate CD) and it works OK to start programs, but not to use the Internet.

I have dialup Internet and use an external modem with lights. I have been using Ubuntu since warty, and have always been able to use the Internet, although it has gotten odd and complicated in the last couple of years.

 I configured with pppconfig and connected with pon. But after the connection, and all the right lights come on, and a few initital blinks of the data lights, nothing further ever goes to or comes from the modem from firefox or synaptic, according to the lights. pppd does show up listed in "system monitor."

I got gnome-ppp (downloaded using natty on another partition on the same computer) and set that up. Starting from a command prompt, the screen says I am authenticated and pppd is started. pppd shows up in "system monitor." After connection, the receive and transmit lights indicate nothing sent from firefox or synaptic gets to the modem.

 Note that gnome-ppp acted strange unless I started it with sudo. Otherwise, it dials, waits awhile, and the screen says disconnected. And it does that over and over again.

I should say I have made myself a member of the dip group, as recommended somewhere, and rebooted. Doing this is how I managed to get the Internet working (using gnome-ppp) with natty, actually. But nothing works with oneiric.

I also tried gppp and wvdial with essentially the same non-result.

 To sum up, the modem is set up right. The connection to the ISP is complete. The IP's list on the screen. Everything is right. But nothing that uses the Internet ever gets any data to the modem, or receives anything back.

 Is there anybody whatsoever that actually has dialup working with oneiric? That would tell me it is possible.

 Since data has to travel to and from the modem to send commands and get responses (which are correct according to the log), what could possibly prevent data from firefox going to and from the modem?
:confused:

---

### Post by dino99 on 2011-10-23
you might find some usefull errors logged to help you.

[http://ubuntuguide.org/wiki/Ubuntu:Oneiric#Modems_.2F_Dial-up](http://ubuntuguide.org/wiki/Ubuntu:Oneiric#Modems_.2F_Dial-up)

---

### Post by kflorek on 2011-10-26
So seemingly no one in the entire world has ever successfully gotten on the Internet with dial-up with Oneiric. WOW.

I tried whatever I could find at the link and what it links to.

 There are no error messages. The modem is connected to the Internet. All messages and logs are exactly the same as when I connect on Natty. It's just that nothing ever goes to the modem after it is connected, from programs such as wget, apt-get, or firefox.


 I had this kind of problem a while ago with Natty when I tried out the 3.00-12 linux kernel from the edgers ppa. When I reverted back to kernel 2.6.38 I got back the ability to transfer to the dial-up modem. I figured it was a fluke incompatibility.

 Now it looks like this is in the kernel, and there is no way to get around it.

---

### Post by dino99 on 2011-10-26
Sounds like the new kernels have removed your needed driver; install one of the 2.6.38 family to compare.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

note to install:
- install headers...all.deb first
- then headers...deb
- and image.deb

download them all into an empty folder, then cd to that folder, and:

sudo dpkg -i *.deb

---

### Post by kflorek on 2011-10-29
Thanks for the kernel links. I downloaded and installed a kernel = 2.6.38-8. Well, that eliminated the possibility of it being the kernel, because the symptoms were unchanged.

Then I looked at more pages about pppd and dialing. According to one trouble shooting guide, which seemed to be very old:

>begin

8.3 pppd message: not replacing existing default route via x.x.x.x

You configured pppd to create a default route to your new PPP link, which is good. However, pppd does _not_ replace an existing route. To avoid this problem remove the default route before you start pppd. The command to remove the default gateway is

route del default

<end

So I looked at the info you get typing

route

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         ma78-ub18       0.0.0.0         UG    100    0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
localnet        *               255.255.255.0   U     0      0        0 eth0

```

and yes there was a "default" listed. So I deleted it as instructed. BING! Now stuff comes and goes to the modem. It works with the 2.6.38 kernel and the current 3.0.0 as well.:popcorn:

I checked a virtual Ubuntu install done with VirtualBox, and it ends up with a "default". So this is the standard way Ubuntu gets installed.

I checked one old version of Ubuntu and it does NOT have a "default." So that explains how this new problem has started. That also means it is possible to not have a default.

  The "default" comes back after rebooting. I have not been able to find where this "default" route is set, and I have looked inside a lot of the files in /etc for hours and hours.

There is no doubt a simple way to do this search from a command line, but I don't know it. How about giving me the command?

 ppp-gnome still must be started with sudo, unlike with Natty. gpppon still does not work. So there is still some kind of odd problem. pon works.

---

