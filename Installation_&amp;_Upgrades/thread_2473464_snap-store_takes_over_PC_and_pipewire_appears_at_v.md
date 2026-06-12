---
title: "snap-store takes over PC and pipewire appears at very high priority"
date: 2022-04-05
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2022-04-05
Around 930 a.m. US EDT, snap-store took over my PC.  Everything came to a stop. PC fan went to higth as did CPU utilization.  I was finally able to get to system monitor. Snap-store was running flat out. Also, a new program pipewire appeared and was set to very high priority.  The snap-store (or someting else) put 20+ pages of carriage returns in a librewriter document I had open. OS = 21.10

I just started another PC. Pipewire, pipewire-media-session and pulseaudio are running at very high priority even though I have not done anyting to PC, but login and allow Ubuntu upgrades to run.  OS is also 21.10. Sanp-store is not running.;

Any reason for what is happening?

John

---

### Post by TheFu on 2022-04-05
IDK, but pipewire is a replacement for pulseaudio, to my knowledge.  I've seen reports that both can coexist. Pipewire provides a pulseaudio server for clients, so, in theory, the pulseaudio server isn't needed when pipewire is there.

Can you disable pulse and see if that solves stuff?

Thank you for testing non-LTS audio.  Much appreciated.

---

