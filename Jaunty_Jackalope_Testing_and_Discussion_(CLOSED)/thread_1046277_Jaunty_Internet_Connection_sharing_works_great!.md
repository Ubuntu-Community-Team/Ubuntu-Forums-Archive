---
title: "Jaunty Internet Connection sharing works great!"
date: 2009-01-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by linux6994 on 2009-01-21
Thanks

Sharing wlan0 to eth0 - I like it! It was easy to set up.

---

### Post by Gourgi on 2009-01-21
can you post some guidelines?
i'd like to try it too.

---

### Post by inportb on 2009-01-22
Hm... that sounds interesting. Is it a GUI app or is it a tool that we could use on the commandline?

---

### Post by tedrampart on 2009-01-22
it must be a gui (I'm running jaunty, but with kde), since internet sharing is already a commandline setup and has been there for as long as I can remember (ip forwarding and such fun stuff).

If it is a gui, this will come in very handy for a lot of folks trying to avoid the CLI  (though I can't imagine why, but I'm a junky for it)

---

### Post by Gina on 2009-01-22
With routers being so cheap these days and very often supplied free by the ISP,  what is the advantage of using a computer for internet sharing?

---

### Post by robert_pectol on 2009-01-22
> **Gina said:**
> With routers being so cheap these days and very often supplied free by the ISP,  what is the advantage of using a computer for internet sharing?

Tons more control!  That's about it.

---

### Post by uBeer on 2009-01-22
Where I live (student flat) we have 1 internet connection for each room and the security is such that I can't connect a router to the Internet. Because after you connected through pppoe over eth0 (which is quite a hassle with Intrepid, had to hack my way through) you have to register your MAC address to some dns or dhcp server. Even after I found out the MAC address of my router, faked it on another pc and registered it didn't work...

So, now I share the Internet through my desktop pc to my laptop. Too bad I haven't been able to set up wireless Internet sharing. The broadcom drivers of my laptop are screwing my system sometimes and it doesn't connect well. When I boot both my desktop and laptop to Vista I can connect, but one of them go Ubuntu and I can't get it to work anymore.

So, any progress on this is very much appreciated!!

---

### Post by inportb on 2009-01-22
> **tedrampart said:**
> it must be a gui (I'm running jaunty, but with kde), since internet sharing is already a commandline setup and has been there for as long as I can remember (ip forwarding and such fun stuff).

If it is a gui, this will come in very handy for a lot of folks trying to avoid the CLI  (though I can't imagine why, but I'm a junky for it)

That's not a perfect argument, because plenty of commandline tools have commandline front-ends. For example, apt-get works with dpkg, iptables/ufw works with netfilter, and so on. I've been doing this on the commandline as well, but was just wondering if there was a *quicker* commandline method. lol.

And yeah, I'm using KDE.

---

### Post by tedrampart on 2009-01-22
> **inportb said:**
> That's not a perfect argument, because plenty of commandline tools have commandline front-ends. For example, apt-get works with dpkg, iptables/ufw works with netfilter, and so on. I've been doing this on the commandline as well, but was just wondering if there was a *quicker* commandline method. lol.

And yeah, I'm using KDE.

thats very true.. plus anything to make things quicker and easier is more than welcome.  especially iptables related

---

### Post by joffe on 2009-01-22
It is possible to do in Intrepid as well. There you need to install the dnsmasq-base package. Then edit the connection in Networkmanager and choose the option "Share to other computers".

Are you saying that it works out of the box now without installing any package?

---

### Post by Davie In Dubai on 2009-01-22
firestarter seems to work a treat

---

### Post by linux6994 on 2009-01-22
Sorry for the lack of info with the post, Everything is just working so well that I started connecting up PCs to fix and update.

Under the network manager I indicated under the IPV4 setting to share with other computers. When the other PCs connect via the eth0 they receive a 10.XXX.XXX.XXX address for DNS and gateway.

I had tried with ipmasq and dnsmasq using that method and had trouble. I removed them along with firestarter and just used the network manager gui. It works fine.

Had to share wireless since I moved my PCs to other end of the house away from the router and wife. Divorced living under the same roof.

---

### Post by tgpraveen on 2009-01-24
i still dont understand it.is there a new network sharing feature in jaunty that was not in intrepid?
also what all features are there?

---

### Post by linux6994 on 2009-01-24
This in Intrepid but I just did not need to use it until I needed it on my Jaunty machine.

The feature allows one port to emulate a router function while sharing the main internet access on the other port.

any pc that needs access > eth0 via direct or hub >   wlan0 > wireless router > internet

---

### Post by Nico0020 on 2009-01-24
I am so happy to hear there is a simple GUI to do this with now.  (Not as important to me as it was about 6 months ago as I finally ran two cat5 cables through my attic into my room) but I still always wanted to see this as a feature in linux that was simple to the ubuntu newbie.

---

### Post by Bou on 2009-01-25
I don't get it. So, let's suppose I have a wired connection but no wireless, and I want to connect two laptops.

If I use the cable to connect the first laptop to the Internet... how can I share that connection with the other PC?

---

### Post by Gina on 2009-01-25
You need two ethernet ports.

---

