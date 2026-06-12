---
title: "How to change GNOME main menu style to UbuntuStudio in Intrepid ?"
date: 2008-10-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Jags_FL on 2008-10-19
How do I change GNOME main menu style to UbuntuStudio (screenshot attached) in Intrepid ?

Tried to customize it thru 'System'  >>  'Preferences'  >>  'Main Menu' but I couldn't include/merge Places, System, Lock Screen, Log Out and Shutdown, all under single/main menu.

Many thanks.

---

### Post by armageddon08 on 2008-10-19
Right Click on the main menu and select Remove from panel. Then Right-Click on the panel and select add to panel. From the list choose 'Main Menu'.

---

### Post by Jags_FL on 2008-10-19
@ 'armageddon08' Thanks a million. Gosshh It was easy... and I tried everything else  :)

On a related note: I just installed bittorrent, bittorrent-gui and python-bittorrent thru Synaptic but after installation I cannot find bittorrent executable in /usr/bin/, neither it created any entry in 'Internet'...

How do I run bittorrent ??   Many thanks.

Edit: How do I get apps minimized on top panel instead of bottom one ?

---

### Post by armageddon08 on 2008-10-19
> **Jags_FL said:**
> @ 'armageddon08' Thanks a million. Gosshh It was easy... and I tried everything else  :)

On a related note: I just installed bittorrent, bittorrent-gui and python-bittorrent thru Synaptic but after installation I cannot find bittorrent executable in /usr/bin/, neither it created any entry in 'Internet'...

How do I run bittorrent ??   Many thanks.

Edit: How do I get apps minimized on top panel instead of bottom one ?
1. You can use Transmission. It is available in Apps > Internet.
2. Right Click on the separator at the left in the lower panel and select 'Remove from panel'. Right Click on the top panel and select 'Add to panel' and select Window List from the list.

---

### Post by Jags_FL on 2008-10-19
goshh again it was right there and I didn't see it... 

```
1. You can use Transmission.
```

Somehow I don't get enough speed(almost 50% compare to uTorrent on the same machine) with Transmission(yes, port is open in router firewall). So thought to give a try to BitTorrent as I get 100% speed(of my 10 MBit/s connection) with uTorrent in Win XP.

Thanks again.

---

### Post by armageddon08 on 2008-10-19
> **Jags_FL said:**
> goshh again it was right there and I didn't see it... 

```
1. You can use Transmission.
```

Somehow I don't get enough speed(almost 50% compare to uTorrent on the same machine) with Transmission(yes, port is open in router firewall). So thought to give a try to BitTorrent as I get 100% speed(of my 10 MBit/s connection) with uTorrent in Win XP.

Thanks again.

Yeah....Transmission is a bit slow(I'm using it myself right now). Perhaps, it is possible to run uTorrent using Wine(am not sure). Search for it, it should be somewhere in the forums.....else google is always there.

***_[EDIT]_*** Here this might help: 
[http://www.jumbabox.com/2008/06/installing-the-utorrent-and-webui-client-on-ubuntu-hardy/]("http://www.jumbabox.com/2008/06/installing-the-utorrent-and-webui-client-on-ubuntu-hardy/")

---

### Post by Jags_FL on 2008-10-19
armageddon08

Many thanks for your help. Though I've read about Wine before, never installed it. Installed Wine & opened uTorrent.exe (right click >> open with Wine).

Still uTorrent doesn't show up in Wine >> Programs list... so do I have to run uTorrent.exe every time or am I missing something and its not getting installed properly.

---

### Post by armageddon08 on 2008-10-19
Congrats! On the problem.....may be you could try uninstalling and reinstalling uTorrent.

**_*[EDIT]*_**Okay...I'd a look at it probably you have to do it that way. Because you are not installing uTorrent just running the executable. You might be able to add it to the Programs menu by some command which I don't know. Perhaps others may be able to help you out.

---

### Post by Jags_FL on 2008-10-19
armageddon08

Thanks again, all of a sudden I saw an entry in Main Menu >> Other >> uTorrent, and when I clicked that, I got the same uTorrent installation screen as before BUT now that 'OTHER' menu has disappeared and I can see a new entry in Main Menu >> Wine >> uTorrent.

I still don't know what happened but it got solved nonetheless.  :)

---

### Post by armageddon08 on 2008-10-19
> **Jags_FL said:**
> armageddon08

Thanks again, all of a sudden I saw an entry in Main Menu >> Other >> uTorrent, and when I clicked that, I got the same uTorrent installation screen as before BUT now that 'OTHER' menu has disappeared and I can see a new entry in Main Menu >> Wine >> uTorrent.

I still don't know what happened but it got solved nonetheless.  :)

You can get the Other menu back. Right Click on the main menu and select Edit Menus. Select Applications on the left side and on the right side tick the check-box next to Other. That should do it. BTW, restart your comp once after doing new installations.

---

