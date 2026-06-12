---
title: "after upgrade 13.04 -&gt; 13.10 issue with upstart for startpar-bridge"
date: 2013-08-28
forum: Installation &amp; Upgrades
---

### Post by nixgeek on 2013-08-28
On this server is my puppet master... 

I discovered an issue with an upstart for startpar-bridge...

root@gecko:/etc/init# puppet resource service
Error: Could not run: Execution of '/sbin/status startpar-bridge' returned 1: status: Unknown parameter: JOB

root@gecko:/etc/init# /sbin/status startpar-bridge
status: Unknown parameter: JOB


Google search finds nothing... 

Any ideas?

---

### Post by bushidoka on 2013-12-10
Did you ever resolve this?

---

### Post by Genesissx on 2013-12-18
Same issue here. Interested in the way you resolved it

---

