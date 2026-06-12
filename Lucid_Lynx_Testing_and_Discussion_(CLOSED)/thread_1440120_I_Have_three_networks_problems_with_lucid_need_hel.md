---
title: "I Have three networks problems with lucid need help fixing them"
date: 2010-03-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-03-27
1.after every restart or log off i can't connect to the internet without using this commands:
```
sudo poff -a && sudo pon dsl-provider
```

my connection is pppoe and i use pppoeconf to set it and after setting it it should 

automaticly connect but it does not.

2.i need to share an internet connection from ubuntu to an xp machine i used firestarter 

in the past but it has caused many problems so i now use this commands:

```
sudo iptables -A FORWARD -i eth1 -o eth0 -s 192.168.0.0/24 -m conntrack  --ctstate NEW -j ACCEPT
sudo iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j  ACCEPT
sudo iptables -A POSTROUTING -t nat -j MASQUERADE 

sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"
```

the problem is that this commands don't last i need to make them permenet some how.

3.i can't print from the remote xp to the local Ubuntu printer xp recognize it as ready

and the port should be open but still she does not print but locally of course she does 

work.

any help with either of this problem would be most appreciated and thanks in advance.:)

---

### Post by aviramof on 2010-03-27
No one know anything?not even about problem #2?

---

### Post by QLee on 2010-03-27
[QUOTE=aviramof]No one know anything?not even about problem #2?[/QUOTE]

Do you have these same "problems" when you run a released version of Ubuntu or just when you try the beta release of Lucid?

---

### Post by aviramof on 2010-03-27
i didn't have problem #1 with ubuntu 8.10 or in the past with lucid as for the rest i don't know because i didn't stayed with 8.10 for too long and 9.04 and 9.10 did not wanted to connect to my isp at all via pppoeconf but i think that the printer problem might be realted to wrongs paths in the
smb.conf file i still need to check it the problem is that i can't always see the netbios name in xp because samba don't always run automaticly and
even then i can't always enter my ubuntu computer because it give an error of no access and you always need to restart xp or ubuntu and the command with init.d to restart samba don't work for me for some reason.
 
i have also tried samba4 but it's also not working well is there a better way then samba or a newer version then what i have?

---

### Post by psyke83 on 2010-03-27
I'll assume that you're using Ubuntu or Kubuntu, without having removed the default set if packages.

> **aviramof said:**
> 1.after every restart or log off i can't connect to the internet without using this commands:
```
sudo poff -a && sudo pon dsl-provider
```my connection is pppoe and i use pppoeconf to set it and after setting it it should 

automaticly connect but it does not.

Why are you going to the trouble of using pppoeconf when Ubuntu is configured to use Network Manager instead? First, remove any of your customized configuration, then right-click on the NetworkManager applet, choose "Edit connections", DSL tab, Add button.

> 2.i need to share an internet connection from ubuntu to an xp machine i used firestarter 

in the past but it has caused many problems so i now use this commands:

```
sudo iptables -A FORWARD -i eth1 -o eth0 -s 192.168.0.0/24 -m conntrack  --ctstate NEW -j ACCEPT
sudo iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j  ACCEPT
sudo iptables -A POSTROUTING -t nat -j MASQUERADE 

sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"
```the problem is that this commands don't last i need to make them permenet some how.
a) Put all those commands into a text file (without reference to sudo) called /etc/network/if-up.d/netsharing:
```
$ sudo gedit /etc/network/if-up.d/netsharing
``````
#!/bin/sh
iptables -A FORWARD -i eth1 -o eth0 -s 192.168.0.0/24 -m conntrack   --ctstate NEW -j ACCEPT
iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j   ACCEPT
iptables -A POSTROUTING -t nat -j MASQUERADE 
echo 1 > /proc/sys/net/ipv4/ip_forward
```b) Make the file executable:
```
sudo chmod +x /etc/network/if-up.d/netsharing
```The effect is that this script will be executed each time a network interface is brought up.

NOTE: Ubuntu uses an application called ufw (uncomplicated firewall) to manage the firewall/iptables settings. There is an interface in the repositories called "gufw" which you may want to investigate as a *possible* alternative to using the scripted batch file above.

---

### Post by aviramof on 2010-03-27
Thank you very much for your help the part about the internet sharing is working perfectly as for the rest i'm affraid it's not for some reason Network Manager don't want to save my password and i also don't have a service to write there maybe that is the cause maybe it's not.

as for the printer and samba problem to be honest i have decided to give up on that i am trying for two weeks to get it working properly and it didn't worked properly even once the best i was able to do is to see the netbios name of my ubuntu machine on xp maybe enter but i was unable to create files and folders in ubuntu and despite the fact that i managed to share my printer and install it on xp i was  unable to actually print from the xp machine to the local ubuntu printer maybe it has something to do with printcap path which should be /var/run/cups/printcap and not /etc/printcap but unfortually i can't check it because again i can't get xp to recognize my ubuntu netbios name but in any case the problem is definetly ubuntu because xp seven connection is working perfectly print and share and even from ubuntu to xp the xp share is working fine the problem is the ubuntu files and folders and printer share and permissions so that i could use this resources from the xp.

i guess that for the time being i would have to continue using sudo poff -a && sudo pon dsl-provider to connect to my isp and windows seven for my home network and also for hd movied since i can't get them to work properly in ubuntu without fglrx driver.

and maybe in the future a better samba would be releasd or something eles because at the moment i'm sorry to say this method is terrible.

---

### Post by Reiger on 2010-03-27
As for printers, this is probably a matter of appropriate settings for CUPS (I imagine it blocks all incoming requests from outside the localhost domain).

Try pointing your browser to [http://localhost:631/](http://localhost:631/) to access the CUPS configuration GUI.

EDIT: I assume that the &#8220;Share this printer&#8221; checkbox in the &#8220;Add Printer&#8221; forms is what you'd be looking for?

---

### Post by aviramof on 2010-03-27
bro i already tried everything i could possibly think of including this option it just doesn't acceptt jobs from the remote xp i'm starting to think now that maybe all this printer and ubuntu permission problems are because of the ext4 file system itself and not because samba on all it's versions or maybe xp can't work properly with ext4 file system on remote computers or something like this or that lucid is just too broken now to work properly now with xp machine on a crossover ipv4 network.

---

### Post by QLee on 2010-03-28
> **aviramof said:**
> i didn't have problem #1 with ubuntu 8.10 or in the past with lucid as for the rest i don't know because i didn't stayed with 8.10 for too long and 9.04 and 9.10 did not wanted to connect to my isp at all via pppoeconf but i think that the printer problem might be realted to wrongs paths in the
smb.conf file i still need to check it the problem is that i can't always see the netbios name in xp because samba don't always run automaticly and
even then i can't always enter my ubuntu computer because it give an error of no access and you always need to restart xp or ubuntu and the command with init.d to restart samba don't work for me for some reason.
 
i have also tried samba4 but it's also not working well is there a better way then samba or a newer version then what i have?

aviramof, in my opinion, the problems you are having are not necessarily related to Lucid being beta software. I think you are making a fundamental mistake by putting your issues all in one thread full of run-on sentences, which are hard to follow logically. 

I do realise how frustrating it can be when things don't work as one wants them to but troubleshoot effectively one has to separate from the negative emotion. 

I'd suggest a different approach, deal with one problem at a time in a separate thread, that way most of the replies will concentrate on that one issue. Give more information about the issue, tell what you tried exactly and exactly what error messages showed up. When you say you've tried everything, that doesn't give any useful information because we can't tell if you tried the correct things or if you did them correctly or if you did them in the correct order. You may have to alter your expectations too, in GNU/Linux not everything is simple point-and-click, until after the sys admin (in this case you) sets it up.

The things you aren't having luck with are probably not because of any fault in Lucid beta. You got good help with one problem in this thread, suggest you continue with new threads for each of your other problems, one problem at a time. Others appear to be able to do the things you can't yet do.

You probably should really be using a released version and posting in the newbies sub-forum or at least in generial, more people who are trying to help people learn about Ubuntu and how it is different from Windows read those forums than read this sub-forum for people testing the pre-release versions.

---

### Post by aviramof on 2010-03-28
i tried seperate threads no one answeared as for released version it's not my fault that 9.04 and 9.10 are not working with my internet connection it's also not my fault that network manager don't want to save my password and even the ics problem is not solved properly in the end and also i really don't understand why i can share a printer install it from ubuntu on xp and still not be able to print from xp or create new folders on ubuntu from xp or other countless problems i had with ubuntu networking it shouldn't be that hard to create a simple crossover home network or to even automaticly dial to the internet and i am no newbie to networks and configuring samba is not hard but it simply doesn't work and that is my problem if to tell you truth i'm happy that i don't need to create an entire linux network because it's terrible to do any networking in ubuntu.

---

