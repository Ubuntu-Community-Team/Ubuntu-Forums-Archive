---
title: "where does bittorrent install go"
date: 2005-04-07
forum: Installation &amp; Upgrades
---

### Post by sean451 on 2005-04-07
Hi, I am new to ubuntu, i guess you can call me a "newbie".   Anyway, i installed bittorrent onto my computer(i typed app-get install bittorrent in root console).  The problem i am having is that i dont know where it installed to, or how to open it up, can someone please help me out.....

---

### Post by reddeathdrinker on 2005-04-07
[QUOTE=sean451]Hi, I am new to ubuntu, i guess you can call me a "newbie".   Anyway, i installed bittorrent onto my computer(i typed app-get install bittorrent in root console).  The problem i am having is that i dont know where it installed to, or how to open it up, can someone please help me out.....[/QUOTE]
 Do a file search for Bittorrent.....:)

Appications > Find Files

Personally, I use Azureus fortorrents, as there are more options for controlling bandwidth etc...

---

### Post by bored2k on 2005-04-07
[QUOTE=reddeathdrinker]Do a file search for Bittorrent.....:)

Appications > Find Files

Personally, I use Azureus fortorrents, as there are more options for controlling bandwidth etc...[/QUOTE]
 No no that's not right.
Bittorrent opens up with the command
> btdownloadcurses name.torrent
If you installed the GUI 
> btdownloadgui
If you got  it through apt-get you got and older one, download
[http://www.bittorrent.com/dl/BitTorrent-4.0.1.tar.gz](http://www.bittorrent.com/dl/BitTorrent-4.0.1.tar.gz) , extract and double click on btdownloadgui.py [you have to make it executable first > right click on the file > permissions; another way is through a terminal typing python /home/user/directory/btdownloadgui.py].

And reddeathdrinker, bittorrent has all those "extra" options you say azureus has [at least the ones users use], some people just don't know the commands for them ;).

---

### Post by reddeathdrinker on 2005-04-07
> **bored2k]No no that's not right.
Bittorrent opens up with the command

If you installed the GUI 

If you got  it through apt-get you got and older one, download
[http://www.bittorrent.com/dl/BitTorrent-4.0.1.tar.gz](http://www.bittorrent.com/dl/BitTorrent-4.0.1.tar.gz) , extract and double click on btdownloadgui.py [you have to make it executable first > right click on the file > permissions said:**
> .

And reddeathdrinker, bittorrent has all those "extra" options you say azureus has [at least the ones users use], some people just don't know the commands for them ;).
 Touche :)

It's been a long time since I played with the original BitTorrent program. What I was hoping to get across was that the Azureus is more eeasily configured from the GUI than BitTorrent......

---

### Post by carlc on 2005-04-08
What are you wanting to do with bittorrent? If you click on a bittorrent file that you want to download, you should have an option to "open with" bittorrent. Chose that option and bittorrent will take care of your torrent file.

---

### Post by bored2k on 2005-04-08
[QUOTE=carlc]What are you wanting to do with bittorrent? If you click on a bittorrent file that you want to download, you should have an option to "open with" bittorrent. Chose that option and bittorrent will take care of your torrent file.[/QUOTE]
 That's gnome-bt, not official bittorrent ;). I don't like gnome-bt :-P

---

### Post by carlc on 2005-04-08
> That's gnome-bt, not official bittorrent . I don't like gnome-bt

What's the difference?
Does the official bittorrent use command line?

---

### Post by bored2k on 2005-04-08
[QUOTE=carlc]What's the difference?
Does the official bittorrent use command line?[/QUOTE]
 Official Bittorrent:
[img]http://img28.exs.cx/img28/8268/a3da.jpg[/img]
You can use it from command line and use it in GUI.

Difference? The official client is way more updated [gnome-bt = 3.x / official = 4.0.1], thus supports latest tracker config. Plus, its prettier than anyother btclient :D .

---

### Post by carlc on 2005-04-08
I will have to give it a try. It does seem to have its advantages over gnome-bt.

---

