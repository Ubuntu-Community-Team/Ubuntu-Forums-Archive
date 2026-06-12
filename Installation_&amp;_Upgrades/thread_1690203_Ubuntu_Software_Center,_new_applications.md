---
title: "Ubuntu Software Center, new applications?"
date: 2011-02-18
forum: Installation &amp; Upgrades
---

### Post by FlurrYx on 2011-02-18
Hi there fellows !

Does anybody know how one can get the Ubuntu software Center to display new software? 

I use Live Ubuntu and Puppy USB's as an OS for different computers. So that I can always have an OS in my back-pocket, and with that live OS there might be applications that I want to install easily each time I want to install it.

Does it have anything to do with APT lines perhaps?

Thanks in advance! ;)

---

### Post by sikander3786 on 2011-02-18
If you have created a Live USB, perhaps all the changes you make to your Ubuntu are vanished at every reboot.

For displaying new software in Software Center, you need to refresh your index. Just run this command in a Terminal.

```
sudo apt-get update
```

Then you can use Software Center, Synaptic, apt-get or whichever package manager you want to.

---

### Post by FlurrYx on 2011-02-22
You can choose when creating the Live USB that you want to store documents and setting in a reserved space, in my case it'll be room for 1.2 gigabytes  for some documents and settings :)

Sorry for stating the question a bit messy, what I want to do is being able to add new repositories for third party software through the terminal

To exemplify, if a want to add spotify:
edit /etc/apt/sources.list

$deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free

$sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E9CFF4E

$sudo apt-get update

$sudo apt-get install spotify-client-qt spotify-client-gnome-support
This fails to work, any ideas ? :/

---

