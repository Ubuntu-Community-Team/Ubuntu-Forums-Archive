---
title: "I can't get my powerbook to boot from cd"
date: 2006-05-09
forum: Installation &amp; Upgrades
---

### Post by dufnutz on 2006-05-09
I have a G4 powerbook. It has an old version of ubuntu on it that is not working so well. I thought it would be best to start from a fresh version of Dapper.

I am not sure how I was able to boot from cd the first time but this time it is giving me a lot of trouble

When I hit the power button I press and hold the "C" button. This does nothing. Then I get to the screen that sets me up to boot for ubuntu. it says press "l" for gnu/linux or "c" for cdrom. So I hit "c". It tries to read from the cd then goes back to the screen. I hit C again and it continues to do this.

I looked at the cd on a different computer and it looks like the burn went ok. Is there a different way I can confirm the CD was burned ok?

I can boot into my old ubuntu system, is there a way that I can type a command that will reboot and then boot from the cd rom on the reboot?

I have successfully installed ubuntu on lots of x86's, this is the first time I have had trouble installing ubuntu. The weird part is that I have installed it on this power book before.

Thanks in advance.

---

### Post by RavenOfOdin on 2006-05-09
Try comparing the CD image to an official one via going into Konsole and typing:

md5sum /path/to/image

---

