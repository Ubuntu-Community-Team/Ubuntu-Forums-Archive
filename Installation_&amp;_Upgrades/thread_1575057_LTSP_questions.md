---
title: "LTSP questions"
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by mittwit on 2010-09-15
I've been trialling ltsp on firstly edubuntu 9.04 and also 10.04 and have had 9.04 with two network connections working ok.
What I would like to do is have fat clients running from a ltsp server with a single network connection and a separate router looking after dhcp. The clients will boot via the network.

My questions are:
1) Is **sudo apt-get install ltsp-server** all I need to do if a separate router is looking after dhcp? 

2) When I run **sudo ltsp-build-client** how do I tell the server to get the packages from a CD or DVD as it is taking up my download quota and time each time I make a client?

3) Has anyone had success making a lubuntu client?

4) Following on from the last question can the clients be a different breed of ubuntu from that of the server? (e.g. edubuntu client on a lubuntu server)

5) Assuming I can get a ltsp server on 9.04 working what are some good reasons for trying to get it to work with 10.04?

Thanks.

---

### Post by mittwit on 2010-09-15
I've started answering my questions.

Q2) A search for 'man ltsp-build-client' lead me to the following page [http://pwet.fr/man/linux/administration_systeme/ltsp_build_client](http://pwet.fr/man/linux/administration_systeme/ltsp_build_client) which contains the following:

> --mirror mirror_url
Allows a local Ubuntu mirror to be chosen for a faster download, urls like file://cdrom can also be specified here. default [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)

So it seems I can use --mirror file://cdrom and put the appropriate install CD in the CD drive. On ubuntu that may be file:///media/cdrom. I'll have to try to find out.

Having looked at [http://manpages.ubuntu.com/manpages/lucid/man8/ltsp-build-client.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/ltsp-build-client.8.html) I can see I can put the mirror option in my ltsp-build-client.conf file. Something like this:
>  # set alternate location for ubuntu mirror (--mirror)
        MIRROR="file:///media/cdrom"

---

### Post by mittwit on 2010-09-16
Q1) No it isn't that simple, not at all.
If my other dhcp server is a windows box then this page looks like where I need to go: [https://help.ubuntu.com/community/UbuntuLTSP/LTSPWindowsDHCP](https://help.ubuntu.com/community/UbuntuLTSP/LTSPWindowsDHCP)

If my dhcp server is a basic router then this page should have the answers: [https://help.ubuntu.com/community/UbuntuLTSP/ProxyDHCP](https://help.ubuntu.com/community/UbuntuLTSP/ProxyDHCP)

---

### Post by nosedrum on 2011-01-12
Hello,

I'm upgrading ltsp server working like a charm, from 9.04 to 10.04. 
I have many issues with nbd-server.

Have you upgrade yours from 9.04 to 10.04 ?

I'm interested by your report, your experience about that.
If you read me, i hope you respond.
Thx.

---

