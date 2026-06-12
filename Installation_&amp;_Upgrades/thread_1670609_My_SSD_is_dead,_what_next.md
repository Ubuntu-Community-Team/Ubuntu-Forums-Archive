---
title: "My SSD is dead, what next?"
date: 2011-01-19
forum: Installation &amp; Upgrades
---

### Post by marshmugger on 2011-01-19
My Acer Aspire One A110 (with the slow 8GB SSD) died and I could not even reinstall Ubuntu 10.04 from the USB (failed while copying).

 I'm waiting for parts to replace the SSD (with flash memory again) and I would like to prevent killing my SSD a second time:

Do I need swap? I have upgraded the RAM to 1.5 GB. Some users recommend to disable swap and hibernation. Good idea?

Do I need journaling? Some users recommend to use the Ext4 file system and then  disable journaling. Others say that the noatime option is enough.

Any other SSD performance hints? Should I schedule fsck or some other file checking on booting. Trim.

I've been using Ubuntu since 9.04 and several times have had my computer die and need a fsck on reboot. I would like to optimise the file system to avoid future problems.

I have an old WinXP laptop, have not reinstalled the OS since 2004. It's a brick, but it works, first time, every time. My challenge to Ubuntu forum members is to get the same stability from Ubuntu.

I would appreciate some general, simple suggestions and nothing too specialised, technical and difficult to implements.

Cheers.

---

### Post by mikewhatever on 2011-01-19
What's next? Funeral, I suppose.

Seriously though, why do you think you'd killed the ssd? All storage media dies eventually, some sooner and some later.

---

### Post by marshmugger on 2011-01-21
If I a fresh install fails while copying the files, I would say the SSD is rooted, wouldn't you??? I had previously installed 10.04 and other versions on this machine. I didn't try something new or different. Too many writes to a SSD (over 2 years) = failure. 

I'm surprised that Ubuntu geeks have not taken up my challenge to make an install that will be stable for 7 years.

---

### Post by randiroo76073 on 2011-01-21
While the newer ssd's have better life times to them you're still asking us to bet on hardware. You should read what the mfg recommends, we don't even know what brand you're buying or the specs on it.

---

### Post by bazzal1941 on 2011-01-21
I have been reading up on ssd mainly because I have made one the root device for a sever I have just built. When I read that my drive was good for a 100G writes per day for five years I stopped reading.

Admittedly some of the information out there on ssd's is confusing but there does appear to be a consensus. Not sure why you would need swap space on a laptop. The advice appears to be ext4 without journalling. Trim only works if the ssd firmware supports it. You should not bother with bootup checks, just let Ubuntu do its own thing.

Not sure what your challenge is all about, or are you suggesting in some way that Ubuntu killed your drive?

---

### Post by psusi on 2011-01-21
You need swap in order to hibernate, which is kind of handy for saving power without completely shutting down.  Without the journal, you will have to endure a full fsck if you crash, and that is a bit more likely to have problems.  Disabling atime is a good idea.

I got a 64gb ssd last march.  In that time, I have migrated entire partitions on and off of it with LVM a few times, and still the SMART stats report I have only used 2% of the write life of the drive.

---

### Post by akand074 on 2011-01-21
> **psusi said:**
> You need swap in order to hibernate, which is kind of handy for saving power without completely shutting down.  Without the journal, you will have to endure a full fsck if you crash, and that is a bit more likely to have problems.  Disabling atime is a good idea.

I got a 64gb ssd last march.  In that time, I have migrated entire partitions on and off of it with LVM a few times, and still the SMART stats report I have only used 2% of the write life of the drive.

Cool where did you check the write life? I got a new SSD with my system I built a little over a month ago.. I didn't do anything I just did a normal install and put swap space even though I never use it. I don't think most people have any idea what they are talking about, they just read stuff on the internet and decided it was true. So I decided not to waste my time. If it lasts me two years that will be more than enough for me though.. I'll just buy a new one then.

---

### Post by psusi on 2011-01-21
It is one of the SMART attributes my drive ( OCZ Vertex ) provides.

---

