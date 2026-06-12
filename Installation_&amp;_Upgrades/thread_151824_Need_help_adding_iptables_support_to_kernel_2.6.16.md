---
title: "Need help adding iptables support to kernel 2.6.16"
date: 2006-03-28
forum: Installation &amp; Upgrades
---

### Post by zgerrz on 2006-03-28
Hello, I have compiled a vanilla 2.6.16 kernel with archck patch, using the vanilla guide in the howtos.

Everything appears to work beautifully except that once I log in to Gnome, I get a popup from firestarter saying the my kernel doesn't have iptables support, so firestarter disables itself.

I went back into xconfig to reconfigure iptables support, but it's tough to find every option required to include iptables. I found maybe 2 instances of items stating that they are "required for iptables," so I enabled them, recompiled, but still get the same error message upon bootup.

Can anyone tell me EVERY item that is required for iptables support, or perhaps a patch to fix it?

---

### Post by zgerrz on 2006-03-28
I finally managed to get some sort of iptables support by adding new compiling options. When I load up my computer, the firewall is now active, but now its blocking all internet traffic. I can only internet access by disabling firestarter.

What's the problem now?

---

### Post by zgerrz on 2006-03-29
Nevermind, I seemed to have managed to solve it after a lot of reading and trial and error.

---

### Post by Thios on 2006-04-04
Hi! I'm having exactly the same problem... Would you mind telling me what you did to solve it, please?

---

### Post by edubbler on 2006-04-12
If anyone has this working, could you please specify exactly what  I need to enable in "make menuconfig" or post your kernel config file?

Thanks!

---

### Post by towsonu2003 on 2006-04-12
same request from me: what did you enable?

I found this, maybe it will work: [http://www.ubuntuforums.org/showpost.php?p=907515&postcount=26](http://www.ubuntuforums.org/showpost.php?p=907515&postcount=26)

---

### Post by edubbler on 2006-04-12
The menu structure must have changed because it does not pick up the old configuration for this area.

I just looked at my kernel config for my previous kernel and manually selected/deselected the netfilter items. Here is what mine looks like. After doing so, everything worked.

**Note this is the relevan excerpt from the config-2.6.14.5 file***
```

# IP: Netfilter Configuration
#
CONFIG_IP_NF_CONNTRACK=m
# CONFIG_IP_NF_CT_ACCT is not set
# CONFIG_IP_NF_CONNTRACK_MARK is not set
# CONFIG_IP_NF_CONNTRACK_EVENTS is not set
# CONFIG_IP_NF_CT_PROTO_SCTP is not set
CONFIG_IP_NF_FTP=m
CONFIG_IP_NF_IRC=m
# CONFIG_IP_NF_NETBIOS_NS is not set
# CONFIG_IP_NF_TFTP is not set
# CONFIG_IP_NF_AMANDA is not set
# CONFIG_IP_NF_PPTP is not set
# CONFIG_IP_NF_QUEUE is not set
CONFIG_IP_NF_IPTABLES=m
CONFIG_IP_NF_MATCH_LIMIT=m
# CONFIG_IP_NF_MATCH_IPRANGE is not set
CONFIG_IP_NF_MATCH_MAC=m
# CONFIG_IP_NF_MATCH_PKTTYPE is not set
CONFIG_IP_NF_MATCH_MARK=m
CONFIG_IP_NF_MATCH_MULTIPORT=m
CONFIG_IP_NF_MATCH_TOS=m
# CONFIG_IP_NF_MATCH_RECENT is not set
# CONFIG_IP_NF_MATCH_ECN is not set
# CONFIG_IP_NF_MATCH_DSCP is not set
CONFIG_IP_NF_MATCH_AH_ESP=m
CONFIG_IP_NF_MATCH_LENGTH=m
CONFIG_IP_NF_MATCH_TTL=m
CONFIG_IP_NF_MATCH_TCPMSS=m
# CONFIG_IP_NF_MATCH_HELPER is not set
CONFIG_IP_NF_MATCH_STATE=m
# CONFIG_IP_NF_MATCH_CONNTRACK is not set
CONFIG_IP_NF_MATCH_OWNER=m
# CONFIG_IP_NF_MATCH_ADDRTYPE is not set
# CONFIG_IP_NF_MATCH_REALM is not set
# CONFIG_IP_NF_MATCH_SCTP is not set
# CONFIG_IP_NF_MATCH_DCCP is not set
# CONFIG_IP_NF_MATCH_COMMENT is not set
# CONFIG_IP_NF_MATCH_HASHLIMIT is not set
# CONFIG_IP_NF_MATCH_STRING is not set
CONFIG_IP_NF_FILTER=m
CONFIG_IP_NF_TARGET_REJECT=m
CONFIG_IP_NF_TARGET_LOG=m
CONFIG_IP_NF_TARGET_ULOG=m
CONFIG_IP_NF_TARGET_TCPMSS=m
# CONFIG_IP_NF_TARGET_NFQUEUE is not set
CONFIG_IP_NF_NAT=m
CONFIG_IP_NF_NAT_NEEDED=y
CONFIG_IP_NF_TARGET_MASQUERADE=m
CONFIG_IP_NF_TARGET_REDIRECT=m
# CONFIG_IP_NF_TARGET_NETMAP is not set
# CONFIG_IP_NF_TARGET_SAME is not set
CONFIG_IP_NF_NAT_SNMP_BASIC=m
CONFIG_IP_NF_NAT_IRC=m
CONFIG_IP_NF_NAT_FTP=m
CONFIG_IP_NF_MANGLE=m
CONFIG_IP_NF_TARGET_TOS=m
# CONFIG_IP_NF_TARGET_ECN is not set
# CONFIG_IP_NF_TARGET_DSCP is not set
CONFIG_IP_NF_TARGET_MARK=m
# CONFIG_IP_NF_TARGET_CLASSIFY is not set
# CONFIG_IP_NF_TARGET_TTL is not set
# CONFIG_IP_NF_RAW is not set
CONFIG_IP_NF_ARPTABLES=m
CONFIG_IP_NF_ARPFILTER=m
# CONFIG_IP_NF_ARP_MANGLE is not set

```

---

### Post by edubbler on 2006-04-12
I realized it would probably be better for me to post the netfilter segment from my actual config-2.6.16.4 file and not from the config-2.6.14.5 file I based my changes in `make menuconfig` on. 

Now with cut & paste abilities, I present to you:

```

#
# Core Netfilter Configuration
#
CONFIG_NETFILTER_NETLINK=y
# CONFIG_NETFILTER_NETLINK_QUEUE is not set
# CONFIG_NETFILTER_NETLINK_LOG is not set
CONFIG_NETFILTER_XTABLES=m
# CONFIG_NETFILTER_XT_TARGET_CLASSIFY is not set
CONFIG_NETFILTER_XT_TARGET_MARK=m
# CONFIG_NETFILTER_XT_TARGET_NFQUEUE is not set
# CONFIG_NETFILTER_XT_MATCH_COMMENT is not set
CONFIG_NETFILTER_XT_MATCH_CONNTRACK=m
# CONFIG_NETFILTER_XT_MATCH_DCCP is not set
# CONFIG_NETFILTER_XT_MATCH_HELPER is not set
CONFIG_NETFILTER_XT_MATCH_LENGTH=m
CONFIG_NETFILTER_XT_MATCH_LIMIT=m
CONFIG_NETFILTER_XT_MATCH_MAC=m
CONFIG_NETFILTER_XT_MATCH_MARK=m
# CONFIG_NETFILTER_XT_MATCH_PKTTYPE is not set
# CONFIG_NETFILTER_XT_MATCH_REALM is not set
# CONFIG_NETFILTER_XT_MATCH_SCTP is not set
CONFIG_NETFILTER_XT_MATCH_STATE=m
# CONFIG_NETFILTER_XT_MATCH_STRING is not set
CONFIG_NETFILTER_XT_MATCH_TCPMSS=m

#
# IP: Netfilter Configuration
#
CONFIG_IP_NF_CONNTRACK=m
# CONFIG_IP_NF_CT_ACCT is not set
# CONFIG_IP_NF_CONNTRACK_MARK is not set
# CONFIG_IP_NF_CONNTRACK_EVENTS is not set
# CONFIG_IP_NF_CONNTRACK_NETLINK is not set
# CONFIG_IP_NF_CT_PROTO_SCTP is not set
CONFIG_IP_NF_FTP=m
CONFIG_IP_NF_IRC=m
# CONFIG_IP_NF_NETBIOS_NS is not set
# CONFIG_IP_NF_TFTP is not set
# CONFIG_IP_NF_AMANDA is not set
# CONFIG_IP_NF_PPTP is not set
# CONFIG_IP_NF_QUEUE is not set
CONFIG_IP_NF_IPTABLES=m
# CONFIG_IP_NF_MATCH_IPRANGE is not set
CONFIG_IP_NF_MATCH_MULTIPORT=m
CONFIG_IP_NF_MATCH_TOS=m
# CONFIG_IP_NF_MATCH_RECENT is not set
# CONFIG_IP_NF_MATCH_ECN is not set
# CONFIG_IP_NF_MATCH_DSCP is not set
CONFIG_IP_NF_MATCH_AH_ESP=m
CONFIG_IP_NF_MATCH_TTL=m
CONFIG_IP_NF_MATCH_OWNER=m
# CONFIG_IP_NF_MATCH_ADDRTYPE is not set
# CONFIG_IP_NF_MATCH_HASHLIMIT is not set
CONFIG_IP_NF_FILTER=m
CONFIG_IP_NF_TARGET_REJECT=m
CONFIG_IP_NF_TARGET_LOG=m
CONFIG_IP_NF_TARGET_ULOG=m
CONFIG_IP_NF_TARGET_TCPMSS=m
CONFIG_IP_NF_NAT=m
CONFIG_IP_NF_NAT_NEEDED=y
CONFIG_IP_NF_TARGET_MASQUERADE=m
CONFIG_IP_NF_TARGET_REDIRECT=m
# CONFIG_IP_NF_TARGET_NETMAP is not set
# CONFIG_IP_NF_TARGET_SAME is not set
CONFIG_IP_NF_NAT_SNMP_BASIC=m
CONFIG_IP_NF_NAT_IRC=m
CONFIG_IP_NF_NAT_FTP=m
CONFIG_IP_NF_MANGLE=m
CONFIG_IP_NF_TARGET_TOS=m
# CONFIG_IP_NF_TARGET_ECN is not set
# CONFIG_IP_NF_TARGET_DSCP is not set
# CONFIG_IP_NF_TARGET_TTL is not set
# CONFIG_IP_NF_RAW is not set
CONFIG_IP_NF_ARPTABLES=m
CONFIG_IP_NF_ARPFILTER=m
# CONFIG_IP_NF_ARP_MANGLE is not set

```

---

### Post by towsonu2003 on 2006-04-13
thanks a lot. This should be useful. Unfortunately, I noticed a lot of old config arguments don't get passed to the new .config (just like iptables support), which seem to cause the numerous error messages I get on shut down. There also seems to be a problem with compiling ndiswrapper, although I didnt work on that much. 

I'll pass on this kernel for now, but thanks a lot for posting the fix for iptables. That gave me a lot of insight :)

---

