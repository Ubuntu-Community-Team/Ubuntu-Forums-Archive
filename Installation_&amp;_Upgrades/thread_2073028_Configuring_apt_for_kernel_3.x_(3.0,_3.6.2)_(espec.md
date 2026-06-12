---
title: "Configuring apt for kernel 3.x (3.0, 3.6.2) (especially rtl8192ce driver)"
date: 2012-10-18
forum: Installation &amp; Upgrades
---

### Post by crismxml on 2012-10-18
I am running Ubuntu 10.04. I upgraded the kernel to 3.6.2, using the howto at [http://www.howopensource.com/2011/08/how-to-compile-and-install-linux-kernel-3-0-in-ubuntu-11-04-10-10-and-10-04/](http://www.howopensource.com/2011/08/how-to-compile-and-install-linux-kernel-3-0-in-ubuntu-11-04-10-10-and-10-04/) and it worked pretty well. It fixed the audio problem I was having.
[*]

Now I would like to configure apt to pick up changes to the kernel, and more importantly, to pick up drivers for this kernel. Wireless isn’t working for me now, and I need to find the rtl8192ce drivers for this kernel.

Any pointers on the apt config lines to use here?

Thanks in advance,
crism
[*] Microphone support had stopped working at some point; the solution was to use the ubuntu-audio-dev repository, but that stopped keeping up with kernel updates for some reason.

---

### Post by wheeze on 2012-10-18
If you compiled your own kernel you're out of luck automatically updating it.

---

### Post by crismxml on 2012-10-18
> **wheeze said:**
> If you compiled your own kernel you're out of luck automatically updating it.

Good point… but I should be able to get notifications for source updates, no? It looks like I might have jumped ahead of the Debian status quo, though, so there aren’t any repositories yet. d-: I guess I need to download the driver source, if I can find it, for rtl8192ce, and then compile the kernel module.

---

### Post by mpc755 on 2012-12-27
The following fixed it for me:

[https://support.skype.com/en/faq/FA11082/what-should-i-do-if-i-have-a-problem-with-my-audio-quality-in-skype-for-linux](https://support.skype.com/en/faq/FA11082/what-should-i-do-if-i-have-a-problem-with-my-audio-quality-in-skype-for-linux)

On Ubuntu, under System Settings - Sounds under the Input tab make sure the input volume of the internal microphone is on

---

### Post by crismxml on 2012-12-27
> **mpc755 said:**
> The following fixed it for me:

[https://support.skype.com/en/faq/FA11082/what-should-i-do-if-i-have-a-problem-with-my-audio-quality-in-skype-for-linux](https://support.skype.com/en/faq/FA11082/what-should-i-do-if-i-have-a-problem-with-my-audio-quality-in-skype-for-linux)

On Ubuntu, under System Settings - Sounds under the Input tab make sure the input volume of the internal microphone is on

Thanks… but no, it is a known kernel bug. I’m now happily using Mint Maya; microphone, wireless, and everything else Just Work, with no worries about Unity or privacy violations.

---

