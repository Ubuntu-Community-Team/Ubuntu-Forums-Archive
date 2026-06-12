---
title: "Ubuntu slow performance after Software Update"
date: 2011-06-29
forum: Installation &amp; Upgrades
---

### Post by linux_burner on 2011-06-29
Hi folks,
I applied recommended software updates today and post-installation, Ubuntu is quite slow in almost everything. Right from booting to shut down. Even mundane actions like launching Firefox takes lot of time. 

I get video play back but it is almost non-smooth i.e. the playback clock ticks on but frames move very slow. It was silky smooth prior to update. 

I think the culprit was Kernel update. I don't remember what Kernel version I was running before the upgrade, but I was running Ubuntu 10.10 32bit (I had myriad problems with 11.04...so downgraded to 10.10). 

Right now my linux kernel is 2.6.35-30 & Gnome is 2.32.0. 

Is there anyway I can roll back the updates? I really don't want to do a fresh installation of 10.10 at this time...

I would appreciate help folks.

Thanks,
- Burner

---

### Post by linux_burner on 2011-06-29
OK,
Its confirmed that Linux kernel 2.6.35-30 is indeed the culprit. Booted into 2.6.35-28 and things just seem great.

Question, is there anyway for me to make Ubuntu boot into this kernel by default? 

Can anyone gimme instructions on how to remove kernel 2.6.35-30? Do I open Synaptic and search for the above kernel and uninstall it? Will it uninstall associated packages as well that were installed during update?

Thanks in advance

---

### Post by zero244 on 2011-06-29
I just did a fresh install of Lucid and did the initial update which updated the kernel.
I do not plan on doing anymore updates....none till I go to the next LTS version of Ubuntu.

To answer your question.......it depends on what version of grub your using.
If you have Grub2 it does things differently than the original grub.
It may just be a matter of making a change in the grub config file.
As to how your make the previous kernel the first choice.
Search around there should be some howto's.

---

### Post by linux_burner on 2011-06-29
Zero244,
Thanks for the reply.

I did look around and found a way to change Grub2 to make my older kernel boot by default. 

Awesome! I love Linux:guitar:

Yep, I will refrain from updating kernels until 11.10 is released. By then, hopefully I should have a new laptop capable of running Gnome 3:)

Regards
- B

P.S: I am marking this thread Solved

---

