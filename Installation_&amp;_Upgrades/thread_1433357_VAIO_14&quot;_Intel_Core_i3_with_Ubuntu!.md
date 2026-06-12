---
title: "VAIO 14&quot; Intel Core i3 with Ubuntu!"
date: 2010-03-18
forum: Installation &amp; Upgrades
---

### Post by davoudi on 2010-03-18
I bought an VAIO 14" Intel Core i3 with recently couldn't wait to install Ubuntu on it. I finally gettinn Ubuntu installed but start having serious problem with everything. First of all, installation was very slow. I installed ubuntu on my older computer and instalation was three-four time faster. Then I receive the message for availability of an driver for the video card. So I proceed with installing the driver. I restart the computer before entering to login window everything gets dark. So I am left with the terminal now. I have problem with wifi too. Can you please help me with this little issue!:)

---

### Post by Ozymandias_117 on 2010-03-18
Try booting into the recovery console terminal, and running 
```
cd /etc/X11/
mv ./xorg.conf ./xorg.conf.bak

```

then rebooting and see if your GUI works.

For wi-fi, when you get your GUI back, you can go to System -> Administration -> Hardware Drivers and you may be able to enable it in there.

---

### Post by benjamimgois on 2010-03-20
Is your laptop the model VGN-FW380AY ? I'm planning to buy this one and use ubuntu on it too.

---

### Post by davoudi on 2010-03-20
> **benjamimgois said:**
> Is your laptop the model VGN-FW380AY ? I'm planning to buy this one and use ubuntu on it too.
It is VPCCW23FDW.

---

### Post by davoudi on 2010-03-20
I just manually remove nvidia driver and I have linux back. I even tried to create edid file but the software crashed, so I change the compatibility to win95 and generate the edid file, but then I receive an error saying that nvida driver not found. I tried other people edid file but the same problem.

---

### Post by davoudi on 2010-03-23
Thanks. With some reading I managed to have my graphic device running well using edid file created by phonix. My wireless is running ok.

---

