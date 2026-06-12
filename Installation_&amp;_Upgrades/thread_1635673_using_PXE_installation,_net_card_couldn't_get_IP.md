---
title: "using PXE installation, net card couldn't get IP"
date: 2010-12-02
forum: Installation &amp; Upgrades
---

### Post by richard_wu0313 on 2010-12-02
Hi All,
i want to install ubuntu by PXE, in the target device i have two net cards, one is connected to ubuntu server in which ubuntu os image stored, the other net card connects PXE server. when installing ubuntu, only one net card could get IP address. one net card connects to os image srver could get IP while the net card connects to PXE couldn't get. Did any guy meet this issue before? Thanks!

---

### Post by MikeyPooh on 2011-03-11
> **richard_wu0313 said:**
> Hi All,
i want to install ubuntu by PXE, in the target device i have two net cards, one is connected to ubuntu server in which ubuntu os image stored, the other net card connects PXE server. when installing ubuntu, only one net card could get IP address. one net card connects to os image srver could get IP while the net card connects to PXE couldn't get. Did any guy meet this issue before? Thanks!

it has been my experience that in order for ubuntu to Assign ip addresses correctly you have to have your dhcp server cofigured correctly, And in the dhcp.conf file you have to have the dhcp pool setup

Check your dhcp .conf and make sure it is done correctly

Also it has been my experience that you need 2 nics in the ubuntu server ...one for Wan and one for Lan / PXE

---

### Post by richard_wu0313 on 2011-04-11
i have two net cards, one for PXE network, named A, the other one is for company network, anmed B. when booting system from pxe and could select pxe menu, but later continue to install system, net card A couldn't get IP address any more. and i checked /var/log/syslog. at be beginning of installation, net card A could get IP address and later network was down. any help?

my dhcp.conf


allow bootp;
allow booting;
ddns-update-style none;

default-lease-time 43200;
max-lease-time 43200;

subnet 10.1.1.0 netmask 255.255.255.0 {
	option domain-name-servers 10.1.1.1;
	option subnet-mask 255.255.255.0;
	range 10.1.1.11 10.1.1.250;
	next-server 10.1.1.1;
	filename	"pxelinux.0";
   
	class "pxeclients" {
	match if substring(option vendor-class-identifier, 0, 9) = "PXEClient";
	next-server 10.1.1.1;
	filename	"pxelinux.0";
	}
}

---

### Post by HansVerbeek on 2011-04-11
I just tried to install Natty Narwhal (Ubuntu 11.04) using PXE, and experienced the same problem. The PXE phase is running OK, but as soon as the Natty Narwhal installer tries to get a DHCP address things go wrong.   I started a Wireshark trace, and investigated the problem. 
  
It appears that the dhcp client is asking for a maximum of 576 bytes (option 57, Maximum DHCP message size). This will prevent my DHCP server (a DD-WRT router/access point) from answering.  During the PXE boot phase a maximum size of 1260 bytes is requested. My DHCP server will send an DHCP offer for such a request. It will also send a reply when no max size is given in the request.  

So the conclusion is that the installer should either allow for more data to be sent in the DHCP reply, or should not restrict the message length at all, in order to get a reply from my DD-WRT DHCP server.   

I just checked with the Maverick Meerkat (Ubuntu 10.10) network installer: this installer works OK, as it is not restricting the maximum size of the reply at all. I did not investigate the source of the bug (this could possibly be a bug in DD-WRT v24-sp2 (03/17/11) mega - build 16454). 

  I would propose that Natty Narwhal is modified in such a way, that (like in Maverick Meerkat) no restrictions are applied to the maximum size of the reply, in order to make it compatible to a broader range of DHCP servers.  

Greetings, Hans Verbeek

---

### Post by richard_wu0313 on 2011-04-12
Verbeek,
do you mean you wouldn't meet the issue in ubuntu10.10 by PXE? BTW, i installed ubuntu10.04 uding the same method, and still met the issue. could you help this?

---

### Post by HansVerbeek on 2011-04-13
Re-reading your original request I now see that your problem is not related to mine. I do not get a DHCP reply at all, while you do get a DHCP reply, but only on 1 interface.

The Ubuntu installer assumes it only needs 1 network interface, and it will use that interface to contact the repository. But in your situation network A is non-routed, so you need to use network B. However the installer will not try to get an IP-address for that interface, as it already got a proper IP-address for interface A.

To solve your problem, I suggest you remove the network cable for network A when the PXE part is over, and the questions about the language and the country are asked.

In that case you will use interface A for the PXE part, and the installer will use interface B to download files from the repository.

---

