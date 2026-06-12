---
title: "apt-get update fails (at McDonalds free Wifi in USA)"
date: 2017-08-19
forum: Installation &amp; Upgrades
---

### Post by timothylegg on 2017-08-19
Hello,

I thought I would be smooth and use the free wifi to run 'sudo apt-get update' to prepare myself for installing mariadb while I was traveling.  I didn't get very far. It appears to me that they have performed some measure to keep people from using their wifi to keep their software installed/up-to-date.

I verified that I was able to load a page through a conventional web browser.

I was under the impression that apt-get downloaded using port 80, just like a web page, so you can imagine I was a bit surprised that I was thwarted.  Certainly, there must be a workaround for this.  I haven't pried to see what else is blocked, but I did notice a few weeks ago that I couldn't download maps for my Android GPS app at three different McD's stops.  (They are losing viability for me as a highway stop.)  Any ideas?


Thanks,  Tim

```

root@EeePC1005HA:/home/legg# apt-get update
Get:1 http://nmd.mcd12106.atl.wayport.net/index.adp?MacAddr=00:25:D3:78:E4:AB&IpAddr=192.168.5.177&Ip6Addr=&vsgpId=&vsgId=112007&UserAgent=&ProxyHost=&TunnelIfId=461115&VlanId=20&origDest=http://us.archive.ubuntu.com/ubuntu zesty InRelease [4,975 B]
Err:1 http://nmd.mcd12106.atl.wayport.net/index.adp?MacAddr=00:25:D3:78:E4:AB&IpAddr=192.168.5.177&Ip6Addr=&vsgpId=&vsgId=112007&UserAgent=&ProxyHost=&TunnelIfId=461115&VlanId=20&origDest=http://us.archive.ubuntu.com/ubuntu zesty InRelease
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Get:2 http://nmd.mcd12106.atl.wayport.net/index.adp?MacAddr=00:25:D3:78:E4:AB&IpAddr=192.168.5.177&Ip6Addr=&vsgpId=&vsgId=112007&UserAgent=&ProxyHost=&TunnelIfId=461115&VlanId=20&origDest=http://security.ubuntu.com/ubuntu zesty-security InRelease [4,989 B]
Err:2 http://nmd.mcd12106.atl.wayport.net/index.adp?MacAddr=00:25:D3:78:E4:AB&IpAddr=192.168.5.177&Ip6Addr=&vsgpId=&vsgId=112007&UserAgent=&ProxyHost=&TunnelIfId=461115&VlanId=20&origDest=http://security.ubuntu.com/ubuntu zesty-security InRelease
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Get:3 http://nmd.mcd12106.atl.wayport.net/index.adp?MacAddr=00:25:D3:78:E4:AB&IpAddr=192.168.5.177&Ip6Addr=&vsgpId=&vsgId=112007&UserAgent=&ProxyHost=&TunnelIfId=461115&VlanId=20&origDest=http://us.archive.ubuntu.com/ubuntu zesty-updates InRelease [4,993 B]
Err:3 http://nmd.mcd12106.atl.wayport.net/index.adp?MacAddr=00:25:D3:78:E4:AB&IpAddr=192.168.5.177&Ip6Addr=&vsgpId=&vsgId=112007&UserAgent=&ProxyHost=&TunnelIfId=461115&VlanId=20&origDest=http://us.archive.ubuntu.com/ubuntu zesty-updates InRelease
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Get:4 http://nmd.mcd12106.atl.wayport.net/index.adp?MacAddr=00:25:D3:78:E4:AB&IpAddr=192.168.5.177&Ip6Addr=&vsgpId=&vsgId=112007&UserAgent=&ProxyHost=&TunnelIfId=461115&VlanId=20&origDest=http://us.archive.ubuntu.com/ubuntu zesty-backports InRelease [4,997 B]
Err:4 http://nmd.mcd12106.atl.wayport.net/index.adp?MacAddr=00:25:D3:78:E4:AB&IpAddr=192.168.5.177&Ip6Addr=&vsgpId=&vsgId=112007&UserAgent=&ProxyHost=&TunnelIfId=461115&VlanId=20&origDest=http://us.archive.ubuntu.com/ubuntu zesty-backports InRelease
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Fetched 20.0 kB in 0s (90.5 kB/s)   
Reading package lists... Done
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/zesty/InRelease  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/zesty-updates/InRelease  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/zesty-backports/InRelease  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
E: Failed to fetch http://security.ubuntu.com/ubuntu/dists/zesty-security/InRelease  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by wildmanne39 on 2017-08-19
McDonald's makes there internet so slow it is not a viable option anyway, I know from personal experience.

---

### Post by vocx on 2017-08-19
> **timothylegg said:**
> ...Certainly, there must be a workaround for this.  I haven't pried to see what else is blocked, but I did notice a few weeks ago that I couldn't download maps for my Android GPS app at three different McD's stops.  (They are losing viability for me as a highway stop.)  Any ideas?

Thanks,  Tim


Ha ha. This is unfortunate, but I guess... there is not much you can do if they actually want to minimize people overusing their routers.

You could try to set the repositories for a different country, maybe? But other than that, I don't have many ideas, other than connecting first to a proxy that can then access the repositories.

---

### Post by lisati on 2017-08-19
Most of the hotspots in my area require you to visit their start page and agree to their T&Cs before you can use their services. Have you done this?

---

### Post by kurt18947 on 2017-08-19
I've noticed some businesses that use 3rd party wifi providers are blocking some content. One business owned by BBA won't even let me connect via Private Internet Access VPN. I don't connect to anything even slightly sensitive using a public network connection without a VPN.

---

### Post by vasa1 on 2017-08-19
Closed after discussion among forum staff because we do not encourage circumventing T&C.

---

