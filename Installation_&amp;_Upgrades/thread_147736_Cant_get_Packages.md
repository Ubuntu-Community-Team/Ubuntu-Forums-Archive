---
title: "Cant get Packages"
date: 2006-03-20
forum: Installation &amp; Upgrades
---

### Post by trejo23 on 2006-03-20
Hi im very noob but i have tried all the help i want my packages for ubuntu, i need certain packages for samba i.e samba-server and i need the apache packages BUT i cant get them this is becoming frustrating i have tried apt-get commands with errors like....

---------------------------------------------------------------------------------------------------
test@wt404-67-136:~$ sudo apt-get dist-upgrade
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
-----------------------------------------------------------------------------------------------------

i have tried to use synaptic which gave that output below

---------------------------------------------------------------------------------------------------
[http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:) Could not connect to archive.ubuntu.com:80 (82.211.81.151). - connect (113 No route to host) [IP: 82.211.81.151 80]
---------------------------------------------------------------------------------------------------
and
----------------------------------------------------------------------------------------------------
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list 
-----------------------------------------------------------------------------------------------------

i have checked connectivity i can use a browser and connect to the repositories....
i have pinged with a destination host not reachable, i am however using a proxy.

plz any help would be good.
i really am gonna cry......

---

### Post by dragomirov on 2006-03-20
```
est@wt404-67-136:~$ sudo apt-get dist-upgrade
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

this is because you use apt-get when synaptic is running (or vice-versa)

```
http://archive.ubuntu.com/ubuntu/dis...y/Release.gpg: Could not connect to archive.ubuntu.com:80 (82.211.81.151). - connect (113 No route to host) [IP: 82.211.81.151 80]
W: Couldn't stat source package list http://archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary -i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_ binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list
```
do you add the key for that repository? Do you have configured the proxy for apt-get?

1) Adding a key for a certain repository: 
```
sudo apt-key filename
```

2) configuring apt-get for using a proxy:
edit /etc/wgetrc

find the line where "http_proxy" and "ftp_proxy", delete the sharp (#) symbol and modify proxy connection with your connection

3) configuring synaptic:

Open synaptic and go to "settings->preferences->network" then add the proxy

h&k

---

### Post by trejo23 on 2006-03-21
hey thanks for the reply i have tried too add a key the Releases.gpg key but it gives a corruption error, i have tried to configure the apt-get file wgetrc but i think i might need the admin to give me some details on the proxy yeah right he will ohhh dear:(  also the key jus isnt working when i try to add.

created directory /home/.gnupg

i think my major problem is this i cant connect ping the site through a terminal or traceroute to these sites in terminal i can use browser i think maybe the only choice at this stage is to download the packages i need for now.

thanks for the help i had a smile for awhile lol  ----->:-D ------->:-| ---------->:(

---

### Post by trejo23 on 2006-03-21
ok hey again i have the details of the proxy i have tried all the pointers you have suggested with no luck :(  except the first i.e the key i have problems with this too...
i have tried the proxy configuration in synaptic still nothing any ideas??

we are moving forward slowly hehe.

---

### Post by dragomirov on 2006-03-22
Hey I'm really running out of ideas. 

Once I was under a proxy and updating was a real pain. If your sysadmin has blocked all your tcp/ip traffic apart from the 80 port (the one yr browser use)...well you can't escape. 

Begging your sysadmin because you need to be upgraded for security matters.
Or you can just corrupt your administrator (every morning coffee?) to let you upgrade ;)

I think (better, I hope) you were behind a transparent proxy, but probably it isn't.

tell me if any new and sorry for the late

---

### Post by trejo23 on 2006-03-22
Hey thanks for the help i no what the problem is the admin has made my account limited ??yeah great lol, so how does this help me it doesnt so i have just decided its ok i have firestarter (standard firewall) so not worried well as for the upgrades its not ubuntu thats messin with me lol, im glad it just wasnt the distributuion bein a pain in the *** like some i have come across.

thanks.8)

---

