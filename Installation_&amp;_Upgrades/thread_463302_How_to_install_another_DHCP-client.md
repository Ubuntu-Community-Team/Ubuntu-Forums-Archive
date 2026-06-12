---
title: "How to install another DHCP-client"
date: 2007-06-03
forum: Installation &amp; Upgrades
---

### Post by hjml on 2007-06-03
Hi all
Hope someone will help me out of this...the current dhcp client do´snt supported by my isp, so they told me to get DHCPD or Udhcp client on my ubuntu...but how do i change/install a new dhcp-clent ?

---

### Post by hjml on 2007-06-04
any ideas anyone ?

---

### Post by louieb on 2007-06-05
> **hjml said:**
> DHCPD or Udhcp client 
There in Synaptic.
**DHCPD:** DHCP client for automatically configuring IPv4 networking. Simple configuration: supports executions of a script when the IP address changes.
 
** Udhcp** is a very small DHCP server. This package is primarily geared towards embedded systems. It does however, strive to be fully functional, and RFC compliant.

But don't have a clue how you would install one without an internet connection. Wonder why your ISP needs some oddball DHCP client. What kind if internet connection is it (Cable, DSL, Dialup)?

---

### Post by hjml on 2007-06-05
> **louieb said:**
> There in Synaptic.
But don't have a clue how you would install one without an internet connection. Wonder why your ISP needs some oddball DHCP client. What kind if internet connection is it (Cable, DSL, Dialup)?

i have SHDSL (DSL) connections...

but have anyone any suggetion for installing that with out internet connection ?

---

### Post by hjml on 2007-06-06
still no one to help me out ?

---

### Post by Pumalite on 2007-06-06
> **hjml said:**
> still no one to help me out ?

You are much better off getting a router. DSL's are famous for 'not supporting Linux'. But if you get a router, you can connect the winmodem that they usually provide to the router and have the router set to provide you with DHCP. This has the advantage of getting a 'Hardware Firewall' and the known fact that all Linuxe's will recognize this connection automatically. This has the added advantage that the DSL provider has much less control over you and your computer. I also have the feeling that they are much less able to 'throttle' you with this setup.Just tell them to install the connection and that 'you will take care of the rest'.

---

### Post by hjml on 2007-06-07
> **Pumalite said:**
> You are much better off getting a router. DSL's are famous for 'not supporting Linux'. But if you get a router, you can connect the winmodem that they usually provide to the router and have the router set to provide you with DHCP. This has the advantage of getting a 'Hardware Firewall' and the known fact that all Linuxe's will recognize this connection automatically. This has the added advantage that the DSL provider has much less control over you and your computer. I also have the feeling that they are much less able to 'throttle' you with this setup.Just tell them to install the connection and that 'you will take care of the rest'.

I tryed with my neightbo´s linksys router and it works....so think you are right on this...will try to buy a router so that i can come on the net again :)

Thanks for the great help both of you

---

