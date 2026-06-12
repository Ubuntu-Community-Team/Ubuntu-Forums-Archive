---
title: "Suggestion for 4GB ram"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by ilSignorCarlo on 2009-11-20
Hi,
today I'm gonna receive a new desktop computer.

I'm still deciding which Ubuntu version to install so I'm here to ask for your help and suggestion.

I'll have 4GB of ram and this processor: Intel® Core™ i7-860 Processor.

I'm not sure if it would be best to install Ubuntu 64bit or just 32bit and use the right PAE kernel.

In both cases I'd like to install a real time kernel because I need to use Jack and a lot of audio application. So, which would be the best option?

Thanks you.

---

### Post by lemming465 on 2009-11-21
With 4 GiB of RAM and performance requirements, I'd go with 64-bit (called "amd64").  In your case it might make sense to look at the derived [64 studio]("http://www.64studio.com/") distribution.

---

### Post by ilSignorCarlo on 2009-11-21
> **lemming465 said:**
> With 4 GiB of RAM and performance requirements, I'd go with 64-bit (called "amd64").  In your case it might make sense to look at the derived [64 studio]("http://www.64studio.com/") distribution.

Thanks. But is this 64studio the same as ubuntustudio, for 64 bit architectures? From what I recall UbuntuStudio is the same as Ubuntu, with the real time kernel and having an Ubuntu it was possible to install the needed packages for UbuntuStudio. Is it the same with 64studio or there are more differences?

---

### Post by lemming465 on 2009-11-24
I haven't tried either 64studio or ubuntu studio personally.  64studio is currently based off ubuntu, so they have some similarities, but they are different projects.  Both projects add real-time kernel patches to improve audio performance and preconfigure a bunch of music and multimedia apps.  Both projects are available in 32 (i386) and 64 (amd64) bit versions.  The 64 bit versions are recommended, I think.

I don't know how the current 64studio beta compares to ubuntu studio 9.10; as of 9.04 there were a fair number of audiophiles who found 64studio less work to configure and more stable in operation.  If you have the time and bandwidth, it's perfectly OK to try both and see which is better for you.

---

