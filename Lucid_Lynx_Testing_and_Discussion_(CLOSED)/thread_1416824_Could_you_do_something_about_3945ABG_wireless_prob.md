---
title: "Could you do something about 3945ABG wireless problem"
date: 2010-02-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Yeeha on 2010-02-26
From karmic alpha 4 theres a wireless problem that is in Lucid too with 3945ABG [Golan] Network Connection (rev 02) cards. [http://ubuntuforums.org/showthread.php?t=1342897&highlight=iwl3945](http://ubuntuforums.org/showthread.php?t=1342897&highlight=iwl3945) People seem to think that card can see networks but not connect because of card is not transmitting anything. And one person told he got things fixed by setting from bios card active from boot. But my bios doesnt have any wireless options so i cant use wireless :S .

---

### Post by MacUntu on 2010-02-26
At least it's not all cards. My 3945agb works just fine (also did with 9.10).

---

### Post by cariboo on 2010-02-26
Are you sure you aren't suffering from the DNS problem?

---

### Post by the.scarecrow on 2010-02-26
As cariboo907 just said, you could be having the same problem discussed here.

[http://ubuntuforums.org/showthread.php?t=1401061](http://ubuntuforums.org/showthread.php?t=1401061)

If so, its easy to fix.

---

### Post by katie-xx on 2010-02-26
[SIZE=2][COLOR=Blue]One or two routers dont seem to like working with Linux and its probably worth checking your set up is ok before spending time analysing your OS.
The main problem seems to be a lack of response from the DHCP server. Its worth checking that your router is set to 802.11g only ..or 802.11b only. Sometimes the DHCP server wont play ball if the router is set for 802.11b/g or 802.11g/n.
Once youve done that and if you still arent getting a response its time to look at things a little closer.

Kate[/COLOR][/SIZE]

---

### Post by KrazyPenguin on 2010-02-26
My 3945ABG stopped working after the last update and reboot.
But it works on karmic.

So it is definitively a lucid problem.

---

### Post by recluce on 2010-02-26
Just to add another data point: Dell Latitude D830, using Intel 3945ABG WLAN chip: no issues under Alpha1, Alpha2 or Alpha3.

---

### Post by Yeeha on 2010-02-27
Tryed setting to opendns like shown here [http://ubuntuforums.org/showpost.php?p=3996845&postcount=5](http://ubuntuforums.org/showpost.php?p=3996845&postcount=5) . Restarted still couldnt connect to router. Just says preparing to connect and with wicd authenticating.
Router is set 802.11g and tryed 802.11b too. Tryed wep, wpa1, wpa2, without security still same thing.

---

### Post by nanog on 2010-02-27
Perhaps you should try using network manager -- its shown dramatic improvement. 3945ABG works perfectly in lucid on all three of my laptops.

---

### Post by Yeeha on 2010-02-27
if you mean instead of wicd, default kubuntu network manager then thats tryed and also failed.

---

### Post by Yeeha on 2010-02-28
And seems like the problem isnt uncommon as [http://ubuntuforums.org/showthread.php?t=1417927](http://ubuntuforums.org/showthread.php?t=1417927) slymi2005 says: If I may butt in, what exactly is the difference between the default network manager and wicd? I had constant wireless issues with 9.10 so I upgraded on thursday and I just had my first issue again today. Ubuntu sees my wireless connection but it just won't connect.

And i dont watch forums very often, yet i have stumbled on thread on original post & slymi2005 comment

---

