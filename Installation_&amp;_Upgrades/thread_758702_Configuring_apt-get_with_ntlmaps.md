---
title: "Configuring apt-get with ntlmaps"
date: 2008-04-18
forum: Installation &amp; Upgrades
---

### Post by fr3nnwex on 2008-04-18
hi

my college network uses ms proxy authentication and i am having trouble configuring apt-get to work with it. i have read some posts on this forum and elsewhere and tried ntlmaps to work around it. i am able to use it for a lot of applications like firefox but not for apt-get. whatever package i try to install i am asked to do it with apt-get. 

i am relatively new to using linux and would greatly appreciate any help in this regard.

---

### Post by Partyboi2 on 2008-04-18
If you are having problems using apt-get to get the ntimaps package you can download the ntimaps package from [here]("http://packages.ubuntu.com/gutsy/ntlmaps") and install it by double clicking on the package. For other packages you can do a search [here]("http://packages.ubuntu.com/") for it.

---

### Post by XplOzIOn on 2008-04-24
> **fr3nnwex said:**
> hi

my college network uses ms proxy authentication and i am having trouble configuring apt-get to work with it. i have read some posts on this forum and elsewhere and tried ntlmaps to work around it. i am able to use it for a lot of applications like firefox but not for apt-get. whatever package i try to install i am asked to do it with apt-get. 

i am relatively new to using linux and would greatly appreciate any help in this regard.

Hello there i think this might help you:

**First of all you need ntlmaps.**

```
sudo apt-get install ntlmaps
```

You will be asked for parent proxy, port, etc, etc..

After the package is installed edit:

```
sudo gedit /etc/ntlmaps/server.cfg
```

Make sure you have everything there!

After making sure everything in /etc/ntlmaps/server.cfg is set you still need to setup apt to work with ntlmaps

so with your favorite editor edit:

```
sudo /etc/apt/apt.conf
```

```
Acquire::http::Proxy "http://127.0.0.1:5865";
```

Remember that the port used in /etc/ntlmaps/server.cfg is the one you have to use.

Save your setting and restart ntlmaps

```
sudo /etc.init.d/ntlmaps -force-reload
```

DONE! know your apt will download at the connection MAX speed Cheesy

It works for me perfectly.. If any problem let me know!!!! If everything worked let us know so this can be marked as SOLVED

//Thanks!

---

### Post by melbourne on 2008-05-23
will ntlmaps start automatically each time we boot or shud we manually do dat?

---

