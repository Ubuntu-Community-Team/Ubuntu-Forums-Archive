---
title: "How do I ex the Session Manager? &amp; Why is my wired internet at all unstable?"
date: 2009-02-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by SplinterOfChaos on 2009-02-07
First: The session manager.

I've simply found I don't like session management. How do I turn it off, or perhaps better, remove it entirely? It didn't come up in the Add/Remove Applications application. 

In case this is just me misusing it and anyone wants to talk me out of this: My biggest annoyance is if an application crashes, when I reboot, it's still crashed! I had to figure out how to launch my xfce panel from the console. Also, not all my applications seemed to work with it (GVim for example, for whatever reason). 

Second: My internet connection.

When I googled this, I found people talking about their wireless internet connection, but not wired. That's why I ask specifically why my **wired** connection is unstable.

I'm sharing a router with someone else, and I do find my connection is much more stable when the other's computer is off, but still not perfect. 

In Windows XP (I'm newly a dual booter), I have no trouble with this, and I even found Kubuntu worked perfectly for internet when I tried it out (Live version). It's Ubunutu, Xubuntu and pretty much every other distro I tried. So, I'm thinking that the problem is definitely hidden in the difference between {U|X} and Kubuntu, which surprises me because I thought the difference was merely graphics.

Thanks in advance.

EDIT:

Here's another question: Why did this post appear in **Ubuntu Forums > The Ubuntu Forum Community  > Other Community Discussions  > Development & Programming  > Jaunty Jackalope Testing and Discussion** when I clicked [Absolute Beginner Talk]("http://ubuntuforums.org/forumdisplay.php?f=326") to get here? Oh well, could a mod move it over to where I intended, or where ever would be most appropriate? Sorry for this; must've clicked the wrong thing.

---

### Post by cariboo on 2009-02-07
I would suggest checking ip addresses on both computers when they are running, you may both be getting the same ip address from the router.

Jim

---

### Post by SplinterOfChaos on 2009-02-08
Indeed that appears the problem. What do I do about it?

---

### Post by Peter09 on 2009-02-08
Your router should be set to provide DHCP ip addresses to any machine that connects to it. Check that this is set up correctly. Also check that both machines are using the DHCP protocol to obtain IP addresses.

The chances are that you have set up static addresses(determined for each machine by the user, not by the router).

What is the IP address that you have?

---

### Post by SplinterOfChaos on 2009-02-08
Wow, Linux is technical. Feels like no amount of googling is going to give me good answers. 	:???:

How do I check they're using DHCP? I bet checking if my router is set up right is specific to my router, so I should call its tech support, right?

My IP? Well, according to different sources it's different numbers. whatismyip.com said 66.188.24.172. 192.168.1.100 is what my "Connection Information" says.

---

### Post by Peter09 on 2009-02-09
Right clicking on your network icon will give you the option to select connection information. This will tell you your internal IP address. This is the one that appears to be 192.168.1.100. This is you Local IP address and any other machine on the network must have a different one. From the form of this I suspect you have DHCP working.

66.188.24.172 is the IP address that your ISP gave you (your external IP). No need to worry about this one.

You need to understand NAT- Network Address Translation - 

Your router changes all the internal IP addresses into one external one,for messages that go out to the internet, so you can have lots of machines on your LAN, but only one external IP address.

Check that machines on your LAN have been given (via DHCP) different numbers at the end of the IP address - 
192.168.1.100, 192.168.1.101, 192.168.1.103 etc

Note that this is nothing to do with Linux, it must be set up for all types of machines on your network.

---

### Post by SplinterOfChaos on 2009-02-09
It might not be Linux specific, but Windows didn't need intervention to do this.

That NAT thing... is that what you were talking about in the next paragraph ("Your router changes all the internal IP addresses") or something *else* for me to Google? I haven't found much on it yet.

I does appear that we have different IP addresses. I tried the trick I found [here]("http://www.wikihow.com/Assign-an-IP-Address-on-a-Linux-Computer") to almost no avail, but it did lead me to making an interfaces file that looks like this:
> auto lo
iface lo inet loopback

address 192.168.1.111
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.1.255
gateway 192.168.0.1
dns-nameservers 216.10.119.241 
I don't know that actually did much, but it allowed another wired network (called wired connection 1) to show up and I was able to copy the MAC address of auto eth0 and go to IPv4 Settings such that Method=manual, Address, netmask, gateway, and DNS server could be copied from the Windows computer and my connection seems pretty stable. The only problem I'm having right now is connecting to photobucket.com, otherwise I'd just've posted a screen shot. But, I had no trouble connecting to Google to make sure I typed photobucket.com right, nor did I have any trouble getting Pigeon to sign onto my various accounts (which is a first for Xubuntu).

As tired of all this as I am, I feel I should probably know why this is, at least temporarily, working. *sigh* Long day, but I shouldn't use Linux unless I'm willing to learn, right? 

And to think when my choices for classes this semester were Networking and Operating Systems and I chose OS. :s

---

### Post by Peter09 on 2009-02-10
If you are using DHCP from your router than you do not need anything in that file except the top two lines.

Try commenting them out by putting a # sign as the first character in the line on the file and see what happens when you restart networking by

```
sudo /etc/init.d/networking restart
```

Just keep it simple, you are making it complex. If DHCP is working you need to do very little.

You appear to have errors in the network file that you made. Best not to use it :(

---

### Post by SplinterOfChaos on 2009-02-11
Ok, seems to be working. Thanks.

---

