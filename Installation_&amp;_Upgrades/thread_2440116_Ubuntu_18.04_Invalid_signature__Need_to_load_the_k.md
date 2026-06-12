---
title: "Ubuntu 18.04 Invalid signature / Need to load the kernel first"
date: 2020-04-06
forum: Installation &amp; Upgrades
---

### Post by ryanallandorn on 2020-04-06
[COLOR=#242729][FONT=Arial][FONT=inherit]I have an older ASUS machine that I installed Ubuntu onto, originally I installed Ubuntu 14.04 (was just the flashed USB that I happened to have), but went through all of the update process to upgrade to 16.04, then to 18.04. I feel like I did all of the upgrades via the Software Manager, but it's been a few months since I did and can't completely remember.[/FONT]
[FONT=inherit]After that I did things like:
[/FONT]

> sudo apt-get autoremove
sudo apt-get autoclean
[/FONT][/COLOR][COLOR=#242729][FONT=Arial]

[FONT=inherit]When I restarted the computer I got a [Kernel Boot Error]("https://i.stack.imgur.com/b0AGZ.jpg")

[/FONT][/FONT][/COLOR][IMG]https://i.stack.imgur.com/b0AGZ.jpg[/IMG][COLOR=#242729][FONT=Arial][FONT=inherit]
[/FONT]
> error: /boot/vmlinuz-5.3.0-7629-generic has invalid signature
error: you need to load the kernel first

[FONT=inherit]I&#8217;ve been doing some reading and think that disabling secure boot may fix this, but would appreciate any other insights / ideas.[/FONT]
[FONT=inherit]Thank you in advance[/FONT]

[FONT=inherit][FONT=inherit][boot]("https://askubuntu.com/questions/tagged/boot") [18.04]("https://askubuntu.com/questions/tagged/18.04") [kernel]("https://askubuntu.com/questions/tagged/kernel")[/FONT]
[/FONT]
[/FONT][/COLOR]

---

### Post by mörgæs on 2020-04-06
Hi, welcome to the fora.
The GNU/Linux community has fought a fierce battle against the so-called 'Secure' Boot and yes, it should always be disabled. 

That being said you will probably also benefit from a fresh install of Ubuntu 18.04.4 or 19.10. Upgrades (from one release number to the next) are risky.

---

