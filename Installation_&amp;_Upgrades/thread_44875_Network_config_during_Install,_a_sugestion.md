---
title: "Network config during Install, a sugestion"
date: 2005-06-27
forum: Installation &amp; Upgrades
---

### Post by jpoyarzun on 2005-06-27
Greets,

I have a complaint/ sugestion about the network config aspect in the default ubuntu install. The issue is about the presumption on the install of a consolidated network setup with dns or fixed ip, but some users (many in my country) just have a dsl (pppoe) modem conected to their nics, and that setup dont provide a fixed or dynamic ip till the user is loged on to the wan.

In some part during the install, the install program tries to detect the user network, an in that part the dsl users get a message like: "the software didn't find a network, maybe is something wrong.... yada yada :P..., you can configure your network manually or later", if you are a first-time installer, maybe you can get scared about that message... many friends of mine do.

My sugestion is just put a single line in a network dectection telling that if you are a dsl modem user, maybe the software will not detect a network, but later when the install was finished it can be solved doing a pppoeconfig.

maybe this is not the instance to say this, but in that case please move this post or tell me where i can post this.

Thanks for your time. 

jpo :)

---

