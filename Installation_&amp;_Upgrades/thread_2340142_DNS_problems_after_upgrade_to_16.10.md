---
title: "DNS problems after upgrade to 16.10"
date: 2016-10-16
forum: Installation &amp; Upgrades
---

### Post by koma77 on 2016-10-16
I'm experiencing intermittent DNS problems after upgrading from 16.04 to 16.10.
After a fresh boot everything works as normal for about an hour or something like that.
Then, some domains (for example imgur.com) cannot be resolved. Other hosts continue to resolve correctly.

I have tried both my ISPs DNS server and Googles 8.8.8.8 and I see the problem with both settings, so it is likely something in my machine.

Other computers on the same LAN can resolve these addresses when I have the issue.

Sometimes the problem goes away after a while only to return at a later time.

I get the issue using both Chrome and Firefox. I've never seen the issue prior to upgrading.

I'm not running a firewall.

Restarting the networking service does not help.

What can I check to try to pinpoint this issue?
Any ideas what I can test?

---

### Post by mephi-mephi on 2016-10-17
I've been getting the exact same issue on my Dell XPS13 laptop. My Ubuntu desktop is unaffected (both on 16.10)
A packet capture on my laptop wifi interface has shown that my PC isn't making DNS requests for the domains that aren't working.

It's not all domains and a reboot fixes it for a short while.

---

### Post by koma77 on 2016-10-17
I'm starting to suspect dnsmasq. I have not have time to investigate but this seems like a potential culprit...

---

### Post by mephi-mephi on 2016-10-17
It looks like dnsmasq has been switched out in 16.10.
According to [http://news.softpedia.com/news/ubuntu-16-10-yakkety-yak-switches-to-a-universal-local-dns-resolver-service-504770.shtml](http://news.softpedia.com/news/ubuntu-16-10-yakkety-yak-switches-to-a-universal-local-dns-resolver-service-504770.shtml) it's systemd-resolved now.
And while I don't have enough detail to confirm if it's the culprit, there's a mailing list statement here: [https://lists.dns-oarc.net/pipermail/dns-operations/2016-June/014964.html](https://lists.dns-oarc.net/pipermail/dns-operations/2016-June/014964.html) with some concerns, specifically:
"[COLOR=#000000]- It won't work well with applications that have their own DNS code
[/COLOR][COLOR=#000000]    itside. Such as browsers. This becomes worse when you think about [/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000000]    browsers supporting draft-shore-tls-dnssec-chain-extension.[/COLOR]"

---

### Post by koma77 on 2016-10-17
I have dnsmasq running on my updated 16.10 machine.
And when the issue happened I forced a reload of the dnsmasq service, and the issue went away!
I don't know if it was a coincidence or not, I will check some more...

---

### Post by AATLEMIDRM on 2016-10-17
I'm seeing the same problem on an upgraded Ubuntu GNOME desktop. Everytime that a site won't load, reloading dnsmasq with ```
sudo service dnsmasq restart
``` seems to fix it for a few hours.

---

### Post by deadflowr on 2016-10-17
I wonder if it relates to this (and the following two posts) problems:
[https://ubuntuforums.org/showthread.php?t=2340042&p=13557382#post13557382]("https://ubuntuforums.org/showthread.php?t=2340042&p=13557382#post13557382")

---

### Post by AATLEMIDRM on 2016-10-17
The line in my /etc/nsswitch.conf reads like the "works much better with" example, except with myhostname inserted:

```
hosts:          files myhostname mdns4_minimal [NOTFOUND=return] resolve [!UNAVAIL=return] dns
```

(That's a copy and paste.)

---

### Post by koma77 on 2016-10-17
Interesting... 
It might very well have something to do with this.
I do not know that much about these things to be able to tell. But it smells right at least.

---

### Post by AATLEMIDRM on 2016-10-17
For the moment I added a line to root's crontab that restarts dnsmasq every minute. It's killing a fly with a flamethrower, but it also seems to be a relatively ferocious fly and a relatively harmless flamethrower, so...

---

### Post by koma77 on 2016-10-17
I honestly do not remember installing dnsmasq. It must have been installed as a dependency of something else.
I wonder if it is safe to remove it?
Is there any way to determine what caused a certain package to get installed in the first place?

---

### Post by mephi-mephi on 2016-10-18
Huh, restarting dnsmasq worked for me too, and I don't remember installing it either.

I tried to remove it to see what it relied on, and it seems like it's a core component:
> mephi@mephi-laptop:~$ sudo apt remove dnsmasq-base 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  account-plugin-tools accountsservice-ubuntu-schemas accountsservice-ubuntu-touch-schemas address-book-service biometryd-bin dns-root-data evolution-data-server-utouch history-service indicator-transfer
  indicator-transfer-download-manager libbiometryd1 libboost-locale1.61.0 libboost-serialization1.61.0 libcapnp-0.5.3 libconnectivity-qt1 libdbus-cpp5 libhardware2 libhistoryservice0 libhybris-common1
  libindicator-transfer0 libjsoncpp1 libleveldb1v5 liblightdm-qt5-3-0 libndp0 libnet-cpp2 libnma-common libnma0 libonline-accounts-daemon1 libonline-accounts-qt1 libpay2 libprocess-cpp3 libqdjango-db0
  libqmenumodel0 libqofono-qt5-0 libqt5concurrent5 libqt5contacts5 libqt5multimediaquick-p5 libqt5systeminfo5 libqt5versit5 libqt5xmlpatterns5 libsystemsettings1 libtelepathy-qt4-2 libtelepathy-qt5-0
  libthumbnailer-qt1.0 libtrust-store2 libubuntu-application-api3 libubuntu-location-service3 libubuntu-platform-hardware-api3 libubuntuoneauth-2.0-0 libudm-priv-common1 libunity-api0 libunity-scopes1.0
  libusermetricsinput1 libusermetricsoutput1 libzmqpp4 mir-client-platform-mesa5 mir-graphics-drivers-desktop mir-platform-graphics-mesa-kms10 mir-platform-graphics-mesa-x10 mir-platform-input-evdev5 pay-ui
  policykit-unity8 qmenumodel-qml qml-module-biometryd qml-module-ofono qml-module-pamauthentication0.1 qml-module-qmltermwidget1.0 qml-module-qtmultimedia qml-module-qtquick-xmllistmodel qml-module-qtsysteminfo
  qml-module-ubuntu-connectivity qml-module-ubuntu-onlineaccounts2 qml-module-ubuntu-settings-components qml-module-ubuntu-thumbnailer0.1 qml-module-ubuntuone qtcontact5-galera qtdeclarative5-gsettings1.0
  qtdeclarative5-qtmir-plugin qtdeclarative5-ubuntu-settings-components qtdeclarative5-ubuntu-telephony0.1 qtdeclarative5-ubuntu-web-plugin qtdeclarative5-unity-notifications-plugin qtmir-desktop
  qtubuntu-desktop smartmontools sqlite3 telephony-service thumbnailer-service tone-generator ubuntu-application-api3-desktop ubuntu-application-api3-test ubuntu-download-manager ubuntu-keyboard-data
  ubuntu-terminal-app ubuntuone-credentials-common unity-plugin-scopes unity8-common usermetricsservice
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libaccount-plugin-facebook libaccount-plugin-twitter
The following packages will be REMOVED
  account-plugin-ubuntuone checkbox-converged checkbox-gui checkbox-qt dnsmasq-base indicator-network network-manager network-manager-gnome network-manager-openvpn network-manager-openvpn-gnome
  network-manager-pptp network-manager-pptp-gnome pay-service plainbox-provider-checkbox plainbox-provider-resource-generic ubuntu-desktop ubuntu-push-client ubuntu-system-settings
  ubuntu-system-settings-online-accounts unity-scope-click unity8 unity8-desktop-session unity8-private
The following NEW packages will be installed
  libaccount-plugin-facebook libaccount-plugin-twitter
0 to upgrade, 2 to newly install, 23 to remove and 0 not to upgrade.
Need to get 10.5 kB of archives.
After this operation, 56.5 MB disk space will be freed.
Do you want to continue? [Y/n] n
Abort.


---

### Post by AATLEMIDRM on 2016-10-19
Just thought that I'd note that I missed the workaround in deadflowr's link on the first page. That workaround was to comment out the dnsmasq line in /etc/NetworkManager/NetworkManager.conf. That seems to do the trick for me (I turned off my earlier crontab "fix"), though I'd classify this as still testing. If I haven't bumped into the problem again by the end of the day then I'll post here again.

By the way, the reason that I missed this is because the workaround said that it was for use with virtual networks. I don't have virtual networks set up on this machine, so it seems that there are situations where it interferes with normal DNS.

---

### Post by alj-3 on 2016-10-19
I, too, am having DNS name resolution problems. I did a fresh install and just checked. I don't even have dnsmasq installed.

---

### Post by AATLEMIDRM on 2016-10-19
Well, a day on my computer and no problems. I think disabling dnsmasq is the workaround.

---

### Post by paul-taniwha on 2016-10-19
I'm seeing this too - I use openconnect to connect to a juniper VPN, it worked perfectly (for years) before 16.10 - now someone interleaves the remote VPN's DNS servers (and domain names) along with 127.0.0.1 in /etc/resolv.conf ... it does it when the VPN goes up (and I have to edit resolv.conf to remove 127.0.0.1) and when the VPN is down and my laptop switches between wifi APS (I have to edit it to remove the VPN DNS servers, that data should have been discarded when the VPN went down) it's like three demented gorillas are fighting over who should supply DNS

---

### Post by thenitai on 2016-10-26
I only saw issues with mail.google.com. It randomly refused to connect to it, everything else worked. In any case, doing a "sudo apt-get remove dnsmasq" solved the issue (so far).

All in all, my experience with 16.10 is not so great (I get the "system crashed" error messages a lot). What's up? No one tested this? :)

---

### Post by gsmetal2 on 2016-10-28
I've disabled dnsmasq and moved my configuration to bind9 and have no problems now.

---

### Post by koma77 on 2016-10-31
I stopped the dnsmasq service and dns resolution still works.
Is dnsmasq really installed with a fresh 16.10 installation? If not I think I will try to uninstall dnsmasq to see if things work better.

---

### Post by koma77 on 2016-10-31
I just installed 16.10 in a VirtualBox and there is no dnsmasq installed by default.

Could it be that Ubuntu switched from dnsmasq to something else and left dnsmasq running, causing some sort of clash?

---

### Post by habana on 2016-11-30
I too have this problem as of today. I upgraded to 16.10 a month ago. Last year I had the problem with 16.04 and solved it by disabling dnsmasq in Network Manager. I have checked and confirmed that dnsmasq is still disabled. As in my case the problem has suddenly appeared, is it do with a recent update?

---

### Post by paul-taniwha on 2016-12-05
I continue to have problems, I've removed dnsmasq, didn't hel;p, essentially I think the problem is that the new systemd DNS does not play well with others.

Often when I switch from the household wifi to household ether it leaves BOTH the IP of the DNS server from the wifi along with the DNS server from the ether in /etc/resolv.conf - some apps end up using one, some the other - in my case the WIFI DNS address isn't routeable from the ether - random things fail

When I run the  VPN to work (I use openconnect) rather than just getting the DNS servers from the VPN tunnel, I get both them AND the DNS of the underlying network device (ether or WIFI) - go to the corp bugzilla server sometimes it works, some times it doesn't depending on which DNS server it chooses.

I'm getting a bit sick of manually editing /etc/resolv.conf every time I open my laptop and connect to the net again or connect or disconnect to/from the corporate VPN

---

### Post by OchoHa on 2017-01-12
Hi all,

I solved this for myself by creating this script as /etc/network/if-post-down.d/nmdnsmasq

```

#/bin/sh

if [ "$IFACE" = "eth1" ]
then
    kill `cat /var/run/NetworkManager/dnsmasq.pid`
fi

```

So far I've only had this problem with eth1. The other interfaces work fine. I haven't discovered why that is.

-mark

---

### Post by phord2 on 2017-02-07
Worked fine for me on Ubuntu 16.4.  After upgrading to 16.10 my DNS no longer resolves on my wired interface.  Seems to work fine on wireless, every time.  I've been disabling my wired interface and using only wireless as a workaround.

After reading this thread, I killed dnsmasq to experiment.  network-manager restarted it automatically.  After that it worked ok, though. Maybe it will fail as it has for others. I'll keep an eye on it, and/or disable it as others here have suggested.

I haven't tried my internal network interface.  This failure occurs on my laptop dock's ethernet interface (Lenovo ThinkPad OneLink).  I noticed OchoHa's problem is also only on the 2nd ethernet interface (eth1).  Is this a clue?

I have 6 interfaces.  'ip addr' lists them in this order:

[FONT=Courier New]$ ip addr| grep ^[0-9]|cut -d: -f-2
1: lo
2: enp0s31f6
4: wlp4s0
5: virbr0
6: virbr0-nic
14: enx0050b6cf4924[/FONT]

---

### Post by rkurnik on 2017-03-14
This problem is killing me....  What have you all done to the dns system.... sheesh

---

### Post by QIII on 2017-03-14
"We" have done nothing, since we are all volunteer users and do not work for Canonical.

If you have a support request, please start your own thread.

---

### Post by rkurnik on 2017-03-14
I worked on this issue for a few days now.  Ran accross a post that I think has my problem solved:

[COLOR=#111111][FONT=Ubuntu]But in your dnsmasq configuration ([/FONT][/COLOR]/etc/dnsmasq.conf[COLOR=#111111][FONT=Ubuntu]), you have to be sure to listen the localhost DNS queries with the line [/FONT][/COLOR]listen-address=127.0.0.1[COLOR=#111111][FONT=Ubuntu].
[/FONT][/COLOR][FONT=Ubuntu, Arial, libra sans, sans-serif][COLOR=#111111]after you change it run [/COLOR][/FONT]  sudo /etc/init.d/dnsmasq restart

---

### Post by MasterCATZ on 2017-04-09
I am having massive issues since 16.04 - 16.1 upgrade

the first is loosing all networking , second no file service are working , and the list goes on 


so far the only way i have gotten network working 

is boot up safe mode / enable networking 

resolve.config file is missing 
 
  apt install --reinstall resolvconfapt install --reinstall network-manager
apt install --reinstall ubuntu-desktop

exit

keep starting up normally 

I do this on every reboot !!! 

WTF is wrong ?

---

### Post by r2ramos on 2017-05-11
I have the same problem since upgrade 17.04. I remember 6 month ago having this issue and solved it by commenting dnsmasq line in resolv.conf as has been said in this post. No more problem until now with the new upgrade, but the dnsmasq commenting thing doesn't seem to do the trick any more.

The funny thing is this: 

I connect to internet with a usb 3G device, when I use networkmanager the DNS does not resolve. As a test, I tried connecting the device with sakis3g and there DNS resolves just fine (hence I can write this in this forum). Go back to connecting with networkmanager and again resolve DNS failure (weird).

I have tried various possible solutions and nothing. Any ideas?

---

### Post by oldos2er on 2017-05-11
You'd get more response if you created a new thread for your question.

---

### Post by entropy1 on 2017-05-11
I had similar problems after a fresh install of Ubuntu-Mate 17.04. After trying two or three things that didn't work, I stumbled across [https://airvpn.org/topic/22715-leaking-dns-with-ubuntu-1704/]("https://airvpn.org/topic/22715-leaking-dns-with-ubuntu-1704/"). So now my file /etc/NetworkManager/NetworkManager.conf contains
```

[main]
plugins=ifupdown,keyfile
dns=none

[ifupdown]
managed=false

```

After rebooting once or twice, I don't have the problem.

---

### Post by litlesam on 2017-05-11
> **entropy1 said:**
> I had similar problems after a fresh install of Ubuntu-Mate 17.04. After trying two or three things that didn't work, I stumbled across [https://airvpn.org/topic/22715-leaking-dns-with-ubuntu-1704/](https://airvpn.org/topic/22715-leaking-dns-with-ubuntu-1704/). So now my file /etc/NetworkManager/NetworkManager.conf contains
```

[main]
plugins=ifupdown,keyfile
dns=none

[ifupdown]
managed=false

```

After rebooting once or twice, I don't have the problem.

This is all I did, just added # to the start of the third line. Restart NetworkManager or reboot computer.

```
[main]
plugins=ifupdown,keyfile,ofono
# dns=dnsmasq

[ifupdown]
managed=false
```

---

### Post by r2ramos on 2017-05-22
Thanks entrop1, it worked!
Although im not really sure that did the trick, because it didn't at the first boot, so i manually changed the dns server from google to my sevice provider's dns; after second reboot it worked; and i was so happy that didn't wanted to mess with the conf any more. But you did say "after rebooting once or twice", so thank you.

---

