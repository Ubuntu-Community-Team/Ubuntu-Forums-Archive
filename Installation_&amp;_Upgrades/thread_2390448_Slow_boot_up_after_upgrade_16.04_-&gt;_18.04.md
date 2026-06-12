---
title: "Slow boot up after upgrade 16.04 -&gt; 18.04"
date: 2018-04-28
forum: Installation &amp; Upgrades
---

### Post by mendieta on 2018-04-28
Yesterday I upgraded to my 16.04 to 18.04. I noticed the reboot took a long time to complete. Something like a minute. I started looking around, and there was nothing obvious. I have the default "quiet" grub flag. So, I started to google around and I found something that rang a bell:

[https://askubuntu.com/questions/1013830/slow-boot-long-kernel-load-time-due-to-wrong-resume-device](https://askubuntu.com/questions/1013830/slow-boot-long-kernel-load-time-due-to-wrong-resume-device)

That solution worked very well for me (thanks to alci). So I thought I would share. Basically, all it took was to edit (as sudo) /etc/initramfs-tools/conf.d/resume, and make the RESUME line look like this: "RESUME=none". Boot time went back to normal (about 15s to a fully logged in deskop).

FWIW: I run off of an SSD, and I have two hard-drives for data/media, and a system that has a problematic BIOS and has been upgraded for many, many releases (starting with Kubuntu long ago). Never a fresh install, except the very first one. So, I tend to carry over old crap. I don't use a swap partition, even though I probably should revisit that. 

Other than that, WOW. What a beautiful release. Super polished, I love the search functionality, The transition Unity -> Gnome was seamless, and the look and feel very similar, it just feels more mature and polished.

---

