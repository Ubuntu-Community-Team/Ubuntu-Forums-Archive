---
title: "no synaptic downloads without firefox first"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by codeandeffect on 2008-07-29
Apologies if this has been answered elsewhere, I have tried various searches to no avail.

On my home network - through an ADSL router, when I ask Synaptic to install something for me it always fails. If I then copy the url it was trying to download into firefox and start to download it, then re-try Synaptic, it works.

I now routinely click apply then cancel to see the url so I can copy and download it. I have no special setup on the router that I know of. It's a wired connection by the way, and I'm using Gutsy.

Is there a way around this?

Thankyou for your time

UPDATE: I am using 'direct connection to the internet' under the networl tab in Synaptic's settings.

---

### Post by codeandeffect on 2008-08-13
After much reading I still don't have a fix for this, but I do have more information:

Setup AT WORK:
At work, I plug in a cable and its fabulous - everything just works.


Setup AT HOME:
D-LINK G624 ADSL Router, DHCP connection assigning two 192.168.1.x IPs to Ubuntu and an WinXP box.
Ubuntu 7.10 on Acer laptop
Wired Ethernet connection

Symptoms AT HOME:
[LIST]
[*]Firefox and email (Thunderbird Portable through WINE, and Evolution) can access the t'interweb without a problem.
[*]Other services (Pidgin connection to MSN, Synaptic updates) cannot access internet resources.
[/LIST]
The Workarounds:
[LIST]
[*] PIDGIN connection to MSN - the only way I can get this to work is by loading Pidgin on my other WinXP desktop on the same network, logging in, and then Pidgin on Ubuntu springs to life, connects, and kicks the WinXP copy off becuase MSN knows I've connected elsewhere.
[*]Synaptic - I select the software package I want in synaptic, click apply, click cancel when the download does nothing, copy the address into Firefox, and start downloading the resource. I then cancel that, go back to Synaptic, and its then able to access the download! I have the same problem when refreshing the repositories, I have to visit them in a browser before Synaptic will update them.
[/LIST]

So to conclude - Something about my network and Ubuntu setup seems incapable of accessing these features unless I either visit them in a browser first, or get another machine on the network to access them for me first.

So far as the router's concerned - there's no firewall, there's no filtering, I cannot see why one (Win) client gets priority over the other (Ubuntu).

I'm using Direct connection to the internet in Network/Firefox/Synaptic and Pidgin preferences - as borne out by the fact that I can connect using these once another browser or another machine 'says its ok'!.

Finally, looking at *ifconfig *shows that my eth0 both at home and work are no different but for their IP addresses.

Pinging can work for synaptic (archive.ubuntu.com) while this doesn't work for messenger.hotmail.com (on either of my machines).

I'd love to hear anyone's thoughts on this!

---

### Post by codeandeffect on 2008-08-14
*bump*

---

### Post by cariboo on 2008-08-14
Check your dns servers, may give opendns a try, it's free. Check it out here:

[http://www.opendns.com/](http://www.opendns.com/)

Jim

---

### Post by codeandeffect on 2008-08-15
Sorted in seconds :) Thankyou thankyou thankyou!

I've a whole load of research work going on in the next three months and having a networked linux environment is absolutely essential for it, I'm so pleased!!!!!!

---

