---
title: "disabling ipv6"
date: 2006-12-09
forum: Installation &amp; Upgrades
---

### Post by xptweakerntn on 2006-12-09
i need to, because it messes up my dsl. i did it in firefox, but want to do it globally. i found an article about /etc/modprobe.d/aliases.txt, and adding in 3 lines. i did that, now, im not sure if it is disabled, i restarted ubuntu, and it doesn't seem to be when i used evolution. here is my file 

alias net-pf-1  unix
alias net-pf-2  ipv4
alias net-pf-3  ax25
alias net-pf-4  ipx
alias net-pf-5  appletalk
alias net-pf-6  netrom
alias net-pf-7  bridge
alias net-pf-8  atm
alias net-pf-9  x25
alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
#alias net-pf-10 ipv6
alias net-pf-11 rose
alias net-pf-12 decnet
# 13 NETBEUI
alias net-pf-15 af_key
alias net-pf-16 af_netlink
alias net-pf-17 af_packet

i think i did it right, not sure. did i? i also saw something somewhere about something i could type in terminal to see if ipv6 is disabled or enabled, but what is it? thanks!
# 18 ASH
alias net-pf-19 af_econet
alias net-pf-20 atm
# 22 SNA
alias net-pf-23 irda
alias net-pf-24 pppoe
alias net-pf-25 wanrouter
alias net-pf-26 llc
alias net-pf-31 bluetooth

---

### Post by catlett on 2006-12-09
[http://www.ubuntuforums.org/showthread.php?t=202838&highlight=ipv6](http://www.ubuntuforums.org/showthread.php?t=202838&highlight=ipv6) You could try rich's way

---

