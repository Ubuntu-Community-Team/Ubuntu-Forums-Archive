---
title: "Navigating on the internet problems"
date: 2008-09-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Trespasser on 2008-09-06
Hi,
I don't know how to explain it exactly but I can connect to certain internet addresses but not others. For example I can connect to my home page, iGoogle, or My Yahoo, but I can't to ubuntuforums (which prevents me from seeking help) and many others. Also, I can't do an update either in Terminal nor Synaptic. In Terminal, after entering sudo apt-get update, the cursor just sits there with "Waiting for Headers" displayed.

This is after a fresh install of Desktop Alpha 5 32bit though I had this problem with Alpha 4 as well. This problem began after the upgrade to the 2.6.27 kernel. My chipset is Via, I'm using an Ati 9600 Pro video card, 3.0 P4 processor (hyper-threading), and 1.5 gigs of Ram.

Any help on this will be appreciated.

P.S.
Luckily I had a copy of a Debian 2.6.25 kernel saved on disk which allowed me to surf unrestricted once again.

Thanks...

---

### Post by Trespasser on 2008-09-06
Sorry for the shameless "bump" but can anyone offer some assistance? I can hardly surf at all the way it stands now with the 2.6.27.2 kernel.

Also, two days ago I compiled a new kernel for Hardy with KernelCheck (2.6.27.rc5) and I experienced the same condition (select internet sites would not load up and no updating).

Thanks...

---

### Post by ronacc on 2008-09-06
see if you can get to this address .
[http://www.opera.com/download/](http://www.opera.com/download/)
if you can, d/l and install opera and see if that helps .
if you can d/l and install opera and it also won't contact those sites you can try blacklisting ipv6  I know my isp (comcast) dosen't use ipv6 and if it is enabled it takes forever to access a site .

---

### Post by Nullack on 2008-09-06
Are you sure your network is setup right:

type sudo ifconfig (name of connection)

e.g. sudo ifconfig eth0

Use ping and nslookup and traceroute to futher diagnose the issue.

---

### Post by Trespasser on 2008-09-07
Just to inform those who tried to help me...

I blacklisted ipv6 but that didn't work, so I booted into the other kernel I had installed and googled for a bit. I found an obscure post that described what I was experiencing and suggested installing Firestarter to fix the problem. I did, and it did. Very nice to be able to surf normally once again.

---

### Post by ronacc on 2008-09-07
firestarter ? thats interesting , please share the post you referenced if you can find it again incase this bites someone else .

---

### Post by Nullack on 2008-09-07
None of this makes sense :) Theres something missing and I think its probably a configuration problem rather than a bug.

---

### Post by ronacc on 2008-09-07
I agree , iptables maybe ? why would installing firestarter enable certain addresses ? thats why I asked for the reference post .

---

### Post by Trespasser on 2008-09-07
The only thing I can say is I could connect on certain sites...like iGoogle (my home page), My Yahoo, and a few others (when I could find them). I switched to another kernel I had installed (Debian 2.6.25.2) and Googled for "Can connect to some sites but not others ubuntu". Eventually I found a site that described the problem I was experiencing and suggested installing Firestarter. At the time I installed Firestarter I also did an update in Synaptic...there were 13 updates that I needed to take. I looked them over but none seemed to relate to iptables (which I assumed to be the problem since blacklisting ipv6 didn't help). After a reboot back into kernel 2.6.27.2 surfing was back to normal after I set up Firestarter. I have the link to this site saved in my bookmarks within a CloneZilla Intrepid image. I'll switch to that image tomorrow (presently in OzOS...:)).

Later...

---

### Post by Trespasser on 2008-09-08
I'm back in Intrepid and if I uninstall firestarter I lose my ability to connect to certain sites (like ubuntuforums for instance). When I reinstall firestarter (I have a copy saved) it works again. Strange, I know.

The link that was requested...

[http://www.ventanazul.com/webzine/articles/cannot-access-websites-ubuntu-gutsy-gibbon](http://www.ventanazul.com/webzine/articles/cannot-access-websites-ubuntu-gutsy-gibbon)

Again, all I can say is when firestarter is installed I can surf normally.

---

### Post by ronacc on 2008-09-08
reading over the site you refered to and the bug report it references it looks like something did mung up your iptables , the question is what ? It may have been the upgrade to intrepid but many of us here have gone the upgrade route without encountering this , have you installed anything non default ? I would think that if this isn't some kind of fluke it would have bitten someone else also .

---

### Post by Trespasser on 2008-09-08
With the default install from the Alpha 5 desktop disc I was unable to connect to the update server to update nor install anything. This problem was present from the first time I booted up. I have no idea why I'm having this problem with the 2.6.27.2 kernel other than possibly my chipset (Via) or maybe a conflict with my router.

Again, I'm clueless as to why this is happening. All I know is with Firestarter installed I can access both updates and the internet normally. I'm fairly sure it's related to the 2.6.27 kernel for anything below (2.6.25 or 2.6.26) works fine.

Thanks for your interest. :).

---

### Post by cariboo on 2008-09-08
I don't suppose you could uninstall firestarter and then run:

```
sudo iptables -L
```

Just to see if it blocking some sites?

Jim

---

### Post by Trespasser on 2008-09-08
Thanks for the reply. Actually I found an Ubuntu wiki/site that had a how-to for configuring iptables and yes I ran that command, plus others, and no ip addresses were listed as being blocked. I even tried ufw (uncomplicated firewall) which you can use to configure iptables. I actually liked ufw...very simple to use...but still no luck. Side note...this failure could have been due to my own lack of knowledge (it's been a long time since I was heavily involved in firewall configuration...yes, my XP days, concerns for security and dialup...what a combination, but it was fun, though...:)).

Later...

---

### Post by Nullack on 2008-09-08
You have all the networking tools you need in Ubuntu with ping, nslookup, traceroute, ifconfig and so forth. Looking through the man pages or google searches on specific tools will give you more info on what they do.

I use UFW because I want to support Intrepid testing and the Ubuntu principle of having one standard supported way of doing things. I like UFW, easy to use and lightweight.

---

