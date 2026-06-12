---
title: "Broken Internet, AGAIN!!"
date: 2009-01-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2009-01-27
Ok, a few days ago some update/removal broke my 'secure wireless' connection. I could connect via neighbors  wireless with no problen (no password needed) So after posting here and being real frustrated with no results, I reinstalled. All was good.
Well after updates yesterday and trying to install 'amarok' and removing it as it was a failure installing 'amarok', I suddenly had a broken 'msql 5.1' again!! or (what ever that was broken the other day and got fixed) Well after updates this morning and a reboot, my wireless internet is broken for my internet, but I can connect from next door neighbors (strong signal, no password). I am not comfortable with "stealing" neighbors wireless connection.
[B]
Some please guide me on what I should be looking for to fix my own wireless. If you need any info please let me know what else I can provide.
Thanks
EDIT: I really do not want to reinstall just to get my wireless working!![/B]

---

### Post by Tomatz on 2009-01-27
> **DougieFresh4U said:**
> Ok, a few days ago some update/removal broke my 'secure wireless' connection. I could connect via neighbors  wireless with no problen (no password needed) So after posting here and being real frustrated with no results, I reinstalled. All was good.
Well after updates yesterday and trying to install 'amarok' and removing it as it was a failure installing 'amarok', I suddenly had a broken 'msql 5.1' again!! or (what ever that was broken the other day and got fixed) Well after updates this morning and a reboot, my wireless internet is broken for my internet, but I can connect from next door neighbors (strong signal, no password). I am not comfortable with "stealing" neighbors wireless connection.
Some please guide me on what I should be looking for to fix my own wireless. If you need any info please let me know what else I can provide.
Thanks

I take it (from your sig) that you are using jaunty. If i were you i would use Intrepid or Hardy as lots of things will probably break in the coming months.

Of course if you want to test then install jaunty as a secondary OS.

---

### Post by DougieFresh4U on 2009-01-27
> **Tomatz said:**
> Of course if you want to test then install jaunty as a secondary OS.
It is not the only computer I have

---

### Post by Tomatz on 2009-01-27
> **DougieFresh4U said:**
> It is not the only computer I have

What wilan card do you have?

---

### Post by ronacc on 2009-01-27
dougie  feel free to add your comments to my bug , [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/321372](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/321372)  . I have 2 networks and since kernel 2.28.4 one of them fails to connect wirelessly much of the time , I havent been able to find out why yet .

---

### Post by DougieFresh4U on 2009-01-27
> **ronacc said:**
> dougie  feel free to add your comments to my bug , [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/321372](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/321372)  . I have 2 networks and since kernel 2.28.4 one of them fails to connect wirelessly much of the time , I havent been able to find out why yet .

Thanks. I just did a fresh install again as I was really 'p'oed'

---

### Post by cariboo on 2009-01-27
If you turn off security on your router can you connect to it?

BTW, whenever I see someone saying they broke the internet again, I really want to say that it works good here so it must be your service provider.

Jim

---

### Post by ronacc on 2009-01-27
I do not have security on either router , ther router that won't connect wirelessly will connect wired  , it was connecting all the time prior to an update to NM that arrived at about the same time as kernel 2.6.28-4 , it went through a few days when it was connecting again and then went out again with updates on jan 25 . Note my eeepc will connect to that router ( or the other ) at all times .

---

### Post by DougieFresh4U on 2009-01-27
> **cariboo907 said:**
> If you turn off security on your router can you connect to it?

BTW, whenever I see someone saying they broke the internet again, I really want to say that it works good here so it must be your service provider.

Jim

There are 7 pc's in my home and 2 are running Ubuntu.  One with Intrepid and one with Jaunty.  **The Jaunty install is the only one that has the 'borked' wireless**

EDIT: I have ran Intrepid on the same machine as Jaunty is on and no problems with wireless

---

### Post by cariboo on 2009-01-28
DougieFresh4U

I guess I should have been a little clearer, what I meant was if you can connect with security disable, then the problem isn't with your wireless device, but with wep/wap, but ronacc indicated that he didn't have security enabled on his routers and he still can't connect. I haven't tried wirelss yet in Jaunty. I have two computers running wireless, one a laptop running XP and the other intrepid, becuase I don't have a free network cable to connect to it the only way to do it is to disconnect the cable to the computer I'm using now and swap cable for wireless.

Edit: I have nine  computersrs on the network at the moment, 3 running XP, 4 running Ubuntu, 1 running AntiX and 1 Mac OS 9.

Jim

---

### Post by Tomatz on 2009-01-28
> **DougieFresh4U said:**
> There are 7 pc's in my home and 2 are running Ubuntu.  One with Intrepid and one with Jaunty.  **The Jaunty install is the only one that has the 'borked' wireless**

EDIT: I have ran Intrepid on the same machine as Jaunty is on and no problems with wireless

It would help if you said what wireless card you have.

---

### Post by caryb on 2009-01-28
Mine is broken as well, I have a Intel wireless card. Mine won't connect via WEP encryption for the last 3 days.


Cary

---

### Post by ronacc on 2009-01-28
I don't remember the name of the card itself but the chip is a realtek rtl8185 and the driver is the rtl8180 driver . I do not think it is the card because it will connect with the other router at all times and sometimes connects with the router in question . later today I will try changing some things around to see if that has any effect.

---

### Post by Gina on 2009-01-28
Does sound puzzling.  Yes, try to narrow it down - be interesting to see what you find.  I've quite often found wireless networking a puzzle.  Currently, mine's fine with Jaunty (with WEP) but it's bcm4306 and rt2500 chipsets which are now well supported.

---

### Post by DougieFresh4U on 2009-01-28
> **caryb said:**
> Mine is broken as well, I have a Intel wireless card. Mine won't connect via WEP encryption for the last 3 days.


Cary

Ditto!
Just want to say that Jaunty is having a 'bad trip' all around with Intel

---

### Post by ronacc on 2009-01-28
ok I ran some tests and am back to connecting to both routers again . here is how I proceded .
1 updated (as of 4 PM eastern time US )  reboot , still no connect to belkin
the router that always connects is an airlink 101 it is set to no encryption (open) and channel 11 
the router that does not connect is a belkin wireless g it is set to no encryption (open) and channel 1 
2 shutdown airlink ( disconnected power )
3 tried to connect to belkin  , no connect .
4 set belkin to channel 11 , no connect .
5 rebooted jaunty  , connect .
6 shut down jaunty box and belkin router , brought airlink back up and using another box set airlink to channel 1 .
7 brought jaunty box and belkin back up , can now connect to either router and can switch "on the fly".

??? did the channel switch cause some config file to be rewritten ? things had been working fine for months prior to the upgrade that took the belkin out .???

---

### Post by Gina on 2009-01-29
Strange!  But that's nothing new        :lolflag:

Glad you got it working :)

---

### Post by Tomatz on 2009-01-29
> **Gina said:**
> Strange!  But that's nothing new        :lolflag:

Glad you got it working :)

Have you tried simply rebooting your router in your router config?

---

### Post by ronacc on 2009-01-29
@Tomatz you may be on to something there , prior to yesterdays tests I had been just doing a hard shutdown and restart on the router (poweroff) , I shut the whole system off and restart a couple of times a day anyway , this morning on start up that box wouldn't connect to either router so I tried your advice and reset the router from its config page and bingo it connected to the belkin but not the airlink ,I'll try a reset on that one (it never gets shutdown normaly ).

EDIT: a reset from the config page on the airlink didn't do it but a reset with the reset button on the router did ???

---

### Post by Tomatz on 2009-01-29
> **ronacc said:**
> @Tomatz you may be on to something there , prior to yesterdays tests I had been just doing a hard shutdown and restart on the router (poweroff) , I shut the whole system off and restart a couple of times a day anyway , this morning on start up that box wouldn't connect to either router so I tried your advice and reset the router from its config page and bingo it connected to the belkin but not the airlink ,I'll try a reset on that one (it never gets shutdown normaly ).

EDIT: a reset from the config page on the airlink didn't do it but a reset with the reset button on the router did ???

Once i had to reinstall the network-manager package on my laptop (hardy usplash error). After i done so my wireless wouldn't connect. After about 1/2 hour of messing about with settings i rebooted my router and laptop and it worked.

Maybe updating network-manager is just having the same effect as reinstalling it?

---

### Post by ronacc on 2009-01-29
I suppose that is possible but the question remains why does the router have to be reset ? NM sees them (both) ok so it should be able to connect :(

---

### Post by Neural oD on 2009-01-29
routers can be pedantic - much like windows - sometimes the only way to get them functioning correctly is to reboot them :(

---

### Post by ronacc on 2009-01-29
I understand that , infact the reason I put a wireless card in my test box (the one running jaunty) was to be able to play with wireless because it can be a problem . however if it is either or both of the routers why can my EEEpc conect to either running either xandros or puppy when Ubuntu won't ?Also If I plug in the cable the test box will connect wired when it wont wirelessly ( it only sits 2 meters from the router so wired is no problem ).What do xandros and puppy have that Ubuntu doesn't ?

---

