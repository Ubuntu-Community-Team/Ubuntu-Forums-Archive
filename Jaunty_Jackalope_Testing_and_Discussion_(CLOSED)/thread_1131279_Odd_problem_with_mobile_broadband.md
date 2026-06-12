---
title: "Odd problem with mobile broadband"
date: 2009-04-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by monkley on 2009-04-20
My Huwei E172 worked perfectly in Intrepid with Network Manger.

I've installed Jaunty RC and I'm seeing odd behaviour. When I insert the E172 into a USB slot, Jaunty recognises it and goes through the setup wizard. Then I see the NM icon in the panel turn into green dots swirling before it turns into the antenna and I get a notification saying that I'm now connected.

But if I try to browse to a site in Firefox, it just times out. Same thing happens if I try to ping.

Can someone advise me how I should troubleshoot?

(Vodafone UK, EeePC 4G)



UPDATE:

I deleted the profile in Network Manager and then reinserted the mobile broadband modem. After setting up the profile again, the modem connected and I could access the internet in Firefox. BUT I disconnected and then reconnected again and this time I was back to being "connected" but unable to access the internet. If I ping, I get a unknown host message.

---

### Post by monkley on 2009-04-21
solved:

network manager installs with the wrong profile settings

change from PPP addresses only to PPP



anyone - should this be entered into launchpad?

---

