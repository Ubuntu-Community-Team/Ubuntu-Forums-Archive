---
title: "installing g++"
date: 2008-04-21
forum: Installation &amp; Upgrades
---

### Post by mkrahmeh on 2008-04-21
guys
am trying to use eclipse CDT for building c++ apps, but it keeps generating g++ commands, 
now am trying to install g++ but its not working with me..i tried the following:
<sudo aptitude install build-essential> on the terminal, i also tried
<sudo apt-get install g++-3.4> which prompted an error about dependency stuff

finally synoptic and adept manager are not being helpful (am new at linux so lets say am not getting along yet :)) 
how can i install the g++ ??

---

### Post by Rocket2DMn on 2008-04-21
build-essential is the right package (it's actually a metapackage).
Try just using apt-get and if it doesn't like the command, post the output here
```
sudo apt-get install build-essential
```
You may need to enable the universe/multiverse repositories from System->Administration->Software Sources, though I don't think it's necessary for this package.

---

### Post by mkrahmeh on 2008-04-21
the apt-get command yielded the following error log
Reading package lists... Done

```
Building dependency tree
Reading state information... Done
E: Couldn't find package build-essentia
```

furthermore, it ddnt prompt me to enter the root's password..
then i tried 
```
mkrahmeh@mkrahmeh-laptop:~$ g++
The program 'g++' can be found in the following packages:
 * g++
 * pentium-builder
Try: sudo apt-get install <selected package>
bash: g++: command not found

```

what do u think?? thx

---

### Post by Rocket2DMn on 2008-04-21
I think you might need to check your repository sources.  Go to System->Administration->Software Sources and make sure the first 4 boxes are checked (main, universe, restricted, multiverse).
Close that, allow it to update, then open a terminal and run
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential
```
If it doesn't go through, copy and paste EVERYTHING here including the command.  Also make sure you spell it correctly :)
(the apt-get update shouldn't be necessary once the Software Sources program asks you to update, but it's just there for good measure.)

---

### Post by mkrahmeh on 2008-04-22
the four checkboxes are checked in software sources..
however, due to previously failed attempts to install the g++, i had to
```
sudo apt-get install -f
```
and the g++-3.4 was removed

now the 
```
sudo aop-get update
sudo apt-get upgrade
```

failed to fetch the ubuntu http resources, as the error indicates
so am afraid that the apt-get manager is not connecting to the internet properly (as for the other package managers)..what do i need to do in such case? given that am browsing the web smoothly !!
thx

---

### Post by mkrahmeh on 2008-04-22
i tried to
```
ping www.google.com
```
for instance, and the result was 4 packets transmitted, 0 received, 100% packet loss
what is going on exactly???? am using firefox and everything is fine....:confused:
the apt-get update error included
```
Err http://archive.ubuntu.com gutsy/universe Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.45). - connect (111 Conn
ection refused) [IP: 91.189.88.45 80]
```
and many others alike..which prompted me to do the ping test
thx

---

### Post by Rocket2DMn on 2008-04-22
That sounds like a DNS problem.  What do you have in
```
cat /etc/resolv.conf
```
You can try resetting your router then computer to hopefully refresh the DNS, otherwise you may need to either
1) copy the DNS info from your router's status page into /etc/resolv.conf (including the search domain and the nameserver DNS IPs)
2) disable ipv6 (I don't think this help much anymore)
3) input publicly available DNS servers into /etc/resolv.conf

It is also possible that the repositories are acting up, they do weird things sometimes.  You may consider switching to a local mirror of the repositories.

---

### Post by mkrahmeh on 2008-04-25
[SIZE="4"][SOLVED][/SIZE]

I looked into resolv.conf but everything seemed to be fine there..
however, through network settings i found out that the system looks for variables named http_proxy and ftp_proxy for setting http and ftp settings respectively, so i ventured to declare these global variables manually in the /etc/profile as 
export http_prox="*proxy server*"
export http_ftp="*ftp server*"

now everything is up and going..ofcourse after 
```
sudo apt-get update
sudo apt-get upgarde
sudo apt-get install build-essential
```

thx alot..
Mohammed Abu Rahmeh
:guitar:

---

