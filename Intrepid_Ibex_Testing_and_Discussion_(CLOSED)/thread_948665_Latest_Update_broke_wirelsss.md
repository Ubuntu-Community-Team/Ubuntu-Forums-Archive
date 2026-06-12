---
title: "Latest Update broke wirelsss"
date: 2008-10-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by zoomy942 on 2008-10-15
So, after updating my tablet this morning, now my wireless card is MIA...

anyone else notice this?

---

### Post by la5lia on 2008-10-15
I got the same problem on my Lenovo N200 laptop.
Updated, and no more wlan :(

---

### Post by ace214 on 2008-10-15
Same problem- Intel PRO/Wireless 2200BG card.

Usually when this happens, people notice it pretty fast, especially if it's going on on Intel cards. Hopefully if we update via ethernet soon it will fix it... Unless someone can identify the offending package to file a bug report.

---

### Post by tholmesm on 2008-10-15
Same problem here with Intel 2200BG card ...

---

### Post by zoomy942 on 2008-10-15
in the network tools, it doesnt even see my wireless card.

---

### Post by AlexBellisBrown on 2008-10-15
Yep, My RTL8187 has dissapeared. Updated to 2.6.24.21 this morning. you guys also?

---

### Post by ace214 on 2008-10-15
> **AlexBellisBrown said:**
> Yep, My RTL8187 has dissapeared. Updated to 2.6.24.21 this morning. you guys also?

The latest generic kernel is 2.6.27... But I'm on 2.6.26-1-rt.

---

### Post by AlexBellisBrown on 2008-10-15
Yep, sorry, forgot to point out im still on Hardy.

---

### Post by tholmesm on 2008-10-15
Just a thought ... but it might be related to this ...

[http://ubuntuforums.org/showthread.php?t=948700](http://ubuntuforums.org/showthread.php?t=948700)

---

### Post by ace214 on 2008-10-15
> **tholmesm said:**
> Just a thought ... but it might be related to this ...

[http://ubuntuforums.org/showthread.php?t=948700](http://ubuntuforums.org/showthread.php?t=948700)

Perhaps, but I don't know if the rt kernel that I'm on is dependent on that package...

---

### Post by Bufke on 2008-10-15
I can confirm this.  here's dmesg.

```
 
iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   33.330686] iwl3945 0000:03:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[   33.330977] firmware: requesting iwlwifi-3945-1.ucode
[   33.466929] iwl3945: iwlwifi-3945-1.ucode firmware file req failed: Reason -2
[   33.466939] iwl3945: Could not read microcode: -2
[   33.467063] iwl3945 0000:03:00.0: PCI INT A disabled
[   33.479523] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   33.479673] iwl3945 0000:03:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[   33.481815] firmware: requesting iwlwifi-3945-1.ucode
[   33.483831] iwl3945: iwlwifi-3945-1.ucode firmware file req failed: Reason -2
[   33.483834] iwl3945: Could not read microcode: -2
[   33.483946] iwl3945 0000:03:00.0: PCI INT A disabled

```

---

### Post by psyke83 on 2008-10-15
> **Bufke said:**
> I can confirm this.  here's dmesg.

```
 
iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   33.330686] iwl3945 0000:03:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[   33.330977] firmware: requesting iwlwifi-3945-1.ucode
[   33.466929] iwl3945: iwlwifi-3945-1.ucode firmware file req failed: Reason -2
[   33.466939] iwl3945: Could not read microcode: -2
[   33.467063] iwl3945 0000:03:00.0: PCI INT A disabled
[   33.479523] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   33.479673] iwl3945 0000:03:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[   33.481815] firmware: requesting iwlwifi-3945-1.ucode
[   33.483831] iwl3945: iwlwifi-3945-1.ucode firmware file req failed: Reason -2
[   33.483834] iwl3945: Could not read microcode: -2
[   33.483946] iwl3945 0000:03:00.0: PCI INT A disabled

```

It's possibly due to pending changes to the firmware packaging.

Once [this]("https://lists.ubuntu.com/archives/intrepid-changes/2008-October/008775.html") package is uploaded, your wireless should work again.

---

### Post by zoomy942 on 2008-10-15
i can confirm this also.  my dsmeg says the same thing

---

### Post by ace214 on 2008-10-15
I don't get that. I get
```
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
firmware: requesting ipw2200-bss.fw
ipw2200: probe of 0000:06:04.0 failed with error -5
```

---

### Post by ace214 on 2008-10-15
> **psyke83 said:**
> It's possibly due to pending changes to the firmware packaging.

Once [this]("https://lists.ubuntu.com/archives/intrepid-changes/2008-October/008775.html") package is uploaded, your wireless should work again.

Here's the change, I think.

> linux-restricted-modules (2.6.27-7.11) intrepid; urgency=low

  [Ben Collins]

  * firmware: Remove all firmware, now provided by linux-firmware

 -- Ben Collins <bcollins@ubuntu.com>  Wed, 15 Oct 2008 07:45:42 -0400

---

### Post by ace214 on 2008-10-15
If you absolutely can't wait to get your wireless working again, the 1.1 debs on this [page]("https://launchpad.net/ubuntu/intrepid/+queue?queue_state=3&queue_text=linux-firmware") worked for me.

This is probably not the recommended way of doing it, but it got mine working again.

---

### Post by zoomy942 on 2008-10-15
i will give it til i elave work today - 5pm mountain time and then i'll get desperate :)

---

### Post by zoomy942 on 2008-10-15
fix has been uploaded.

update away my friends

---

### Post by lifestream on 2008-10-15
Would anyone give me a .deb of this?
:3 I only use wireless (no wired connection) 

Edit: got one in irc. Thank you :D

---

### Post by Eklöf on 2008-10-15
> **zoomy942 said:**
> fix has been uploaded.

update away my friends


I just updated. No wireless for me. But I'm using a mirror. Perhaps there is a delay? What's the official repo to use if I want the latest packages as soon as possible?

---

### Post by ace214 on 2008-10-15
> **Eklöf said:**
> I just updated. No wireless for me. But I'm using a mirror. Perhaps there is a delay? What's the official repo to use if I want the latest packages as soon as possible?
I use us.archive.ubuntu.com. Or you can use the debs I linked to in my previous post.

---

### Post by la5lia on 2008-10-15
> **Eklöf said:**
> I just updated. No wireless for me. But I'm using a mirror. Perhaps there is a delay? What's the official repo to use if I want the latest packages as soon as possible?

Yes it is. I changed to "main server" and I got it fixed !:)
I really was nervous there for a while.
My girlfriend kept nagging me about going back to windows.

Tnx to the team for quick action on the problem.

/Steinar

---

### Post by andreselsuave on 2008-10-15
> So, after updating my tablet this morning, now my wireless card is MIA...

anyone else notice this?
I got the same problem and now i will try to update via ethernet. by the way,, what does MIA mean?

---

### Post by ace214 on 2008-10-15
> **andreselsuave said:**
> by the way,, what does MIA mean?

Missing In Action.... Google it....

---

### Post by iponeverything on 2008-10-16
My wireless was not working after the last update either. I looked at the logs and saw that it could not find the firmware for the card. Once I put the firmware where the driver could find it, everything came up fine.

It reminds me a bit of Mr. Magoo dropping his glasses..

---

### Post by Prosthetic Head on 2008-10-16
No wireles for me on thinkpad X31, just updated an hour ago, so the fix hasn't reached me yet.

---

### Post by xakarix84 on 2008-10-16
bro,
i installed the deb n fixed the wireless problem, however i'm facing this problem.


E: /var/cache/apt/archives/linux-firmware_1.1_all.deb: trying to overwrite `/lib/firmware/aic94xx-seq.fw', which is also in package scsi-firmware


*solved by running recovery mode > repair broken packages

---

### Post by Murrquan on 2008-10-16
I installed the .deb, and that fixed the problem for me too. Thanks!

---

### Post by bobnutfield on 2008-10-16
Got home tonight and found that there are 158 updates for 162mb of download.  Really don't want to lose my wireless.  I was warned that this would only be a partial update, but the only thing that is unchecked is the 2K file for linux-restricted-modules.  Does anyone know that status of this update and whether the wireless breakage has been fixed yet before I do this update?

---

### Post by ace214 on 2008-10-16
> **bobnutfield said:**
> Got home tonight and found that there are 158 updates for 162mb of download.  Really don't want to lose my wireless.  I was warned that this would only be a partial update, but the only thing that is unchecked is the 2K file for linux-restricted-modules.  Does anyone know that status of this update and whether the wireless breakage has been fixed yet before I do this update?

If it's asking to do a partial upgrade, you won't be able to see if linux-firmware is one of the packages...
Be sure you reload the update manager and if you're really scared download the deb that I linked to earlier in the topic. Then if you reboot and it's not working, you've already downloaded the fix.

---

### Post by bobnutfield on 2008-10-16
> **ace214 said:**
> If it's asking to do a partial upgrade, you won't be able to see if linux-firmware is one of the packages...
Be sure you reload the update manager and if you're really scared download the deb that I linked to earlier in the topic. Then if you reboot and it's not working, you've already downloaded the fix.

Thanks for that, but when I go to that page, I don't find a download, just a description of the changelog and checksums in text.  Where is the .deb download?

EDIT: Sorry, just having a really dumb moment...found it.  Did you download the "all-deb" or just the nic .deb?

---

### Post by ace214 on 2008-10-16
> **bobnutfield said:**
> Thanks for that, but when I go to that page, I don't find a download, just a description of the changelog and checksums in text.  Where is the .deb download?

Go [https://launchpad.net/ubuntu/intrepid/+queue?queue_state=3&queue_text=linux-firmware](https://launchpad.net/ubuntu/intrepid/+queue?queue_state=3&queue_text=linux-firmware)

Click the triangle to the left of "linux-firmware (i386)" version 1.1 and you will see 3 debs.

---

### Post by bobnutfield on 2008-10-16
Thanks...don't know if I will need it, but I feel better having it after reading some of these posts.  Thanks for the assistance.

---

### Post by LinuxT60 on 2008-10-16
> **ace214 said:**
> Go [https://launchpad.net/ubuntu/intrepid/+queue?queue_state=3&queue_text=linux-firmware](https://launchpad.net/ubuntu/intrepid/+queue?queue_state=3&queue_text=linux-firmware)

Click the triangle to the left of "linux-firmware (i386)" version 1.1 and you will see 3 debs.

Works like a charm...Thanks!

---

### Post by darco on 2008-10-16
I upgraded today and lost WL...I connected via eth0 and did a partial upgrade which had the linux-firmware. All is good again....
Intel 3945 
darco

---

### Post by LinuxT60 on 2008-10-17
Interesting, I did a update and upgrade at 6 CST or so and it didn't fix it for me.  I definitely had to go the launchpad to get the firmware.

---

### Post by ryawn on 2008-10-26
I had the same problem, and this solution worked for me..

```
sudo apt-get install linux-backports-modules-intrepid
```

Reboot, and you should be good to go. For the record, I'm using Atheros AR5007 wireless.

---

