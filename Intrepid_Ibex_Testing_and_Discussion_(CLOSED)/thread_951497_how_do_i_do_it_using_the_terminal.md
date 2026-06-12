---
title: "how do i do it using the terminal?"
date: 2008-10-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by justborn on 2008-10-18
i tried upgrading to ibex using my cd.now when i restarted after upgrade,i couldn't use the comp after logging in .it gets stuck after a login.


i think that it is because some processes didn't take place properly while upgrade.i now am using the terminal form the recovery mode & i think that if i update via internet my comp will become ok.but the thing is that my net connection is also disconfigured and now i want to reconfigure it in the terminal a & then update to solve the problem,please help me by giving me the terminal commands to set my net connection


for doing so i want to know how to do the following

1.set my ip as static .
2.set my ip address as 192.168.1.2
3.set my network mask as 255.255.255.0
4.set my gateway as 192.168.1.1
and how do i activate this connection?

---

### Post by sisco311 on 2008-10-18
post the output of:
```
ifconfig
```and
```
cat /etc/network/interfaces
```

---

### Post by justborn on 2008-10-18
> **sisco311 said:**
> post the output of:
```
ifconfig
```and
```
cat /etc/network/interfaces
```

isn't ifconf for on the ip address
how do i dothe rest?

---

### Post by sisco311 on 2008-10-18
ifconfig shows the status of the currently configured interfaces.

/etc/network/interfaces is the configuration file of the network interfaces.

EDIT: oh, you are in recovery mode.
in recovery mode the network is not started.

try:```
sudo /etc/init.d/networking start
```to start the network.

---

### Post by justborn on 2008-10-18
> **sisco311 said:**
> ifconfig shows the status of the currently configured interfaces.

/etc/network/interfaces is the configuration file of the network interfaces.

it did show ,and the settings are correct.but when i tried to upgade it didn't happen ,is the a way to check if my comp is connected or not
 and if not how do i connect it using the command line?

---

### Post by sisco311 on 2008-10-18
i've edited my post above.

---

### Post by justborn on 2008-10-18
> **sisco311 said:**
> ifconfig shows the status of the currently configured interfaces.

/etc/network/interfaces is the configuration file of the network interfaces.

EDIT: oh, you are in recovery mode.
in recovery mode the network is not started.

try:```
sudo /etc/init.d/networking start
```to start the network.


it did work 
but still when i try to update



the comp fails to fetch the sites

---

### Post by justborn on 2008-10-18
my comp is not ableto resolve the sites from which to update

---

### Post by tukuyomi on 2008-10-18
What if you type ```
# dhclient
```?

---

### Post by justborn on 2008-10-18
> **tukuyomi said:**
> What if you type ```
# dhclient
```?
dhclient seems to be ok


but i have this error
wwhen i try to update"failed to fetch http//repoubuntusoftware.info/dists/hardy/all/binary-i386/pakages.gz 404 not found
some index files failed to download,they have been ignored,or old once used instead."

please help me ......

---

### Post by sisco311 on 2008-10-18
The Ultimate Linux reposietories are down.

Disable them from the sources.list and try the update again.

---

### Post by justborn on 2008-10-18
> **sisco311 said:**
> The Ultimate Linux reposietories are down.

Disable them from the sources.list and try the update again.

can i disable all third-party repositories and then try to update?

---

### Post by justborn on 2008-10-18
> **sisco311 said:**
> The Ultimate Linux reposietories are down.

Disable them from the sources.list and try the update again.

and wha do u mean by"the ultimate linux repositories are down"

---

### Post by sisco311 on 2008-10-18
yes, type:
```
sudo nano /etc/apt/sources.list
```to edit the sources.list.

place a comment symbol (#) in front of any lines that mention 'repoubuntusoftware'.

save the file and exit(Ctr;+o, Enter, Ctrl+x).

then run:
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by tukuyomi on 2008-10-18
http//repoubuntusoftware.info/dists/hardy/all/binary-i386/pakages.gz
is not a valid address. Furthermore, 
[http://repoubuntusoftware.info/dists/hardy/all/binary-i386/pakages.gz](http://repoubuntusoftware.info/dists/hardy/all/binary-i386/pakages.gz)
is not found either for me. Maybe the repo is down...?
But still, the main site at [http://repoubuntusoftware.info/](http://repoubuntusoftware.info/) is up, so I suggest you to wait for some time to let them fix the repository :)

---

### Post by justborn on 2008-10-18
> **sisco311 said:**
> yes, type:
```
sudo nano /etc/apt/sources.list
```to edit the sources.list.

place a comment symbol (#) in front of any lines that mention 'repoubuntusoftware'.

save the file and exit(Ctr;+o, Enter, Ctrl+x).

then run:
```
sudo apt-get update
sudo apt-get upgrade
```


dude please can u just paste all the working ibex repositories i'll  delete all the repositories in the source list and add only the needed once
this will be a better idea to solve my problem ,isn't?

and by doing this iwill be sure that nothing else is wrong with my system

---

### Post by sisco311 on 2008-10-18
backup the original file:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

change the sources.list so it only contains this:
> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted universe multiverse

then run:
```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

### Post by justborn on 2008-10-18
> **sisco311 said:**
> backup the original file:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

change the sources.list so it only contains this:


then run:
```
sudo aptitude update
sudo aptitude dist-upgrade
```

i'll try it ,can i cp the list to the root directory itself?

---

### Post by justborn on 2008-10-18
> **sisco311 said:**
> backup the original file:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

change the sources.list so it only contains this:


then run:
```
sudo aptitude update
sudo aptitude dist-upgrade
```

should i start the line with "#" or "##"?

---

### Post by sisco311 on 2008-10-18
> **justborn said:**
> i'll try it ,can i cp the list to the root directory itself?

yes, it's just a buckup, you can copy it wherever you want.

---

### Post by justborn on 2008-10-18
> **sisco311 said:**
> yes, it's just a buckup, you can copy it wherever you want.

i have backed it up,not i should clear my whole source.list and type what ........ in it?

---

### Post by sisco311 on 2008-10-18
> **justborn said:**
> should i start the line with "#" or "##"?
no, a line starting with # or ## is a comment and will be ignored.

example:
> #this is a comment :)
##the line below is a comment:
#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted universe multiverse
##the line below is NOT a comment
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted universe multiverse

---

### Post by sisco311 on 2008-10-18
> **justborn said:**
> i have backed it up,not i should clear my whole source.list and type what ........ in it?

yes clear the whole file and type a single line:
```
deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted universe multiverse
```

---

### Post by justborn on 2008-10-18
> **sisco311 said:**
> no, a line starting with # or ## is a comment and will be ignored.

example:

i completely get u,i have typed in the repository 
now how do i save it and exit?

---

### Post by sisco311 on 2008-10-18
> **justborn said:**
> i completely get u,i have typed in the repository 
now how do i save it and exit?

press Ctrl+o, Enter to save the file and
Ctrl+x to exit.

---

### Post by justborn on 2008-10-18
> **sisco311 said:**
> press Ctrl+o, Enter to save the file and
Ctrl+x to exit.

saved and i did exit,now  i should first connect to the net (becoz i am in recovery mode--root shell)& then perform the update command & then ugrade commang
am i rite?

---

### Post by sisco311 on 2008-10-18
yes.

---

### Post by justborn on 2008-10-18
> **sisco311 said:**
> yes.

i am logged-in in the fail-safe terminal session
and i tried synaptic
and tried to reload,but it gives me an error 

W.failed to fetch ............(five repositories-five lines)

what should i do?

---

### Post by justborn on 2008-10-18
> **sisco311 said:**
> yes.
when i try "apt-get upgrade"

i get"E: sub-process /usr/bin/dpkg returned an error code (1)"

what should i do?

---

### Post by sisco311 on 2008-10-18
> **justborn said:**
> when i try "apt-get upgrade"

i get"E: sub-process /usr/bin/dpkg returned an error code (1)"

what should i do?

try:
```
sudo apt-get -f install
sudo apt-get upgrade
```

---

### Post by justborn on 2008-10-18
> **sisco311 said:**
> try:
```
sudo apt-get -f install
sudo apt-get upgrade
```

after trying the first command i get the same error

---

### Post by Sef on 2008-10-18
Moved to Ibex forum.

---

### Post by justborn on 2008-10-20
my comp skipped some index files while upgrading to ibex,can some one tell the command(s)for installing the required index files,so that i can work on my gnome-normal session .(rem ,i am in the recovery mode,and ihave dropped myself into the root prompt)

---

### Post by netz on 2008-10-20
If you have an working internet connection logged in as root try:

```

apt-get update
apt-get dist-upgrade
apt-get install ubuntu-desktop
```

---

### Post by GuitarRocker2562 on 2008-10-20
just run dpkg --configure -a to make sure something didn't fail to install.

---

### Post by justborn on 2008-10-21
> **netz said:**
> If you have an working internet connection logged in as root try:

```

apt-get update
apt-get dist-upgrade
apt-get install ubuntu-desktop
```
i have tried it earlier,but it didn't work

---

### Post by justborn on 2008-10-21
> **GuitarRocker2562 said:**
> just run dpkg --configure -a to make sure something didn't fail to install.

running the command doesn't give me any error

---

### Post by nystire on 2008-10-21
and if you rerun the suggested apt-get commands do you still get an error?

---

### Post by justborn on 2008-10-21
> **nystire said:**
> and if you rerun the suggested apt-get commands do you still get an error?

no,not at all ,now i have installed all the index files but still my comp won't work normally.it just gets stuck after i log-in.

---

