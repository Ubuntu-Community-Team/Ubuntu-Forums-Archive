---
title: "Hardware RAID0 After Install"
date: 2008-05-09
forum: Installation &amp; Upgrades
---

### Post by mbazdell on 2008-05-09
Hi all. I've searched the forums already and can't find anything really for what I'm looking for. What I have is ubuntu server already installed on hda. What I'm looking to do is simply pop in a Promise Fast Track 2000TX hardware RAID controller, and simply run a RAID0.

Now since the system has been up and running for a few months now, I'm not sure what will happen if I attempt this. My thinking is that it will rename the drives to hdc or something, and all configs pointing to hda will not work. Is this an issue I'm likely to have?

---

### Post by dstew on 2008-05-09
Are you going to add in the Promise controller, or replace the previous controller? If you are just going to add it in, my guess is that it would not cause your hda disk to be renamed. You could try it and see. If it does, remove the Promise controller, then think more about what to do.

To operate the RAID0 from Ubuntu, I think you use the dmraid program.

---

### Post by mbazdell on 2008-05-09
Sorry I should have mentioned that. The system currently has no RAID controllers. It's plugged directly into the primary IDE port on the motherboard.

I figured that's what I was going to do anyways tonight. Didn't know I needed software to run it. I always though Hardware RAID was always controlled on the card and all the config of the drives we setup during the boot. Guess I was wrong...

---

### Post by dstew on 2008-05-09
See the [FakeRaidHowTo]("https://help.ubuntu.com/community/FakeRaidHowto") for information about this type of software-assisted hardware RAID. The controller can assemble the RAID, and when the BIOS is probed it reports the RAID as a single device, so in that sense it is a hardware RAID. However, for RAID-5 anyway, the OS and CPU are needed to do the parity calculations, so there is some software that is needed to maintain the RAID.

---

### Post by mbazdell on 2008-05-12
So I installed the RAID card on the weekend and it did exactly what I thought it would do. It ended up changing HDA to HDE, which is fine because I was able to get it to boot enough to let me change the config files that were pointing at HDA.

However even though the RAID controller is set to mirrored, and it created the array and copied the image and all that jazz, when I boot the server, I get HDE and HDG. Shouldn't it only be HDE?

Again this is hardware RAID0 with 2 identical drives and ext3. I can't seem to find any information on how to get it to actually start RAIDing... I can mount the HDG and it will look the same as HDE, but if I touch a new file, and look on the other drive, it's not there... Odd..

---

### Post by gdmix on 2008-05-12
Are you sure it&#8217;s hardware RAID? If it&#8217;s SATA, you might need DMRAID (as mentioned).

---

### Post by mbazdell on 2008-05-12
Pretty sure. It's a Promise Fasttrack TX2000. It's PCI IDE ATA133. I've searched the net and it appears that this is in fact hardware RAID.

I think I know what I did wrong... I haven't tried anything yet, but I think it's because I set the card to "RAID0" and "Mirrored" rather than "RAID1"... Who knows.. might be all I need to change..

---

### Post by gdmix on 2008-05-13
If you need drivers for an XP/Vista install (should say in manual), it's probably not hardware.

All of the Promise ATA RAID controllers I have seen have been pseudo-RAID.

---

