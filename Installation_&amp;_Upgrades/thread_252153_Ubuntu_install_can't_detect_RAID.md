---
title: "Ubuntu install can't detect RAID???"
date: 2006-09-06
forum: Installation &amp; Upgrades
---

### Post by xp_newbie on 2006-09-06
I am trying to install Ubuntu on a friend's computer where he has two 40GB IDE drive configured in BIOS as RAID 0+2 stripe.

Ubuntu installation only detects them as two separate physical drives.

I cannot let Ubuntu install proceed because there is some data on an existing partition on that RAID drive.

Am I out of luck?

If not, could you point me to the right source where I can learn how to overcome this problem?

Thanks!

---

### Post by John.Michael.Kane on 2006-09-06
xp_newbie that is a software setup,and most likely your going to have issues getting it installed. you could try moving the data that on the drive you whish to install to over to the other drive or back it up to some other medium. 

Also what is the make model of this motherboard is it intel amd nforce other?

---

### Post by xp_newbie on 2006-09-06
> **SD-Plissken said:**
> that is a software setup,and most likely your going to have issues getting it installed. you could try moving the data that on the drive you whish to install to over to the other drive or back it up to some other medium.Windows can be installed on such a configuration, why can't Linux?

> Also what is the make model of this motherboard is it intel amd nforce other?It is an ASUS A7V333.

Please help since I am trying to convert this guy to Linux and so far the only thing he saw about Linux is this failed attempt...

Thanks!

---

### Post by John.Michael.Kane on 2006-09-06
> **xp_newbie said:**
> Windows can be installed on such a configuration, why can't Linux?
Linux is not windows. 
It is an ASUS A7V333.

Please help since I am trying to convert this guy to Linux and so far the only thing he saw about Linux is this failed attempt...

Thanks!

Linux is not windows. 

Your going to have issues installing ubuntu with the way you have it setup.

Your going to have to turn the raid off in the bios,and install ubuntu to the drive you want.

---

### Post by xp_newbie on 2006-09-06
> **SD-Plissken said:**
> Linux is not windows.I would like to learn more about what you mean by that. Are you suggesting that Linux developers deliberately decided not to support BIOS-based RAID? If so, do you happen to know why?

> **SD-Plissken said:**
> Your going to have issues installing ubuntu with the way you have it setup.Yes, I noticed that.

> **SD-Plissken said:**
> Your going to have to turn the raid off in the bios, and install ubuntu to the drive you want.Is this the only way to go about this? This friend of mine is so scared of Linux that he wants to keep his existing Windows XP partition. Isn't there a way "to eat the cake and have it too"?

(I just managed to install Ubuntu [on a motherboard that was blacklisted]("http://ubuntuforums.org/showthread.php?t=252268"))

Thanks!

---

### Post by klyick on 2007-11-24
Wow. I have never seen a more unhelpful answer on these forums. Could someone who actually knows what they are doing respond?

-Klyick

---

### Post by Cr0n_J0b on 2007-11-24
There are a bunch of issues with runnign the type of RAID that you are trying to run on Linux.  Most of them are related to the way the card handles the RAID calculations.  In some RAID cards, the Card itself does most of the work and just presents to the OS physical volumes that it creates.  With the type of card (chipset) that is usually built into the bios, the heavylifting is left to the operating system.  It just presents the disks as independent disks and helps the OS manage swaping them and general care and feeding.  So, for linux to support this, you would need a drive that did some of that work.  I think, but I'm not sure, that there is something called a FakeRaid driver that might help.  I think that this would act more or less the way Windows acts when it sees disks presented through your type of setup.  I'm not sure how it works though, so you would need to do a little digging first.  I suggest using google to lookup the actual RAID chip your Mobo uses (Nforce, Sil Image, Adaptec etc) and then see if anyone has had experience getting it to run proprely.  It is more than likely that you would need to rebuild the set and format the disks for this to work as well.

Also, you might want to have a look at software RAID.  mdadm is a tool for building and configuring software RAID in linux.  it would allow you to build a wide range of different RAID groups.  The issue is that it's a bit manual and it will use the OS and hardware of your system to do most of the work...it is also usually slower than hardware RAID.

that's my best shot at assistance.

---

### Post by Cr0n_J0b on 2007-11-24
here's a nice link to read.

[http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)

---

### Post by psusi on 2007-11-26
I think you mean raid0, not raid 0+2, which does not exist.  As for that card, it isn't really hardware raid at all; see [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto) for more information and instructions to get it working.  It isn't easy, but can be done.

---

### Post by Cr0n_J0b on 2007-11-26
> **psusi said:**
> I think you mean raid0, not raid 0+2, which does not exist.  As for that card, it isn't really hardware raid at all; see [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto) for more information and instructions to get it working.  It isn't easy, but can be done.


Yeah, I was guessing it was FakeRAID...and I would bet he's trying for 0+1 and the 0+2 was a typo.

By the way, is fakeraid any better than pure software raid?

---

### Post by Pumalite on 2007-11-26
FakeRaid IS pure software Raid.

---

### Post by psusi on 2007-11-29
The only two advantages that fakeraid has over conventional software raid is the ability to boot directly from the array, and the ability to dual boot with windows.

---

