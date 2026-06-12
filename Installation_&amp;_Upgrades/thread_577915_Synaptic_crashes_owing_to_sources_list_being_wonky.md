---
title: "Synaptic crashes owing to sources list being wonky"
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by larryfroot on 2007-10-16
A quote from synaptic...on start up...this is a pop up window loading before the full app becomes available...

": Malformed line 54 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report." 

If I OK it, synaptic crashes. If I close it, synaptic crashes. If I leave it there, then I get old as I watch the timer go around and around and around and around...

Synaptic is sort of important...so please! Someone heeeeelp! Thanks!

---

### Post by Pumalite on 2007-10-16
Post:
cat /etc/apt/sources.list

---

### Post by larryfroot on 2007-10-16
OK chaps...panic over. I went into software sources and removed a non-free repositary from the third party bit. Synaptic back to normal. Thanks for looking anyways!:)

---

