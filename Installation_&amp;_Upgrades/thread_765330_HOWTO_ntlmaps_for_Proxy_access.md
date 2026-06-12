---
title: "HOWTO: ntlmaps for Proxy access"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by XplOzIOn on 2008-04-24
Just deicided to make an HOWTO from a reply i gave to someone in the archives. Since there is still people having problem to apt-get here is how i finally make everything work right!

**First of all you need ntlmaps.**

```
sudo apt-get install ntlmaps
```

After the package is installed edit:

```
sudo gedit /etc/ntlmaps/server.cfg
```

Fill with proper info EVERY option. Sometimes ntlmaps wont work without a domain configures in the file! remember this!


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

Also configure the proxy setting in your favority internet browser using:

**localhost **and the port your use in **/etc/ntlmaps/server.cfg**

DONE! know your apt will download at the connection MAX speed Cheesy

It works for me perfectly.. If any problem let me know!!!!


**TO-DO:**
I will attach my working /etc/ntlmaps/server.cfg

//note: where the howto goes now? :lolflag:

---

### Post by tech9 on 2008-05-09
> **XplOzIOn said:**
> Just deicided to make an HOWTO from a reply i gave to someone in the archives. Since there is still people having problem to apt-get here is how i finally make everything work right!

**First of all you need ntlmaps.**

```
sudo apt-get install ntlmaps
```After the package is installed edit:

```
sudo gedit /etc/ntlmaps/server.cfg
```Fill with proper info EVERY option. Sometimes ntlmaps wont work without a domain configures in the file! remember this!


After making sure everything in /etc/ntlmaps/server.cfg is set you still need to setup apt to work with ntlmaps

so with your favorite editor edit:

```
sudo /etc/apt/apt.conf
``````
Acquire::http::Proxy "http://127.0.0.1:5865";
```Remember that the port used in /etc/ntlmaps/server.cfg is the one you have to use.

Save your setting and restart ntlmaps

```
sudo /etc.init.d/ntlmaps -force-reload
```Also configure the proxy setting in your favority internet browser using:

**localhost **and the port your use in **/etc/ntlmaps/server.cfg**

DONE! know your apt will download at the connection MAX speed Cheesy

It works for me perfectly.. If any problem let me know!!!!


**TO-DO:**
I will attach my working /etc/ntlmaps/server.cfg

//note: where the howto goes now? :lolflag:

Hi XplOzIOn,

    Did you get this working in PCLinuxOS Gnome 2008 or PCLinuxOS 2007? Because I was able to install and get ntlmaps working under ubuntu. My question was has anyone got it working under those OS as stated earlier? I know how to install and configure ntlmaps.

see original post...
[http://ubuntuforums.org/showthread.php?p=4919644#post4919644](http://ubuntuforums.org/showthread.php?p=4919644#post4919644)

Thanks for the reply,

T9

---

### Post by hotstepperk on 2009-05-12
Thanks a million! that worked PERFECTLY for me

---

### Post by XplOzIOn on 2009-05-12
> **hotstepperk said:**
> Thanks a million! that worked PERFECTLY for me

Great!

I also use this to bypass proxy under Windows now hahaha.

Everyone at work is loving me for this :guitar:

---

### Post by hotstepperk on 2009-05-21
Wait... are u for real. it bypasses proxies now!

---

### Post by hotstepperk on 2009-06-30
Has anyone noticed how much resources is taken up my the main.py application when ntlmaps is in use?? Its starting to get to me as it takes up 50% of my cpu! help!! :confused:

---

### Post by XplOzIOn on 2009-06-30
Wow... thats strange! It doesnt happen like that here.

---

### Post by hotstepperk on 2009-07-02
Yeah, well, mine does. Now I'm starting to worry. Any ideas on what may be causing it?

---

