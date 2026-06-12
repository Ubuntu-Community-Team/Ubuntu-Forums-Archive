---
title: "setting up a torrent box"
date: 2008-03-18
forum: Installation &amp; Upgrades
---

### Post by markp1989 on 2008-03-18
i have been given an old pc, (1.7ghz 256mb 80gb) that i would like to set up as a torrent slave.

i would like to use icebuntu, and Deluge, because i know deluge has web management ,

a couple of questions about Deluge web management.

how can i set it to be accessible from out site my home network?

I understand that i will need to enable port forwarding, but i am not sure how to do that with my router (speed touch 510) 

i would also like to be able to use ftp to copy my files over the network to my other computers after they have finished downloading, what FTP servers and client software would you recommend?

i would like to keep a graphical environment, because it may be used for occasional webbrowsing


Edit: just found a spare ram module and added it , so now it has 512 + 256 mb of ram

---

### Post by insineratehymn on 2008-03-18
I have a torrent slave, kinda...

If the computer is slow (from what it looks, it isn't **that** slow), but you may want to consider it being headless, as in no xclient running on the computer.

I use rTorrent, it is completely headless and uber-customizable.

You can ssh into your computer from anywhere you can run PuTTY (which fits onto any flash drive ever made) and you can check your torrents or add new ones, or even configure it so it will watch a folder and automatically add the torrents as they come in.

It even appears as though Deluge uses the same libtorrent as rtorrent.

You can run rtorrent in screen (basically puts it in the background) so you can logout and it runs as long as the computer is on.

---

### Post by markp1989 on 2008-03-18
> **insineratehymn said:**
> I have a torrent slave, kinda...

If the computer is slow (from what it looks, it isn't **that** slow), but you may want to consider it being headless, as in no xclient running on the computer.

I use rTorrent, it is completely headless and uber-customizable.

You can ssh into your computer from anywhere you can run PuTTY (which fits onto any flash drive ever made) and you can check your torrents or add new ones, or even configure it so it will watch a folder and automatically add the torrents as they come in.

It even appears as though Deluge uses the same libtorrent as rtorrent.

You can run rtorrent in screen (basically puts it in the background) so you can logout and it runs as long as the computer is on.


using rtorrent, is it possible to do web management?  like in deluge, and i have only ever done deluge for internal network , how would i make it accessible to the world, so i can add torrents when im out etc

---

### Post by insineratehymn on 2008-03-19
No, rTorrent doesn't have an HTML interface, but it is manageable through the web via an ssh console...

If you want to set any server up to listen to the web this is what you need to do:

1) Get some DNS forwarding software, like [No-IP]("http://www.no-ip.com"). The software for that one is in the repositories as "no-ip" I believe. They will set you up with a domain name that points to your homes IP address (taking care of that silly dynamic IP address problem).

2) Make sure your router forwards the requests for whatever port the web management tool is running on to the computer on which the server is running. So, if your web management tool says it is running on port 8081, make sure that your router points all incoming requests for port 8081 to your computers IP address.

3) Make sure your server is running and there may even be a checkbox for something like "allow internet requests". If there is a checkbox that even sounds like that, its probably worth checking.

4) Secure your network! If **you** are able to logon, view your torrents, move them to a desired folder once they are done, delete bad stuff, add new torrents, etc... then **I** or anyone else can do the same. Not everyone has the best intentions. 

P.s.: Try to find a web management utility that uses SSH as its protocol. It won't add any of the top-level security that I've mentioned in step 4, but it will help prevent against some nasty "man-in-the-middle" attacks and will encrypt your traffic as it flows over das intraweb.

---

### Post by markp1989 on 2008-03-19
after thinking about it i think it would be better to make it head less like you suggested, i read about a program called torrent flux, which seemed to fit exactly what i want.

due to port forwarding etc i would assume that i would have to set up the torrent slave to use static ip?

---

### Post by markp1989 on 2008-03-19
was in the process of installing ubuntu server on it , a puf of smoke came from the heat sink, pulled the power plug straight  away and now i get continuos beeping if i power it on, so i asume that the cpu burnt out

still want to set up a torrent slave, i a spare motherboard and cpu i had laying around in the same case

the motherboard had a 256mb module in it, so now added to the  ram from the dead PC, it has 1ghz cpu and 1gb of ram, seems kind of waste to be using it command line only. and other uses i could add to it, aswell as a torrent slave

---

### Post by insineratehymn on 2008-03-19
Either way...

You don't need a static IP with no-ip, it runs a piece of software on your computer that updates your IP every so often to no-ip's DNS servers so they always know where you are.

---

### Post by markp1989 on 2008-03-20
what i meant was that my router gives out address to the computers in my house randomly, somthing like 10.0.0.X, but if i set port forwarding for 10.0.0.X, and for some reason the torrent slave gets turned off, when it turns on i will most likely get given a different address , so that port forwarding wont work

im not sure if that complete gibberish i have written up there or not :S

---

### Post by markp1989 on 2008-03-20
so far i have it set up downloading torrents, i am able to manage it from my other computers, but not from out side my network (away)

any one know of any thing else that this can be used for, so far it has command line ubuntu, torrentflux and ssh installed.

currently it is spending most of its time idling, are there any other uses i could add to this setup, im open to suggestions 

spec is the torrent slave in my sig

```
  21:08:21 up  1:01,  0 users,  load average: 0.00, 0.00, 0.00
```
```

             total       used       free     shared    buffers     cached
Mem:          1011        894        116          0         11        796
Swap:            0          0          0
```


edit : i have installed folding@home, those spare cpu cycles may aswell be used for something 

still looking for other uses to add to it.

---

### Post by markp1989 on 2008-03-20
i have signed up to no-ip, but when i go to the link given i get sent to my router configuration page insted of my computer

---

### Post by insineratehymn on 2008-03-22
When you click the link you end up at your routers page.
That is a good sign, it means that it is working.

What you need to do is go into your router and forward port 80 to whatever computer you want it to go to.

If you need to restart your torrent slave quite often (doesn't make a lot of sense; why restart a server?) you can assign an IP to a MAC address in some routers.

---

### Post by markp1989 on 2008-03-23
> **insineratehymn said:**
> When you click the link you end up at your routers page.
That is a good sign, it means that it is working.

What you need to do is go into your router and forward port 80 to whatever computer you want it to go to.

If you need to restart your torrent slave quite often (doesn't make a lot of sense; why restart a server?) you can assign an IP to a MAC address in some routers.

i dont intent to turn  it off

just mean if for some reason it does, such as a power cut or something (there were 2 short powercuts here last week, each lasted for under a second, but it still made the computers turn off

---

### Post by insineratehymn on 2008-03-24
Ok, so if your router has the ability to bind an IP address to your computers MAC address, then that will be your solution.

---

### Post by markp1989 on 2008-03-24
i set my server to ask for a static address, and my router is fine with it , i have set up portforwarding for torrentflux web configuration, and ssh, and no-ip is working fine.


thankyou for all the information you have given my, i appriciate it

---

### Post by insineratehymn on 2008-03-24
Sounds fun.

Make sure everything is secure and you should be worry free.

Pass it on!

---

