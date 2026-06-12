---
title: "How do I run BitTorrent?"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by dmckenna on 2008-02-01
I have installed the 7.1 version of Ubuntu and when I look at the programs installed it shows that Bittorrent has been installed.

How do I run Bittorrent on my system?

---

### Post by lespaul_rentals on 2008-02-01
Click on the menu, open the BitTorrent client of your choosing, and load a torrent?

I'm not sure I understand what you're asking.

---

### Post by erfahren on 2008-02-01
to download a torrent - (look here for example: [http://releases.ubuntu.com/7.10/](http://releases.ubuntu.com/7.10/))

scroll down to the list of downloads and if you click on one ending with ".torrent" it will dowload and the BitTorrent client will "take over" the download.

---

### Post by costre on 2008-02-03
Well, it's all good when you want to download. Just download a torrent and it will start. 

I am concerned with how to seed. How can I be sure that there is a program running seeding all my data? A window that pops up and goes away as soon as the download is finished doesn't do it for me. 

As many torrent sites require you to seed as much as you can, it would be nice to have more control over your torrents.

---

### Post by PmDematagoda on 2008-02-03
You can install a more featured torrent client called Deluge using:-      ```
sudo apt-get install deluge-torrent
``` After installation Deluge can be found in Applications>Internet>Deluge

---

### Post by erfahren on 2008-02-03
> **costre said:**
> Well, it's all good when you want to download. Just download a torrent and it will start. 

I am concerned with how to seed. How can I be sure that there is a program running seeding all my data? A window that pops up and goes away as soon as the download is finished doesn't do it for me. 

As many torrent sites require you to seed as much as you can, it would be nice to have more control over your torrents.
go to System > Administration > Synaptic Package Manager - open it and search for "bittorrent"

along with the default bittorrent program that's installed on Ubuntu there should be "bittornado"  along with the "bittornado-gui" package. See the description - iIt might be what you want.

---

### Post by costre on 2008-02-03
I haven't tried it out completely, but I feel BitTornado is pretty much the same as BitTorrent. 
It gives you more info, sure, but it's still one window for each torrent. Not a single program you can run, and immediatly resume any torrents you were seeding.

---

### Post by orange2k on 2008-02-03
Transmission will be the default torrent client in Hardy and here you can find the packages for Gutsy: [http://www.getdeb.net/app/Transmission](http://www.getdeb.net/app/Transmission)

Deluge is also a very nice and fast torrent client. Packages are here: [http://deluge-torrent.org/downloads.php](http://deluge-torrent.org/downloads.php)

---

### Post by costre on 2008-02-04
I have found a great replacement for the standard BitTorrent application. 
It is called Deluge Torrent. Download it and check it out. 

It presents a clean window where your active torrents are listed. Data on all torrents are available. 
I just downloaded a torrent, chose to "always open" it with Deluge Torrent and it works like a charm!  \\:D/

---

### Post by defazn on 2008-02-07
thanks for the recommendation of deluge-torrent..been looking for a replacement over bittorrent other than azureus :)

---

### Post by cryptozoologist on 2008-02-08
i have been very happy with ktorrent available from your friendly neighborhood repos.

peace
cryptozoologist

---

