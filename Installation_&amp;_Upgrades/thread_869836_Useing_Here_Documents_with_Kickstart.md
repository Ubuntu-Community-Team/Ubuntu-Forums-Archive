---
title: "Useing Here Documents with Kickstart"
date: 2008-07-25
forum: Installation &amp; Upgrades
---

### Post by paxindustria on 2008-07-25
Hi! 

We deploy a number of RHEL and Ubuntu Servers with Kickstart, and do a number of thing on the Red Hat side dynamically through kick start. I'm rebulding our Ubuntu images to Hardy, and am trying to replicate some of that behavior on our Ubuntu builds. One of the things I'm trying to accomplish is, during the install, have the installer in %post grab the dynamic address from DHCP, and create a static assignment in /etc/network/interfaces Here is the snippit of code from my %post section of the kickstart file that I'm trying to run:

```
# No More DHCP for us! 
cat > /etc/network/interfaces <<EOF
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static

        address `ifconfig eth0 | grep "inet addr" | \
        awk ' { print $2 } ' | awk -F: ' { print $NF } '`
        netmask ifconfig eth0 | grep Mask |  \
        awk ' { print $NF } ' | awk -F: ' { print $NF } '`
        gateway `route -n| grep "^0.0.0.0" | awk '{ print $2 }'`
EOF
```


The syntax works ok in RHEL4/5 but doesn't seem to run in Ubuntu. Does anyone know if Here Doc's aren't supported? Is there another means with Ubuntu that I might grab this same information on output it to my interfaces file? I suppose I could just echo out to the interfaces file line by line, but that seems like a bit of a hack..


Thanks!

-Pax

---

