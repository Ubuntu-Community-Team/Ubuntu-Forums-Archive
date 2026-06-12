---
title: "apt-cacher-ng failover proxy configuration"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by pboedt on 2010-05-04
Hello All,
i have set up apt-cacher-ng and it is working fine.
I have configured the clients using the synaptic gui, (configuration-preferences-network-set proxy...)

Is there a way to configure the clients so that they use the proxy when it is available (at the office) and they fall back to using no proxy when the proxy cannot be reached?

We have a lot of laptops at the office which are on the road a lot, in the office i want them to use apt-cacher-ng for updates and installation, when the users are not in the office they should be able to install software without having to change the synaptic conf...

---

### Post by nbotticelli on 2010-05-05
This link is for the apt-cacher program (not apt-cacher-ng) but they have some solutions for what you are looking for: [https://help.ubuntu.com/community/Apt-Cacher-Server]("https://help.ubuntu.com/community/Apt-Cacher-Server")

I'm trying to set up an apt-cacher-ng server myself and for some reason I keep running into problems getting it to work properly.

I've done it before in the past and had it work fine but it's been a while and I can't figure the same steps that I took before.

Do you have your server pulling updates/packages through itself too? 

Could you tell me the actual steps you took to make things work? So far the tutorials I've found online are all fairly old but they look like they should still work and even reading through the documentation it seems pretty straight forward and yet I am somehow still doing something wrong.

When I look at the stats page on the server it just says I have tons of misses and nothing seems to actually go through it.

Any ideas?

Thanks!

---

### Post by pboedt on 2010-05-10
I just installed it from the repository, changed the config file and it was ready to go.
I don t have the server pulling updates himself, it just acts as a cache for the clients who downloaded the updates.

I have to do a lucid server apt-cacher-ng install soon, i will post details when finished

---

