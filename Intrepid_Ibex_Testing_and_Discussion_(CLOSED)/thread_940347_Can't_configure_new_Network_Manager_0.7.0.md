---
title: "Can't configure new Network Manager 0.7.0"
date: 2008-10-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by iClouseau88 on 2008-10-06
Hi,

Toshiba laptop dual boot XP-Intrepid beta.

Recently I upgraded Hardy to Intrepid beta.  Today after updating I got the new version 0.7.0 of Network Manager (Before, I got a green globe but today I got a dark globe and an Interdiction sign over the mouse icon).  It shows my wired and wireless connections to be "never", etc.  eth0:"unmanaged", eth1: "disconnected".  I CAN get wired connection automatically through DHCP, but I can't change the settings back to those in the previous version of Network Manager, since it won't let me.  I tried entering correct Ip address but the positions of the decimals result in wrong address.  The 3 digit numbers don't fit in the fields.  For example, if I type 192.168.110.X I will get 1.92 or 19.2. The default decimal points get in the way, even though I just typed in the number without typing the decimals.

Any idea how I can revert to previous Network Manager version?

Thanks a lot for your help.

---

### Post by iClouseau88 on 2008-10-07
Any helpful suggestion at all?

---

### Post by Perfect Storm on 2008-10-07
Thread moved to Intrepid Ibex Testing and Discussion.

---

### Post by xlinuks on 2008-10-07
Unfortunately I can't help, but what's further "amazing" is that it doesn't even feature "special" GUI input boxes for IP adresses, they are just text fields. I hate to say it, but in this regard this program has to learn from Window$.

---

### Post by wgrant on 2008-10-07
> **xlinuks said:**
> Unfortunately I can't help, but what's further "amazing" is that it doesn't even feature "special" GUI input boxes for IP adresses, they are just text fields. I hate to say it, but in this regard this program has to learn from Window$.

What benefit do such specialised IP address input widgets give? I always found them a hindrance.

---

### Post by AngelX on 2008-10-07
Recently upgraded from 8.04 to 8.10 

Adding to the Network Manger problems, I have an Atheros wireless card and it simply won't connect it just hangs in the "acquiring network address" and then it prompt me for the WEP key over and over, I manually configured to not use DHCP and it tells me it's connected but it really isn't, if I ping my router I get the "Destination Host Unreachable" message.

I have no issues with the text boxes getting the IP numbers in.

On the good side, hard wire network works, so I'm not completely isolated.

Any ideas on the NM 0.7 wireless issue?

Thanks in advance for the help.

---

### Post by xlinuks on 2008-10-07
> **wgrant said:**
> What benefit do such specialised IP address input widgets give? I always found them a hindrance.

I agree with you, you are so right... it is so much better without having a handy IP gui field. Now sarcasm aside, as long as we have these kinds of bias/bigotry we will continue being under 1% share and because of that having companies like Nvidia throwing bones at us instead of fast and qualitative drivers like the ones for window$. I would work for free for Canonical if they let me do certain decisions for Ubuntu that people are asking for years (easy to fix but lots of pple complaining about them).

---

### Post by xlinuks on 2008-10-07
It's not the only artefact, the standard Gtk doesn't have a table component.. I was amazed.. I really hope all of this will be addressed in Gtk+ 3.0

---

### Post by mister_pink on 2008-10-07
The new network manager does seem to have made things a hell of a lot more complicated. I have very simple requirements, namely I need to set a static ip address, the netmask, gateway and 2 dns servers. It initially took me a while to fathom the program out, and now I have it just doesn't work.

On trying to set the DNS servers I now am told "Updating Connection failed: nm-ifupdown-connection.c.82 - connection update not supported (read-only).."

Help would be appreciated, I'm going to try killing the applet and seeing if I can remember how to set things with the command line. Can't really report the bug properly until I can get on the internet at home!

I really do wonder what was the point in the radical change. I can understand putting new features in but this has some overly complex options. Does the average user need a nice interface to set their MAC address? Does the average user even know what MTU is?

---

### Post by wgrant on 2008-10-07
> **xlinuks said:**
> I agree with you, you are so right... it is so much better without having a handy IP gui field. <snip excessive irrelevance, which lacked any rationale>

... why? You're yet to give a reason that having a specialised widget is better ("handy" is a completely useless reason). Accusing devs of bias or bigotry (especially without rationale) also isn't very polite.

---

### Post by Polygon on 2008-10-07
im guessing its a bit easier to type the ip...since you just have to type numbers and the dots are automatically positioned in the right spot? I dunno, i don't care if its text or an ip widget either way.

---

### Post by mister_pink on 2008-10-07
> **wgrant said:**
> ... why? You're yet to give a reason that having a specialised widget is better 

I'm with you on this - the ip field thing was annoying. If you made a mistake it wouldn't let you delete the last number in a section as that would make it an invalid ip, so you had to type the first number of the correct one, then delete the incorrect number, then finish writing the correct one.

---

### Post by mrtrevin on 2008-10-07
I too am getting the error, "Updating connection failed: nm-ifupdown-connection.c.82-connection update not supported (read-only).  I am able to define all of the IP settings besides the DNS in the command line.  I cannot get Intrepid to use /etc/resolv.conf.  Any suggestions?

Thanks
Mike Trevino

---

### Post by kadafi69 on 2008-10-07
im also getting this error.

Updating connection failed: nm-iofupdown-connection.c.82-connection update not supported (read-only)

When I try to create a new connection setting I can input all the correct settings, it then saves but it fails to connect, when you check the settings the subnet has been changed to 24, changing it back is futile.

another query of mine is the system setting check box at the top, having this checked or unchecked seems to make no difference to any settings ive found.

---

### Post by ShirishAg75 on 2008-10-07
Hi all, 
 Dear friends instead of bickering, there are two bugs which have been filed, 

a. [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/279433/](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/279433/)

There is something called (Does this bug affect you?) click on that if it affects you as well, what this will do is instead of having me too replies the developers would know we are affected by the bug, (logically) it should raise the priority of the bug as well. 

The second bug which has also been filed which also raised the issue being discussed is :-

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/279384/](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/279384/)

Now as stated in the bug itself the issue is something which needs to be kicked upstairs, i.e. at the GNOME folks level and see what they have to say about it. (upstream)

If the GNOME guys are already thinking of something similar or not or what are/were the reasons why things have been done in a certain way we need to be aware, just bashing developers without that info. is not cool IMHO. 

Also be aware that I'm not in anyway gained or employed by Canonical in any way, just another user :)

---

### Post by mrtrevin on 2008-10-07
Thanks for those bug reports.  Anyone have any thoughts for a temporary fix? I made the mistake of upgrading my primary work computer to Intrepid and now I am without connectivity. Doesn't look good for the it guy not to have a working computer ;).  Thanks.

P.S. I think that [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/279262]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/279262") is a more relevant bug.

---

### Post by jstalin on 2008-10-07
Same problem here. The update killed my wired networking. The network manager says "device is unmanaged." I'm stuck borrowing someone's wireless until this gets resolved.

---

### Post by ShirishAg75 on 2008-10-07
mrtervin 
thanx, made the other one a duplicate, less work for the developers so they can put energy into fixing this one.

jstalin, please do not put stuff on the bug saying me too, there is actually a link a little above on the right-side which says does this bug affect you, use that . If you are just going to say me too, it will just add *noise* to the bug and doesn't help either the developers or bug-triagers or anybody with that.

---

### Post by jstalin on 2008-10-07
Sorry, I'm new to bug reporting :)

---

### Post by kadafi69 on 2008-10-07
> **ShirishAg75 said:**
> please do not put stuff on the bug saying me too, there is actually a link a little above on the right-side which says does this bug affect you

no there isnt, if there is i certainly dont see it.

---

### Post by Perfect Storm on 2008-10-07
> **jstalin said:**
> Sorry, I'm new to bug reporting :)

Please read the: [http://ubuntuforums.org/showthread.php?t=896777](http://ubuntuforums.org/showthread.php?t=896777)
It's important to report or search if anyone have reported a bug you find.

---

### Post by billyShears on 2008-10-07
I've had the same problem too, I couldn't connect to the internet with my wired connection and change settings from network manager, I've solved it by manually deleting my old static ip configuration from /etc/network/interfaces, I've left just "auto eth0" and now internet is working again, but I didn't try to set again a static ip with network manager.

---

### Post by kadafi69 on 2008-10-07
anyone know how to downgrade the nm package to the previous one installed?

---

### Post by tofuconfetti on 2008-10-07
This may or may not help, but I had fits with the new network manager for about an hour last night.  When I first booted up after install, I had a DHCP connection (wired on a desktop) computer working fine.  Then I wanted a static IP (to ftp things around) and tried to set it.  That's when I could not get an "ok" button to light up.  I tried then to set things manually in /etc/network/interfaces, which gave me a connection but shut down the network manager with some funny listed connections and it locked out any changes.

So then, I deleted that listing, shut down the network (/etc/init.d/networking stop) and changed the network via the manager.

What was tripping me up was listing the DNS servers manually.  Use ONLY a space between them (no commas).  I noted that with one server listed, the OK button would become available.  But when I listed two DNS servers, it went off, but I separated them by a comma.  Removing the comma make it okay.

As of last night, it was working fine and I could change things at will.

Obviously, the settings are stored somewhere other than /etc/networking/interfaces.

---

### Post by blakamin on 2008-10-07
> **kadafi69 said:**
> no there isnt, if there is i certainly dont see it.
I couldn't find it either (even doing a search on the page) and this bug definately affects me

---

### Post by wgrant on 2008-10-07
> **blakamin said:**
> I couldn't find it either (even doing a search on the page) and this bug definately affects me

It's not on Launchpad production yet - only on [edge](https://edge.launchpad.net/), which runs the latest version of the Launchpad codebase.

---

### Post by kadafi69 on 2008-10-08
problem seems to be solved, as someone mentioned above.

my original /etc/network/interfaces read like this:

> auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.2.136
netmask 255.255.255.0
gateway 192.168.2.1

iface wlan0 inet static
address 192.168.2.136
netmask 255.255.255.0
gateway 192.168.2.1
wireless-key ***********
wireless-essid Broadcast

auto wlan0

auto eth0

as someone mentioned on laucnhpad, adding the auto eth0 then commenting out iface eth0 inet static. so my new
/etc/network/interfaces looks like:

> auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet static
address 192.168.2.136
netmask 255.255.255.0
gateway 192.168.2.1

iface wlan0 inet static
address 192.168.2.136
netmask 255.255.255.0
gateway 192.168.2.1
wireless-key ***********
wireless-essid Broadcast

auto wlan0

auto eth0

when i rebooted a network had connected automatically (one i had previously tried to save, unsuccessfully), connecting to the internet worked fine. clicking on the NM icon displayed a list of network connections, all of which where previous failed attempts at making a connection. i managed to delete the remaining connections through NM, the ifup connection wasnt there.

---

### Post by carusoswi on 2008-10-08
This worked for me, and I wanted to say thanks to Sokraates, as I first read this solution in a thread that he posted (here??).  I printed out his post and yours, Kadafi69.  I was running xp at the time.  Booted into Intrepid, fixed the problem, wanted to come back here to say thanks - can't find Sokraates' post, so, someone will have to pass my thanks on to him . . . THANKS!

Caruso

> **kadafi69 said:**
> problem seems to be solved, as someone mentioned above.

my original /etc/network/interfaces read like this:



as someone mentioned on laucnhpad, adding the auto eth0 then commenting out iface eth0 inet static. so my new
/etc/network/interfaces looks like:



when i rebooted a network had connected automatically (one i had previously tried to save, unsuccessfully), connecting to the internet worked fine. clicking on the NM icon displayed a list of network connections, all of which where previous failed attempts at making a connection. i managed to delete the remaining connections through NM, the ifup connection wasnt there.

---

### Post by kforum on 2008-10-08
> **iClouseau88 said:**
> Hi,

Toshiba laptop dual boot XP-Intrepid beta.

Recently I upgraded Hardy to Intrepid beta.  Today after updating I got the new version 0.7.0 of Network Manager (Before, I got a green globe but today I got a dark globe and an Interdiction sign over the mouse icon).  It shows my wired and wireless connections to be "never", etc.  eth0:"unmanaged", eth1: "disconnected".  I CAN get wired connection automatically through DHCP, but I can't change the settings back to those in the previous version of Network Manager, since it won't let me.  I tried entering correct Ip address but the positions of the decimals result in wrong address.  The 3 digit numbers don't fit in the fields.  For example, if I type 192.168.110.X I will get 1.92 or 19.2. The default decimal points get in the way, even though I just typed in the number without typing the decimals.

Any idea how I can revert to previous Network Manager version?

Thanks a lot for your help.

i dont know if you still have this problem but, it seems to me like a syntax/input issue.
Do the following, when trying to input a new ip address, simple click on the ip field(at the end preferably) and hold backspace until it erases everything and more.
that should move the dot line from 19.2 to 192.,
see if it helps.

and yes, the new net manager has its quirks, but if you force it behaves ok.

even though personally, i still dont have my static ip wifi working.

cheers.
^^

---

### Post by iClouseau88 on 2008-10-08
Hi all,

Following the thread by kadafi69 (not related to Colonel Khadafy?), I added a comment sign # to iface eth0 inet dhcp in my /etc/network/interfaces file and saved it.  This solves 2 problems:

1. Messed up network manager
2. Firefox not starting up consistently because of automatic "File-work offline"

I also got my login sound back, but perhaps this is due to updating to kernel 2.6.27.6a. 

Once again, I thank kadafi69 and others for helping me.  I also thank kforum for his suggestion.

---

