---
title: "Cisco AnyConnect VPN Client"
date: 2010-03-04
forum: Installation &amp; Upgrades
---

### Post by 2uRcJQ34G1 on 2010-03-04
[FONT=Verdana][SIZE=2][COLOR=Black]Hiya,

In order to gain access to my university network remotely I was asked to open a website that would act as a gateway. Upon opening the site I was asked to run a Java application, which installed a _Cisco AnyConnect VPN_ client on the system. However, now I do not need this, but I cannot find a way to uninstall it. It does not appear in the Synaptic Manager or the the ubuntu Software centre, so I cannot find the package to uninstall it. The software does appear in the 'Internet' section in the Application drop down menu and runs without the need of Firefox. I read the Cisco release notes but I could not find a way to uninstall the software. Does anyone else have a clue??

Thanks in advance.[/COLOR][/SIZE][/FONT]

---

### Post by 2uRcJQ34G1 on 2010-03-04
Just so you know, this client is different from the **network-manager-vpnc** package.

---

### Post by SGAZ on 2010-03-04
Cisco Says:

Uninstalling the Cisco AnyConnect VPN Client

To manually uninstall the AnyConnect client from a Windows system, use the standard "Add or Remove Programs" Control Panel available from the Start menu.

The procedure for manually uninstalling the AnyConnect client from a Linux or Mac OS X system is the same for both systems. As root, run the following shell script:

/opt/cisco/vpn/bin/vpn_uninstall.sh

Typically, you would do this via sudo, as follows:

$ sudo /opt/cisco/vpn/bin/vpn_uninstall.sh

If you do not use sudo, use a root shell:

# /opt/cisco/vpn/bin/vpn_uninstall.sh

The Cisco page with the really long URL is [here]("http://www.cisco.com/en/US/docs/security/vpn_client/anyconnect/anyconnect21/release/notes/anyconnect21.html#wp755495").

---

### Post by e24ohm on 2010-03-04
I deployed SSL and anyconnect at home on my 5505, and the provided script worked well.

thanks.

---

### Post by 2uRcJQ34G1 on 2010-03-04
Thanks a lot mate, worked like a charm. Cheers.

---

### Post by SGAZ on 2010-03-04
Good Deal.  Glad you asked because reading your post I realized I needed to know too.

---

