---
title: "karmic kde networkmanager-plasma-applet not connecting wireless"
date: 2009-07-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jithin1987 on 2009-07-02
In karmic network manager plasma applet is not connecting to any wireless while nm-applet works fine. 

Is there anyone else facing this issue. Any solution available?

---

### Post by fifth on 2009-07-02
> **jithin1987 said:**
> In karmic network manager plasma applet is not connecting to any wireless while nm-applet works fine. 

Is there anyone else facing this issue. Any solution available?

Same problem here. I've been using nm-applet for quiet a while, but have tested the Plasma Widget on n off after KDE updates without any joy yet :(

---

### Post by PRGUY85 on 2009-07-02
Tested Kubuntu Karmic daily yesterday and still doesn't connect to wireless networks with the plasmid network manager.

---

### Post by jithin1987 on 2009-07-02
Both jaunty and karmic has  networkmanager-plasma-applet built from same svn source. How come jaunty one works and karmic one does not?

---

### Post by Dread Knight on 2009-07-03
This is so annoying T_T

I should stop updating when my system is fine.

---

### Post by descendent87 on 2009-07-03
network manager plasma works fine for me (always has since it first came out) using WEP encryption

---

### Post by jithin1987 on 2009-07-03
> **descendent87 said:**
> network manager plasma works fine for me (always has since it first came out) using WEP encryption

That's interesting. Did you do a fresh install or upgraded from jaunty?.

---

### Post by Yes_It's_Me on 2009-07-04
I have this very same issue.

Network Manager under Ubuntu karmic works fine, but the applet under kubuntu karmic just simply REFUSES to connect (using wpa). It's insanely frustrating. It seems to connect to ethernet fine. Has anyone submitted a bug report or should I do so.

What's everyones chipsets? Mine is the intel 4965. I don't understand why it's not working when the stack is identical.

---

### Post by jithin1987 on 2009-07-04
Bug already reported but seems no one is looking into it.
[https://bugs.launchpad.net/ubuntu/+source/plasma-widget-network-manager/+bug/392593](https://bugs.launchpad.net/ubuntu/+source/plasma-widget-network-manager/+bug/392593)

---

### Post by descendent87 on 2009-07-04
> **jithin1987 said:**
> That's interesting. Did you do a fresh install or upgraded from jaunty?.
Upgraded from jaunty originally and worked fine, messed up grub so did a fresh install of alpha 2 and still works fine for me. I seem to have got lucky with it as not many people can get it working

---

### Post by fifth on 2009-07-05
The plasmoid worked fine for me in Jaunty. It was also working after the Karmic upgrade, but it got hosed a while back after some updates - cant remember what the updates were though.

---

### Post by decoherence on 2009-07-13
Same problem. Output from lshw -C network:

       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation

wicd works fine though.

---

### Post by inportb on 2009-07-13
The network manager plasmoid works just fine for me. I'm connected on both wired and wireless interfaces at the moment, but I'm pretty sure the wireless is my primary interface at the moment.

---

### Post by jbernardo on 2009-07-14
It doesn't work for me, I have to use nm-applet (from network-manager-gnome) to be able to connect using wifi, on a aspire one 110L.

---

### Post by nikolardo on 2009-07-28
Funnily enough, my plasma network manager works fine and connects to wireless, but while connected to wireless, the icon displayed is the "wired network not connected" icon, not the "wireless connected icon."

---

### Post by buzzmandt on 2009-07-28
> **jbernardo said:**
> It doesn't work for me, I have to use nm-applet (from network-manager-gnome) to be able to connect using wifi, on a aspire one 110L.
nm-applet for me too. and aspire 3680.
I wonder if it's in the acer family this problem presents itself?

---

### Post by Kobalt on 2009-07-29
Unfortunately, I have to add myself to this long list of plasma network manager not working (using an up-to-date Koala)... It refuses to connect to a protected wifi network (any kind of encryption). I'll try with nm-applet.

---

### Post by Jay_Bee on 2009-07-29
Didn't work for me in Jaunty and it's still not working in Karmic Alpha 3 :(
This is preventing me to try running KDE for a few months.
I have intel wlan, and the connection is wpa encrypted. Plasmoid keeps showing a window to enter a password even though I entered the right password.

---

### Post by fifth on 2009-07-29
> **Jay_Bee said:**
> Didn't work for me in Jaunty and it's still not working in Karmic Alpha 3 :(
This is preventing me to try running KDE for a few months.
I have intel wlan, and the connection is wpa encrypted. Plasmoid keeps showing a window to enter a password even though I entered the right password.

Most of us are using nm-applet as an alternative until this gets fixed. Remove the plasmoid and add 'nm-applet' to your auto start apps, or F2-'nm-applet'.

[edit] Obviously I'm assuming you can get the gnome applet packages :/

---

### Post by fifth on 2009-07-30
Looks like upgrades might be on there way. Just got svn1002871 and adding the widget pops up a message recommending use of knetworkmanager since;

> 'Networkmanager is changing! It is highly unstable and may crash your desktop. Until further notice, please use KDE4 knetworkmanager instead.'

I've not tried  knetworkmanager yet, although last time I did I couldn't get that to connect either.

---

### Post by caryb on 2009-07-30
I have had the same experience as posted above in my case I can get it to work flawlessly by using WEP & not using hidden SSID the minute I use hidden it breaks. I have not tried using WPA as I have about a dozen items including printers to reconfigure & I'm just over pc support when I get home.


Cary

---

### Post by fifth on 2009-08-02
[#392593 [karmic regression] cannot connect to wireless network]("https://bugs.launchpad.net/ubuntu/+source/plasma-widget-network-manager/+bug/392593")
> 
Changed in knetworkmanager:
status: 	Unknown &#8594; In Progress


---

### Post by aamukahvi on 2009-08-02
Does it work if you set your Solid network backend to wicd?

System Settings -> advanced -> Hardware

---

### Post by fifth on 2009-08-02
> **aamukahvi said:**
> Does it work if you set your Solid network backend to wicd?

System Settings -> advanced -> Hardware

Changing the settings (for me) doesn't enable the apply button, so I cant change the settings.

Also, when selecting wicd for installation, it wants to remove the networkmanager and the plasmoid. So I don't think this would work at the moment.

---

### Post by SilvaRizla on 2009-08-02
I'm currently using wicd, I find it better however on Karmic it doesn't receive an ip address (I may have issues with DHCP as well)

dmesg output:

>    90.216443] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 1)                                                                                                
[   90.257269] b44: eth0: powering down PHY                                                                                                                       
[   90.410749] ADDRCONF(NETDEV_UP): eth0: link is not ready                                                                                                       
[   90.420037] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 2)                                                                                                
[   90.424349] wlan0 direct probe responded                                                                                                                       
[   90.424355] wlan0: authenticate with AP 00:0f:3d:65:4e:fe (try 1)                                                                                              
[   90.425945] wlan0: authenticated                                                                                                                               
[   90.425980] wlan0: associate with AP 00:0f:3d:65:4e:fe (try 1)                                                                                                 
[   90.428298] wlan0: RX AssocResp from 00:0f:3d:65:4e:fe (capab=0x421 status=0 aid=1)                                                                            
[   90.428303] wlan0: associated                                                                                                                                  
[   90.437799] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready                                                                                                 
[   93.816184] b44: eth0: Link is up at 100 Mbps, full duplex.                                                                                                    
[   93.816192] b44: eth0: Flow control is off for TX and off for RX.                                                                                              
[   93.816897] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready                                                                                                  
[  100.948019] wlan0: no IPv6 routers present                                                                                                                     
[  104.656013] eth0: no IPv6 routers present                                                                                                                      
[  144.133226] b44: eth0: powering down PHY                                                                                                                       
[  144.147554] ADDRCONF(NETDEV_UP): eth0: link is not ready                                                                                                       
[  144.352219] b44: eth0: powering down PHY                                                                                                                       
[  144.366225] ADDRCONF(NETDEV_UP): eth0: link is not ready                                                                                                       
[  147.804175] b44: eth0: Link is up at 100 Mbps, full duplex.                                                                                                    
[  147.804182] b44: eth0: Flow control is off for TX and off for RX.                                                                                              
[  147.804874] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready                                                                                                  
[  148.344217] b44: eth0: powering down PHY                                                                                                                       
[  148.362264] ADDRCONF(NETDEV_UP): eth0: link is not ready                                                                                                       
[  148.380087] wlan0: deauthenticating by local choice (reason=3)                                                                                                 
[  148.697347] ADDRCONF(NETDEV_UP): wlan0: link is not ready                                                                                                      
[  148.701190] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 1)                                                                                                
[  148.900047] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 2)                                                                                                
[  148.902839] wlan0 direct probe responded                                                                                                                       
[  148.902846] wlan0: authenticate with AP 00:0f:3d:65:4e:fe (try 1)                                                                                              
[  148.904436] wlan0: authenticated                                                                                                                               
[  148.904470] wlan0: associate with AP 00:0f:3d:65:4e:fe (try 1)                                                                                                 
[  148.906567] wlan0: RX AssocResp from 00:0f:3d:65:4e:fe (capab=0x421 status=0 aid=1)                                                                            
[  148.906572] wlan0: associated                                                                                                                                  
[  148.915680] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready                                                                                                 
[  151.804181] b44: eth0: Link is up at 100 Mbps, full duplex.                                                                                                    
[  151.804188] b44: eth0: Flow control is off for TX and off for RX.                                                                                              
[  151.804881] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready                                                                                                  
[  155.005032] No probe response from AP 00:0f:3d:65:4e:fe after 200ms, disconnecting.                                                                            
[  159.440017] wlan0: no IPv6 routers present                                                                                                                     
[  162.064016] eth0: no IPv6 routers present                                                                                                                      
[  171.721292] ADDRCONF(NETDEV_UP): wlan0: link is not ready                                                                                                      
[  171.722063] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 1)                                                                                                
[  171.724839] wlan0 direct probe responded                                                                                                                       
[  171.724846] wlan0: authenticate with AP 00:0f:3d:65:4e:fe (try 1)                                                                                              
[  171.726461] wlan0: authenticated                                                                                                                               
[  171.726503] wlan0: associate with AP 00:0f:3d:65:4e:fe (try 1)                                                                                                 
[  171.729716] wlan0: RX AssocResp from 00:0f:3d:65:4e:fe (capab=0x421 status=0 aid=1)                                                                            
[  171.729724] wlan0: associated                                                                                                                                  
[  171.740952] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready                                                                                                 
[  171.764218] b44: eth0: powering down PHY                                                                                                                       
[  171.882412] ADDRCONF(NETDEV_UP): eth0: link is not ready                                                                                                       
[  174.816180] b44: eth0: Link is up at 100 Mbps, full duplex.                                                                                                    
[  174.816188] b44: eth0: Flow control is off for TX and off for RX.                                                                                              
[  174.816886] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready                                                                                                  
[  182.372015] wlan0: no IPv6 routers present                                                                                                                     
[  185.524023] eth0: no IPv6 routers present                                                                                                                      
[  186.005028] No probe response from AP 00:0f:3d:65:4e:fe after 200ms, disconnecting.                                                                            
[  510.540395] wlan0: deauthenticating by local choice (reason=3)                                                                                                 
[  510.541186] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 1)                                                                                                
[ 1663.468215] b44: eth0: powering down PHY                                                                                                                       
[ 1663.482428] ADDRCONF(NETDEV_UP): eth0: link is not ready                                                                                                       
[ 1663.801726] ADDRCONF(NETDEV_UP): wlan0: link is not ready                                                                                                      
[ 1663.876188] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 1)                                                                                                
[ 1664.072030] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 2)                                                                                                
[ 1664.074830] wlan0 direct probe responded                                                                                                                       
[ 1664.074836] wlan0: authenticate with AP 00:0f:3d:65:4e:fe (try 1)                                                                                              
[ 1664.076562] wlan0: authenticated                                                                                                                               
[ 1664.076595] wlan0: associate with AP 00:0f:3d:65:4e:fe (try 1)                                                                                                 
[ 1664.078696] wlan0: RX AssocResp from 00:0f:3d:65:4e:fe (capab=0x421 status=0 aid=1)                                                                            
[ 1664.078701] wlan0: associated                                                                                                                                  
[ 1664.088174] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready                                                                                                 
[ 1666.804178] b44: eth0: Link is up at 100 Mbps, full duplex.                                                                                                    
[ 1666.804185] b44: eth0: Flow control is off for TX and off for RX.                                                                                              
[ 1666.804897] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready                                                                                                  
[ 1673.004028] No probe response from AP 00:0f:3d:65:4e:fe after 200ms, disconnecting.                                                                            
[ 1674.917018] wlan0: no IPv6 routers present                                                                                                                     
[ 1677.572019] eth0: no IPv6 routers present                                                                                                                      
[ 1723.742188] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 1)                                                                                                
[ 1723.940034] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 2)                                                                                                
[ 1724.140027] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 3)                                                                                                
[ 1724.340026] wlan0: direct probe to AP 00:0f:3d:65:4e:fe timed out                                                                                              
[ 1777.804098] b44: eth0: Link is down.                                                                                                                           
[ 1785.804181] b44: eth0: Link is up at 100 Mbps, full duplex.                                                                                                    
[ 1785.804188] b44: eth0: Flow control is off for TX and off for RX.                                                                                              
[ 1802.803188] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 1)                                                                                                
[ 1803.001040] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 2)                                                                                                
[ 1803.200031] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 3)                                                                                                
[ 1803.401036] wlan0: direct probe to AP 00:0f:3d:65:4e:fe timed out
[ 1809.441217] b44: eth0: powering down PHY
[ 1809.455769] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1809.770339] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1809.771189] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 1)
[ 1809.968061] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 2)
[ 1809.970853] wlan0 direct probe responded
[ 1809.970859] wlan0: authenticate with AP 00:0f:3d:65:4e:fe (try 1)
[ 1809.972445] wlan0: authenticated
[ 1809.972483] wlan0: associate with AP 00:0f:3d:65:4e:fe (try 1)
[ 1809.974578] wlan0: RX AssocResp from 00:0f:3d:65:4e:fe (capab=0x421 status=0 aid=1)
[ 1809.974583] wlan0: associated
[ 1809.983831] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1812.816186] b44: eth0: Link is up at 100 Mbps, full duplex.
[ 1812.816194] b44: eth0: Flow control is off for TX and off for RX.
[ 1812.816906] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1813.017034] No probe response from AP 00:0f:3d:65:4e:fe after 200ms, disconnecting.
[ 1820.476017] wlan0: no IPv6 routers present
[ 1823.384018] eth0: no IPv6 routers present
[ 1874.349189] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 1)
[ 1874.549030] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 2)
[ 1874.749024] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 3)
[ 1874.949026] wlan0: direct probe to AP 00:0f:3d:65:4e:fe timed out
[ 1887.341333] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1887.343190] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 1)
[ 1887.388240] b44: eth0: powering down PHY
[ 1887.513329] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1887.541092] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 2)
[ 1887.544328] wlan0 direct probe responded
[ 1887.544340] wlan0: authenticate with AP 00:0f:3d:65:4e:fe (try 1)
[ 1887.557188] wlan0: authenticated
[ 1887.557224] wlan0: associate with AP 00:0f:3d:65:4e:fe (try 1)
[ 1887.571712] wlan0: RX AssocResp from 00:0f:3d:65:4e:fe (capab=0x421 status=0 aid=1)
[ 1887.571720] wlan0: associated
[ 1887.585963] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


As you can see it will associate but I then get an error from wicd of unable to obtain IP address, I don't get any DHCP OFFERS

---

### Post by flavouride on 2009-08-02
my usb mobile broadband encountered the same problem with kernel 2.6.31.4  after the latest sudo aptitude full-upgrade.

whilst everything is fine when I use the previous kernel 2.6.31.3.

---

### Post by Zorael on 2009-08-02
As I understand, the plasma widget itself is being refactored into a new "monolithic client". Slightly edited snippets from the kubuntu-devel mailing list;
> On Wednesday 29 July 2009 20:03:33 Yuriy Kozlov wrote:
> On Wed, Jul 29, 2009 at 10:03 AM, Jonathan Thomas<echidnaman@???> wrote:
> > Riddel's email setup is a bit busted at the moment, so he asked me to
> > send this one out.
> >
> > Our favorite NetworkManager plasma widget developers have decided to
> > switch primary focus from the plasma widget to a standalone application
> > called KNetworkManager (sound familiar?) This is a monolithic client
> > written from scratch, and will probably be what all of our hopes will
> > rest upon for an un- mangled Network experience in Kubuntu 9.10.
> >
> > If you can, we would very much appreciate testing. You can record your
> > results at
> > [https://wiki.kubuntu.org/Kubuntu/PlasmaWidgetNetworkManager/0.0+svn1002781-0ubuntu1~ppa1](https://wiki.kubuntu.org/Kubuntu/PlasmaWidgetNetworkManager/0.0+svn1002781-0ubuntu1~ppa1)
> >
> >
> > That page should have sufficient instructions for the testing.
> >
> > Thanks in advance,
> > Jonathan
>
> Monolithic client? Can you clarify?

Beginning of June, we have refactored the networkmanager code for two reasons:

- it was becoming complex, too complex
- we want the networkmanager plasmoid to be usable with alternatives to
networkmanager as well, wicd, connman for example

This refactoring is mainly done, and it proves to have been a very good idea. It's
relatively easy now to "get into the code", and thus easier to make things work. Will
has written a system-tray like "monolithic" app, I'm working on the plasmoid right
now. I've taken the same opportunity to also redo the user interface. The "staple
extenders on top of each other" approach is neat and flexible, but it can be
problematic with smaller displays. The new design is more netbook-friendly (works on
a confined space, uses more horizontal space rather than vertical space), and I'm
almost at a point where I can use it myself.

Will's monolithic client is a bit further towards being stable, as its UI code is a
lot simpler, so that's probably the safest option for karmic.

Both clients share the same infrastructure, so fixing bugs in one often fixes the
other, too (though not for UI bugs).

> It's still just an interface to the NetworkManager daemon right?

Yes.
> > Monolithic client? Can you clarify?
It's a single application, as compared to a plugin for Plasma like the plasma
widget.

> It's still just an interface to the NetworkManager daemon right?
Correct.

> Do you know why the move to a standalone app from a plasmoid?

Probably easier to maintain without worrying about QGraphics* and layout
issues and the like. The whole visual presentation of the plasma widget is
undergoing major upheaval at the moment, and a system tray-type icon is easier
to do at the moment.

For what it's worth, it does use the new system tray protocol like Klipper
does, so we get a nice Plasma-themed tooltip and hover/click animations.
> > I guess the networking code is the same, so this won't help people who can't
> connect to some wifi networks. Or do I miss something?

I suspect it does use the same code - I still have no succcess with
wireless WPA-PSK (just keeps reconnecting).
See [https://lists.ubuntu.com/archives/kubuntu-devel/2009-July/003100.html](https://lists.ubuntu.com/archives/kubuntu-devel/2009-July/003100.html) for the entire thread.

So it looks like the connecting bits (that doesn't work for some people) is still the same, though at least it's getting attention.

---

