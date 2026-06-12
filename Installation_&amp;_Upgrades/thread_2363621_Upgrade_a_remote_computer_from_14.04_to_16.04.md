---
title: "Upgrade a remote computer from 14.04 to 16.04"
date: 2017-06-12
forum: Installation &amp; Upgrades
---

### Post by foxy123 on 2017-06-12
I need to upgrade Ubuntu on a laptop from 14.04 to 16.04. The problem is that I have only a remote access to the laptop and I usually use TeamViewer if I need to do anything on it. I am quite wary to try to upgrade Ubuntu over TeamViewer. However, any other option are problematic as the person on that end is far from being a techie. Any advise or suggestions will be really appreciated.

---

### Post by TheFu on 2017-06-12
Use ssh.  Forget the GUI. It will be a problem.
Also, after the reboot, ssh will probably break, so you really need to setup DHCP reservations for the machine to have the same IP always before beginning.

Last time I did a remote upgrade was from 10.04 to 12.04.  Everything was fine, but I waited to do it until I was in the same town (about 3 months).  With 16.04, many things changed thanks to systemd.  Most of my systems are still running 14.04 and the few 16.04 machines were not upgrades, so I don't know of any issues or that it generally works perfectly.

Sorry.

---

### Post by foxy123 on 2017-06-13
> **TheFu said:**
> Use ssh.  Forget the GUI. It will be a problem.
Also, after the reboot, ssh will probably break, so you really need to setup DHCP reservations for the machine to have the same IP always before beginning.

Last time I did a remote upgrade was from 10.04 to 12.04.  Everything was fine, but I waited to do it until I was in the same town (about 3 months).  With 16.04, many things changed thanks to systemd.  Most of my systems are still running 14.04 and the few 16.04 machines were not upgrades, so I don't know of any issues or that it generally works perfectly.

Sorry.

Thanks a lot. I will probably wait. 14.04 is supported till April 2019.

---

### Post by TheFu on 2017-06-13
> **foxy123 said:**
> Thanks a lot. I will probably wait. 14.04 is supported till April 2019.

I remotely managed my Mom's system over ssh for years.  Also did weekly backups of her stuff to my systems 3 states away.

Learn the ssh.  It is an amazing tool and really is THE method for pretty much all remote, anything.  It only needs 1 port open. Securing it is a fairly well-traveled path. Lots and lots of core Unix tools make use of ssh automatically.  In comparison, TV is a hack, IMHO.  We are Linux people. We can do this without giving up the system security to some 3rd party.

---

### Post by sp40140 on 2017-06-13
@TheFu
Could you elaborate on "TV is a hack" part?
I don't know much about it's inner workings. I just use it.

---

### Post by foxy123 on 2017-06-13
> **TheFu said:**
> I remotely managed my Mom's system over ssh for years.  Also did weekly backups of her stuff to my systems 3 states away.

Learn the ssh.  It is an amazing tool and really is THE method for pretty much all remote, anything.  It only needs 1 port open. Securing it is a fairly well-traveled path. Lots and lots of core Unix tools make use of ssh automatically.  In comparison, TV is a hack, IMHO.  We are Linux people. We can do this without giving up the system security to some 3rd party.

I can use ssh. The problem that it is a bit tricky to log in on the provider on the side of the laptop. It is not a straight forward IP address. Last time I tried a few years ago, I had to have a long discussion with the Customer Service in a different country to figure out how to do it. As I remember you have to have something running on the laptop to be able to ssh into it. So if something goes wrong there will be no way to access it. Thanks a lot, anyway.

---

### Post by TheFu on 2017-06-13
> **sp40140 said:**
> @TheFu
Could you elaborate on "TV is a hack" part?
I don't know much about it's inner workings. I just use it.

Just because a service is popular, that doesn't mean using it is a good idea for everyone or anyone.

Wine for remote access? Hack.

Trusting 3rd party you aren't paying and don't have an enforceable contract with?  Hack.
 
How much is convenience worth?

When you use a valet parking service, do you leave them with a copy of your keys so they can borrow your vehicle later, if they like, when the car is somewhere else?  
Do you have a garage opener in the vehicle? 
Do you lock the garage door to the house?  
That's what you do by using TV - giving some free service access to all the data on your network.

Installed TV on a work computer?  Would the corp security guys like to know that TV company has access to everything on the corp LAN to which you have access?

Just because a service is popular, that doesn't mean using it is a good idea for everyone or anyone.  If they do what they claim, great. How can we prove they don't do more - things we wouldn't want? Can anyone prove that?  Or has everyone trusted them without actually checking?

I have other reasons for NOT using TV.

---

### Post by sp40140 on 2017-06-13
I wasn't aware of them using Wine. And it does make sense.
About third party free service, it's like google. There is always price to pay.

Good to know. Thanks,

Cheers,

---

