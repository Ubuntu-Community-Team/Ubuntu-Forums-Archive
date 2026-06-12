---
title: "Gutsy saying up to date on update manager"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by HazeUK on 2008-07-05
My gutsy 7.10 is not letting me update to 8.

Can't work out why, and I can't install a linux msn, having to use a web based one.

Thanks, Haze

---

### Post by Pumalite on 2008-07-05
To get ready to upgrade; you need to remove all third parties from your sources.list, including the Medibuntu folder if you have it as a repo. You need to be fully updated. Then try again. If that doesn't, you might want to try the Alternate CD:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by HazeUK on 2008-07-06
Can I get a simple-ish guide as to what to do? I also can't install Pidgin MSGer cause it says there's a conflict or some dependancy problem.. annoying.

---

### Post by zvacet on 2008-07-06
As Pumalite adviced you g oto the system>admin<software sources and under third party tab uncheck all.Reload.In terminal 

```
sudo apt-get update && sudo apt-get upgrade
```

Then go to the system>admin>update manager and you should see message that new version is available for upgrade.When you finish with upgrade go again to the system>admin>software sources and check third party repos.Reload.

```
sudo apt-get upgrade
```

---

### Post by HazeUK on 2008-07-06
Using terminal does basically the same error as the GUI'd add remove program bit when I try to update list.


> haze@Haze-Gamer:~$ sudo apt-get update
[sudo] password for haze:
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg                      
  Could not connect to security.ubuntu.com:80 (42.1.4.80). - connect (113 No route to host)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg                                                                            
  Could not connect to archive.ubuntu.com:80 (42.1.4.80), connection timed out
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy Release.gpg                                                                         
  Could not create a socket for 2a01:450:10:1::10 (f=10 t=1 p=6) - socket (97 Address family not supported by protocol) [IP: 2a01:450:10:1::10 80]
0% [Connecting to archive.ubuntu.com (42.1.4.80)] [Connecting to gb.archive.ubuntu.com (42.1.4.80)] [Connecting to security


---

### Post by iaculallad on 2008-07-06
Do post the output of the terminal command below:

```
cat /etc/hosts
```

---

### Post by Pumalite on 2008-07-06
Check your connection. Are you behind a proxy?

---

### Post by HazeUK on 2008-07-06
haze@Haze-Gamer:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 Haze-Gamer

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


----------


I'm not behind a proxy, not that I know of atleast :lolflag:

Had been having problems with my wifi though...

---

### Post by iaculallad on 2008-07-06
Try to unset your proxy then redo the update:

```
unset http-proxy
sudo apt-get update
```

---

### Post by HazeUK on 2008-07-06
haze@Haze-Gamer:~$ unset http-proxy
bash: unset: `http-proxy': not a valid identifier

-----------


:confused:

---

### Post by iaculallad on 2008-07-06
> **HazeUK said:**
> haze@Haze-Gamer:~$ unset http-proxy
bash: unset: `http-proxy': not a valid identifier

-----------


:confused:

My mistake, that should be an underscore character:

```
unset http_proxy
sudo apt-get update
```

Could you try it again and post any displayed error or mesages.

---

### Post by HazeUK on 2008-07-06
> haze@Haze-Gamer:~$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory


Ty for help :)

---

### Post by Pumalite on 2008-07-06
Close Synaptic

---

### Post by iaculallad on 2008-07-06
> **HazeUK said:**
> Ty for help :)

That's a good error, at least it only says that there's an active apt-get or update manager process running in background. Try to kill/stop/end those process and proceed with your normal **sudo apt-get update**.

To view the process:

```
ps | grep apt
ps | grep sudo
ps ax | grep apt
```

What does this command displays?

```
ps ax | grep apt
```

---

### Post by HazeUK on 2008-07-06
I closed the package manager, it still times out or doesn't pass the security or something.

> haze@Haze-Gamer:~$ ps ax | grep apt
 5288 pts/2    S+     0:00 apt-get update
 5290 pts/2    S+     0:00 /usr/lib/apt/methods/http
 5291 pts/2    S+     0:00 /usr/lib/apt/methods/http
 6320 pts/0    R+     0:00 grep apt


---

### Post by iaculallad on 2008-07-06
> **HazeUK said:**
> I closed the package manager, it still times out or doesn't pass the security or something.

On your terminal, kill the existing process for apt-get update:

```
sudo kill -9 5288
sudo apt-get update
```

---

### Post by HazeUK on 2008-07-06
> haze@Haze-Gamer:~$ sudo apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg                      
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_GB     
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg                                
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
0% [Connecting to archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.


it's doing this again :(

---

### Post by iaculallad on 2008-07-06
Is this your first time to update? Try to change your download server. Navigate to System->Administration->Software Sources, on the "Ubuntu Software" tab, check if Main, Universe, Restricted, and Multiverse are all checked. Change "Download From:" to "Main Server". Click on close button and drop to your terminal again:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by HazeUK on 2008-07-07
Ok last night it started working.. I could download things etc, now it's not connecting to things again.. it was working shortly after I booted linux but as I said it's not working again.

> haze@Haze-Gamer:~$ sudo apt-get update
0% [Connecting to archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu


I tried ending all possible processes to make sure there wasn't a conflict but it's the internet or some connectivity issue :(


Edit: I am trying to download package info btw, in add/remove apps.

---

