---
title: "No sound anymore from GP108 after upgrade from 22.4 to 22.10"
date: 2022-10-26
forum: Installation &amp; Upgrades
---

### Post by gertversteeg1956 on 2022-10-26
Yesterday I upgraded my pc from Ubuntu 22.4 to 22.10 . It hosts an on board audio controller ('NVIDIA Corporation GP108 High Definition Audio Controller' ). After the upgrade the pc does not produce sound anymore. It worked fine before the upgrade . The additional drivers program indicates that 'NVIDIA driver metapackage van nvidia-driver-515' is being used. However in settings I can not select it. The only option I can select is Dummy Output.

Can someone give me a tip on how to make it work again?
I added 2 screendumps. Posted the question also in the Dutch Ubuntu forum

I few weeks ago I read some article about NVIDIA Audio controllers. Newer Linux kernels should support them natively. Unfortunately I cannot find it anymore.

---

### Post by gertversteeg1956 on 2022-10-27
Thanks for responding. Audio should be a standard thing and work out of the box in my opinion. Yesterday I did a clean installation (on a separate partition) of xubuntu 20.4 . Audio works fine. I'll try to figure out how to install Pipewire and will experiment with clean installations of 22.10 as well
In synaptic you can see that several pipewire modules are installed; I'll try to install some more of them (PipeWire ALSA plugin, transitional package for pipewire-alsa and pipewire-jack, libraries for the PipeWire multimedia server - documentation, PipeWire JACK plugin, PipeWire multimedia server - tests and examples, PipeWire V4L2 plugin and PipeWire audio plugins for VLC),

---

### Post by QIII on 2022-10-27
Note on continuity of this thread:

A post by another member was moved to a different thread because that user, though finding a similar symptom, is using different hardware.

---

### Post by QIII on 2022-10-27
> **gertversteeg1956 said:**
> Audio should be a standard thing and work out of the box in my opinion. 


Yes, it should.  Please note that you are using an interim release, not an LTS.  Interim releases are sometimes subject to more frequent bugs than LTS releases.  I do not use interim releases for daily production machines and consider them to be community testing platforms leading to the next LTS release.  That being the case, it is often a good idea to submit bug reports when such things as this are encountered.

As we help each other work through difficulties here, we find work-arounds or solutions that might be instructional for the community.

As there is no 22.20 release, I presume you mean 22.04?  That is an LTS release and I expect that your sound issue should not appear.

---

### Post by gertversteeg1956 on 2022-10-27
sorry 22.20 should be 22.10. I corrected it
I use Ubuntu since 2006 and always used the interim releases as well.
Do you know if I can undo the upgrade?
I'll install 22.10 on a less critical machine and file a bug report.
By the way: installation of the other modules does not work

---

### Post by gertversteeg1956 on 2022-10-27
I installed 22.04 on a separate partition. Everything works fine now.
Will test again with 22.10 in a later stage.

---

