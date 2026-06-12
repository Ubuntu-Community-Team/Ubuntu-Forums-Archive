---
title: "Ubuntu 16.04 pulseaudio problem"
date: 2017-09-06
forum: Installation &amp; Upgrades
---

### Post by krce on 2017-09-06
Hey Guys,

I have a strange problem here.

pulseaudio is not working so pulseaudio equalizer is not working though.

When I wrote this to terminal 

[COLOR=#000000]pulseaudio

[/COLOR]
I get

E: [pulseaudio] module-ladspa-sink.c: Master sink not foundE: [pulseaudio] module.c: Failed to load module "module-ladspa-sink" (argument: "sink_name=ladspa_output.mbeq_1197.mbeq master= plugin=mbeq_1197 label=mbeq control=6.1,4.3,4.3,1.7,1.7,1.7,-0.1,-0.1,-0.1,0.8,-10.7,-14.2,-15.1,-7.2,0.0"): initialization failed.
E: [pulseaudio] main.c: Module load failed.
E: [pulseaudio] main.c: Failed to initialize daemon.

ps: my audio works fine btw.

 how can i solve this and make pulseaudio work again..

edit: /etc/pulse file is empty, there should be some text files i guess?

---

