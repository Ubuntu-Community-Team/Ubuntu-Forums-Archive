---
title: "[SOLVED] Intrepid: Can't access Youtube, Amazon, Linuxtoday"
date: 2008-10-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jonathanmotes on 2008-10-11
**[SIZE=3]The Problem:[/SIZE]**

Certain websites (seems to be the more complex ones) will not send a response after DNS resolution. Web browser displays "waiting for website" in status bar for long period of time before eventually timing out.
There was no problem in Hardy, and Windows machines on my network have no problem.

**Some sites that didn't work for me:**
cnet.com
liveleak.com
youtube.com
amazon.com
linuxtoday.com
lifehacker.com
myspace.com
news.yahoo.com
shopping.yahoo.com

**Typical wget response from sites that don't work:**
```
user@computer-name:~$ wget youtube.com
--2008-10-12 23:29:59--  http://youtube.com/
Resolving youtube.com... 208.65.153.238, 208.117.236.69, 208.65.153.251
Connecting to youtube.com|208.65.153.238|:80... connected.
HTTP request sent, awaiting response... 303 See Other
Location: http://www.youtube.com/ [following]
--2008-10-12 23:30:00--  http://www.youtube.com/
Resolving www.youtube.com... 208.117.236.72
Connecting to www.youtube.com|208.117.236.72|:80... connected.
HTTP request sent, awaiting response...
```

**[SIZE=3]Cause of problem:[/SIZE]**
NetworkManager 0.7 sometimes doesn't choose the correct MTU (Maximum Transmission Unit) for your connection. There seems to be a bug in NetworkManager causing it. In my case it always chooses the standard 1500 bytes instead of the 1492 bytes that my router wants to use. 

My router is a NetGear WGR 614. I'm curious if anyone else with this router has the same problem.

**[SIZE="5"]The solution[/SIZE]**

**Quick Fix:**
```
sudo /sbin/ifconfig wlan0 mtu 1492
```
Change wlan0 to ethx (where x is most likely 0 or possibly 1) if you have a wired connection.

**Intrepid only: Permanent Fix (requires reboot)*:**
[LIST=1]
[*]Right click on the NetworkManager applet
[*]Select "Edit Connections..."
[*]Select your connection from the wired or wireless tab
[*]Click "Edit"
[*]In the Edit window, change the MTU setting (under the first tab) from automatic to something between 1300 and 1500 (A size of 1492 bytes works for me).
[*]Reboot
[/LIST]

*The need to reboot after applying the permanent fix is caused by another bug in NetWorkManager 0.7. It might be fixed before the Intrepid release, so try your webpage again before rebooting.

---

### Post by jonathanmotes on 2008-10-11
Anybody? 

I was able to connect to youtube a couple of times today, but it stopped working after a few minutes. The strange thing is that one time youtube started working after I restarted the ufw firewall, but trying that again after it stopped working didn't help (I did try going to youtube with the firewall off, and that didn't work either).

---

### Post by ShirishAg75 on 2008-10-12
There is possibility of you having some bug of network-manager. Lots of people have been having them like [lpbug]280372[/lpbug] (web-browsers start in off-line mode) or bug [lpbug]279262[/lpbug] (network-manager after reboot totally broken which is more likely)

What happens AFAI understand is that after every reboot, the information which should be saved/kept either in network-manager or in ifconfig or wherever doesn't get saved and one has to input the details all over again. 

See if you are able to say do something like this :-

```

ping -c5 google.com 

```If you are getting ping: unknown host google.com or something like that then most likely its one of those bugs. 

There are few more bugs [lpbug]105234[/lpbug] and [lpbug]279737[/lpbug] which are more or less similar bugs. 

They are working on resolving them but will take time. 

This is on the assumption that it is the bug which is afflicting you. If you are getting intermittent connects then most probably its another bug altogether.

---

### Post by jonathanmotes on 2008-10-12
Thanks for the reply ShirishAg75! I don't think my problem is related to those bugs since I can still connect to many other websites like google.com, yahoo.com, or linux.com (although it does seem like it sometimes takes longer to load them than on hardy).

I was at a friends house today and was able to access linuxtoday.com on their wireless although youtube and amazon didn't load.

Pings are very slow though: here's a ping of google:
```
user@computer-name:~$ ping -c5 google.com
PING google.com (64.233.187.99) 56(84) bytes of data.
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=1 ttl=241 time=56.5 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=2 ttl=241 time=56.0 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=3 ttl=241 time=57.1 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=4 ttl=241 time=56.0 ms
64 bytes from jc-in-f99.google.com (64.233.187.99): icmp_seq=5 ttl=241 time=56.4 ms

```

Ping of youtube (youtube is actually working at the moment)
```
user@computer-name:~$ ping -c5 youtube.com
PING youtube.com (208.65.153.251) 56(84) bytes of data.
64 bytes from youtube.com (208.65.153.251): icmp_seq=1 ttl=237 time=67.6 ms
64 bytes from youtube.com (208.65.153.251): icmp_seq=2 ttl=237 time=68.6 ms
64 bytes from youtube.com (208.65.153.251): icmp_seq=3 ttl=237 time=67.3 ms
64 bytes from youtube.com (208.65.153.251): icmp_seq=4 ttl=237 time=67.6 ms
64 bytes from youtube.com (208.65.153.251): icmp_seq=5 ttl=237 time=68.1 ms

--- youtube.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4015ms
rtt min/avg/max/mdev = 67.345/67.902/68.699/0.471 ms

```

But here's what pinging amazon.com gives (amazon.com has never worked)
```
user@computer-name:~$ ping -c5 amazon.com
PING amazon.com (72.21.206.5) 56(84) bytes of data.

--- amazon.com ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4017ms
```

You can see that the DNS request worked, but no reply was ever received from Amazon. 
For some more information that might be useful, I have my router configured to use OpenDNS and Windows machines on the network have no difficulty accessing Amazon....

Thanks for your help in trying to help me resolve this problem!

---

### Post by jonathanmotes on 2008-10-12
Update:

I just installed updates (for the second time today). One of those updates was for the if-up if-down programs (I don't completely understand them, but I think they are scripts for closing and starting network connections). 

Amazon is working for the first time after I installed the updates! (I actually had to try twice before it would connect and it is a little slow), and ping requests to Amazon still don't work. The page doesn't quit loading either (some of the images never get loaded).

Youtube is not working after the updates (and Linuxtoday for one is still not working)....Sad! I thought for a moment my problems were fixed!

Update: pings to Youtube are working (take 74 milliseconds), but the page won't load at all....this is really strange!

I'm just really glad I can access ubuntuforums!

---

### Post by incubus on 2008-10-12
You sure your DNS addresses are getting updated in /etc/resolv.conf?  I'd also suggesting using some public DNS just to test.

By the way, amazon.com doesn't seem to respond to pings.  I just tried here and there was no response, even though I can access the page normally.

---

### Post by jonathanmotes on 2008-10-12
> **incubus said:**
> You sure your DNS addresses are getting updated in /etc/resolv.conf?

This is what my resolv.conf file contains (10.0.0.1 is the ip address of my router - which is configured to use OpenDNS):
```
user@computer-name:~$ cat /etc/resolv.conf 
# Generated by NetworkManager
nameserver 10.0.0.1
```

> **incubus said:**
> I'd also suggesting using some public DNS just to test.
I'm not sure what you mean. As mentioned above my router is using OpenDNS....

> **incubus said:**
> By the way, amazon.com doesn't seem to respond to pings.  I just tried here and there was no response, even though I can access the page normally.
Thanks for the note!

Do you think I should try to manually configure my DNS? I'm not quite sure how to. I tried tried putting the OpenDNS nameservers into the resolv.conf file and restarting the network, but that didn't solve any problems...

Thanks for helping me!

---

### Post by incubus on 2008-10-12
Jonathan,

> **jonathanmotes said:**
> 
Do you think I should try to manually configure my DNS? I'm not quite sure how to. I tried tried putting the OpenDNS nameservers into the resolv.conf file and restarting the network, but that didn't solve any problems...

Thanks for helping me!

Yes, that's exactly what I meant, sorry for being vague there.  I only mentioned that because I've had problems with DNS more than once.  Just to be sure, after you put an entry on resolv.conf you need to restart your browser before testing.  The only other thing I can think of regarding this is trying another DNS server.

Was it working normally with 8.04?  Can you try a live CD?

incubus

---

### Post by jonathanmotes on 2008-10-12
> **incubus said:**
> 
Was it working normally with 8.04?  Can you try a live CD?
incubus

Yes, it was working fine in 8.04. I had to reinstall because I was starting to have some issues with compiz and a few other things. I tried the beta live disc and it seemed to work fine (Should have tested more!). 

I retried the Intrepid Beta live disc and I had the same problems. I also couldn't access ubuntuforums!

I would go back to Hardy but I'm reluctant to because I really enjoy the new features in Intrepid....

Oh yes: I did try restarting Firefox after putting the nameservers in, but I still had the same results...

---

### Post by mc4100 on 2008-10-12
So it's not a DNS issue ... but does a
```
cat /etc/hosts
```
show anything unusual?

---

### Post by jonathanmotes on 2008-10-12
> **mc4100 said:**
> So it's not a DNS issue ... but does a
```
cat /etc/hosts
```
show anything unusual?

This is it:

```
127.0.0.1	localhost
127.0.1.1	my-computer-name
10.0.0.2	another-computer-on-network-manually-added

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Thanks for your help!

---

### Post by Rotund on 2008-10-13
I've got the same problem, but different websites.  Mine has YouTube working, but MySpace does not.

I know one of the 2.6.27 kernels had tcp_ecn on, which would cause the problems.  (cat /proc/sys/net/ipv4/tcp_ecn should be 0)

If I use Tor and FoxyProxy, I can get to the sites.  I can also get to them on my Hardy box.  I'm going to bet some exotic TCP feature got turned on either in the kernel or Firefox.  I'm using 2.6.27-6 kernel (2.6.27-7 hangs)

---

### Post by incubus on 2008-10-13
That's so weird.  If you guys can't find anything on Launchpad, I'd say it's time to file a bug complaint.

---

### Post by jonathanmotes on 2008-10-13
> **Rotund said:**
> I've got the same problem, but different websites.  Mine has YouTube working, but MySpace does not.

I know one of the 2.6.27 kernels had tcp_ecn on, which would cause the problems.  (cat /proc/sys/net/ipv4/tcp_ecn should be 0)

If I use Tor and FoxyProxy, I can get to the sites.  I can also get to them on my Hardy box.  I'm going to bet some exotic TCP feature got turned on either in the kernel or Firefox.  I'm using 2.6.27-6 kernel (2.6.27-7 hangs)

I'm using the 2.6.27-7-generic kernel. I cannot get to myspace.com either: (I get a 200 OK response, but it gets stuck on transferring data). 

Also, cat /proc/sys/net/ipv4/tcp_ecn gives me 0, so I guess that's not the problem.
I might try a proxy tomorrow (its late here) and see how that goes.

Thanks for the suggestions! Maybe one of us will hit on the right problem soon....

---

### Post by marmuta on 2008-10-13
Something you could try is lowering the MTU of your network interface to something between 1300-1500 (1500 being the default). e.g: 
```
sudo /sbin/ifconfig eth0 mtu 1430

```
found this old answer:
[https://answers.launchpad.net/ubuntu/+source/network-manager/+question/14122]("https://answers.launchpad.net/ubuntu/+source/network-manager/+question/14122")

There is supposed to be a way to do it with network manager, but it doesn't work yet, see [#258743]("https://bugs.launchpad.net/network-manager/+bug/258743").

---

### Post by jonathanmotes on 2008-10-13
I've tried everything and just wondering if there are others with similar issues.

Thanks a lot!

---

### Post by Luffield on 2008-10-13
Works fine for me.

---

### Post by Rotund on 2008-10-13
Thanks.  That totally fixed it for me.  I'll have to see what it was before.  I am using an Intel wireless.  Is that what the other guy had too?

---

### Post by cariboo on 2008-10-13
I tried it when I first saw your post in the Intrepid forum, It loads properly for me.

Jim

---

### Post by beercz on 2008-10-13
works here too :-)

Have you tried again?  The site may have been down earlier.

---

### Post by jonathanmotes on 2008-10-13
> **Rotund said:**
> Thanks.  That totally fixed it for me.  I'll have to see what it was before.  I am using an Intel wireless.  Is that what the other guy had too?
Yes, I'm using Intel wireless. I'm at school now (where I'm not having any problems, strangely enough). I will try changing the MTU settings when I get home tonight.

---

### Post by jonathanmotes on 2008-10-13
> **beercz said:**
> works here too :-)

Have you tried again?  The site may have been down earlier.

The strange thing was that I went over to a friend's house and was able to access linuxtoday (although I still had problems with youtube and amazon, among several other websites). I'm at school now, where I'm not having any problems at all....

---

### Post by beercz on 2008-10-13
> **jonathanmotes said:**
> The strange thing was that I went over to a friend's house and was able to access linuxtoday (although I still had problems with youtube and amazon, among several other websites). I'm at school now, where I'm not having any problems at all....
Is it a firewall or router problem?

---

### Post by jonathanmotes on 2008-10-13
> **beercz said:**
> Is it a firewall or router problem?
I guess it could be related, but other computers on my home network have no problem. The operating systems are Ubuntu 8.04 and Windows XP. In my original forum post ([here]("http://ubuntuforums.org/showthread.php?t=944600")), I descibe several things that I did, such as disabling my firewall (on the computer), etc, with no improvement. 

Post #15, by marmuta, shows a fix that has worked for another user. I am going to try it when I get home.

---

### Post by beercz on 2008-10-13
> **jonathanmotes said:**
> I guess it could be related, but other computers on my home network have no problem. The operating systems are Ubuntu 8.04 and Windows XP. In my original forum post ([here]("http://ubuntuforums.org/showthread.php?t=944600")), I descibe several things that I did, such as disabling my firewall (on the computer), etc, with no improvement. 

Post #15, by marmuta, shows a fix that has worked for another user. I am going to try it when I get home.
Good luck - let us know how you get on, it may help others.

---

### Post by jonathanmotes on 2008-10-14
> **marmuta said:**
> Something you could try is lowering the MTU of your network interface to something between 1300-1500 (1500 being the default). e.g: 
```
sudo /sbin/ifconfig eth0 mtu 1430

```
found this old answer:
[https://answers.launchpad.net/ubuntu/+source/network-manager/+question/14122]("https://answers.launchpad.net/ubuntu/+source/network-manager/+question/14122")

There is supposed to be a way to do it with network manager, but it doesn't work yet, see [#258743]("https://bugs.launchpad.net/network-manager/+bug/258743").

I'm sorry for not posting back earlier. I created a new profile for Firefox and now I can't access ubuntuforums from home.

Changing the MTU didn't help any for me.....
I really don't know what else to try. Does anyone have any more ideas? 

Thanks!

---

### Post by jonathanmotes on 2008-10-15
Solved the problem!! 

It turns out that the MTU setting was too high. I was just copying and pasting the command that marmuta gave me. The problem was that I was using my wireless card (wlan0), not the ethernet card (eth0). I don't know why I didn't realize that until now!

The fix:
```
sudo /sbin/ifconfig wlan0 mtu 1492
```

This is incredibly awesome! Thanks so much guys!

---

### Post by pHreaksYcle on 2008-10-18
I'm about to go try this.

Got scared, thought Google hacked Ubuntu because I could only access Google and sites hosted by Google. Weird I tell you...

---

### Post by Leo the Lion on 2008-10-19
I have not had the same luck as you guys. I tried changing the mtu to lower than 1500 but nothing happened. Still can't access ubuntuforums and other sites. Any other ideas? 
Thanks.

---

### Post by jonathanmotes on 2008-10-19
> **Leo the Lion said:**
> I have not had the same luck as you guys. I tried changing the mtu to lower than 1500 but nothing happened. Still can't access ubuntuforums and other sites. Any other ideas? 
Thanks.

Try:
1. Disabling IPv6 support in Firefox by typing about:config in the URL bar, then searching for network.dns.disableIPv6. Double-click on it to change its value from false to true.

2. If you have access to your router or modem, change your DNS servers configuration to [OpenDNS]("https://www.opendns.com/smb/start/router/") (if you haven't already).

3. When I first tried to lower my MTU size, I was setting it for the wrong network connection (in my case eth0 instead of wlan0). To double check that you are doing setting your's correctly, type *ifconfig* in the terminal and look for ethX if you are using a wired connection, wlanX if you are on a wireless connection (where X is an integer >= 0). Modify one of the commands below for your connection:
```
sudo /sbin/ifconfig wlanX mtu 1492
```
or
```
sudo /sbin/ifconfig ethX mtu 1492
```

Experiment with the MTU sizes and see if you have any luck (don't go below 1300 or above 1500 though....)

There are some other things you could try, but their not coming to mind at the moment....

Hope this helps!

---

### Post by chudak on 2008-10-19
I'm having MAJOR slowdown issues as well on my new Lenovo t400. The last update broke my wifi card. I was able to fix it with the firmware copy suggested elsewhere but my web surfing is slow as hell. It wasn't this way before the update.

FWIW, I'm using a T60 running Hardy that is sitting right next to my new t400 and it has none of these issues. It's not my router, my DNS server, my ISP and I strongly doubt it is the IPV6 support in firefox (this is not disabled in Hardy and works fine).

Any other ideas? My new laptop is unusable in it's current update state. Takes MINUTES to load pages like gmail of slashdot because it has to do a DNS lookup for every single link in the page and they are all slow as hell.

---

### Post by jonathanmotes on 2008-10-19
> **chudak said:**
> I'm having MAJOR slowdown issues as well on my new Lenovo t400. The last update broke my wifi card. I was able to fix it with the firmware copy suggested elsewhere but my web surfing is slow as hell. It wasn't this way before the update.

FWIW, I'm using a T60 running Hardy that is sitting right next to my new t400 and it has none of these issues. It's not my router, my DNS server, my ISP and I strongly doubt it is the IPV6 support in firefox (this is not disabled in Hardy and works fine).

Any other ideas? My new laptop is unusable in it's current update state. Takes MINUTES to load pages like gmail of slashdot because it has to do a DNS lookup for every single link in the page and they are all slow as hell.

Your problem sounds like one I had with the Gutsy (7.10) beta. DNS lookups took up to 20 seconds at times. All I had to do was disable IPv6 (steps described in [my reply to another post]("http://ubuntuforums.org/showpost.php?p=5995913&postcount=29"))....

---

### Post by chudak on 2008-10-19
Ok, here was the problem. I have vpnc installed and use it to connect to my work. Even after rebooting several times since the last time that I was connected with vpnc, /etc/resolv.conf STILL had the name servers for my company vpn. This might be because I had to do a hard shutdown due to a shutdown hang?

In any event, removing the stale dns server entries from /etc/resolvconf/run/resolv.conf and restarting fixed the problem.

Too strange...:mad:

---

### Post by jonathanmotes on 2008-10-19
> **chudak said:**
> Ok, here was the problem. I have vpnc installed and use it to connect to my work. Even after rebooting several times since the last time that I was connected with vpnc, /etc/resolv.conf STILL had the name servers for my company vpn. This might be because I had to do a hard shutdown due to a shutdown hang?

In any event, removing the stale dns server entries from /etc/resolvconf/run/resolv.conf and restarting fixed the problem.

Too strange...:mad:

Thanks for giving us your solution!:) I've had a situation similar to this one myself. I might create a tutorial page on fixing slow/broken connections if there are enough solution posts here.

---

### Post by Leo the Lion on 2008-10-19
> **jonathanmotes said:**
> Try:
1. Disabling IPv6 support in Firefox by typing about:config in the URL bar, then searching for network.dns.disableIPv6. Double-click on it to change its value from false to true.

2. If you have access to your router or modem, change your DNS servers to use [OpenDNS]("https://www.opendns.com/smb/start/router/") (if you haven't already).

3. When I first tried to lower my MTU size, I was setting it for the wrong network connection (in my case eth0 instead of wlan0). To double check that you are doing setting your's correctly, type *ifconfig* in the terminal and look for ethX if you are using a wired connection, wlanX if you are on a wireless connection (where X is an integer >= 0). Modify one of the commands below for your connection:
```
sudo /sbin/ifconfig wlanX mtu 1492
```
or
```
sudo /sbin/ifconfig ethX mtu 1492
```

Experiment with the MTU sizes and see if you have any luck (don't go below 1300 or above 1500 though....)

There are some other things you could try, but their not coming to mind at the moment....

Hope this helps!

Thanks a bunch jonathanmotes! I'll try it when I get home.

Cheers

---

