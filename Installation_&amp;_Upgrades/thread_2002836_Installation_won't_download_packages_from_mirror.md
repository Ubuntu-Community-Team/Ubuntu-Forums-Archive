---
title: "Installation won't download packages from mirror?"
date: 2012-06-13
forum: Installation &amp; Upgrades
---

### Post by Cyberpawz on 2012-06-13
I have the bootstrap version of Ubuntu, so that means 27mb on a CD.

My install gets stuck pretty early on the install, right when it is Checking the Ubuntu archive Mirror.

It gets to 100% and then freezes there. 

After about 10 minutes it tells me An Error has been detected while trying to use the specified Ubuntu archive mirror. 

I'm using the one the CD demands, is there another I should try?

---

### Post by cortman on 2012-06-13
How did you set up your network? Are you behind a proxy?

---

### Post by Cyberpawz on 2012-06-13
> **cortman said:**
> How did you set up your network? Are you behind a proxy?

Standard network, no proxy. Hard wired into the system, connected to a 4 port hub, which is connected to the router.  The firewall is not active on the router at this time. I thought that may be the problem, but it's not.

---

### Post by cortman on 2012-06-13
Try your country's official mirror- us.archive.ubuntu.com for the USA.
If that still doesn't work, did you check the md5sum of the image you downloaded? I've had corrupted images do weird things already in installation.
I assume from your comment on the 27 MB size that you're using the Ubuntu Minimal CD?

---

### Post by Cyberpawz on 2012-06-13
> **cortman said:**
> Try your country's official mirror- us.archive.ubuntu.com for the USA.
If that still doesn't work, did you check the md5sum of the image you downloaded? I've had corrupted images do weird things already in installation.
I assume from your comment on the 27 MB size that you're using the Ubuntu Minimal CD?

Yes, I'm doing the minimal CD because I want to make sure I know what is going into my computer. As for the md5sum, I checked that first thing, it's correct... 

And the official mirror, I can't choose anything but it, wish I could though.

---

### Post by cortman on 2012-06-13
> **Cyberpawz said:**
> Yes, I'm doing the minimal CD because I want to make sure I know what is going into my computer. As for the md5sum, I checked that first thing, it's correct... 

And the official mirror, I can't choose anything but it, wish I could though.

I like the minimal CD a lot myself. That's what I use for all my Ubuntu installations.
I'm not sure what else could be the problem. You might try pinging the mirror from a live CD or something to make sure it is reachable...

---

### Post by Cyberpawz on 2012-06-13
> **cortman said:**
> I like the minimal CD a lot myself. That's what I use for all my Ubuntu installations.
I'm not sure what else could be the problem. You might try pinging the mirror from a live CD or something to make sure it is reachable...

Already did, the server pings fine, I guess it was overloaded or something. I got to finish the install after everything was said and done.

---

