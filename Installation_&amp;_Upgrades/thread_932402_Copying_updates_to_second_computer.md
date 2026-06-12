---
title: "Copying updates to second computer"
date: 2008-09-28
forum: Installation &amp; Upgrades
---

### Post by DivinityX on 2008-09-28
I just put UBUNTU to a friend's Laptop. it doesn't have internet access here. (no wireless card) is there a way i can copy my updates to his computer?

K Thanks! =P

---

### Post by WWSmith36 on 2008-09-28
If you are updating between releases, you could just download the latest ISO, burn it to a CD, and use that to update his computer.  I recommend the alternate install CD for this.  Here is a torrent link

May i suggest to install Deluge client, to download torrent files, from [http://deluge-torrent.org/downloads.php](http://deluge-torrent.org/downloads.php) and please download the Ubuntu 8.04 release you need by selecting a .torrent link from [http://releases.ubuntu.com/releases/8.04/](http://releases.ubuntu.com/releases/8.04/)

Here all the Ubuntu releases [http://cdimage.ubuntu.com/releases/](http://cdimage.ubuntu.com/releases/) with .torrent links

If the customer has any special packages installed which were not part of the original install CD, then there may be some things that cannot be upgraded. Your apt update tool of choice should let you know about that though:

apt-cdrom add
aptitude update
aptitude dist-upgrade

Hopefully that does what you need.

You will probably want to remove the CD line from his apt repositories (/etc/apt/sources.list) after the update.

---

### Post by Elfy on 2008-09-28
You could use aptoncd, which is available from the repos and install it on both machines.

```
sudo apt-get install aptoncd
```

However, if there are packages on his machine and not yours then they will not get updated as you wouldn't receive them in the first place.

Would be the same deal if there were dependencies stopping an install on the friends laptop.

---

### Post by DivinityX on 2008-09-28
I just gave him 8.04 but we can't connect him to the internet to get his udates. I'm trying to see if i can get the udates off of my computer and copy them to his computer...is that possible?

---

### Post by Elfy on 2008-09-28
You can use aptoncd to do that, but you could have dependency issues.

I have successfully copied the cache from my machine and updated with the cache, usually when I'm reinstalling the same version on my own pc, but there's no reason why it couldn't be a different machine.

But if you have different packages on your machine than opn your friends laptop it could cause more problems.

Why can't it connect to the net - is it because you can't get it working or soem other reason?

---

### Post by DivinityX on 2008-09-28
his wireless card wasn't working at all, and we had no eathernet cables...so yeah....

---

