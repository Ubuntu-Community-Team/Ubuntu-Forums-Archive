---
title: "Network Manager openvpn doesn't work on 16.04 Xenial Xerus"
date: 2016-04-22
forum: Installation &amp; Upgrades
---

### Post by k-kristoferb on 2016-04-22
Hi,

Yesterday I installed the final Ubuntu 16.04 release and am now configuring it. I ran into an issue with openvpn that I have never seen before. Usually I configure openvpn using the network manager by installing the **network-manager-openvpn** package.

After installing it the VPN option should appear in the network manager VPN wizard but I can still only see PPTP VPN option there. I restarted network-manager and even rebooted my machine but I'm still stuck. Looking at logs I can't find anything openvpn-related after the apt install logs. 

Any ideas on where to go next to troubleshoot this?
Thanks
Kris

---

### Post by sammiev on 2016-04-22
> **k-kristoferb said:**
> Hi,

Yesterday I installed the final Ubuntu 16.04 release and am now configuring it. I ran into an issue with openvpn that I have never seen before. Usually I configure openvpn using the network manager by installing the **network-manager-openvpn** package.

After installing it the VPN option should appear in the network manager VPN wizard but I can still only see PPTP VPN option there. I restarted network-manager and even rebooted my machine but I'm still stuck. Looking at logs I can't find anything openvpn-related after the apt install logs. 

Any ideas on where to go next to troubleshoot this?
Thanks
Kris

Hi,

Is openvpn installed?

Works great here.

---

### Post by rich-looklively on 2016-04-22
Yes, I can confirm openvpn not working for me either.
I can import the vpn conf but it wont run.

Throws ;

"connection.gateway-ping-timeout: cannot set property:
value of "6619252" of type 'guint' is invalid or out of range
for property type 'gateway-ping-timeout' of type 'guint'
"

Using kubuntu.

---

### Post by k-kristoferb on 2016-04-22
> **sammiev said:**
> Hi,

Is openvpn installed?

Works great here.

Yes, that was installed as a dependency and is working just fine. I'm running from terminal as a temporary workaround.

Related to rich-looklively's post I can't even import a VPN config as that option is also missing from the dropdown.

I'm attaching a screenshot for clarity...

[IMG]https://tec.libertar.se/wp-content/uploads/2016/04/openvpn.png[/IMG]

---

### Post by sammiev on 2016-04-22
You need 3 files for openvpn, see attached.

---

### Post by k-kristoferb on 2016-04-22
> **sammiev said:**
> You need 3 files for openvpn, see attached.

Thanks for the tip, with that it works now after installing **network-manager-openvpn-gnome**!

Still find it strange that the package has a new dependency which is categorized as GNOME even though I'm running unity... Also, if that is indeed a dependency, why not specify as such so that it's automatically installed together? Wrong place for the question I know but just wanted to get that small rant out...

---

### Post by sammiev on 2016-04-22
> **k-kristoferb said:**
> Thanks for the tip, with that it works now after installing **network-manager-openvpn-gnome**!

Still find it strange that the package has a new dependency which is categorized as GNOME even though I'm running unity... Also, if that is indeed a dependency, why not specify as such so that it's automatically installed together? Wrong place for the question I know but just wanted to get that small rant out...

I have 6 flavors of 16.04 installed and all of them require those 3 selections. 

Glad you have it solved and hope you mark this thread as solved to help the next person.

Thanks

---

### Post by Terry_Boldt on 2016-04-28
> **sammiev said:**
> You need 3 files for openvpn, see attached.

How do I get to see the "attached". Having the same problem and installed "network-manager-openvpn-gnome', but problem persists, so I assume there still 2 other files that I need to download/install. But I don't know what they are.

The problem (for me at least) is only for a fresh install of 16.04. On 2 other machines I did upgrades from 15.10 and the problem doesn't surface with network-manager-openvpn-gnome not installed.

---

### Post by steve zissou on 2016-06-01
Hey, what's the solution? I have the same problem and can't see the attachment. 

Cheers

---

### Post by boweeb on 2016-06-09
Attached?  Where?

---

### Post by steve zissou on 2016-06-11
Yes the attachment doesn't seem to be available. the solution is to install [FONT=arial]network-manager-openvpn-gnome.[/FONT]

---

### Post by MikeMecanic on 2016-06-11
This is the command line I’m using after a fresh install.  No need to reboot and  VPN can be set immediately:
 
 
 ```
sudo apt install network-manager-openvpn-gnome


```

---

### Post by Mahmoud_Khateeb on 2016-06-14
> **sammiev said:**
> You need 3 files for openvpn, see attached.

attached?

> **steve zissou said:**
> Yes the attachment doesn't seem to be available. the solution is to install network-manager-openvpn-gnome.
That worked. Thanks!

---

### Post by aguilla1 on 2016-08-29
I have a HP pavilion with ubuntu 11 on it. The internal antenna as well as a USB 8.11 port works to get WI FI connections. I installed lubuntu 16.04 and wi fi did not work at all. I installed 14.04  and the USB 8.11n was recognized, not the internal antenna. I will have to wait with installing 16.xx until the designers have fixed the problem.

---

### Post by willyjrobinson on 2017-08-12
Thank you! This worked for me!

---

### Post by oldos2er on 2017-08-12
Old thread closed.

---

