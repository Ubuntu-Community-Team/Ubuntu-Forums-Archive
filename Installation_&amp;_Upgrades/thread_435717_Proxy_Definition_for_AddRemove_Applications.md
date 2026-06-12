---
title: "Proxy Definition for Add/Remove Applications?"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by Sal-Lutz on 2007-05-07
I am behind a company proxy server.  I have entered the proxy in the System : Preferences : Network Proxy.  That seems to allow the Update Manager to work.  However, the Add/Remove Applications does not work.  It consistently reports a "407 Proxy authorization required" error.

I have not found any settings for the proxy in the Add/Remove Applications, nor any reference on how to do it in the manuals or these forums.

I have successfully installed a distribution (Java6) using apt-get in the Terminal after adding the proxy definition by adding a apt.conf file in /etc/apt in the following format (with my real data of course).

Acquire::http::Proxy "http://user:pass@xxx.xxx.xxx.xxx:port/";
Acquire::ftp::Proxy "http://user:pass@xxx.xxx.xxx.xxx:port/";

Any advice on how to get Add/Remove Applications to work through a proxy?

TIA - Sal :)

---

### Post by bapoumba on 2007-05-07
Hello,
with your current proxy settings in apt.conf, does synaptic work ?

---

### Post by Sal-Lutz on 2007-05-08
No, Synaptic does not work either.  Same error 407.  Even after I enter the Proxy manually under Preferences : Network (I tried entering both the proxy DNS and IP) and my authentication, Synaptic does not work.

Thanks for the reply -

- Sal  ;-)

---

### Post by bapoumba on 2007-05-08
Just for me to understand this correctly: apt-get and aptitude work OK from the terminal and Add/Remove or synaptic do not from GUI ? Is that right ?
Please check if you have set up the proxy in synaptic, and set it to direct. Just have it set up in gnome-network-preferences.

---

### Post by Sal-Lutz on 2007-05-09
I found a workaround after you started asking about Synaptic as well as Add/Remove.

I found it here from a 6.10 user

[http://ubuntuforums.org/showthread.php?t=183093](http://ubuntuforums.org/showthread.php?t=183093)

If I remove the manual proxy setting from System : Preferences : Network Proxy, and leave it set manually in Synaptic, then Synaptic works ... and coincidently, so does Add/Remove.

System : Administration : Update Manager seems to work as well.

So, what do I need to enter the proxy setting in System : Preferences : Network Proxy for, anything?  Maybe I don't need it?

Firefox uses its own proxy setting, so it works fine too.

- Sal  :)

---

### Post by bapoumba on 2007-05-09
Hi,
I'm doing it the other way around.

I set up the global proxy setting in GNOME (> System > Prefs > Network, or gnome-network-preferences from the CLI) so that other GNOME apps can use it (liferea, epiphany ...) and I keep the proxy settings clear in synaptic. Synaptic and Add/Remove do read the GNOME proxy settings, but once again, remove it from synaptic own settings.

For apt-get/aptitude, they use /etc/apt/apt.conf. You can also choose to set it globally in .bashrc. I do not, as I have a laptop, proxy at work, no proxy at home, and I just find it easier to play with apt.conf when needed. But thats just me ^^

So basically, GUI and CLI apps, GNOME/no GNOME apps get the proxy settings from different conf files.
For ex, epiphany is going to get it from GNOME, Firefox has its own.

---

### Post by Sal-Lutz on 2007-05-09
What you just described is the set up I had initially when Add/Remove was giving the 407 errors.

Does your work proxy require authorization?

- Sal

---

### Post by Najand on 2007-05-09
There is a seperate proxy setting for synaptic.
You should open "Synaptic Package manager" at'
System -> Administration -> Synaptic Package manager
Then Click on'
Setting ->  Preferences -> Network
And select "Manual Proxy Configuration" and add your proxy setting.

---

### Post by bapoumba on 2007-05-09
> **Sal-Lutz said:**
> What you just described is the set up I had initially when Add/Remove was giving the 407 errors.

Does your work proxy require authorization?

- Sal
nope, no authorization. In addition, my university network runs on debian, not windows. That may also be a difference. Anyway, whatever works for you is the best.
Cheers.

---

### Post by treblesix on 2007-05-10
Hi,

I was having the same problems, but got it working by doing this .................

Download ntlmaps
Extract the archive
Edit the server.cfg file.

Change The Following ........

# If you want APS to authenticate you at WWW servers using NTLM then just leave this

# value blank like PARENT_PROXY: and APS will connect to web servers directly.

# You can specify more than one proxy by leaving a space between each one, and

# APS will detect when one fails and automatically fail-over to the next. EG:

#PARENT_PROXY:first_proxy second_proxy third_proxy

# And NOTE that NTLM cannot pass through another proxy server.

PARENT_PROXY:PROXY_NAME_HERE



PARENT_PROXY_PORT:8080
# Windows Domain.

# NOTE: it is not full qualified internet domain, but windows network domain.

NT_DOMAIN:DOMAIN_NAME_HERE

# Password. Just leave it blank here and server will request it at the start time,

# or, if you enable NTLM_TO_BASIC, below, you can either leave this blank or simply

# hash it out, and you *won't* be prompted for a password at start time.

PASSWORD:


Go into a console, cd into your extracted dir and type....
./main.py
OR double click on the main.py and choose to run it in a terminal
enter your password (if prompted)

change your proxy settings in Firefox and System/Preferences/NetworkProxy, to....
127.0.0.1 and enter the port your proxy is running on.

**NOTE** REMOVE all proxy settings in the Synaptic Package Manager.

---

### Post by Sal-Lutz on 2007-05-12
treblesix -

My company proxy server is not a Microsoft proxy server, and therefore is not using NTLM.  So, as I understand it, this would not work for my situation.

I wonder if there is something for a non-Microsoft proxy server?

I use Proxomitron on my Windows workstation as an ad-blocker and a proxy server authentication.  Proxomitron works under Windows as you described for ntlmaps, but not with NTLM, just plain authentication.

- Sal

---

