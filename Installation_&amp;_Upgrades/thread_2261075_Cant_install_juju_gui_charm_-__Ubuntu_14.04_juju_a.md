---
title: "Cant install juju gui charm -  Ubuntu 14.04 juju and Maas"
date: 2015-01-16
forum: Installation &amp; Upgrades
---

### Post by jgalvin2010 on 2015-01-16
Hi All,

Im new to this Forum sorry if i posted this thread in the wrong place,

I am having issues installing JUJU with MAAS

MAAS setup looks fine and I can add nodes to MAAS etc.

JUJU also bootstrapped Okay,

But when I am trying to install the juju GUI charm on a node I cant seem to see URL juju is supposed to give me after the charm is deployed,

Here is what I get from juju status :

root@deployment1:/home/james# juju status
environment: maas
machines:
  "0":
    agent-state: started
    agent-version: 1.20.14
    dns-name: ceph4.maas
    instance-id: /MAAS/api/1.0/nodes/node-a14059f4-9c07-11e4-9cf2-00237da2e4b8/
    series: trusty
    hardware: arch=amd64 cpu-cores=8 mem=16384M
    state-server-member-status: has-vote
  "1":
    agent-state-info: 'getInstanceNetworkInterfaces failed: invalid hardware information
      for node "/MAAS/api/1.0/nodes/node-03d57758-9c02-11e4-b4fa-00237da2e4b8/"'
    instance-id: pending
    series: trusty
services:
  juju-gui:
    charm: cs:trusty/juju-gui-17
    exposed: true
    units:
      juju-gui/0:
        agent-state: pending
        machine: "1"


All my servers are HP DL360 with firmware etc up to date ilo and eth2 setup on each server to the switch,

Any idea how I can fix this ?

environments.yaml:

root@deployment1:/home/james# cat /root/.juju/environments.yaml 
environments:
  maas:
    type: maas
    maas-server: 'http://172.16.1.3:80/MAAS'
    maas-oauth: 'BcNRn5VZJnHvjt6sKS:fDe6jQwvqWQeJkW876:tDYKVnBWv9ZpyaPxKJKBewTDsaCSuT7B'
    admin-secret: Password12
    default-series: trusty
    authorized-keys-path: /root/.ssh/id_rsa.pub
    bootstrap-timeout: 3600
root@deployment1:/home/james# 


Thanks,

James

---

### Post by jgalvin2010 on 2015-01-17
I got this working by disabling the ufw temporarily if anyone else runs into the same issue

service ufw disable

---

### Post by grahammechanical on 2015-01-17
There is a section of the forum called Ubuntu Servers, Cloud and Juju. I never go into this section as I have absolutely no experience with any of that stuff. It has two sub-sections: Server Platforms

[http://ubuntuforums.org/forumdisplay.php?f=339](http://ubuntuforums.org/forumdisplay.php?f=339)

and Ubuntu Cloud and Juju

[http://ubuntuforums.org/forumdisplay.php?f=392](http://ubuntuforums.org/forumdisplay.php?f=392)

I would not be surprised if some of the regulars in Ubuntu Servers, Cloud and Juju rarely frequent the Desktop Environments section. If we are not limited by our experience, as I am, we most certainly are limited by our time.

Regards.

---

### Post by MAFoElffen on 2015-01-17
Is Juju install on iron or in VM? If in VM, then you have to add some firewall rules to make sure that the host's dnsmasq does not interfere with the MAAS server's dnsmasq. For MAAS... If on a desktop, you should disable dnsmasq in network manager (edit /etc/NetworkManager/NetworkManager.conf to comment out dns=dnsmasq. If you look at this, I think some of those details are here: [Wiki/Security Team/Testing MAAS]("https://wiki.ubuntu.com/SecurityTeam/TestingMAAS")

It has to do with dnsmasg, not soley on port. MAAS is through port 80. You don't want to turn UFW completely off. You just want to set rules to allow what you want through, to be able for "that" to get through. (unless it is on a subnet and there is not any access to/from the outside world.)

And yes... this would get better exposure if a MOD would move this thread to the Juju / MAAS sub-forum of the Server Section.

---

