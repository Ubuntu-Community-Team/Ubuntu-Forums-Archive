---
title: "Network issues on upgrade from 9.04 to 9.10"
date: 2010-02-13
forum: Installation &amp; Upgrades
---

### Post by slaguth on 2010-02-13
Hi,

About a week ago I upgraded from Ubuntu 9.04 to 9.10 (x86 running on a x86_64 machine). Initially, I was unable to connect to the internet, and spent the next couple hours debugging the problem. After confirming that my ethernet port was in fact working, I eventually found that the machine had somehow acquired a bogus IP address and that running dhclient would solve the problem. I thought my problem was solved, so I let the machine sit for a week.

Now it seems that I might have cured the symptom of my problem rather than the cause, since I need to run dhclient every time I start the machine in order to get my IP address sorted out with my router.

I'm wondering if anyone has suggestions for what might be going on with my system, and if there are any easy fixes to my problem (other than manually adding a call to dhclient in a startup script).

Thanks. I would be happy to provide additional information upon request.

---

