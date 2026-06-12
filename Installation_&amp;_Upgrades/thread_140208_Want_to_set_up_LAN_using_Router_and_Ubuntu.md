---
title: "Want to set up LAN using Router and Ubuntu"
date: 2006-03-05
forum: Installation &amp; Upgrades
---

### Post by Jeremy'sCoding on 2006-03-05
Hello I am new, so please forgive my extremely basic questions.

I just recently installed Ubuntu linux on two of my desktop computers at home.  I would like to set up a small home network.  

Here is my basic setup.  I have Comcast cable internet feeding from the external cable modem to a ZyXEL router.  Each computer is seperately connected to the router using ethernet cables and cards.  The internet is plugged into the WAN slot and each computer is plugged into the router under slots called LAN 1 and LAN 2.  FYI, I am able to surf the net with no problems on both computers.  

Q1?  It appears that I have everything I need to create my own LAN.  Is that correct?  Do I need a switch?

Q2: Is there an online reference to get me started?  I need to know what to install and how it all works together?

Q3: I have both computers and the router set to DHCP.  Is it possible to share files between the computers using DHCP?

Thanks!

---

### Post by Jason_25 on 2006-03-05
1.The router has an internal switch/hub.  
2.Not sure on that one
3.I'm not a fan of DHCP.  I prefer static IP addresses as it keeps things much neater.  DHCP is not a file transfer protocol.  NFS is what you should use to share files between your PC's.  There should be a graphical setup for file sharing under system > administration.

---

### Post by Jeremy'sCoding on 2006-03-05
thanks for the help

In addition to your comments, I found the following thread which has helped a lot: 
[http://www.ubuntuforums.org/showthread.php?t=139174&highlight=LAN](http://www.ubuntuforums.org/showthread.php?t=139174&highlight=LAN)

Here is something for you to laugh about.  I don't even know how to close out a thread.  Can you help me out on this last question?

---

### Post by Herman on 2006-03-05
Try [this page]("http://www.users.bigpond.net.au/hermanzone/p11.htm") on setting up SSH networking and see if you like it.

I use a router too, so it should just work for you the same way. It shows how to switch from the default DHCP to fixed internal IP address (inside your LAN), you will need to do that to use SSH. 

Your outside IP address can still be roving or static. I, like most home users, just have the standard roving IP to the outside world. Static ones normally cost more. If you get your ISP to rent you a static IP address you can even access your home computers with SSH when you are away travelling. That's more for business use though, and not covered by the web page as it introduces all kinds of extra considerations. (Port forwarding, security precautions, etc).

As long as you have good secure passwords set, SSH is very secure for internal home networking, especially since your router will have a hardware firewall. The networking section and the security section of this web forum are the best places to learn more about that.

:-D (Herman)

---

### Post by Jeremy'sCoding on 2006-03-05
Thanks for the advice Herman.  I like the SSH networking site.  

Jeremy

PS I will definitely use the Networking forum next time.  Unfortunately, I discovered it after I started this thread.

---

### Post by Jeremy'sCoding on 2006-03-05
Herman,

Your SSH networking instructions worked perfectly.  I am now able to see my additional computer and share files.

Thanks sooooooooooo much.

I also learned a bit about IP addresses.

---

### Post by Herman on 2006-03-06
Great, Jeremy, I'm happy if I can help. :-D
And, I didn't mean to imply anything by suggesting the networking forum. I just meant that's a great place to go for more advanced technical learning on the subject. (It's where I go to read up on what the experts have to say). You were installing networking, so I guess that's half and half, you're fine, don't worry so much, it's a freindly forum. :-D  
All I want, and probably most other forum members here, is that you enjoy Ubuntu as much as we do, and have fun learning lots of neat stuff! ;) (Herman)

---

