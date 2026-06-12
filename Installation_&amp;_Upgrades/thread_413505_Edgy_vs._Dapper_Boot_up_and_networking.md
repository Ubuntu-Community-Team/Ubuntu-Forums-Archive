---
title: "Edgy vs. Dapper Boot up and networking"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by RyanGT on 2007-04-19
I am having troubles with Edgy and my wireless card.  It works fine if after boot up I restart networking.  But boot up hangs 2-3 minutes waiting for the network card to connect to my wireless network.  When I restart, I use
sudo /etc/init.d/networking restart
so I don't understand why it works fine the second time (i.e. after boot up).

I also don't know how to make Edgy skip networking at boot up or shorten the time it waits for DHCP or whatever it is waiting for.  And Ctrl-C doesn't work to cancel a boot item like it does with Dapper (I think this is because of upstart).

All this to say if Feisty doesn't solve this problem, I am thinking of reverting to Dapper.  I definitely notice a difference in boot up times and waiting for networking between the Edgy and Dapper live CD's (I actually have Edgy installed on the HD, but wanted an apples to apples comparison to see if Dapper really handles my networking card better).  Dapper gives a message about starting basic networking and then tries the wireless card a little later.  But it doesn't wait terribly long if the wireless card doesn't configure completely correctly.

But I don't want to do major surgery.  Is there an easy way to make Edgy handle networking and boot up similar to Dapper?  If my interaces file in/etc/network is correct, if there any reason Edgy wouldn't be able to easily and quickly configure the networking and my wireless card?

Thanks,

Ryan

---

