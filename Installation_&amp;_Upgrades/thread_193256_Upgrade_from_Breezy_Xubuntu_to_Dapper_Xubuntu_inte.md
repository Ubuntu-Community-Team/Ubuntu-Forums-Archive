---
title: "Upgrade from Breezy Xubuntu to Dapper Xubuntu interrupted"
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by djjazzyjeff on 2006-06-09
I had a problem with this uprade that I caused myself and I'm probably screwed but I thought I'd take a shot here.  

I went here [https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades) and took the steps in "Upgrading from an Ubuntu 6.06 CD".  It seemed to want to go out on the internet to get the upgraded components instead of the CD but this was OK as I had a good connection. After retrieving the components, the installation of them began. This stopped at one point looking for my input about which version of /etc/aliases I wanted to keep. I entered the character that displays the differences in the 2 versions and somehow got messed up returning to the install. I ended up doing a Ctrl-C that aborted the dist-upgrade process and then shutdown the system! What an idiot :cry: 

Now when I start the machine it fails to start X and I can't get networking to start. Is there any way to recover my upgrade by picking up where it left off or maybe the components are still on my system and I could rerun dist-upgrade from the beginning. I've not installed Dapper yet but I figure I could reinstall if I had to and just retain my existing /home partition whci I created as a separate file system for upgrading convenience. 

BTW, if anyone can get me out of this self-inflicted mess I promise never to be stupid again :rolleyes:

---

### Post by rbeldin on 2006-06-09
I had similar problems with an upgrade from Breezy.  I thought maybe I could force my out with apt, so I did a: 

apt-get dist-upgrade -f

It told me that I had a bunch fo errors and that dpkg had not finished.  Finally, it indicated that I should try: 

dpkg configure -a 

At least that is what I recall... It not longer gives me this message now that I am 'functional'. ...but that is another post.. 

After doing the incantation above, dpkg resumed configuring and installing packages that it had downloaded. Once finished, apt gave no more errors...

---

### Post by djjazzyjeff on 2006-06-10
Het rbelden, this worked and many thanks. The next time I attempt to do a version upgrade, I'll wait to start until I have plenty of time. One minor change, when I did the:

apt-get dist-upgrade -f

output stated I needed to do:

dpkg --configure -a

Thanks again, I have a few things to cleanup but Dapper/XFCE looks great!

-Jeff

---

