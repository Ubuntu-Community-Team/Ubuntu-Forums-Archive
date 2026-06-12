---
title: "Running Deluge Makes Internet Slow"
date: 2008-09-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Trueno22 on 2008-09-20
I have a 15Mb connection.  When I was using hardy I would download at 1.6 Megabytes a second.  And even downloading at that speed my internet browsing was unaffected.


I boot up to my Ibex partition run the same torrent in Deluge and I get only 800 to 1000kb/s.  Not only that but even without my connection being maxed by the torrent internet browsing is painfully slow.

:confused:

---

### Post by MaX on 2008-09-21
What happpens with transmission?

---

### Post by olskar on 2008-09-21
Perhaps you should give latest deluge a try, works better for me :)

[http://deluge-torrent.org/](http://deluge-torrent.org/)

---

### Post by zolookas on 2008-09-21
Check you max connections limit and contract with your ISP, maybe they are limiting numer of sessions (connections).

---

### Post by fusionisthefuture on 2008-10-01
ive got this same problem, although its in hardy, not ibex, and its with any torrent application, by which i mean deluge and ktorrent both, i refuse to test transmission, it hurts me to use such a limited application.  i cant for the life of me figure out my problem.  my roommate always has a torrent program running on xp, and it never slows the internet, but whenever i open ktorrent or deluge now, it completely breaks the internet.  im using a nonstandard port above 40000 with port forwarding enabled in the router, ive got the max connections set to 130 and im using dd-wrt firmware on a buffalo router, with max connections on it set to 512 (which i never reach).  ive tried QoS and everything else i can think of, but the internet is painfully slow.  my max upload is around 55KBytes/s and my max dl is around 550KBytes/s.  the 3 torrents im currently trying to dl never go above 15KBytes/s max all together, and never above 5KBytes/s up, all together.  when i tried QoS, i didnt notice any change, and i set http to exempt (the highest) and bittorrent to bulk (the lowest).  i tried adding a custom entry for my specific port range, but it wouldnt get added to the list, for an unknown reason.  
any ideas, anyone?

---

### Post by MaX on 2008-10-01
What happens if your room mate shuts down his torrent?
Does it help?

It might have something to do with the network card drivers in the end... better support in Windows???

---

### Post by fusionisthefuture on 2008-10-01
no him shutting his down doesnt help, and my network card driver is supported just fine.  im using a laptop, and ive previously had torrents running on it (in ubuntu) no problem.  this is a rather recent occurance, which is odd because nothing i know of has changed.

---

### Post by priegog on 2008-10-01
I'm gonna jump right in and suggest to fusionisthefuture to deactivate QoS in dd-wrt. I seem to recall to having had the exact same problem when I activated that feature. What hardware is your router, btw?

---

### Post by Whiffle on 2008-10-01
Some routers get bogged down by the sheer number of connections torrents make, causing the interwebs to slow down.

 [http://www.goarticles.com/cgi-bin/showa.cgi?C=1113901](http://www.goarticles.com/cgi-bin/showa.cgi?C=1113901)

---

### Post by fusionisthefuture on 2008-10-01
i guess i should have mentioned that i already re-disabled qos after enabling it, in order to get rid of lag i was experiencing in a game for no apparent reason.  i thought something i had changed had caused it to be worse than before without torrents on.  i think the feature is broken tho, or im not using it right.  

im using a buffalo router, a little 4 port G one, i forget the number of it.  the dd-wrt firmware i loaded has a defualt connections limit set to 512.  i tried opening that up to max 4096, but it dindt change anything.  like i said, torrents are fine if run under windows, by azureus or whatever, i can set global max connections to 300+ and have it run fine.  both deuluge and ktorrent i have set to max 130, but it doesnt matter, the exact second that i start a torrent, the internet browsing goes to ****, and the exact second i turn it off it gets better.  i know im not connecting to a trillion peers at once, and the transfer rate in either direction is barely a trickle.  it leads me to believe theres something inherently wrong in the fact that its a torrent on linux thats breaking everything, or some sort of ghost bandwidth usage...

---

### Post by priegog on 2008-10-01
That is intriguing... I'm out of ideas ATM... I'll have to sleep on it.

---

### Post by fusionisthefuture on 2008-10-01
well i thought that i could run torrents just fine under windows on that laptop... (wireless) but it has exactly the same problem (go linux!) next step is a different wired computer.

---

### Post by Lorenz on 2008-10-03
I have a similar problem with Deluge. Previous versions of it (before 1.0) always gave me great speeds, while leaving the internet performance while browsing untouched. 

All the RCs and now the final version of 1.0 makes it impossible to surf the web and use Deluge, additionally I cannot connect to seeders either. I will have to go and find an older version of Deluge again - or does anyone here know a solution? I don't have this problem with any other torrent client, but I made my best experiences with the older Deluge versions, so I'd like to keep on using it...

---

### Post by wgrant on 2008-10-03
Have you tried limiting the upload speed? That often helps.

---

### Post by MaX on 2008-10-03
> **Lorenz said:**
> I have a similar problem with Deluge. Previous versions of it (before 1.0) always gave me great speeds, while leaving the internet performance while browsing untouched. 

All the RCs and now the final version of 1.0 makes it impossible to surf the web and use Deluge, additionally I cannot connect to seeders either. I will have to go and find an older version of Deluge again - or does anyone here know a solution? I don't have this problem with any other torrent client, but I made my best experiences with the older Deluge versions, so I'd like to keep on using it...

Have you tried asking in the Deluge forums?
If it's a regression you might want to report it to them instead of just posting here.

---

### Post by meastp on 2008-10-03
I had this exact problem. Browsing and download speeds (in Deluge) were very slow. Also, Deluge made my Pidgin connections terminate.

**Solution:**

(Note that I haven't tweaked/experimented with optimal settings, but this works)

Max. Connections : 100
Max. Half Open Connections: 80
Max. Connection Attempts per Second: 8

Note that you have to restart Deluge for the setting changes to have effect.

Also, you may want to set your upload speed.

*In my opinion, Deluge should have something like the above as default, and not everything set to unlimited.*

---

### Post by Lorenz on 2008-10-03
> **wgrant said:**
> Have you tried limiting the upload speed? That often helps.

I usually limit the download to 200kb/s which leaves 100 kb/s for surfing (upload limited to 30kb/s). Weird thing is, as I said, that I didn't have those problems with the previous versions of Deluge.

@maX: will post in the Deluge forums now, good idea
@meastp: thank you for the suggestion, will try that right away!

---

### Post by meastp on 2008-10-04
> **Lorenz said:**
> I usually limit the download to 200kb/s which leaves 100 kb/s for surfing (upload limited to 30kb/s). Weird thing is, as I said, that I didn't have those problems with the previous versions of Deluge.

@maX: will post in the Deluge forums now, good idea
@meastp: thank you for the suggestion, will try that right away!

Did it help?

Yeah, until I limited the connections, the download/upload limits had no effect for me, either. The reason it worked in previous versions of Deluge, is that they didn't have those connection settings set to unlimited, I guess.

---

### Post by Lorenz on 2008-10-04
> **meastp said:**
> Did it help?

Yeah, until I limited the connections, the download/upload limits had no effect for me, either. The reason it worked in previous versions of Deluge, is that they didn't have those connection settings set to unlimited, I guess.

No, didn't work unfortunately :(
Whatever I set in Deluge, it completely locks up my internet connection and I cannot access any website anymore. I went back to the latest 0.5 version and that works a treat.

---

### Post by schmickey on 2008-10-07
Ever look into Usenet? Giganews costs a bit, but d/l speeds are good and don't affect my browsing.

---

### Post by TenPlus1 on 2008-10-07
Try changing the settings to these (for 2mb line):

Global:
Max Connections = 600
Max Upload Slots = 6
Mac Download Speed = -1.0 (max)
Max Upload Speed = 20
Max Half-Open Connections = 10
Max Connection Attempts Per Sec = 8

Per Torrent:
Max Connections = 150
Max Upload Slots = 2
Max Download Speed = -1.0 (max)
Max Upload Speed = 20

---

