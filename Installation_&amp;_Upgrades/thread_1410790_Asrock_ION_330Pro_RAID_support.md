---
title: "Asrock ION 330Pro RAID support"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by d41k4n on 2010-02-19
I'm planning to get an Asrock ION 330Pro box running on (Minimal) Ubuntu... Does anyone know if the built-in RAID (it can be set up in the BIOS) will be recognized out-of-the-box?

If so, would it make sense to install additional tools to monitor/control RAID status on OS level?

Any input is greatly appreciated.

---

### Post by toekneewood on 2010-11-09
Not sure what RAID card is fitted.  What I would look out for is "fake RAID" as I think that Ubuntu and possibly Linux will refuse to work with fake RAID.  I would suggest you do a quick google on it before you commit.  

See the following link from the Ubuntu site: [https://help.ubuntu.com/community/FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto")

---

### Post by dddw on 2010-12-17
I got a asrock ion nettop330pro, and only just found out about the raid option :P
I'll test it out for you, since i needed to do a fresh install of 10.10 anyway.

---

### Post by dddw on 2010-12-17
> **dddw said:**
> I got a asrock ion nettop330pro, and only just found out about the raid option :P
I'll test it out for you, since i needed to do a fresh install of 10.10 anyway.

ha sorry, don't got 2 identical drives... wont work.
Great piece of machinery though, never regretted buying it.

I believe the raid controller comes from nvidia
as you can see in [this manual]("http://europe.asrock.com/manual/raid/ION%20330Pro/English.pdf")
I'm also curious if this is fakeraid or realraid

since you need software (windows) to install it I supose it's fakeraid (i could be mistaken though)

Any use in installing another HD then for me to use (fake)raid?

---

### Post by ronparent on 2010-12-17
The nvidia fakeraid is supported. If you are booting windows side by side with ubuntu (or any linux distro) fakeraid is what you need to set up raid drives readable by both windows and ubuntu. Otherwise linux software raid would be more flexible.

Edit: The fakeraid software is dmraid and comes included with the 9.10. 10.04 and 10.10 desktop cd. The software raid program is mdadm and is easily installed from the repositories.

---

