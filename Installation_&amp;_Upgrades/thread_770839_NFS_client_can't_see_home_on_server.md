---
title: "NFS client can't see /home on server"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by tparker on 2008-04-27
No response in networking forum so reposting here since it worked in Dapper and doesn't after installing Hardy. 

My /home directory is on a network server accessed via NFS, the server is Fedora 8 and uses it's default nfs-utils-lib-1.1.0-4 and nfs-utils-1.1.0-6. A Fedora core 6 machine on the network can mount the shares. There is currently no firewall running on the server. Network card itself works fine, I can ping the server, internet works.

I have installed nfs-common and portmap via (Hardy) Synaptic. When I try to log in I get a message that no /home exists and I can't log in. The NFS on my box will not mount the NFS shares on the server. The /home directory is the same one I have been using for couple years under Dapper so I know it is there I just can't get Hardy to see it. This was a new install from CD of Hardy, not a Dapper>Hardy upgrade.

I have gone through all the set-ups and how-tos I can find and done what they say (they all say pretty much the same thing). I have turned off roaming in Sys>Admin>Network and enabled DHCP.

What am I missing? I can post config files, command outputs, anything needed that will help get this solved, just let me know what to post.

Thanks for any ideas.

---

### Post by trd79 on 2008-05-31
Hi, I have recently upgraded Gutsy -> Hardy and cannot mount NFS shares either. Am fairly sure that my problem relates to this bug [https://bugs.launchpad.net/ubuntu/+bug/213444]("https://bugs.launchpad.net/ubuntu/+bug/213444").
Have not managed to fix it yet and am considering a fresh install of Gutsy - I need a system that works and the Heron seems a little bit to broken at the moment :(

---

