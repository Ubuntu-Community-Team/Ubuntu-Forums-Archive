---
title: "ipv6 not working in bridge at karmic"
date: 2009-10-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by trunet on 2009-10-22
Hello guys,

I upgraded a computer to karmic today and my ipv6 stops working:
```

# /sbin/ip -6 addr add 2001:470:x:x::1/64 dev virbr0
RTNETLINK answers: Permission denied

```This exact same line worked flawless in jaunty.

Bug???

Thanks,

Wagner Sartori Junior

---

### Post by trunet on 2009-10-22
Well,

redhat disabled the ipv6 support in bridge interface as written in [https://bugzilla.redhat.com/show_bug.cgi?id=501934](https://bugzilla.redhat.com/show_bug.cgi?id=501934)

Until there I put a sysctl -w net.ipv6.conf.virbr0.disable_ipv6=0 in my rc.local(because libvirt starts after sysctl).

Thanks,

Wagner Sartori Junior

---

