---
title: "Install and run Node-Red on Ubuntu Core"
date: 2018-08-21
forum: Installation &amp; Upgrades
---

### Post by xav38 on 2018-08-21
Hello everybody,

I'm pretty new on the ubuntu core environnment and basic user of linux in general. I'm facing an issue after installation of Node-Red. I tried to start it with "snap node-red" but I always have an error : error: unknown command "node-red", see 'snap help'

error: unknown command "node-red", see 'snap help'

After checking the snap help, I tried "start" and "run" command without success. Does anybody use Node-Red on ubuntu Core (Raspberry Pi image) ?

Thanks by advance for your answer.

Xavier

---

### Post by xav38 on 2018-08-21
I finally answer to my question, it was regarding the active directory. When you connect via ssh, you come in the wrong folder (seen when I tried to run the "hello" snap). You just need to go to the root directory and everything run smoothly.

---

