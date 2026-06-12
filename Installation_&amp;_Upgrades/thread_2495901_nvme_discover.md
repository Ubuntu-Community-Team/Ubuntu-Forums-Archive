---
title: "nvme discover"
date: 2024-03-06
forum: Installation &amp; Upgrades
---

### Post by hxman on 2024-03-06
I am getting the following errors when trying to add/configure NVME-FC.....

# nvme discover --transport=fc --traddr=nn-0xxxxxxxxxxx --host-traddr=nn-0xxxxxxxxxxx
Failed to write to /dev/nvme-fabrics: Invalid argument




/var/log/messages 
kernel: nvme_fc: nvme_fc_parse_traddr: bad traddr string

---

### Post by MAFoElffen on 2024-03-07
The error said the format of your command was wrong...

RE: man page nvme-doscover ([https://manpages.ubuntu.com/manpages/jammy/man1/nvme-discover.1.html](https://manpages.ubuntu.com/manpages/jammy/man1/nvme-discover.1.html))
> 
EXAMPLES

       •   Query the Discover Controller with IP4 address 192.168.1.3 for all resources allocated
           for NVMe Host name host1-rogue-nqn on the RDMA network. Port 4420 is used by default:

               # nvme discover --transport=rdma --traddr=192.168.1.3 \
               --hostnqn=host1-rogue-nqn

       •   Issue a nvme discover command using a /etc/nvme/discovery.conf file:

               # Machine default 'nvme discover' commands.  Query the
               # Discovery Controller's two ports (some resources may only
               # be accessible on a single port).  Note an official
               # nqn (Host) name defined in the NVMe specification is being used
               # in this example.
               -t rdma -a 192.168.69.33 -s 4420 -q nqn.2014-08.com.example:nvme:nvm-subsystem-sn-d78432
               -t rdma -a 192.168.1.4   -s 4420 -q nqn.2014-08.com.example:nvme:nvm-subsystem-sn-d78432

               At the prompt type "nvme discover".

You are using the rough format of nvme-connevt for discovery:

RE: man page nvme-connect([https://manpages.ubuntu.com/manpages/jammy/man1/nvme-connect.1.html](https://manpages.ubuntu.com/manpages/jammy/man1/nvme-connect.1.html))
> 
EXAMPLES

       •   Connect to a subsystem named nqn.2014-08.com.example:nvme:nvm-subsystem-sn-d78432 on
           the IP4 address 192.168.1.3. Port 4420 is used by default:

               # nvme connect --transport=rdma --traddr=192.168.1.3 \
               --nqn=nqn.2014-08.com.example:nvme:nvm-subsystem-sn-d78432

The -transport' option is for mnvme-connect, but not as an option for nvme-discover... That is why it is saying it is having an nmve-fc parse error. Then since no IP address, in IP address format in the tddr field.... then further parse errors.

That is what I see from what you posted.

But not using any IP address to point it to...

---

### Post by hxman on 2024-03-07
Your example when using nvme-discover "[COLOR=#000000]*--transport=rdma" *[/COLOR][COLOR=#111111][FONT=monospace]specifies the network fabric being used for a NVMe-over-Fabrics network.
[/FONT][/COLOR][COLOR=#000000][I]In my case it's FC not RDMA.

 For example:
[/I][/COLOR]nvme discover --transport=fc --traddr=nn-0xxxxxxxxxxx --host-traddr=nn-0xxxxxxxxxxx

---

